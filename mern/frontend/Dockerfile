#---------stage 1: build react app--------
#base image
FROM node:18.9.1-alpine AS builder
WORKDIR /app
# Copy package files first to leverage Docker cache
COPY package*.json ./
# Install dependencies (no cache, production only)
RUN npm ci 
COPY . .
# Build optimized production bundle
RUN npm run build
#---------stage 2: serve react app with nginx server--------
FROM node:18.9.1-alpine
WORKDIR /app
# Copy built files only from the previous stage
COPY --from=builder /app/dist ./dist
# Install a lightweight static file server
RUN npm install -g serve
EXPOSE 5173
CMD ["serve", "-s", "dist"]