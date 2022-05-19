# Arquitectura de DasSplit

A continuación, describiremos la arquitectura realiza para la aplicación DasSplit.

## Prerrequisitos
- Docker
- Docker Compose
- [Requisitos de DasSplit Backend](https://github.com/Jose-Gomez-C/DasSplit-Backend/blob/main/README.md)
- [Requisitos de DasSplit Frontend](https://github.com/Jose-Gomez-C/DasSplit-Frontend/blob/main/README.md)
- tener Descargados los siguientes repositorios:
  - [DasSplit DockerCompose](https://github.com/Jose-Gomez-C/DasSplit-DockerCompose)
  - [DasSplit Backend](https://github.com/Jose-Gomez-C/DasSplit-Backend)
  - [DasSplit Frontend](https://github.com/Jose-Gomez-C/DasSplit-Frontend)

## Arquitectura:
![](https://github.com/Jose-Gomez-C/DasSplit-DockerCompose/blob/main/img/Diagrama%20en%20blanco.png?raw=true)

Como vemos en la anterior imagen se creara dos imágenes de Docker en las cuales estará empaquetado el backend y el frontend de nuestra aplicación DasSplit. El frontend se realizara en [JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript) con ayuda de la librería [React](https://es.reactjs.org), la cual se comunicará con nuestra capa de aplicación y para esto utilizaremos el puerto 8080, el backend se creara con [Java](https://www.java.com/es/download/help/whatis_java.html) y el  [framework Spring Boot](https://spring.io/projects/spring-boot) el cual se  comunicara con una base de datos  [MongoDB](https://www.mongodb.com/es)que se encargara de mantener la información de nuestros usuarios. En este caso usaremos [una maquina EC2 de AWS](https://aws.amazon.com/es/ec2/?trk=58ace84c-cd27-448f-9f64-ec1187db737b&sc_channel=ps&sc_campaign=acquisition&sc_medium=ACQ-P|PS-GO|Brand|Desktop|SU|Compute|EC2|LATAMO|ES|Text&s_kwcid=AL!4422!3!590500029748!e!!g!!amazon%20ec2%20vps&ef_id=Cj0KCQjw1ZeUBhDyARIsAOzAqQIA-Kluq3NdQHaUUppxb3u2aA6mrwalDLN1BowpMnndPZmcs_OdWJkaAqwtEALw_wcB:G:s&s_kwcid=AL!4422!3!590500029748!e!!g!!amazon%20ec2%20vps) para almacenar nuestra app en ejecución, pero como usamos Docker podemos desplegar este servicio en cualquier máquina que cumpla con los requisitos.

## Instalación

- Agregar un archivo .env en el backend, cual estén las credenciales de nuestra base de datos, utilizar como nombre de las variables las siguientes:
  ~~~
  USER={Usuario}
  PASSWORD={Contraseña}
  NAME_DATA_BASE={Nombre de la base de datos}
  ~~~
- Ejecutar en el proyecto de DasSplit Backend el siguiente comando:
  ~~~
  $ gradle build
  ~~~
- Agregar un archivo .env en el frontend, cual estén las credenciales de nuestro servicio de FireBase y la ruta de nuestro backend, utilizar como nombre de las variables las siguientes:
  ~~~
  REACT_APP_API_HOST= {}
  REACT_APP_API_PROTOCOL= "http"
  REACT_APP_FIREBASE_API_KEY= {Informacion que se encontrar en Firebase}
  REACT_APP_AUTH_DOMAIN= {Informacion que se encontrar en Firebase}
  REACT_APP_DATABASES_URL= {Informacion que se encontrar en Firebase}
  REACT_APP_PROJECT_ID = {Informacion que se encontrar en Firebase}
  REACT_APP_STORAGE_BUCKET= {Informacion que se encontrar en Firebase}
  REACT_APP_MESSAGING_SENDER_ID= {Informacion que se encontrar en Firebase}
  REACT_APP_APP_ID= {Informacion que se encontrar en Firebase}
  ~~~
- Ir a la ruta de nuestro DasSplit DockerCompose y constuir nuestra app para eso ejecutaremos el siguente comando:
  ~~~
  $ docker compose build
  ~~~
- Si deseamos ejecutar nuestra app por un tiempo corto tiempo ejecutaremos el siguente comando:
  ~~~
  $ docker compose up
  ~~~
- Si lo queremos dejar ejecutando en segundo plano ejecutamos el comando:
  ~~~
  $ docker compose up -d 
  ~~~
## Autor

[José Luis Gómez Camacho](https://github.com/Jose-Gomez-C)

## Licencia
Este proyecto está licenciado bajo la GNU v3.0 - ver el archivo [LICENSE.md](https://github.com/Jose-Gomez-C/DasSplit-DockerCompose/blob/main/LICENSE.md) para más detalles
