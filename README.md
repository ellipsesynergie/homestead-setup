# homestead-setup
Fastest way to setup homestead

### Delete folder with previous VM and run those commands (found in https://laravel.com/docs/5.8/homestead)
git clone https://github.com/laravel/homestead.git ~/Homestead &&
cd ~/Homestead &&
git checkout release &&
bash init.sh

### Setup homestead
1. Copy lines inside commands.txt and insert them into after.sh located in Homestead directory.
2. Run vagrant provision
3. Delete added lines in after.sh
4. Add your configuration in homestead.yaml (don't forget MariaDB)
