FROM node:13-alpine as build-stage

WORKDIR /app

COPY package*.json /app/
RUN npm install

COPY . /app
RUN npm run build


FROM nginx:alpine as production

COPY --from=build-stage /app/nginx.conf /etc/nginx/nginx.conf
COPY --from=build-stage /app/build/ /var/www/html

EXPOSE 3000