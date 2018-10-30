# we want to use Node v8.12.0 installed in a alpine Linux image
FROM node:8.12.0-alpine as base

MAINTAINER Razaq Ijaduola

WORKDIR /app
COPY package.json .
COPY yarn.lock .
COPY .docker/nginx.conf .

RUN npm install --silent

# End of dev 
# This stage and beyond is for production and deployment
# build app and serve it via nginx
FROM base as builder

RUN npm install --production
COPY . .
RUN npm run build --production

# Final stage serve via nginx
FROM nginx:alpine

# Set working directory and copy static files from the build stage
WORKDIR /usr/share/nginx/html
COPY --from=base /app/nginx.conf /etc/nginx/nginx.conf
COPY --from=builder /app/build .