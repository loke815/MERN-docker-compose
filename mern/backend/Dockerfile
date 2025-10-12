<<<<<<< HEAD
# stage first 1;
FROM node:18.9.1-alpine AS builder
WORKDIR /app
COPY package.json package-lock.json* ./ 
RUN npm ci --omit=dev
# stage second 2;
FROM node:18.9.1-alpine
WORKDIR /app
COPY --from=builder /app/node_modules ./node_modules
COPY . .
EXPOSE 5050
CMD ["npm", "start"]

=======
FROM node:18.9.1
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5050
CMD [ "npm","start"]
>>>>>>> 326d25015f241f61f2b849ee11481fe9e5f225c4
