# Stage 1
FROM node:16-alpine As build

WORKDIR /backend_app

COPY --chown=node:node package*.json ./

RUN npm ci

COPY --chown=node:node . .

RUN npm run build

USER node

# Stage 2
FROM node:16-alpine

WORKDIR /backend_app

COPY --chown=node:node package*.json ./

RUN npm ci --only=production && npm cache clean --force



COPY --chown=node:node --from=build /backend_app/dist ./dist

CMD [ "node", "dist/main.js" ]