# IETI-H2-DATABASE 🗄️

Completando la guia de [Spring Boot With H2 Database](https://www.baeldung.com/spring-boot-h2-database)

## Parte 1️⃣

Agregando las dependencias necesarias para el proyecto.

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>
</dependencies>
```

## Parte 2️⃣

Configurando la base de datos H2.

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
```

Si queremos que la base de datos no se borre al reiniciar la aplicacion, podemos agregar la siguiente linea.

```properties
spring.datasource.url=jdbc:h2:file:/data/demo
```

Esto creara un archivo en la ruta /data/demo

## Parte 3️⃣

Para guardar datos en la base de datos creamos el archivo `data.sql` en la carpeta `src/main/resources` con el siguiente contenido.

```sql
INSERT INTO countries (id, name) VALUES (1, 'USA');
INSERT INTO countries (id, name) VALUES (2, 'France');
INSERT INTO countries (id, name) VALUES (3, 'Brazil');
INSERT INTO countries (id, name) VALUES (4, 'Italy');
INSERT INTO countries (id, name) VALUES (5, 'Canada');
```

## Parte 4️⃣

Accediendo a la consola de H2.

Agregamos la siguiente configuracion en el archivo `application.properties`

```properties
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
spring.h2.console.settings.trace=false
spring.h2.console.settings.web-allow-others=false
```

Ejecutamos la aplicación y accedemos a la consola de H2 en la ruta [http://localhost:8080/h2-console](http://localhost:8080/h2-console)
