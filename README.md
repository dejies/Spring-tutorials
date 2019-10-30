# Spring-tutorials
This repo contains basic documents about spring and spring boot

##Spring Boot 

Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run". 

Spring Boot is an opinionated view of the Spring platform and third-party libraries so you can get started with minimum fuss.  

Most Spring Boot applications need very little Spring configuration. 

 

###Features of Spring Boot 

Create stand-alone Spring applications 

Embed Tomcat, Jetty or Undertow directly (no need to deploy WAR files) 

Provide opinionated 'starter' dependencies to simplify your build configuration 

Automatically configure Spring and 3rd party libraries whenever possible 

Provide production-ready features such as metrics, health checks and externalized configuration 

Absolutely no code generation and no requirement for XML configuration 

Spring Initializr 

Spring Initializr provides an extensible API to generate JVM-based projects with implementations for several common concepts: 

Basic language generation for Java, Kotlin and Groovy. 

Build system abstraction with implementations for Apache Maven and Gradle. 

.gitignore support. 

Several hook-points for custom resources generations. 

The various options for the projects are expressed in a metadata model that allows you to configure the list of dependencies, supported JVM and platform versions, etc. 

Spring Initializr also exposes web endpoints to generate an actual project and also serve its metadata in a well-known format to allow third-party clients to provide the necessary assistance. 

Page Break
 

Modules 

Spring Initializr has the following modules: 

initializr-actuator: optional module to provide additional information and statistics on project generation. 

initializr-bom: provides a Bill of Materials for easier dependency management in your project. 

initializr-docs: documentation. 

initializr-generator: core project generation library. 

initializr-generator-spring: optional module defining the conventions for a typical Spring Boot project. Can be reused or replaced by your own conventions. 

initializr-generator-test: test infrastructure for project generation. 

initializr-metadata: metadata infrastructure for various aspects of the project. 

initializr-service-sample: showcases a basic custom instance. 

initializr-version-resolver: optional module to extract version numbers from an arbitrary POM. 

initializr-web: web endpoints for third party clients. 

 

How Spring Boot work? 

Spring Boot automatically configures your application based on the dependencies you have added to the project by using @EnableAutoConfiguration annotation. For example, if MySQL database is on your classpath, but you have not configured any database connection, then Spring Boot auto-configures an in-memory database. 

The entry point of the spring boot application is the class contains @SpringBootApplication annotation and the main method. 

Spring Boot automatically scans all the components included in the project by using @ComponentScan annotation. 

 

Spring Boot Starters 

Handling dependency management is a difficult task for big projects. Spring Boot resolves this problem by providing a set of dependencies for developer's convenience. 

For example, if you want to use Spring and JPA for database access, it is sufficient if you include spring-boot-starter-data-jpa dependency in your project. 

Note that all Spring Boot starters follow the same naming pattern spring-boot-starter- *, where * indicates that it is a type of the application. 

 

 

 

Auto Configuration 

Spring Boot Auto Configuration automatically configures your Spring application based on the JAR dependencies you added in the project. 

For this purpose, you need to add @EnableAutoConfiguration annotation or @SpringBootApplication annotation to your main class file. Then, your Spring Boot application will be automatically configured. 

 

import org.springframework.boot.SpringApplication; 

import org.springframework.boot.autoconfigure.SpringBootApplication; 

  

@SpringBootApplication 

public class HelloWorldApplication { 

   public static void main(String[] args) { 

      SpringApplication.run(HelloWorldApplication.class, args); 

   } 

} 

 

Component Scan 

The first step of defining Spring Beans is by adding the right annotation - @Component or @Service or @Repository. 

However, Spring does not know about the bean unless it knows where to search for it. 

@ComponentScan “tell Spring where to search” for @Component or @Service or @Repository resides. 

The programmer defines the packages that have to be scanned. Once you define a Component Scan for a package, Spring would search the package and all its sub packages for components/beans. 

Page Break
 

If your other packages hierarchies are below your main app with the @SpringBootApplication annotation, you’re covered by implicit components scan. 

If there are beans/components in other packages which are not sub packages of the main package, you should manually add them as @ComponentScan 

 

 

Case 1 

@SpringBootApplication defines an automatic component scan on package  

package com.dejies.springboot.sample; 

@SpringBootApplication 

public class SpringBootSampleApplication {} 

In this case it will scan for all components under com.dejies.springboot.sample and its sub-packages. 

Case 2 

package com.dejies.springboot.sample; 

@ComponentScan({"com.dejies.springboot.sample", 

                "com.dejies.springboot.others"}) 
@SpringBootApplication 

public class SpringBootSampleApplication {} 

What is the difference between @Component and @ComponentScan? 

@Component and @ComponentScan are for different purposes. 

@Component indicates that a class might be a candidate for creating a bean. 

@ComponentScan is searching packages for Components.  
