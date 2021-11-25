FROM node:12.18.1-alpine as compilation
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run compilation
FROM nginx:1.13.12-alpine as production
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]