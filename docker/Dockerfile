#FROM php:8.0-apache as base
#COPY . /var/www/html/
#WORKDIR /var/www/html/
#EXPOSE 80

FROM node:14-alpine as builder
WORKDIR /app
COPY . .
RUN npm install

FROM php:8.0-apache
COPY --from=builder /app /var/www/html
WORKDIR /var/www/html
RUN apt-get update && \
    apt-get install -y procps && \
    npm install -g serve
CMD ["npx", "serve", "-s", ".", "-l", "80"]
