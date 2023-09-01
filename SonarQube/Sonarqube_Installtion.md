---------------------- SonarQube Installation -----------------------------

````
sudo yum update –y
sudo yum install java-11-amazon-corretto-devel
java -version
````
````
cd /opt
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.9.56886.zip
````
````
unzip sonarqube-8.9.9.56886.zip
````
````
mv sonarqube-8.9.9.56886 sonarqube
````
````
cd sonarqube
````
````
cd logs
````
````
useradd sonaradmin
````
````
passwd sonaradmin
````
````
chown -R sonaradmin:sonaradmin /opt/sonarqube
````
````
su – sonaradmin
````
````
cd /opt/sonarqube/bin
````
````
cd linux-x86-64
````
````
./sonar.sh start
./sonar.sh status
````

http:// server-ip address:9000



                                                  SONARQUBE INTEGRATION ON JENKINS

--> install sonarqube scanner pluggin

--> go to sonarqube --> create project and generate key --> save anywhere

--> manage jenkins --> global tool configuration --> SonarQube Scanner --> home=sonarqube 4.7.0 --> install automatically-->save

--> Manage Jenkins --> Credentials --> add 	secret text --> id: sonarqube password (sonar-user-password) --> save



                                                   SONARQUBE WEBHOOK CREATION
          


Administration - -> Configuration - -> Webhooks - -> 
Name : Jenkinswebhook
URL : http://13.234.30.90:8080/Sonarqube-webhook/
