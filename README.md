# homestead-setup
Fastest way to setup homestead

### First step (creation)
1. Delete folder with previous VM 
2. Run following commands (found in https://laravel.com/docs/5.8/homestead)

git clone https://github.com/laravel/homestead.git ~/Homestead &&
cd ~/Homestead &&
git checkout release &&
bash init.sh

### Setup homestead
1. Copy lines inside commands.txt and insert them into after.sh located in Homestead directory.
2. Run vagrant up
3. Run vagrant provision
4. Delete added lines in after.sh
5. Add your configuration in homestead.yaml (don't forget MariaDB)
