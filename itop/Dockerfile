FROM php:7.2-apache

# add helper script
#ADD https://raw.githubusercontent.com/mlocati/docker-php-extension-installer/master/install-php-extensions /usr/local/bin/
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

# install extra packages
RUN apt-get update \
	&& apt-get install -y \
		graphviz \
		mariadb-client \
		unzip \
	&& chmod uga+x /usr/local/bin/install-php-extensions \
	&& install-php-extensions \
		gd \
		ldap \
		mcrypt \
		mysqli \
		soap \
		zip 

# Load iTop files
RUN curl -L -o /tmp/iTop.zip https://gigenet.dl.sourceforge.net/project/itop/itop/2.7.0-2/iTop-2.7.0-2-5689.zip \
	&& unzip /tmp/iTop.zip -d /tmp/ web/* \
	&& mv -v /tmp/web/* /var/www/html/ \
	&& chown -R www-data: /var/www/html/ \
	&& rm -rf /tmp/iTop.zip /tmp/web

# Add default configuration
#COPY php.ini /usr/local/etc/php/php.ini
#COPY config-itop.php /var/www/html/conf/production/config-itop.php
#RUN chown -R www-data: /var/www/html/conf

ENV DB_HOSTNAME="db" DB_PREFIX=""
