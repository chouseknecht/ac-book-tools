#Set the base image
FROM centos:latest

# File Author / Maintainer
LABEL maintainer "Your name here!"

# Add Nginx and PHP repos
ADD nginx.repo /etc/yum.repos.d/nginx.repo

# Installing nginx
RUN yum -y update && \
    yum -y install epel-release \
    yum -y install nginx && \
    yum -y --enablerepo=remi,remi-php56 install nginx php-fpm php-common &&\
    yum install -y python-pip python-develop python-setuptools && \
    pip install supervisor

# Add nginx configuration files
ADD nginx.conf /etc/nginx/nginx.conf
ADD default.conf /etc/nginx/conf.d/default.conf

# Add Supervisor configuration file
ADD supervisord.conf /etc/

# Add default index.php
ADD index.php /var/www/index.php

# Expose port 80
EXPOSE 80

# Start Supervisor
CMD ["supervisord", "-n"]
