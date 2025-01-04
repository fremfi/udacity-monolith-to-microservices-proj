FROM beevelop/ionic:latest AS ionic

WORKDIR /usr/src/app

COPY package*.json ./

ENV NODE_OPTIONS=--openssl-legacy-provider

RUN npm ci -f

COPY . .
RUN ionic build

FROM nginx:alpine

COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html