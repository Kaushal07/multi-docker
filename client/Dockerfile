FROM node:14.14.0-alpine as builder

WORKDIR /usr/app

COPY package.json .

RUN npm install

RUN mkdir /usr/app/node_modules/.cache && chmod -R 777 /usr/app/node_modules/.cache

COPY . .

RUN npm run build


FROM nginx

EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/app/build /usr/share/nginx/html

