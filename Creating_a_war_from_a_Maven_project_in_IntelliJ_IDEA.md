# Creating a war from a Maven project in IntelliJ IDEA

* Open the SpringBoot project in IDEA

* Update the MainApplication.java

  ```java
  package com.ams;
  
  import org.springframework.boot.autoconfigure.SpringBootApplication;
  import org.springframework.boot.SpringApplication;
  
  @SpringBootApplication
  public class MainApplication {
      public static void main(String[] args) {
          SpringApplication.run(MainApplication.class, args);
      }
  }
  ```

  to

  ```java
  package com.ams;
  
  import org.springframework.boot.autoconfigure.SpringBootApplication;
  import org.springframework.boot.web.servlet.support.SpringBootServletInitializer;
  import org.springframework.boot.SpringApplication;
  import org.springframework.boot.builder.SpringApplicationBuilder;
  
  @SpringBootApplication
  public class MainApplication extends SpringBootServletInitializer {
      public static void main(String[] args) {
          SpringApplication.run(MainApplication.class, args);
      }
  
      @Override
      protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
          return application.sources(MainApplication.class);
      }
  }
  ```

* Update the pom.xml

  ```xml
  <!-- <name>main</name> -->
  <packaging>war</packaging>
  <!-- <description>Azure Monitoring Suite</description> -->
  ```

* Click the 'Maven Projects' sidebar

* Double click 'clean' in lifecycle folder

* Double click 'package' in lifecycle folder then you will get D:\IdeaProjects\AzureMonitoringSuite\target\main-0.0.1-SNAPSHOT.war