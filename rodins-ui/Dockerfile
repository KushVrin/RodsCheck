# Build stage
FROM node:latest AS build-stage
WORKDIR /app

COPY . .

# Install dependencies and build the React.js code
RUN npm i
RUN npm run build

# Production stage
FROM nginx:latest
COPY --from=build-stage /app/dist/rodins /usr/share/nginx/html
COPY default.conf /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
