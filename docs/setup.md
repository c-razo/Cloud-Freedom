# Setup Guide

## Hardware Requirements

### **1. Your Base Device**
You’ll need a device to act as your server. Here are some options:
- **MacBook Pro or Desktop Computer** (recommended for beginners):
  - Ideal if you’re testing or using this system personally.
- **Raspberry Pi**:
  - A low-cost, energy-efficient option for 24/7 operation.
- **Old PC or Laptop**:
  - Repurpose your existing hardware as a dedicated server.

### **2. Storage Options**
Your storage requirements depend on the size and type of files you’ll store:
- **External Hard Drives**:
  - Affordable and easy to expand (e.g., 1TB drives start at ~$50).
- **Internal Drives** (for PCs):
  - Use SSDs for faster performance or HDDs for larger storage at a lower cost.
- **Network Attached Storage (NAS)**:
  - Best for advanced users requiring expandable, professional-grade storage.

---

## Software Requirements

### **1. Operating System**
Choose an operating system to run your cloud storage software:
- **macOS** (if using a MacBook Pro).
- **Ubuntu or Debian Linux** (ideal for Raspberry Pi or PCs).
- **Windows** (optional but less common for this purpose).

### **2. Cloud Storage Software**
We’ll use **Nextcloud** for this guide. It’s a free, open-source platform that provides:
- File storage and sharing.
- Synchronization across devices.
- Built-in security features.

You can also explore:
- **TrueNAS**: Great for NAS setups.
- **OpenMediaVault**: Lightweight and beginner-friendly.

### **3. Additional Tools**
- **Web Server Software**:
  - **Apache** or **Nginx** (required for hosting Nextcloud).
- **Database**:
  - **MariaDB** or **MySQL** for managing cloud data.
- **SSL Certificate**:
  - Use Let’s Encrypt for secure HTTPS access.

---

## Tools and Equipment

### **Recommended Tools**
- **Router/Internet Connection**: For remote access.
- **Keyboard and Monitor**: For initial setup (if not using a laptop).
- **Uninterruptible Power Supply (UPS)**: Optional but protects your system from power outages.

---

## Ready to Start?
Once you’ve gathered your hardware and software, we’ll walk you through installing and configuring your system in the next section.

## Step-by-Step Setup Instructions

Follow this guide to set up your private cloud storage system. Each step is broken down with clear instructions to make the process as simple as possible.

---

### Step 1: Gather Your Tools

To get started, you'll need the following:
- A dedicated storage device (e.g., an external hard drive or a NAS).
- A computer or Raspberry Pi to act as the server.
- Reliable internet access.

> 📷 **Add Screenshot Here**: A visual of the required hardware setup (e.g., a Raspberry Pi with a connected hard drive) would be helpful.

---

### Step 2: Install Your Operating System

Choose an operating system (e.g., Ubuntu Server or Raspberry Pi OS) and install it on your server device:
1. Download the OS image from the official website.
2. Use a tool like **Rufus** or **Etcher** to create a bootable USB drive.
3. Install the OS on your server device following the on-screen instructions.

> 📷 **Add Screenshot Here**: Include a screenshot of the OS installation process or bootable USB creation.

---

### Step 3: Configure Network Settings

Ensure your server is accessible from your local network:
1. Assign a static IP address to your server.
2. Enable SSH for remote access.

> 📷 **Add Screenshot Here**: Add a screenshot of the network settings configuration page.

---

### Step 4: Install Cloud Storage Software

Choose a cloud storage platform (e.g., Nextcloud, ownCloud) and install it:
1. Update your server:  
   ```bash
   sudo apt update && sudo apt upgrade
   ```
2. Install the required packages:  
   ```bash
   sudo apt install apache2 mariadb-server php libapache2-mod-php
   ```
3. Download and set up the software following the official documentation.

> 📷 **Add Screenshot Here**: Add a visual of the software installation progress or login screen after setup.

---

### Step 5: Test Your Setup

Before proceeding to advanced configurations, test your setup:
1. Access your cloud storage interface through a web browser.
2. Upload a test file and check if it syncs properly across devices.

> 📷 **Add Screenshot Here**: Include a screenshot of the web interface after a successful test.

---

<div style="display: flex; justify-content: space-between;">
  <a href="introduction">&larr; Previous</a>
  <a href="configuration">Next &rarr;</a>
</div>
