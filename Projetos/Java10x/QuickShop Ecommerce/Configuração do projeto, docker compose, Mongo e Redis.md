___
- Para iniciar o nosso projeto, vamos no site [Spring Initializr](https://start.spring.io/#!type=maven-project&language=java&platformVersion=3.5.9&packaging=jar&configurationFileFormat=yaml&jvmVersion=21&groupId=dev.java.quickshop&artifactId=quickshop&name=Quick%20Shop&description=Demo%20project%20for%20Spring%20Boot&packageName=dev.java.quickshop&dependencies=web,lombok,data-mongodb,cloud-feign,data-redis,cache,validation);
- Nele vamos fazer as configurações necessárias e baixar o nosso projeto.
- Agora vamos abrir em nosso ***IDE*** de escolha.

### Configurações no application.yaml
- No arquivo ***`application.yaml`***, vamos fazer as seguintes configurações:
```yaml
spring:
	application:
		name: quickshop
	
	data:
		mongodb:
			host: localhost
			port: 27017
			database: quickshopdb
		redis:	
			host: localhost
			port: 6379
			password: sa
	cache:
		redis:
			time-to-live: 60000		
```

### Configurações no docker-compose
- Em nosso arquivo ***docker-compose***, vamos utilizar as seguintes configurações:
```yml
services:  
  mongo:  
    container_name: mongodb  
    image: mongo:4  
    environment:  
      MONGO_DATA_DIR: /data/db  
    ports:  
      - '27017:27017'  
    volumes:  
      - mongo-data:/data/db  
  
  redis:  
    container_name: redis  
    image: redis  
    environment:  
      - ALLOW_EMPTY_PASSWORD=yes  
    ports:  
      - '6379:6379'  
  
volumes:  
  mongo-data:
```
- Desta maneira a nossa aplicação já está configurada perfeitamente para podermos criar os endpoints.