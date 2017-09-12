FROM yusufhm/ubuntu
MAINTAINER Yusuf HASAN MIYAN <yusuf.hasanmiyan@gmail.com>

# Install php CLI
RUN apt-get update
RUN apt-get install -qy php7.1-cli php7.1-xml php7.1-curl php7.1-mbstring

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --install-dir=bin --filename=composer
RUN rm composer-setup.php
RUN echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> /etc/bash.bashrc
RUN composer global require hirak/prestissimo
