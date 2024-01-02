# Run This App Using Docker

#### Run This App

```
docker compose up
```

#### Stop This App

```
Ctrl + C
```

#### Delete Containers

```
docker compose down
```

#### Delete Containers with volumes

```
docker compose down -v
```

# Individual Commands

See more on [commands.md](./commands.md)

## Create Network

```
docker network create mern_network
```

## Create MongoDB Container

```
docker run --rm --name mongodb -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=secret -it --network=mern_network -v data:/data/db mongo
```

## Backend Container

#### Create Container

```
docker build -t backend .
```

#### Run container

```
docker run -it -p 4040:4040 -v "%cd%:/app" --network=mern_network backend
```

## Frontend Container

#### Create Container

```
docker build -t frontend .
```

#### Run backend container

```
docker run -it -p 8000:8000 --rm frontend
```
