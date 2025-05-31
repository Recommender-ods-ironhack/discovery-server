# discovery-server

## Descripción

El microservicio discovery-server actúa como servidor Eureka dentro de la arquitectura de microservicios. Su función principal es permitir el **registro y descubrimiento dinámico** de otros servicios, facilitando la escalabilidad y resiliencia del sistema. Los microservicios cliente se registran automáticamente en este servidor y pueden encontrarse entre ellos sin necesidad de conocer sus ubicaciones físicas exactas.

## Características

- **Servidor Eureka:** Permite que otros microservicios se registren y se descubran entre sí dinámicamente.
- **Descubrimiento Dinámico:** Centraliza la información de las instancias disponibles en el sistema.
- **Interfaz Web:** Proporciona una consola accesible vía navegador para visualizar los servicios registrados.

## Tecnologías Utilizadas

- [Spring Boot](https://spring.io/projects/spring-boot)
- [Maven](https://maven.apache.org/)
- [Spring Cloud Netflix Eureka Server](https://cloud.spring.io/spring-cloud-netflix/multi/multi_spring-cloud-eureka-server.html)

## Endpoints

> **Nota:** Este microservicio no expone endpoints personalizados, pero sí proporciona una consola de Eureka.

### Consola Web de Eureka

- **URL por defecto:**  
  [http://localhost:8761](http://localhost:8761)

- **Función:**  
  Muestra los servicios registrados, su estado y sus instancias activas.

## Configuración y Ejecución

### Archivo de Configuración

Dentro de la carpeta `src/main/resources`, crea el archivo `application.properties` con la siguiente configuración:

```properties
# Nombre de la aplicación
spring.application.name=discovery-server

# Puerto del servidor Eureka
server.port=8761
``
## Ejecución del Microservicio

1. **Ejecuta el microservicio:**  
   Ejecuta la clase principal `DiscoveryServerApplication.java` desde tu IDE o mediante la línea de comandos.

2. **Accede a la consola Eureka:**  
   Abre el navegador en [http://localhost:8761](http://localhost:8761) para verificar que el servidor esté en funcionamiento y pueda recibir registros de otros servicios.

## Consideraciones

- Otros microservicios deben estar configurados como **clientes Eureka** (`@EnableEurekaClient`) y apuntar al `discovery-server` mediante la propiedad:

  ```properties
  eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/
```

Asegúrate de iniciar primero el discovery-server antes de los servicios que deben registrarse.