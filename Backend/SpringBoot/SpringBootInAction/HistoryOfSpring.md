SpringBoot was released in order to enable end-to-end global continuous delivery via a software platform that
facilitates both extensibility and resiliency.

Spring Timeline

Spring 1.0

- Brought dependency injection and declarative transactions(managing transactions using configuration rather then hard coding in the source code)
  Spring 2.0
- We can use custom XML namespaces for configuration
- Spring 2.5 gave us a much more elegant annotation-oriented dependencyinjection model with the @Component and @Autowired annotations, as well as
  an annotation-oriented Spring MVC programming model.
- No more explicit declaration of application components

- Then with Spring 3.0 we were given a new Java-based configuration alternative to
  XML that was improved further in Spring 3.1 with a variety of @Enable-prefixed
  annotations. For the first time, it become realistic to write a complete Spring
  application with no XML configuration whatsoever. It couldn’t get any better.
- Spring 4.0 unleashed support for conditional configuration, where runtime
  decisions would determine which configuration would be used and which
  would be ignored based on the application’s classpath, environment, and other
  factors. We no longer needed to write scripts to make those decisions at build
  time and pick which configuration should be included in the deployment. How
  could it possibly get any better?
