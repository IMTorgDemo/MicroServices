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
docker build -t "java_spring" .
docker run -d -p 8888:8888 -p 8000:8000 -v $(pwd)/demoMicroServices/spring/app:/usr/bin/app java_spring


