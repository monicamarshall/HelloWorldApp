# HelloWorldApp
Simple web application that prints "Hello World!" to a webpage.
Use URL:  http://localhost:8000/sayHello if you decide to run the HelloWorldApp using 
the built-in django sqlite3 webserver.

This application can be run in a docker container.  

The app can be containerized using one of the 3 available docker-compose files.

1. docker-compose-sqlite.yml uses the django built in webserver.

2. docker-compose-gunicorn.yml uses the gunicorn wsgi http channel.

3. docker-compose.yml uses the nginx webserver.

Build a docker container image and run it using the command:
docker-compose up -d --build

To build and run the docker-compose image, you must install 

1. Docker engine.  For centos, use this link:  https://docs.docker.com/engine/install/centos/

2. Install docker-compose with the command: sudo pip install docker-compose

3. CD to the HelloWorldApp top directory where manage.py is located and run the command to 
build and run the docker-compose image: 

docker-compose up -d --build 

Since the docker-compose.yml file exposes the nginx port 1337:80, access the HelloWorldApp at:
http://localhost:1337/sayHello/

To build and run the HelloWorldApp from docker images login into Dockerhub (https://hub.docker.com/) and download the 3 images:
1. monicamarshall/postgres
2. monicamarshall/helloproject-web
3. monicamarshall/helloproject-nginx

You can also open a terminal on your linux box, login into dockerhub using the command: docker login -u <username>, enter you password,
Then issue the 3 docker commands to download the HelloWorldApp images.  After downloading them all, use the command:  docker-compose up
to run the images:

docker pull monicamarshall/helloproject_nginx:latest

docker pull monicamarshall/helloproject_web:latest

docker pull monicamarshall/postgres:11

