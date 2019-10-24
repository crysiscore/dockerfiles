#Base image for openmrs
#Download base image ubuntu 16.04
FROM ubuntu:16.04
LABEL mantainer="Agnaldo Samuel  <asamuel@pedaids.org>"


#ENV DEBIAN_FRONTEND noninteractive
#MySQL
ENV MYSQL_PWD password
RUN echo "mysql-server mysql-server/root_password password $MYSQL_PWD" | debconf-set-selections
RUN echo "mysql-server mysql-server/root_password_again password $MYSQL_PWD" | debconf-set-selections

RUN echo "deb http://archive.ubuntu.com/ubuntu trusty universe" >> /etc/apt/sources.list

# Update Ubuntu Software repository
# Install dependencies
# SHELL ["/bin/bash", "-c"]

RUN apt-get update && \
#apt-get install -y software-properties-common && \
#add-apt-repository 'deb http://archive.ubuntu.com/ubuntu trusty universe' && \
#apt-get update && \
apt-get install -y curl wget apt-utils net-tools mysql-server-5.6 mysql-client-5.6


RUN mv /etc/mysql/my.cnf.fallback  /etc/mysql/my.cnf


COPY my.cnf  /etc/mysql/my.cnf

RUN  mkdir /opt/data
RUN apt-get clean && rm -rf  /tmp/* /var/tmp/*

EXPOSE 3306
CMD ["/usr/bin/mysqld_safe"]



