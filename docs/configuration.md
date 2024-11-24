# Configuration

This section walks you through the process of installing and configuring the software required for your private cloud storage system.

---

## Step 1: Install the Operating System

### **Option 1: macOS (MacBook Pro Users)**
If you’re using your MacBook Pro, you can skip this step, as macOS is pre-installed.

### **Option 2: Ubuntu or Debian (for Raspberry Pi or PCs)**
1. Download the latest version of Ubuntu or Debian:
   - Visit [ubuntu.com](https://ubuntu.com) or [debian.org](https://www.debian.org).
2. Create a bootable USB drive:
   - Use **Balena Etcher** (free) to flash the OS image to a USB drive.
3. Install the OS on your device:
   - Boot the system using the USB drive and follow the on-screen instructions.

> 📷 **Add Screenshot Here**: Include an image of the bootable USB creation process or OS installation screen.

---

## Step 2: Install Nextcloud

Nextcloud is the software we’ll use to create your cloud storage system.

### **Option 1: Using Docker (Recommended)**
1. Install Docker:
   - On macOS, run:
     ```bash
     brew install docker
     ```
   - On Ubuntu/Debian, run:
     ```bash
     sudo apt install docker.io
     ```
2. Pull the Nextcloud Docker image:
   ```bash
   docker pull nextcloud
   ```
3. Run the container:
   ```bash
   docker run -d -p 8080:80 --name nextcloud -v nextcloud_data:/var/www/html nextcloud
   ```

> 📷 **Add Screenshot Here**: Add a screenshot of the terminal running the `docker pull` and `docker run` commands.

### **Option 2: Manual Installation**
1. Install prerequisites:
   ```bash
   sudo apt update
   sudo apt install apache2 mariadb-server php libapache2-mod-php php-mysql php-xml php-mbstring php-zip php-intl
   ```
2. Download Nextcloud:
   ```bash
   wget https://download.nextcloud.com/server/releases/nextcloud-XX.tar.bz2
   tar -xvf nextcloud-XX.tar.bz2
   sudo mv nextcloud /var/www/html/
   ```
3. Configure Apache:
   - Create a configuration file for Nextcloud:
     ```bash
     sudo nano /etc/apache2/sites-available/nextcloud.conf
     ```
   - Add the following:
     ```
     <VirtualHost *:80>
         DocumentRoot /var/www/html/nextcloud
         ServerName your-domain.com
         <Directory /var/www/html/nextcloud/>
             Options +FollowSymlinks
             AllowOverride All
             Require all granted
         </Directory>
     </VirtualHost>
     ```
   - Enable the site and restart Apache:
     ```bash
     sudo a2ensite nextcloud.conf
     sudo systemctl restart apache2
     ```

> 📷 **Add Screenshot Here**: Include a screenshot of the Apache configuration or service restart command output.

---

## Step 3: Secure Your System

### **Install an SSL Certificate**
1. Install Certbot:
   ```bash
   sudo apt install certbot python3-certbot-apache
   ```
2. Obtain a certificate:
   ```bash
   sudo certbot --apache
   ```
3. Test your SSL setup by visiting your domain using `https://`.

> 📷 **Add Screenshot Here**: Screenshot the Certbot process showing a successful certificate installation.

---

## Step 4: Access Your Cloud

1. Open your browser and navigate to:
   - `http://localhost:8080` (if running locally).
   - `https://your-domain.com` (if using a domain).
2. Complete the Nextcloud setup wizard:
   - Create an admin account.
   - Configure the database (if prompted).

> 📷 **Add Screenshot Here**: Screenshot the Nextcloud setup wizard and database configuration.

---

### Finished

Congratulations! Your cloud storage system is now up and running.

---

<div style="display: flex; justify-content: space-between;">
  <a href="setup">&larr; Previous</a>
  <a href="security">Next &rarr;</a>
</div>
