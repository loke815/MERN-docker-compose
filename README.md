## Docker Setup

This project includes optimized Docker images for frontend and backend. You can run the entire stack locally using Docker Compose.

### Run from Docker Hub

Pull the production-ready images and run:

```bash
docker-compose up -d

## run on locally ---
Frontend: http://localhost:5173
Backend API: http://localhost:5050


If you want to build your own images:

# Build backend
docker build -t <your-username>/mern-backend:prod ./backend

# Build frontend
docker build -t <your-username>/mern-frontend:prod ./frontend

# Start services
docker-compose up -d

s
