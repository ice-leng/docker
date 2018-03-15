FROM nginx:latest

COPY ./sources.list.jessie /etc/apt/sources.list

RUN apt-get update && apt-get install certbot  &&  apt-get install cron
