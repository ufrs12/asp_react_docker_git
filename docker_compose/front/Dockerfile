FROM node:18-alpine as build
WORKDIR /app
COPY ./react/package*.json ./
RUN npm install
COPY ./react .
RUN npm run build

FROM nginx:1.18.0-alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
