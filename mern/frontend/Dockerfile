#---------stage 1: build react app--------
#base image
FROM node:18.9.1-alpine AS builder
WORKDIR /app

# Copy package files and install all dependencies (including dev)
COPY package*.json ./
RUN npm ci --include=dev --ignore-scripts
COPY . .
# Build optimized production bundle
RUN npm run build
#---------stage 2: serve react --------
FROM node:18.9.1-alpine
WORKDIR /app

# Install a lightweight static file server
RUN npm install -g serve
# Copy built files only from the previous stage
COPY --from=builder /app/dist ./dist

EXPOSE 3000
CMD ["serve", "-s", "dist"]