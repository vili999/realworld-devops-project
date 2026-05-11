FROM node:22-alpine

WORKDIR /app

COPY package*.json ./
COPY backend/package*.json ./backend/

RUN npm install --workspace backend

COPY backend ./backend

WORKDIR /app/backend

EXPOSE 3001

CMD ["npm", "run", "dev"]