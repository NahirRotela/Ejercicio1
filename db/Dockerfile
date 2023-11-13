FROM mysql:latest

ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=prueba

COPY personas.sql /docker-entrypoint-initdb.d/
