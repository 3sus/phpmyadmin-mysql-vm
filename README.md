#phpMyAdmin-MySQL-VM

How to run MySQL on an Ubuntu Virtual Machine (NAT configuration) and access it through phpMyAdmin on the host OS
----------------------------
1.[Install MySQL and phpMyAdmin on the Ubuntu Server VM]  
  ```bash
  sudo apt update
  sudo apt install mysql-server phpmyadmin
  ```
2.[Configure VirtualBox network settings]  
    
  Forward the host’s port 8080 to the guest’s port 80.
  Unplug and replug the network cable in the VM’s network settings UI to apply changes.

3.[If UFW (firewall) is enabled on the VM, allow MySQL port]  
  ```bash
  sudo ufw allow 3306/tcp
  sudo ufw reload
  ```
4.[Link phpMyAdmin to Apache]  
  ```bash
  sudo ln -s /usr/share/phpmyadmin /var/www/html
  sudo systemctl restart apache2
  ```

5.[Change MySQL root user authentication to use password]  
  ```bash
  sudo mysql -u root
**Inside MySQL shell:**
  ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_new_password';
  FLUSH PRIVILEGES;
  EXIT;
**Then restart MySQL:**
  sudo systemctl restart mysql
  ```

6.[Access phpMyAdmin on host OS]  
  Open your browser and visit:
  http://localhost:8080/phpmyadmin/

Notes:
  Replace 'your_new_password' with a strong password you choose.

  Make sure your VM network is set to NAT for port forwarding to work.

  This setup assumes Apache is your web server.
