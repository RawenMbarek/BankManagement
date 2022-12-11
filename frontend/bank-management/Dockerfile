### STAGE 1: Build ###
FROM node:12.7-alpine AS build
WORKDIR /usr/src/app
ENV NODE_OPTIONS='--openssl-legacy-provider'
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build --prod

### STAGE 2: Run ###
FROM nginx:1.17.1-alpine
EXPOSE 80
COPY ./nginx.config /etc/nginx/conf.d/default.conf
COPY /dist/icin-bank /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]