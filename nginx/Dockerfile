FROM nginx:1.15.5
COPY default.conf /etc/nginx/conf.d/
COPY nginx.conf /etc/nginx/
RUN apt-get update && \
    apt-get install openssl && \
    mkdir -p /etc/nginx/ssl/ && \
    mkdir -p /var/lib/nginx/cache && \
    openssl dhparam -out /etc/nginx/ssl/dhparam.pem 1024
