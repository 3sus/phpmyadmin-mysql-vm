# phpmyadmin-mysql-vm

How to un mysql on a ubuntu virtual machine (NAT configuration) and access it through phpmyadmin on host OS
----------------------------
1.[Install MySQL and phpMyAdmin on the Ubuntu Server VM]  
  sudo apt install mysql-server && sudo apt install phpmyadmin

2.[Network configuration through virutal box's settings UI]  
  port forward hosts port 8080 to guests port 80 unplug and replug cable

3.[If UFW is enabled on the VM]  
  sudo ufw allow 3306/tcp
  sudo ufw reload

4.[Link phpMyAdmin to Apache]  
  sudo ln -s /usr/share/phpmyadmin /var/www/html
  sudo systemctl restart apache2

5.[Change MySQL Root Authentication to Use Password]  
  sudo mysql -u root
  ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_new_password';
  FLUSH PRIVILEGES;
  EXIT;
  sudo systemctl restart mysql

6.[Visit on host OS]  
  http://localhost:8080/phpmyadmin/
