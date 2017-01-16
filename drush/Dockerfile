FROM yusufhm/composer
MAINTAINER Yusuf HASAN MIYAN <yusuf.hasanmiyan@gmail.com>

# Install drush
RUN composer global require drush/drush
RUN mkdir -p /root/.acquia /root/.drush

ADD acquiacloud/.drush/acapi.drush.inc /root/.drush/acapi.drush.inc
ADD acquiacloud/.drush/cloudapi.acquia.com.pem /root/.drush/cloudapi.acquia.com.pem
RUN chmod 600 /root/.drush/acapi.drush.inc /root/.drush/cloudapi.acquia.com.pem
