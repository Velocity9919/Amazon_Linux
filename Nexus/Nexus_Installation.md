INSTALLING SONATYPE NEXUS


Sonatype Nexus System Requirements


Minimum 1 VCPU & 2 GB Memory
Server firewall opened for port 22 & 8081
OpenJDK 8 or open JDK 11
All Nexus processes should run as a non-root nexus user.

Step 1: Login to your Linux server and update the yum packages. Also install required utilities.
````
sudo yum update -y
sudo yum install wget -y
````
Step 2: Install OpenJDK 1.8
````
sudo yum install java-1.8.0-amazon-corretto-devel -y
java -version
````
````
cd /opt/
wget https://download.sonatype.com/nexus/3/nexus-3.50.0-01-unix.tar.gz
tar -xvf nexus-3.50.0-01-unix.tar.gz
mv nexus-3.50.0-01 nexus
````

Step 5: As a good security practice, it is not advised to run nexus service with root privileges. So create a new user named nexus to run the nexus service.
````
sudo adduser nexus
````
````
sudo passwd nexus
````
````
sudo chown -R nexus:nexus /opt/nexus
````
````
sudo chown -R nexus:nexus /opt/sonatype-work
````
````
vi /etc/sudoers
````
````
nexus ALL=(ALL) ALL
````
````
su - nexus
````
Step 6: Open /opt/nexus/bin/nexus.rc file
````
sudo vi  /opt/nexus/bin/nexus.rc
````
````
run_as_user="nexus"
````
````     
sudo vi /etc/systemd/system/nexus.service
````
````
Unit]
Description=nexus service
After=network.target

[Service]
Type=forking
LimitNOFILE=65536
User=nexus
Group=nexus
ExecStart=/opt/nexus/bin/nexus start
ExecStop=/opt/nexus/bin/nexus stop
User=nexus
Restart=on-abort

[Install]
WantedBy=multi-user.target
````
````
sudo chkconfig nexus on
````
````
sudo systemctl start nexus
````
````
sudo systemctl status nexus
````
visit http://public IP:8081. You will be able to see the nexus homepage

Default username is admin

admin password in /opt/sonatype-work/nexus3/admin.password
````
cat /opt/sonatype-work/nexus3/admin.password
````
````
sudo systemctl restart nexus
````



SETUP NEXUS IN JENKINSJOB


PLUGIN : nexus artifact uploader

newitem --> item name --> maven project  --> ok
Add Build Step --> nexus artifact uploader
Nexus version (NEXUS3)
HTTP
give nexus url : 43.205.209.52:8081
credencials --> ADD
Group Id : ( from source code - pom.xml )
version : 1.0-SNAPSHOT
repository : maven-snapshot
Artifactory id :
file type : war/jar
file : **/*.jar
save and Buildnow

console output failure (if job will fail for that)

go to the console output and search for (building)

Building jar: /var/lib/jenkins/workspace/jenkins-maven-nexus/target/maven-jar-sample-1.0-SNAPSHOT.jar

copy the jar file path and select the job and configure --> paste on file : **/*.jar

Buildnow

now console output will sucessful and file will be deployed in to the nexus artifactory
