# Paso 1 
Creo el archivo db 
configuro el Dockerfile y el archivo sql 
## Realizo los comandos 
```docker build -t mysql-personas -f Dockerfile.mysql .
```
```docker run -d --name mysql-container -p 3306:3306 mysql-personas
```
## Al crear el contenedor compruebo que funcione 
Comandos a ejecutar: 
```mysql -u root -p
```
```mysql> show databases;
```
```mysql>  select * from personas;
```
+-----------+---------+----------+
| Apellidos | Nombres | dni      |
+-----------+---------+----------+
| Rotela    | Nahir   | 45532620 |
+-----------+---------+----------+

# Paso 2 
Creo la carpeta app-Rest
Dentro creo los archivos 
### index.js 
### Dockerfile
Ejecuto los comandos 
```npm init -y
```
```npm i express cors sequelize mysql 2
```
Corro el servidor 
```node index.js
```
CREO LA IMAGEN Y EJECUTO 
```docker build -t rest-service .
```
````docker run -d --name rest-container -p 8080:8080 rest-service
````
# Paso 3 
Creo la carpeta app-Soat
Dentro creo los archivos 
### app.js 
### Dockerfile
### consulta.wsdl
Ejecuto los comandos 
```npm init -y
```
```npm i cors sequelize mysql 2 soap
```
Corro el servidor 
```node index.js
```
CREO LA IMAGEN Y EJECUTO 
```docker build -t swarm_soap_service .
```
````docker run -d --name soap-container -p 8080:8080 swarm_soap_service 
````
# Paso 4
Creo la carpeta app-consumer
Dentro creo los archivos 
### index.html 
### Dockerfile

CREO LA IMAGEN Y EJECUTO 
````docker build -t swarm_front_service .
````

````docker run -d --name front-container -p 8080:8080 swarm_front_service 
````
# Paso 5 
Vuelvo a la carpeta raiz del proyecto y ejecuto 

 ```` docker swarm init
 ````
 ````docker stack deploy -c docker_compose.yml parcial
 ````

Por ultimo en el navegador pongo 
### localhost:80 

Servicio REST
Nombre: 
 Apellido: 
 DNI: 
 Enviar
Servicio SOAP
Listado consultado con SOAP:
ID	Apellidos	Nombres	DNI
1	Rotela	Nahir	45532620
1	Rotela	Nahir	45532620