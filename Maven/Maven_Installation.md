# Maven installation
----------- Java Installation -----------
````
sudo yum install java-11-amazon-corretto-devel
java -version
````
````
cd /opt
````
````
wget https://dlcdn.apache.org/maven/maven-3/3.9.1/binaries/apache-maven-3.9.1-bin.tar.gz
tar -xvf apache-maven-3.9.1-bin.tar.gz
mv apache-maven-3.9.1 maven
````
````
cd /etc/profile.d/
````
````
vim maven.sh
````
```
# Apache Maven Environment Variables
# MAVEN_HOME for Maven 1 - M2_HOME for Maven 2
export M2_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}
````
````
chmod +x maven.sh
````
````
source /etc/profile.d/maven.sh
````
````
mvn --version
````

------------- Java Home Path ---------------
````
find /usr/lib/jvm/java-11* | head -n 3
````

JAVA_HOME
````
/usr/lib/jvm/java-11-amazon-corretto.x86_64
````
