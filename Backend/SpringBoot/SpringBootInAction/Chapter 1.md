## Chapter 1: BootStarting Spring

    InOrder to create an application using spring you needed ...

- A project structure, complete with a a mvn or gradle build file including required dependencies
- atleast Spring MVC and Servlet API dependencies installed
- A web.xml file that declares Spring's DispatcherServlet(dispatcher handles requests)
- A Spring configuration that enables Spring MVC.
- A web application server like tomcat to deploy the application to
- A controller class that will respond to HTTP requests with “Hello World”.

- All of this is boilerplate(needed in any web application) except for the controller class

In Springboot, all that is needed to run an application is this...
@RestController
class HelloController {
@RequestMapping("/")
def hello() {
return "Hello World"
}
}

- There’s no configuration. No web.xml. No build specification. Not even an application server. This is the entire application. Spring Boot will handle the logistics of executing the application. You only need to bring the application code

### SpringBoot essientals

**automatic configuration**

Before, we had alot of java or xml configuration for dependencies....

e.g ...

@Bean
public JdbcTemplate jdbcTemplate(DataSource dataSource) {
return new JdbcTemplate(dataSource);
}

- The simple bean declaration creates an instance of Jdbc template, injectedwith datasource dependency
  Now we need to configure datasource bean so that the dependency will be met.

- Springboot can reduce this to a 1/4 of the code.

- If Spring boot detects jdbc template in the classpath, it will config it for you

- If Spring Boot detects that you have the H2 database library in your application’s classpath, it will automatically configure an embedded H2 database

**Starter dependencies**

- When using the spring mvc framework we would have to have 8 dependencies in your build

■ org.springframework:spring-core
■ org.springframework:spring-web
■ org.springframework:spring-webmvc
■ com.fasterxml.jackson.core:jackson-databind
■ org.hibernate:hibernate-validator
■ org.apache.tomcat.embed:tomcat-embed-core
■ org.apache.tomcat.embed:tomcat-embed-el
■ org.apache.tomcat.embed:tomcat-embed-logging-juli

- With Springboot, you can add the spring boot web starter depedency, and it will pull all the dependencies.

- You also avoid incompatibility

**CLI**

- You can run applications using the CLI

**The ACTUATOR**

- The actuator is used to inspect the internal workings of the application at runtime

- The Actuator exposes this information in two ways: via web endpoints or via a shell
  interface

**SpringBoot is not** ....

- Not an application server... this comes from the self executable jar files that can run on the cli...

- Spring Boot doesn’t implement JPA, but it does support JPA by auto-configuring the
  appropriate beans for a JPA implementation (such as Hibernate).

- Spring Boot doesn’t employ any form of code generation to accomplish its
  magic. Instead, it leverages conditional configuration features from Spring 4, along
  with transitive dependency resolution offered by Maven and Gradle, to automatically
  configure beans in the Spring application context

## initializing a springboot project with spring initializer

- using spring initializer helps us avoid the ardous process of creating a project structure, creating a build file with all the dependencies and all that from stratch.
44s