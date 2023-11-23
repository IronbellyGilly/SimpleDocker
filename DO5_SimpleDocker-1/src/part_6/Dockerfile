FROM alpine

COPY /nginx/nginx.conf /etc/nginx/
COPY run.sh /home/

RUN apk update && \
    apk add --no-cache nginx && \
    addgroup nginx root && \
    apk add --no-cache gcc spawn-fcgi fcgi fcgi-dev musl-dev && \
    for i in $(find /* -type d 2> dev/null); do chown -R nginx:nginx $i 2> dev/null; done

USER nginx
WORKDIR /home/
CMD [ "sh", "./run.sh" ]
HEALTHCHECK --interval=1m --timeout=5s --retries=3 CMD curl -f http://localhost/ || exit 1