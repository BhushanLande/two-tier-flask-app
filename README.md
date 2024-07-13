Docker lab:

Sudo apt update -y 
sudo apt install docker.io -y
git clone https://github.com/BhushanLande/two-tier-flask-app
cd two-tier-flask-app/
cat Dockerfile
cat requirements.txt
sudo usermod -aG docker $USER
newgrp docker
docker ps -a
docker network create twotier
docker login
usename: bhushanlande525@gmail.com
pass: paawd
docker build . -t bhushan525/flaskapp	

docker run -d -p 5000:5000 --network twotier -e MYSQL_HOST=mysql -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_DB=myDb –name flaskapp bhushan525/flaskapp:latest

docker run -d -p 3360:3306 --network twotier -e MYSQL_DATABASE=myDb -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_ROOT_PASSWORD=admin --name=mysql bhushan525/mysql:5.7

docker inspect network twotier
docker exec -it mysql
CREATE TABLE messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT
);
show databases;
user myDb;

select * from messages;
open ec2 public ip with port 5000 and add message
check message again

docker push bhushan525/flaskapp:latest
