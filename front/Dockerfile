FROM node:22-alpine AS dev
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0", "--port", "4200"]

EXPOSE 4200

FROM dev AS build
RUN npm run build


FROM nginx:alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf

# COPY --from=node-22-build /app/dist /usr/share/nginx/html
COPY --from=dev /app/dist /etc/nginx/html/

EXPOSE 8080