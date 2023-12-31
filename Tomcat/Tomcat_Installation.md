------------------ Install Apache Tomcat ------------------------

````
sudo yum update –y
sudo yum install java-11-amazon-corretto-devel
java -version
````
````
cd /opt
````
````
wget https://archive.apache.org/dist/tomcat/tomcat-7/v7.0.106/bin/apache-tomcat-7.0.106.tar.gz   
````
````
tar -xvzf apache-tomcat-7.0.106.tar.gz
````
````
mv apache-tomcat-7.0.106 tomcat
````
````
cd tomcat
cd bin
sh startup.sh 
shutdown.sh
````
````
cd conf
````
````
vim tomcat-users.xml
````
1. Update users information in the tomcat-users.xml file
````
<role rolename="manager-script"/>
<role rolename="manager-gui"/>
<role rolename="manager-jmx"/>
<role rolename="manager-status"/>
<role rolename="admin-gui"/>
<user username="tomcat" password="tomcat" roles="manager-script,admin-gui,manager-gui,manager-jmx,manager-status"/>
````
paste end of the script
````
chmod +x /opt/tomcat/bin/startup.sh
````

Check point :

access tomcat application from browser on port 8080  
 
 - http://<Public_IP>:8080

username : tomcat

password : tomcat

----------------------------- Deploy to container Plugin installation ---------------------------------------------

jenkins--> Manage plugin --> available --> deploy to container--> Click Install without restart


Manage Jenkins --> manage Credentials --> add Credentials

username : tomcat

password : tomcat

id : tomcat-user

descripition : tomcat-username-password

click on add

--------------------------------------- DEPLOY WARFILE ON TOMCAT USING TOMCAT --------------------------------------------

source code : https://github.com/ynareshbabu/war-file--tomcat.git

go to the jenkins--> new item --> item name : deploying war file

select maven project --> ok

description : deploying war file on tomcat

source code management : git

Build : pom.xml --> clean install


Post Build Action
   deploy war/ear to a container
   
   WAR/EAR files : **/*.war
   
   contest path : ----
   
   containers : tomcat 7.x remote
               
               credentials : 
               
               tomcat url : http://13.232.221.139:8080/
               
               apply and save
  
  Build now
  
  build is successful
