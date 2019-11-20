# Shared Static Data Service

Shared Static Data Service provides access to static data required by several applications. Static does not strictly imply the data cannot be changed. This service offers a solution to allow CRUD actions to data offered through this service. 

## Pre-Build Tasks
##### Configurations

SharedDataService.java

In the SharedDataService class you will find the WebMvcConfigurer. You will need to modify by adding the urls that you would like to have access to the share data service. If you need to specify a port appended it to the url. 

Ex.
```
@Bean
public WebMvcConfigurer corsConfigurer() {
  return new WebMvcConfigurerAdapter() {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/api/SharedStaticDataServices/**").allowedOrigins(
            "http://someURLsGoHere",
            "http://someOtherUrlGoesHere:80"
        );
    }
  };
}  
```

This will be moved to the application properties soon. From there you will be able to update a single file for configurations.

application.properties

In the application.properties file be sure to update the host, port, username, and password.

Ex.
```
# Database Properties
spring.jpa.hibernate.ddl-auto=create
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
spring.datasource.url=jdbc:mysql://hostname:1234/shared_static_data?useSSL=false

# Development
spring.datasource.username=myUsername
spring.datasource.password=MyP4ssw0rd
```

## Build
##### Maven
To build with Maven, simply run maven's package command:

```
mvn package
```

## Installation
Once the package is successful you should find the war file in the target directory. Install into your tomcat or jetty server.

```
drwxr-xr-x 1 197121        0 Nov 19 23:47 m2e-wtp/
drwxr-xr-x 1 197121        0 Nov 20 14:19 maven-status/
drwxr-xr-x 1 197121        0 Nov 20 14:19 generated-sources/
drwxr-xr-x 1 197121        0 Nov 20 14:20 classes/
drwxr-xr-x 1 197121        0 Nov 20 14:20 static-shared-data-service/
drwxr-xr-x 1 197121        0 Nov 20 14:20 maven-archiver/
-rw-r--r-- 1 197121 28400026 Nov 20 14:20 static-shared-data-service.war
```
