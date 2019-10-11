#Base image for openmrs
#Download base image ubuntu 16.04
FROM ubuntu:16.04


LABEL mantainer="Agnaldo Samuel  <asamuel@pedaids.org>"

# Update Ubuntu Software repository
# Install dependencies

RUN add-apt-repository 'deb http://archive.ubuntu.com/ubuntu trusty universe' && \
apt-get update && \
apt-get install -y curl wget apt-utils net-tools mysql-server-5.6 mysql-client-5.6

RUN mv /etc/mysql/my.cnf.fallback  /etc/mysql/my.cnf

COPY my.cnf  /etc/mysql/my.cnf
RUN ls -la /root/
RUN chmod -R 777 /root/.OpenMRS/

ENV CATALINA_HOME /usr/local/tomcat7
ENV PATH $PATH:$CATALINA_HOME/bin


VOLUME ["/usr/local/tomcat7/webapps","/root/"]

WORKDIR /usr/local/tomcat7/

EXPOSE 8080

# Launch Tomcat
CMD ["catalina.sh", "run"]



