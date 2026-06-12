# Tailscale — Private Mesh VPN

Unlike everything else in this repo, Tailscale runs **natively on the host** (not in Docker). As a subnet router it needs direct access to the host network stack — running it on bare metal is simpler and more reliable than a container with `NET_ADMIN` tricks.

## What it does in this setup

- 🔑 **Private remote access** to the *entire* home network — admin UIs (Portainer, NPM, Pi-hole, Prometheus) are **not** exposed through the Cloudflare Tunnel; they're reachable only via LAN or Tailscale
- 🛰 **Subnet router**: the Pi advertises the home LAN (`192.168.178.0/24`), so your phone/laptop can reach *every* device at home — not just the Pi — without installing Tailscale on each one
- 🔒 Zero open ports (same philosophy as the Cloudflare Tunnel): the connection is outbound, WireGuard-based, end-to-end encrypted

## Install (Raspberry Pi OS / Debian)

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

## Setup as subnet router

```bash
# 1. Allow IP forwarding (required for subnet routing)
echo 'net.ipv4.ip_forward = 1' | sudo tee -a /etc/sysctl.d/99-tailscale.conf
echo 'net.ipv6.conf.all.forwarding = 1' | sudo tee -a /etc/sysctl.d/99-tailscale.conf
sudo sysctl -p /etc/sysctl.d/99-tailscale.conf

# 2. Bring Tailscale up and advertise your LAN subnet
#    (replace with YOUR subnet if it differs)
sudo tailscale up --advertise-routes=192.168.178.0/24

# 3. A login URL is printed — open it and authenticate.
#    No auth key is stored in any config file.
```

## Approve the route (Web UI)

1. Open the [Tailscale admin console](https://login.tailscale.com/admin/machines)
2. Find the Pi → **⋯ → Edit route settings** → approve `192.168.178.0/24`
3. Optional: **⋯ → Disable key expiry** for the Pi, so the server never gets logged out silently

## Use it

- Install the Tailscale app on phone/laptop → log in with the same account → done
- Your devices can now open `http://192.168.178.x:9000` (Portainer etc.) from anywhere, as if at home
- Combine with Pi-hole: in the admin console under **DNS**, add the Pi's Tailscale IP as a nameserver and enable **Override local DNS** — ad blocking + local domain resolution on the go ✨

## Verify

```bash
tailscale status          # all devices + connection state
tailscale ip -4           # the Pi's tailnet IP (100.x.y.z)
```

## Security notes

- **Never commit** auth keys, tailnet device lists, or `tailscale status` output to a public repo
- Use the ACL editor in the admin console to restrict which devices may reach the subnet route — by default, every device in the tailnet can
- The state file lives at `/var/lib/tailscale/tailscaled.state` (contains the node key) — it is host-only and not part of this repo
