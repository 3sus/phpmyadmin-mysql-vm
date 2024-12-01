# phpMyAdmin-MySQL-VM

How to run MySQL on an Ubuntu Virtual Machine (NAT configuration) and access it through phpMyAdmin on the host OS
----------------------------
1.[Install MySQL and phpMyAdmin on the Ubuntu Server VM]  
  ```bash
  sudo apt install mysql-server && sudo apt install phpmyadmin
  ```
2.[Network configuration through VirtualBox's settings UI]  
  Forward the host's port 8080 to the guest's port 80. Unplug and replug the network cable.

3.[If UFW is enabled on the VM]  
  ```bash
  sudo ufw allow 3306/tcp
  sudo ufw reload
  ```
4.[Link phpMyAdmin to Apache]  
  ```bash
  sudo ln -s /usr/share/phpmyadmin /var/www/html
  sudo systemctl restart apache2
  ```

5.[Change MySQL Root Authentication to Use Password]  
  ```bash
  sudo mysql -u root
  ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_new_password';
  FLUSH PRIVILEGES;
  EXIT;
  sudo systemctl restart mysql
  ```

6.[Visit on Host OS]  
  http://localhost:8080/phpmyadmin/
