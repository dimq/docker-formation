# Étape de build
FROM node:14-alpine as build
WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build

# Étape de production
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
WORKDIR /etc/nginx
COPY ./nginx.conf ./conf.d/default.conf
EXPOSE 80
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
