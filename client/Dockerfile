FROM node:alpine as BUILDER
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
RUN npm run build

FROM nginx as PUBLISH
EXPOSE 3000
COPY --from=BUILDER /app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
