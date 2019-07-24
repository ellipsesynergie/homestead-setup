# homestead-setup
Fastest way to setup homestead

### First step (creation)
1. Run vagrant destroy
2. If you deleted the homestead folder run following commands (found in https://laravel.com/docs/5.8/homestead)

```bash
git clone https://github.com/laravel/homestead.git ~/Homestead &&
cd ~/Homestead &&
git checkout release &&
bash init.sh
```

### Setup homestead
1. Copy the following lines and insert them into after.sh located in Homestead directory.

```bash
# Basis commands for a new VM

sudo apt-get update

# Java
sudo apt-get install -y default-jre

# Language
sudo locale-gen en_CA.utf8
sudo locale-gen fr_CA.utf8

# xdebug missing configs for all php versions

# Loop on every php version in the directory /etc/php/*
phpVDirs=/etc/php/*
for phpVDir in $phpVDirs
do

        # Keep only php version and cut directory
        phpV=$(echo $phpVDir| cut -d '/' -f 4)

        # condition to make sur it doesn't duplicate
        isInFile=$(cat /etc/php/$phpV/fpm/conf.d/20-xdebug.ini | grep -c "xdebug.remote_host")

        if [ $isInFile -eq 0 ]; then
                 # Create xdebug cli
                 sudo phpenmod -v $phpV xdebug

                # This will add and deletes the following lines in the simlink that link cli and fpm 20-xdebug.ini
                sudo sed -i '/xdebug.remote_connect_back/ d' /etc/php/$phpV/mods-available/xdebug.ini                 #delete
                sudo sed -i '$s/$/\nxdebug.remote_host = 192.168.10.1/' /etc/php/$phpV/mods-available/xdebug.ini      #insert
                sudo sed -i '$s/$/\nxdebug.remote_autostart=1/' /etc/php/$phpV/mods-available/xdebug.ini              #insert

                sudo service php$phpV-fpm restart
        fi
done

sudo service nginx restart
```

3. Run vagrant up
4. Run vagrant provision
5. Add your configuration in homestead.yaml (don't forget MariaDB)
