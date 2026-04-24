docker build -t mern-frontend . 

docker build -t mern-backend .

docker run --name frontend --network mern -d -p 5173:5173 mern-frontend

docker run -d   --name backend   --network mern   -p 5050:5050   -e MONGO_URI=mongodb://mongodb:27017/mydb   mern-backend

docker run -d   --name mongodb   --network mern   -p 27017:27017   mongo:latest
