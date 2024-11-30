sudo apt update -y
sudo apt list --upgradable
sudo apt upgrade -y
sudo -i passwd
sudo apt install mysql-server -y
sudo su
sudo mysql -u root -p
CREATE USER 'admin'@'localhost' IDENTIFIED BY 'admin';
