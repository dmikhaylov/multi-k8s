FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
ENV NODE_OPTIONS=--openssl-legacy-provider
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html