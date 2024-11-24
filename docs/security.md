# Security

Securing your cloud storage system is crucial to protect your data from unauthorized access, breaches, and other potential risks. In this section, we’ll cover essential security steps.

---

## Step 1: Create Strong User Accounts

### **1. Use Strong Passwords**
- Your admin and user accounts should have passwords that are at least:
  - 12 characters long.
  - Include a mix of uppercase and lowercase letters, numbers, and special characters.
- Use a password manager like **Bitwarden** or **1Password** to generate and store passwords.

### **2. Avoid Default Accounts**
- Avoid using default usernames like `admin`.
- Create unique usernames for all users.

---

## Step 2: Enable Two-Factor Authentication (2FA)

- Two-factor authentication adds an extra layer of security.
- Steps to enable 2FA in Nextcloud:
  1. Log in as the admin user.
  2. Go to **Settings > Security**.
  3. Enable **Two-Factor Authentication** and follow the instructions.

---

## Step 3: Secure Your Server

### **1. Enable Firewall Rules**
- Use **UFW (Uncomplicated Firewall)** to block unwanted traffic:
  ```bash
  sudo ufw allow 80/tcp
  sudo ufw allow 443/tcp
  sudo ufw enable
  ```
- Verify firewall status:
  ```bash
  sudo ufw status
  ```

### **2. Regular Updates**
- Always keep your software up-to-date:
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```

---

## Step 4: Secure Remote Access

### **1. Use HTTPS**
- Ensure your system uses HTTPS for all connections:
  - Install an SSL certificate (covered in the configuration section).
  - Regularly renew your certificates (e.g., Let’s Encrypt automatically renews certificates).

### **2. Limit Access to Trusted IPs**
- Restrict access to specific IP ranges if applicable:
  ```bash
  sudo nano /etc/apache2/sites-available/nextcloud.conf
  ```
- Add the following within the `<Directory>` block:
  ```
  Require ip YOUR.IP.ADDRESS
  ```

---

## Step 5: Regular Backups

- Back up your data regularly to an external drive or cloud service:
  - Use tools like **rsync** or **Nextcloud’s built-in backup tool**.
  - Example command to back up Nextcloud data:
    ```bash
    rsync -a /var/www/html/nextcloud /path/to/backup/location
    ```

---

## Final Thoughts

By implementing these security measures, you’ll ensure your cloud storage system is safe, reliable, and protected from potential threats. Remember to audit your system periodically to maintain security.

---

<div style="display: flex; justify-content: space-between;">
  <a href="configuration">&larr; Previous</a>
  <a href="multi-user-setup">Next &rarr;</a>
</div>
