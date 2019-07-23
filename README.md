# homestead-setup
Fastest way to setup homestead

# Commands to start-up (documentation in https://laravel.com/docs/5.8/homestead)
# Delete folder with previous VM and run those commands
git clone https://github.com/laravel/homestead.git ~/Homestead
cd ~/Homestead
git checkout release
bash init.sh

# Copy the following lines in after.sh

##############################################################################################################

sudo apt-get update

# Java
sudo apt-get install -y default-jre

# Language
sudo locale-gen en_CA.utf8
sudo locale-gen fr_CA.utf8

# xdebug missing configs 

# 7.1
# FPM
sudo sed -i '$s/$/\nxdebug.scream = 0/' /etc/php/7.1/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.cli_color = 1/' /etc/php/7.1/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.show_local_vars = 1/' /etc/php/7.1/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\n; Used only when remote_connect_back is 0/' /etc/php/7.1/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_host = 192.168.10.1/' /etc/php/7.1/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_autostart=1/' /etc/php/7.1/fpm/conf.d/20-xdebug.ini
# CLI
sudo sed -i '$s/$/\nxdebug.scream = 0/' /etc/php/7.1/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.cli_color = 1/' /etc/php/7.1/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.show_local_vars = 1/' /etc/php/7.1/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\n; Used only when remote_connect_back is 0/' /etc/php/7.1/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_host = 192.168.10.1/' /etc/php/7.1/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_autostart=1/' /etc/php/7.1/cli/conf.d/20-xdebug.ini

sudo service php7.1-fpm restart

# 7.2
# FPM
sudo sed -i '$s/$/\nxdebug.scream = 0/' /etc/php/7.2/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.cli_color = 1/' /etc/php/7.2/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.show_local_vars = 1/' /etc/php/7.2/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\n; Used only when remote_connect_back is 0/' /etc/php/7.2/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_host = 192.168.10.1/' /etc/php/7.2/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_autostart=1/' /etc/php/7.2/fpm/conf.d/20-xdebug.ini
# CLI
sudo sed -i '$s/$/\nxdebug.scream = 0/' /etc/php/7.2/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.cli_color = 1/' /etc/php/7.2/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.show_local_vars = 1/' /etc/php/7.2/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\n; Used only when remote_connect_back is 0/' /etc/php/7.2/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_host = 192.168.10.1/' /etc/php/7.2/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_autostart=1/' /etc/php/7.2/cli/conf.d/20-xdebug.ini

sudo service php7.2-fpm restart

# 7.3
# FPM
sudo sed -i '$s/$/\nxdebug.scream = 0/' /etc/php/7.3/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.cli_color = 1/' /etc/php/7.3/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.show_local_vars = 1/' /etc/php/7.3/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\n; Used only when remote_connect_back is 0/' /etc/php/7.3/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_host = 192.168.10.1/' /etc/php/7.3/fpm/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_autostart=1/' /etc/php/7.3/fpm/conf.d/20-xdebug.ini
# CLI
sudo sed -i '$s/$/\nxdebug.scream = 0/' /etc/php/7.3/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.cli_color = 1/' /etc/php/7.3/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.show_local_vars = 1/' /etc/php/7.3/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\n; Used only when remote_connect_back is 0/' /etc/php/7.3/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_host = 192.168.10.1/' /etc/php/7.3/cli/conf.d/20-xdebug.ini
sudo sed -i '$s/$/\nxdebug.remote_autostart=1/' /etc/php/7.3/cli/conf.d/20-xdebug.ini

sudo service php7.3-fpm restart

# nginx

sudo service nginx restart

##############################################################################################################


# Don't forget to turn on mariaDB (homestead.yaml)
