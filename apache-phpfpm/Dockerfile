FROM ubuntu:14.04
MAINTAINER Yusuf HASAN MIYAN <yusuf.hasanmiyan@gmail.com>

# Run with --build-arg au=1 to get AU apt sources
#ARG au=0
# Run with --build-arg drupal=1 to add the apache vhost config for Drupal
#ARG drupal

# Replace sources for AUS
RUN sed -i 's/archive.ubuntu.com/au.archive.ubuntu.com/g' /etc/apt/sources.list
RUN echo 'Australia/Sydney' > /etc/timezone
RUN cp /usr/share/zoneinfo/Australia/Sydney /etc/localtime

# Add php56 repo
RUN apt-get update
RUN apt-get install -qy software-properties-common python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php

RUN apt-get update
RUN apt-get install -qy python-software-properties apache2 php5.6-fpm supervisor libapache2-mod-rpaf mariadb-client
# Common PHP modules
RUN apt-get install -qy php5.6-cgi php5.6-mysql php5.6-gd php5.6-curl php5.6-cli php5.6-memcache php5.6-mcrypt

RUN a2enmod expires rewrite headers proxy_fcgi
RUN rm -r /var/www/html/*

RUN mkdir -p /var/log/supervisor
RUN mkdir /run/php
# Default timezone
RUN sed -i 's/;date\.timezone.*/date.timezone = Australia\/Sydney/g' /etc/php/5.6/fpm/php.ini
# Set up tcp/ip instead of socket
RUN sed -i s'/listen = \/var\/run\/php5-fpm.sock/listen = 127.0.0.1:9000/' /etc/php/5.6/fpm/pool.d/www.conf
RUN phpenmod mcrypt

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD apache_phpfpm.conf /etc/apache2/conf-enabled/apache_phpfpm.conf
ADD apache_drupal.conf /etc/apache2/conf-enabled/apache_drupal.conf

# Install Drush
RUN php -r "readfile('http://files.drush.org/drush.phar');" > /usr/local/bin/drush
RUN chmod +x /usr/local/bin/drush
RUN drush init -y

EXPOSE 80
CMD ["/usr/bin/supervisord"]