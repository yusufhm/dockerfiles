FROM ubuntu:14.04
MAINTAINER Yusuf HASAN MIYAN, yusuf.hasanmiyan@gmail.com

# Run with --build-arg au=1 to get AU apt sources
ARG au=0
# Run with --build-arg drupal=1 to add the apache vhost config for Drupal
ARG drupal

# Replace sources for AUS
RUN if [ $au -eq 1 ]; then sed -i 's/archive.ubuntu.com/au.archive.ubuntu.com/g' /etc/apt/sources.list; fi

RUN apt-get update
RUN apt-get install -qy apache2 php5-fpm supervisor libapache2-mod-rpaf
# Common PHP modules
RUN apt-get install -qy php5-cgi php5-mysql php5-gd php5-curl php5-cli php5-memcache php5-mcrypt

RUN a2enmod expires rewrite headers proxy_fcgi
RUN rm -r /var/www/html/*

RUN mkdir -p /var/log/supervisor
# Default timezone
RUN sed -i 's/;date\.timezone.*/date.timezone = Australia\/Sydney/g' /etc/php5/fpm/php.ini
RUN php5enmod mcrypt

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD apache_phpfpm.conf /etc/apache2/conf-enabled/apache_phpfpm.conf
ADD apache_drupal.conf ${drupal:+/etc/apache2/conf-enabled/apache_drupal.conf}

EXPOSE 80
CMD ["/usr/bin/supervisord"]