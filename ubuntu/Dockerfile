FROM ubuntu:16.04
MAINTAINER Yusuf HASAN MIYAN <yusuf.hasanmiyan@gmail.com>

# Replace sources for AUS
RUN sed -i 's/archive.ubuntu.com/au.archive.ubuntu.com/g' /etc/apt/sources.list
RUN echo 'Australia/Sydney' > /etc/timezone
RUN cp /usr/share/zoneinfo/Australia/Sydney /etc/localtime

RUN apt-get update
RUN apt-get install -qy software-properties-common python-software-properties aptitude git ssh curl zip unzip
RUN aptitude safe-upgrade -y
