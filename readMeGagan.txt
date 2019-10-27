10.How to create Eureka server:
1)Create a spring boot project and add following dependency 
<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>

Better Create it using Spring Initializer(https://start.spring.io)
 and select dependency as Eureka Server.
 
 ----------------------------------------------------------
 Now there might be multiple Eureka servers and they might need to register with themselves
 in real life application to ensure that registery is in sync.
 Also if anyone is down , our applications can communicate with other Eureka servers to 
 fetch url of service.
 
 But right now we have spawned only one Eureka server which will try to find other Eureka servers
 and hence we will get connection refused exception in logs
 To avoid do below:
 ----------------------------------------------------------------
 
 2)Set below properties in application.properties file
 
 a)eureka.client.register-with-eureka=false
#Indicates whether or not this instance should register its information with eureka server for discovery by others. 
#In some cases, you do not want your instances to be discovered whereas you just want do discover other instances.
b)eureka.client.fetch-registry=false
#Indicates whether this client should fetch eureka registry information from eureka server.

3)Add @EnableEurekaServer annotation over your Spring Boot Main class
Now run spring boot application and get Eureka server UI on localhost:8080
On UI you will get instances of service(Eureka clients) and their status
registered by Eureka server

Thereafter read point 11 from readMeGagan movie-info-service
