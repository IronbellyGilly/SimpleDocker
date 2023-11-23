FROM nginx

USER root

COPY /nginx/nginx.conf /etc/nginx/
COPY server.c /home/
COPY run.sh /home/
WORKDIR /home/

RUN apt-get update; \
    apt install -y gcc spawn-fcgi libfcgi-dev
ENTRYPOINT [ "sh", "./run.sh" ]

