FROM dockerfile/java:openjdk-7-jdk
MAINTAINER docker@opentdc.org
ENV VERSION 1.0.0
ENV PLATFORM jre-1.7
ENV HOME /root

# Install ant, apache2, nullmailer
RUN apt-get update && apt-get install -y \
  ant \
  apache2 \
  libapache2-mod-jk \
  nullmailer

# Do not expose port 8080 of Tomcat --> front Tomcat with Apache using AJP
RUN echo "<VirtualHost *:80>" > /etc/apache2/sites-available/000-default.conf \
  && echo "  ServerAdmin webmaster@localhost" >> /etc/apache2/sites-available/000-default.conf \
  && echo "  DocumentRoot /var/www/html" >> /etc/apache2/sites-available/000-default.conf \
  && echo "  LogLevel info" >> /etc/apache2/sites-available/000-default.conf \
  && echo "  ErrorLog \${APACHE_LOG_DIR}/error.log" >> /etc/apache2/sites-available/000-default.conf \
  && echo "  CustomLog \${APACHE_LOG_DIR}/access.log combined" >> /etc/apache2/sites-available/000-default.conf \
  && echo "  JkMount /* ajp13_worker" >> /etc/apache2/sites-available/000-default.conf \
  && echo "</VirtualHost>" >> /etc/apache2/sites-available/000-default.conf \
  && apache2ctl restart

# Get and install opentdc
RUN mkdir --parents $HOME/opt/opentdc
COPY files/apache-tomee-1.7.1-jaxrs.tar.gz $HOME/opt/opentdc/
RUN cd $HOME/opt/opentdc \
  && tar xf apache-tomee-1.7.1-jaxrs.tar.gz \
  && ls -al $HOME/opt/opentdc \
  && rm apache-tomee-1.7.1-jaxrs.tar.gz \
  && ls -al $HOME/opt/opentdc
COPY files/opentdc-services-test.war $HOME/opt/opentdc/apache-tomee-jaxrs-1.7.1/webapps/
VOLUME ["/root/opt/opentdc/apache-tomee-jaxrs-1.7.1/logs", "/root/opt/opentdc/apache-tomee-jaxrs-1.7.1/temp", "/root/opt/opentdc/apache-tomee-jaxrs-1.7.1/work"]
COPY ./docker-entrypoint.sh /
RUN chmod a+x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
EXPOSE 80 8001 8009
CMD cd /root/opt/opentdc/apache-tomee-jaxrs-1.7.1;./bin/catalina.sh run
