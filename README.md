# Demo of MicroServices

These demo microservices configure REST APIs for the following frameworks:
* Plumber (R)
* Flask (Python)
* Spring (Java)

All servers are run from inside docker containers and port 8000.

# Plumber
docker exec -it --user root <container> bash
Rscript index.R
    #(browser) http://127.0.0.1:8000/mean

# Flask
docker exec -it --user root <container> bash
pipenv install
pipenv shell
python server.py
    #(browser) http://127.0.0.1:8000/

# Spring
[dockerfile: java and gradle](https://github.com/keeganwitt/docker-gradle/blob/1fcbfdaa2566e3cf3fb055fbd1342f2aa462bb85/jdk8/Dockerfile)
docker build -t "java_spring" .
docker run -td -p 8888:8888 -p 8000:8000 -v $(pwd):/usr/bin/app java_spring bash
docker exec -it --user root <container>  bash


cd core/
gradle build
java -jar build/libs/gs-spring-boot-0.1.0.jar --server.port=8000
http://127.0.0.1:8000/