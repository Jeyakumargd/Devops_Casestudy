FROM ubuntu:18.04

RUN apt-get update
RUN apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs
RUN mkdir -p /var/app

WORKDIR /var/app
COPY main.js main.js
CMD [ "node", "main.js" ]

EXPOSE 8081
