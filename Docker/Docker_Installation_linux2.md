-------------------- Doocker Installation On Amazon Linux2 -----------------------------------------------
````
sudo yum update -y
````
````
yum install java-11-openjdk
````
````
sudo amazon-linux-extras install java-openjdk11 -y
````
````
sudo yum install docker -y
````
````
sudo usermod -a -G docker ec2-user
````
````
newgrp docker
````
````
sudo yum install python3-pip
````
````
sudo pip3 install docker-compose
````
````
sudo systemctl enable docker.service
sudo systemctl start docker.service
sudo systemctl status docker.service
````
````
docker --version
````
````
docker info
````
````
docker compose --version
````
````
sudo find / -name "docker-compose" -ls
````
/usr/local/bin/docker-compose

# if it is not docker compose path you need to add path
echo "$PATH"
export PATH=$PATH:/usr/local/bin
