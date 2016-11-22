FROM yusufhm/ubuntu
MAINTAINER Yusuf HASAN MIYAN <yusuf.hasanmiyan@gmail.com>

# Install php CLI
RUN apt-get update
RUN apt-get install -qy php-cli php-xml

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --install-dir=bin --filename=composer
RUN rm composer-setup.php
RUN echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> /etc/bash.bashrc
