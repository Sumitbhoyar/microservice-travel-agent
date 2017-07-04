# microservice-travel-agent

### Features :
- Maven docker plugin
- build images without dockerfile
- Docker in a multi module project
- docker-compose definition
- [Eureka](https://github.com/Netflix/eureka/wiki)
- [Turbine](https://github.com/Netflix/Turbine/wiki)
- [Hystrix](https://github.com/Netflix/Hystrix/wiki)
- [Zuul](https://github.com/Netflix/zuul/wiki)
- [Config Server](http://www.baeldung.com/spring-cloud-configuration)
### How to run this example :
* build docker images
```
mvn clean install
```
* should display three freshly built docker images
```
docker images
```

* start up all instances
```
docker-compose up
```

* starts a 2nd instance of echo-service
```
docker-compose scale echo-service=2
```

### Once all the services are up, the following URLs will be available

Address | Description
--- | ---
http://<\<docker-host>\>:8761 | Eureka service.
http://<\<docker-host>\>:9090/routes | Zuul route definitions
http://<\<docker-host>\>:9090/api/echo-service/echo | Echo service through Zuul api gateway, looked up from Eureka registry
http://<\<docker-host>\>:9090/api/echo-service/echo/remote-echo | Echo service calling remote echo services
http://<\<docker-host>\>:9090/api/echo-service-by-dns/echo/remote-echo | Echo service through Zuul api gateway, located by DNS entry http://echo-service:9098 


### Useful docker commands :

* Starting multiple echo services
```
docker-compose scale echo-service=3
```

* Replace a running container with the latest version (during development)
```
mvn install
docker-compose stop echo-service
docker-compose up -d echo-service
```

List all images
```
sudo docker images -a
```  

List all containers
```
sudo docker ps -a
```

List all running containers
```
sudo docker ps
``` 
  