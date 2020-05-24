# Creating a jar/war from a Maven project in IntelliJ IDEA

* Open the SpringBoot project in IDEA
* Click the 'Maven Projects' sidebar
* Double click 'package' in lifecycle folder
* java -jar .\main-0.0.1-SNAPSHOT.jar

* If you want a war, configure packaging in pom.xml first:

  ```xml
  <name>main</name>
  <packaging>war</packaging>
  <description>Azure Monitoring Suite</description>
  ```

  