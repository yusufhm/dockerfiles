FROM ubuntu:16.04
MAINTAINER Yusuf HASAN MIYAN <yusuf.hasanmiyan@gmail.com>

ENV TZ Australia/Sydney

# Replace sources for AUS
RUN sed -i 's/archive.ubuntu.com/au.archive.ubuntu.com/g' /etc/apt/sources.list

RUN apt-get update
RUN apt-get install -qy software-properties-common python-software-properties aptitude git ssh curl zip unzip tzdata
RUN aptitude safe-upgrade -y

# Set timezone
RUN echo $TZ > /etc/timezone
RUN rm /etc/localtime && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata && apt-get clean
