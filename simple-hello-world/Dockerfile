# BUILD STAGE
FROM node:16.15-alpine AS builder

WORKDIR /app

COPY . .

RUN npm install && npm run build

# SERVE BUILD RESULT
FROM nginx:alpine

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=builder /app/build .

EXPOSE 80

ENTRYPOINT ["nginx","-g","daemon off;"]