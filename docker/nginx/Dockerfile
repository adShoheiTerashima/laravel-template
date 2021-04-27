FROM nginx:1.20-alpine

RUN apk update && \
  apk add --update --no-cache --virtual=.build-dependencies g++

COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./conf.d/default.conf /etc/nginx/conf.d/default.conf