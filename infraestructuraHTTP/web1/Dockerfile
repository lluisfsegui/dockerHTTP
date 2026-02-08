FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive

# Evitar problemes amb systemd dins LXC
RUN echo "exit 0" > /usr/sbin/policy-rc.d

# Instal·lar Apache
RUN apt update && apt install -y apache2

# Crear carpetes per als logs
RUN mkdir -p /var/www/com/logs
RUN mkdir -p /var/www/org/logs

# Copiar els VirtualHosts
COPY config/domini.com.conf /etc/apache2/sites-available/domini.com.conf
COPY config/domini.org.conf /etc/apache2/sites-available/domini.org.conf

# Activar els VirtualHosts i desactivar el default
RUN a2ensite domini.com.conf
RUN a2ensite domini.org.conf
RUN a2dissite 000-default.conf

# Copiar els continguts de les webs (segons la teva estructura real)
COPY www/com/ /var/www/com/
COPY www/org/ /var/www/org/

# Donar permisos correctes
RUN chown -R www-data:www-data /var/www/com /var/www/org

# Afegir ServerName global per evitar l’avís
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Exposar el port 80
EXPOSE 80

# Arrencar Apache en primer pla
CMD ["apache2ctl", "-D", "FOREGROUND"]
