# setp 1
FROM node:16-alpine3.16 as build

WORKDIR /backend_app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
USER node

# step 2
FROM nginx:1.22-alpine
COPY --from=build /backend_app/dist /usr/share/nginx/html