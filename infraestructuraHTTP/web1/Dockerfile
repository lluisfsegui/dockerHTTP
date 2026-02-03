FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y nginx && \
    mkdir -p /var/www/html && \
    rm -rf /var/www/html/*

COPY config/nginx.conf /etc/nginx/nginx.conf
COPY www/ /var/www/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
