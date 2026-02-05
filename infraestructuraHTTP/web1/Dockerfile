FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y apache2

# Copiem els VirtualHosts
COPY config/domini.com.conf /etc/apache2/sites-available/domini.com.conf
COPY config/domini.org.conf /etc/apache2/sites-available/domini.org.conf

# Activem els VirtualHosts
RUN a2ensite domini.com.conf
RUN a2ensite domini.org.conf

# Copiem els fitxers web
COPY www/com/ /var/www/com/
COPY www/org/ /var/www/org/

CMD ["apachectl", "-D", "FOREGROUND"]
