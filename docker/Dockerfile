FROM alpine:3.10

LABEL maintainer="rupgautam@gmail.com"

RUN apk update && \
    apk add --no-cache nginx curl && \
    rm /etc/nginx/conf.d/* && \
    mkdir -p /run/nginx/ 

ADD app.conf /etc/nginx/conf.d/
ADD index.html /usr/share/nginx/html/

EXPOSE 80 443
ENTRYPOINT /usr/sbin/nginx -g 'daemon off;'

# Healthz check
HEALTHCHECK CMD curl --fail http://localhost:80/ || exit 1