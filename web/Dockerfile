# Stage 1: Build Angular application
FROM node:latest as build

WORKDIR /usr/local/app

COPY package*.json ./

COPY ./ /usr/local/app/

RUN npm install

WORKDIR /usr/local/app
RUN npm install -g @angular/cli  # Install Angular CLI globally
RUN ng build

# Stage 2: Create production-ready image with NGINX
FROM nginx:latest

COPY --from=build /usr/local/app/dist/ProyectoFinal /usr/share/nginx/html

EXPOSE 80
