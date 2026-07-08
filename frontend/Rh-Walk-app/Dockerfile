
#build stage
FROM  node:18-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build

#production stage
FROM nginx:alpine

WORKDIR /app

COPY --from=build /app/dist/rh-walk-app /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


