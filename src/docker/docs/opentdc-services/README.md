# What is opentdc

@TODO

> [opentdc.org](http://www.opentdc.org)

![logo](https://raw.githubusercontent.com/docker-library/docs/master/opentdc/logo.png)

# How to use this image

## Build this image

    docker build -t opentdc-services:latest .
    
## Run this image

    docker run -d -p 9080:80 -p 9009:8009 -p 9001:8001 --name opentdc-services --link opentdc-opencrx:opentdc-opencrx opentdc-services:latest
    
## Stop container

    docker stop opentdc-services
    
## Start container

    docker start opentdc-services
    
## Inspect logs

    docker logs -f opentdc-services
    docker exec -i opentdc-services cat /root/opt/opentdc/apache-tomee-jaxrs-1.7.1/logs/catalina.yyyy-mm-dd.log
    docker cp opentdc-services:/root/opt/opentdc/apache-tomee-jaxrs-1.7.1/logs/catalina.yyyy-mm-dd.log .

# How to extend this image

Here is an example of a custom Dockerfile which replaces the default tomee.xml by a custom configuration:

    FROM opentdc-services:latest
    MAINTAINER demo@opentdc.org
    COPY ./tomee.xml $HOME/opt/apache-tomee-jaxrs-1.7.1/conf/
