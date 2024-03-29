FROM node:14-alpine as builder
WORKDIR /app
COPY . .
RUN npm install

FROM php:8.0-apache
COPY --from=builder /app /var/www/html
WORKDIR /var/www/html
RUN apt-get update && \
    apt-get install -y procps
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash - && \
    apt-get install -y nodejs
RUN npm install -g serve
CMD ["npx", "serve", "-s", ".", "-l", "80"]
EXPOSE 80