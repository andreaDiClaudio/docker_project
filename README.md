
# Travel Destination with Docker

This project contains a monorepo with a backend (Node.js with Express) and frontend (plain JavaScript, HTML, CSS), along with a MongoDB database. 

## Prerequisites
Make sure you have the following installed:
- Docker
- Docker Compose
- Docker daemon must be running on your machine
- A MongoDB instance should be up and running locally

## How to setup server repo
3. Create a `.env` file and set the `PORT=` to the desired port.
4. Run `node app.js`.

### How to connect to db
1. Create new connection in mongodb compass.
2. Set the `MONGODB_URI` to your mongodb_uri in the `.env` file
3. Run `node app.js`.

### Auth
1. Set the `JWT_SECRET` to your secret in the `.env` file

## Docker Compose

The `docker-compose.yml` file sets up three services: 
1. **MongoDB** (for the database),
2. **Frontend** (served with Nginx),
3. **Backend** (Node.js with Express connected to MongoDB).


## Running the Project

To run the app using Docker Compose:

1. Open a terminal and navigate to the project root directory.
2. Build and start the services using the following command:

   ```bash
   docker compose up --build
   ```

   This command will:
   - Pull the MongoDB image,
   - Build the frontend with Nginx,
   - Build the backend with Node.js and Express.

3. Open your browser and go to `http://localhost` to see the frontend.
   The backend API will be accessible at `http://localhost:8080`.

### Stopping the Project
To stop and remove the running containers:

```bash
docker compose down
```

## Notes

- The MongoDB container will persist the data in a volume named `mongo_db`.
- Ensure that the `client/pages` folder contains the `index.html` file to serve the frontend correctly.
- Adjust the port mapping in the `docker-compose.yml` file if you have conflicting services.

