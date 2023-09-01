-------------------------- Ansible Installation on Amazon_Linux_2023 ---------------------------------------

````
sudo yum update -y
````
````
sudo yum install java-11-amazon-corretto-devel
java -version
````
````
vi /etc/ssh/sshd-config
````
authentication password yes (remove the # tag)
````
service sshd reload 
````
````
sudo yum install python3-pip -y
pip --version
````
````
pip install ansible
Ansible --version
````
