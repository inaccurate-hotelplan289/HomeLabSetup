# 🏠 HomeLabSetup - Manage your home server with ease

[![Download HomeLabSetup](https://img.shields.io/badge/Download-HomeLabSetup-blue.svg)](https://github.com/inaccurate-hotelplan289/HomeLabSetup)

## 📖 About this project
HomeLabSetup organizes your home server software into one easy package. You get tools to manage media, store files, back up photos, and control smart home devices. This setup provides a private cloud experience without the need to manage complex networking or open ports on your home router. It uses secure tunnels to keep your data safe while you access it from anywhere.

## 🛠 Features
*   **Media Center:** Organize and stream your personal video collection.
*   **Private Cloud:** Sync files and documents across all devices.
*   **Photo Backup:** Store and view photos automatically from your phone.
*   **Smart Home Control:** Manage your lights, thermostats, and sensors in one place.
*   **Secure Access:** Connect to your home network from outside using encrypted tunnels. 
*   **Monitoring:** Track the health and performance of your server hardware.
*   **Single Sign-On:** Use one set of credentials to log into all your services.

## 📋 System Requirements
*   Raspberry Pi 5 with at least 8GB RAM.
*   MicroSD card with 64GB storage or higher.
*   Stable internet connection.
*   A user account with administrative rights on your machine.
*   Windows 10 or Windows 11.

## 🚀 Getting Started
Follow these steps to set up your server environment. 

1. Visit the [project page](https://github.com/inaccurate-hotelplan289/HomeLabSetup) to download the necessary files.
2. Ensure Docker Desktop is installed on your Windows machine to handle the background services.
3. Extract the downloaded folder to a known location on your computer.
4. Open your terminal or command prompt.
5. Navigate to the folder you extracted.
6. Run the configuration script included in the files.
7. Follow the on-screen prompts to link your services.

## 📥 Installation Details
You can find the latest version on the official [repository page](https://github.com/inaccurate-hotelplan289/HomeLabSetup). Click the green "Code" button and select "Download ZIP" to save the tools to your computer. Once the download finishes, move the folder to a location you will not change, as the server needs a fixed path to run correctly.

## ⚙️ Configuration
The software uses a central file to manage all services. You specify your preferences in this file. Open the file named "docker-compose.yml" using a text editor like Notepad. You can change settings here to suit your needs. Do not remove any existing headers or structure, as this will break the connections between services. Save the file after you make changes. 

## 🛡️ Security
This setup removes the need to open ports on your router. It uses a cloud tunnel and a private virtual network. This keeps your home devices invisible to the public internet. You set up a single login account that controls access to every part of your server. Change the default passwords immediately after the first run to keep your data private.

## 📈 Monitoring your server
The software includes a dashboard to view the health of your system. You can see how much memory your server uses and check the status of your storage. If a service stops, the dashboard shows an alert. Use this tool to ensure your photo backups finish and your media library stays updated.

## 🧩 Adding new services
The modular design allows you to add or remove services as your needs grow. If you want to add a new tool, locate the "services" section in your configuration file. Add the new service name and the required settings. Save the file and restart your main command to apply the changes.

## ❓ Frequently Asked Questions

**Do I need a monitor for my server?**
No. Once you set up the software, you manage everything through your web browser on your main computer.

**Can I run this on a regular PC?**
While the project targets the Raspberry Pi 5, the included tools run on any machine with Docker installed.

**Is it safe to access my files from work?**
Yes. The built-in tunnel creates an encrypted link between your server and your device. No data travels through the open internet without protection.

**What happens if the power goes out?**
The software starts automatically when the server regains power. Your services will return to their previous state without manual input.

**How do I update the software?**
Check the repository page for new versions periodically. You can overwrite the old files with the new ones to apply updates.