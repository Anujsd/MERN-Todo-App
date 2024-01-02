docker network create mern_network

docker run --rm --name mongodb -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=secret -it --network=mern_network -v data:/data/db mongo

docker build -t backend .

docker run -it -p 4040:4040 -v %cd%:/app --network=mern_network backend
docker run -it -p 4040:4040 -v "/mnt/c/Users/admin/Desktop/Development/MERN/Bookstore-MERN/backend:/app" --network=mern_network backend

docker build -t frontend .

docker run -it -p 8000:8000 --rm frontend
docker run -it -p 8000:8000 --rm -v "/mnt/c/Users/admin/Desktop/Development/MERN/Bookstore-MERN/frontend:/app" frontend
