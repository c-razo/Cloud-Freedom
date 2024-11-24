# Troubleshooting

Even with the most well-prepared setup, issues can arise. This section provides solutions to common problems you might encounter while building or using your private cloud storage system. Organized by categories, it ensures you can quickly find the help you need.

---

## Common Installation Issues

### **Problem: Cannot Access Server After Installation**
- **Solution**:
  1. Ensure the server is powered on and connected to the network.
  2. Check your static IP address settings.
  3. Verify the server’s firewall rules to confirm port `80` (HTTP) and port `443` (HTTPS) are open:
     ```bash
     sudo ufw status
     ```

> 📷 **Add Screenshot Here**: Show a terminal with `ufw status` output confirming open ports.

---

### **Problem: OS Installation Fails**
- **Solution**:
  1. Ensure the bootable USB drive is properly created.
  2. Use tools like **Balena Etcher** to flash the OS image and verify the integrity of the image file.
  3. Check that the BIOS/UEFI is configured to boot from the USB device.

> 📷 **Add Visual Here**: Include an image showing BIOS/UEFI settings for boot order.

---

## Configuration Errors

### **Problem: Nextcloud Installation Fails**
- **Solution**:
  1. Ensure all prerequisites are installed (e.g., Apache, PHP, MariaDB).
  2. Check logs for specific errors:
     ```bash
     sudo tail -f /var/log/apache2/error.log
     ```
  3. Verify file permissions:
     ```bash
     sudo chown -R www-data:www-data /var/www/html/nextcloud
     sudo chmod -R 755 /var/www/html/nextcloud
     ```

> 📷 **Add Screenshot Here**: Provide an example of the Nextcloud setup screen or error logs.

---

## Sync and Access Problems

### **Problem: Mobile App Cannot Connect to Server**
- **Solution**:
  1. Confirm the URL is correct (e.g., `https://your-domain.com` or `http://your-local-ip:8080`).
  2. Verify the server is reachable from the mobile network.
  3. Ensure the SSL certificate is valid for secure connections.

> 📷 **Add Visual Here**: Show the Nextcloud app connection screen with a successful connection.

---

### **Problem: Files Not Syncing**
- **Solution**:
  1. Check the sync settings in the Nextcloud app.
  2. Ensure sufficient storage is available on the server and device.
  3. Restart the Nextcloud sync client or mobile app.

> 📷 **Add Screenshot Here**: Provide an image of the sync settings in the app.

---

## Security Concerns

### **Problem: SSL Certificate Not Working**
- **Solution**:
  1. Verify Certbot is installed and functioning:
     ```bash
     sudo certbot renew --dry-run
     ```
  2. Check that the Apache configuration includes the SSL module:
     ```bash
     sudo a2enmod ssl
     sudo systemctl restart apache2
     ```

> 📷 **Add Screenshot Here**: Show a secure connection with a valid SSL certificate in a browser.

---

## Best Practices for Troubleshooting
1. Keep all software up-to-date with regular updates:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. Regularly back up configuration files and data to avoid data loss.
3. Document any custom configurations or changes for future reference.

> 📷 **Add Diagram Here**: A troubleshooting workflow diagram for common issues.

---

## FAQs
**Q: How do I reset a forgotten admin password?**  
**A:** Use the Nextcloud CLI tool to reset the password:
```bash
sudo -u www-data php /var/www/html/nextcloud/occ user:resetpassword admin
```

**Q: Can I access my cloud storage outside my local network?**  
**A:** Yes, by using port forwarding on your router or setting up a dynamic DNS service.

---

<div style="display: flex; justify-content: space-between;">
  <a href="how-to-use">&larr; Previous</a>
  <a href="index">&larr; Home</a>
</div>
