# What is openCRX

openCRX is an open source CRM solution that meets the needs of organizations requiring multifunctional, enterprise-wide coordination of sales generation, sales fulfillment, marketing and service activities to customers, partners, suppliers or intermediaries.

> [opencrx.org](http://www.opencrx.org)

![logo](https://raw.githubusercontent.com/docker-library/docs/master/opencrx/logo.png)

# How to use this image

## Build this image

    docker build -t opentdc-opencrx:latest .
    
## Run this image

    docker run -d -p 8080:80 -p 8009:8009 -p 1143:1143 -p 1389:1389 -p 8001:8001 --name opentdc-opencrx opentdc-opencrx:latest
    
## Stop container

    docker stop opentdc-opencrx
    
## Start container

    docker start opentdc-opencrx
    
## Inspect logs

    docker logs -f opentdc-opencrx
    docker exec -i opentdc-opencrx cat /root/opt/opencrx/apache-tomee-webprofile-1.7.1/logs/catalina.yyyy-mm-dd.log
    docker cp opentdc-opencrx:/root/opt/opencrx/apache-tomee-webprofile-1.7.1/logs/catalina.yyyy-mm-dd.log .

# How to extend this image

Here is an example of a custom Dockerfile which replaces the default tomee.xml by a custom configuration:

    FROM opentdc-opencrx:latest
    MAINTAINER demo@opencrx.org
    COPY ./tomee.xml $HOME/opt/opencrx/apache-tomee-webprofile-1.7.1/conf/
