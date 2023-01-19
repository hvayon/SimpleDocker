FROM nginx:latest
USER root
WORKDIR /home/
COPY ./server/nginx/nginx.conf /etc/nginx/nginx.conf
COPY ./server/main.c /home/main.c
COPY ./start.sh /home/start.sh
RUN apt-get update; \
    apt-get install -y gcc spawn-fcgi libfcgi-dev; \
    chmod 777 start.sh
ENTRYPOINT ["./start.sh"]