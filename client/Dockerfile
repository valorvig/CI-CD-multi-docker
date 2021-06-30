FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
# overwrite the default
COPY ./nignx/default.conf /etc/nginx/conf.d/default.conf
# according to the default.conf file
COPY --from=builder /app/build /usr/share/nginx/html

