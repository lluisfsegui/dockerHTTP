FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y apache2

COPY config/domini.com.conf /etc/apache2/sites-available/domini.com.conf
COPY config/domini.org.conf /etc/apache2/sites-available/domini.org.conf

RUN mkdir -p /var/www/appave/logs \
    && mkdir -p /var/www/isitechorg/logs \
    && mkdir -p /srv/www/appave/imatges

COPY www/com/ /var/www/appave/
COPY www/org/ /var/www/isitechorg/

RUN a2ensite domini.com.conf
RUN a2ensite domini.org.conf
RUN a2dissite 000-default.conf

CMD ["apachectl", "-D", "FOREGROUND"]

