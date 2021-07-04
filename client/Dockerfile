FROM node:13-slim as build

WORKDIR /frontend

COPY package*.json /frontend/

RUN npm install 

COPY . /frontend/

RUN npm run build

# Nginx
FROM nginx:1.16.0-alpine
COPY --from=build /app/build /usr/share/nginx/html
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d

EXPOSE 3000

CMD [ "nginx" ]
CMD ["npm", "start"]