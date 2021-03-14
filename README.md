# K8S Guacamole

![banner](assets/k8s-guacamole-banner.png)

Apache Guacamole is a clientless HTML5 web based remote desktop gateway that makes it easy to access remote servers and desktops through a web browser. It supports standard protocols like VNC, RDP, and SSH.

In this repository, we are going to learn how to setup Guacamole web-based remote desktop access tool on Kubernetes server.

You can see below a simple demo of Guacamole :

[![Watch the video](assets/k8s-guacamole-preview.png)](https://youtu.be/AjuHJHtd4zU)

## Install 


```bash

Создаем БД guacamole_db

Генерируем скрипт со схемой данных
docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --postgres > initdb.sql

Копируем и выполняем на сервере БД
pbcopy < initdb.sql

Create a user for Guacamole within PostgreSQL with access to the tables and sequences of this database, such as guacamole_user.

CREATE USER guacamole_user WITH PASSWORD 'some_password';

GRANT SELECT,INSERT,UPDATE,DELETE ON ALL TABLES IN SCHEMA public TO guacamole_user;

GRANT SELECT,USAGE ON ALL SEQUENCES IN SCHEMA public TO guacamole_user;


kubectl apply -f 01-namespace.yaml  

kubectl apply -f 07-daemon-deployement.yaml

kubectl apply -f 06-daemon-service.yaml 

kubectl apply -f configmap.yaml 

kubectl apply -f 09-app-deployment.yaml

kubectl apply -f 08-app-service.yaml 
```
