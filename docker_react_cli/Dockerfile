# we want to use Node v8.12.0 installed in a alpine Linux image
FROM node:8.12.0-alpine

MAINTAINER Razaq Ijaduola

RUN npm install -g create-react-app \
                   create-react-native-app \
                   react-native-cli

# Create app directory and use it as the working directory
RUN mkdir /app
WORKDIR /app
ADD . /app