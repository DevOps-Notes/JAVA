# Deploying SpringBoot Based WAR Application to Docker

```sh
# Pull Image
docker pull tomcat

# Start a container
docker run -d -p 8088:8080 tomcat

# Enter the container
docker exec -it 35 /bin/bash

# Enable default welcome page & Visit http://127.0.0.1:8088
rmdir /usr/local/tomcat/webapps && mv /usr/local/tomcat/webapps.dist /usr/local/tomcat/webapps

# Upload war file, it will be automatically unzipped and started by Tomcat.
docker cp D:\IdeaProjects\AzureMonitoringSuite\target\main-0.0.1-SNAPSHOT.war 35:/usr/local/tomcat/webapps
```

