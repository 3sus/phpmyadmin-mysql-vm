# phpmyadmin-mysql-vm


----------------------------
1.sudo apt install mysql-server && sudo apt install phpmyadmin

2.port forward hosts port 8080 to guests port 80 unplug and replug connection

3.check if UFW blocks anything

4.sudo ln -s /usr/share/phpmyadmin /var/www/html
  sudo systemctl restart apache2

5.sudo mysql -u root
  ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_new_password';
  FLUSH PRIVILEGES;
  EXIT;
  sudo systemctl restart mysql
