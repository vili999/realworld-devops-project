FROM node:22-alpine AS dependencies

WORKDIR /app

COPY package*.json ./
COPY backend/package*.json ./backend/

RUN npm install --workspace backend


FROM node:22-alpine

WORKDIR /app

COPY --from=dependencies /app/node_modules ./node_modules
COPY package*.json ./
COPY backend/package*.json ./backend/

COPY backend ./backend

WORKDIR /app/backend

EXPOSE 3001

CMD ["npm", "run", "dev"]