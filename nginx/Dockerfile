FROM nginx:latest

COPY ./sources.list.jessie /etc/apt/sources.list

RUN apt-get update

COPY ./vhosts /etc/nginx/conf.d
