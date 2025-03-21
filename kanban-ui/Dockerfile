FROM node:12.7-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx:1.17.1-alpine

COPY default.conf /etc/nginx/conf.d/default.conf

COPY --from=build /app/dist/kanban-ui /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]