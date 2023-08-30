# Jenkins Installation Steps
--------- Java Installation --------
````
sudo yum install java-11-amazon-corretto-devel
java -version
````
````
find /usr/lib/jvm/java-11* | head -n 3
````
/usr/lib/jvm/java-11-amazon-corretto.x86_64
````
vi ~/.bash_profile
````
````
JAVA_HOME=/usr/lib/jvm/java-11-amazon-corretto.x86_64
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH
````
````
source .bash_profile
````
````
echo $PATH
````
--------- Install Jenkins ------------
````
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
````
````
sudo systemctl daemon-reload
````
````
sudo yum upgrade
````
````
sudo yum install jenkins
````
````
sudo systemctl enable jenkins
````
````
sudo systemctl start jenkins
````
````
sudo systemctl status jenkins
````
