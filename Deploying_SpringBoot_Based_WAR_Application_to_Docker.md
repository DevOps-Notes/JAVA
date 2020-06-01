# Deploying SpringBoot Based WAR Application to Docker

* Install Maven

  ```sh
  yum -y install java-1.8.0-openjdk-devel
  wget https://mirror.bit.edu.cn/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip
  unzip -q apache-maven-3.6.3-bin.zip
  vim /etc/profile
  #
  export MAVEN_HOME=/root/apache-maven-3.6.3
  export PATH=$MAVEN_HOME/bin:$PATH
  #
  . /etc/profile
  mvn -version
  ```

* Upload the SpringBoot project (whole folder) to server, then build it with Maven

  ```sh
  cd AzureMonitoringSuite/
  mvn clean install
  mv /root/.m2/repository/com/ams/main/0.0.1-SNAPSHOT/main-0.0.1-SNAPSHOT.war /root/ROOT.war
  ```

* Deploy the war to Docker

  ```sh
  # Pull Image
  docker pull tomcat
  
  # Start a container
  docker run -d -p 8080:8080 tomcat
  
  # Enter the container, empty the webapps folder
  docker exec -it 35 /bin/bash
  rm -rf /usr/local/tomcat/webapps/*
  exit
  
  # Upload war file, it will be automatically unzipped and started by Tomcat.
  docker cp /root/ROOT.war 35:/usr/local/tomcat/webapps
  
  # Wait for a minute, then you may visit http://ip:8080
  ```

  

