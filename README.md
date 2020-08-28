# HelloWorldApp
Simple web application that prints "Hello World!" to a webpage.
Use URL:  http://localhost:8000/sayHello if you decide to run the HelloWorldApp using 
the built-in django sqlite3 webserver.   (python manage.py runserver).

This application can be run in a docker container.  

The app can be containerized using one of the 3 available docker-compose files.

1. docker-compose-sqlite.yml uses the django built in webserver.

2. docker-compose-gunicorn.yml uses the gunicorn wsgi http wsgi channel.

3. docker-compose.yml uses docker-compose.yml to run the web image spinning up nginx and the database is separate containers.

Build a docker container image and run it using the command:
docker-compose up -d --build

After running docker-compose up -d --build, make sure to run the following 3 commands:

1. PS C:\data\minikubeTests\HelloWorldApp> docker-compose exec web python manage.py collectstatic

2. PS C:\data\minikubeTests\HelloWorldApp> docker-compose exec web python manage.py migrate --run-syncdb  (We don't need to run this command because the app does not read/write to the db)

3. PS C:\data\minikubeTests\HelloWorldApp> docker-compose exec web python manage.py createsuperuser

Run PS C:\data\minikubeTests\HelloWorldApp> docker-compose logs -f  to view the logs.

To build and run the docker-compose image, you must install 

1. Docker engine.  For centos, use this link:  https://docs.docker.com/engine/install/centos/

2. Install docker-compose with the command: sudo pip install docker-compose

3. CD to the HelloWorldApp top directory where manage.py is located and run the command to 
build and run the docker-compose image: 

docker-compose up -d --build  (by default it looks for a deployment file called docker-compose.yml, otherwise use the -f option if the docker-compose file has a different name.)

Port 1337 is specified in docker-compose.yml file
Access helloworldapp at:

http://helloworld.info:1337/sayHello   or   http://localhost:1337/sayHello (an ingress url helloworld.info is added to ALLOWED_HOSTS in settings file.  Make sure to add helloworld.info to your hosts file.

Access helloworldapp admin console:

http://helloworld.info:1337/admin/   or http://localhost:1337/admin/

To build and run the HelloWorldApp from docker images login into Dockerhub (https://hub.docker.com/) and download the web image:

monicamarshall/helloproject-web

You can also open a terminal on your linux box, login into dockerhub using the command: docker login -u <username>, enter you password,
Then issue the docker commands to download the HelloWorldApp web image.  Then use the command:  docker-compose up
to run the images:

docker pull monicamarshall/helloproject_web:latest

