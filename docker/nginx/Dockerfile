FROM nginx:1.20-alpine

RUN apk update && \
  apk add --update --no-cache --virtual=.build-dependencies g++

COPY ./docker/nginx/nginx.conf /etc/nginx/nginx.conf
COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf