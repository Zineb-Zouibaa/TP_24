# Étape 1 : construction de l'application Angular
FROM node:14.15.0-alpine as builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod

# Étape 2 : création de l'image finale avec Nginx
FROM nginx:alpine
COPY --from=builder /app/dist/smart-home /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
