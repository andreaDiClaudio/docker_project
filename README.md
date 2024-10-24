
# Frontend Application with Docker and Nginx

This project demonstrates how to containerize a frontend application (using HTML, CSS, and JavaScript) with Nginx, using Docker and Docker-Compose. The Nginx web server will serve the static frontend files.

## Prerequisites

Make sure you have the following installed on your machine:
- [Docker](https://docs.docker.com/get-docker/)
- [Docker-Compose](https://docs.docker.com/compose/install/)

## Folder Structure

```
project-root/
│
├── client/
│   ├── api/               # API directory
│   ├── assets/            # Assets (images, styles, etc.)
│   ├── pages/             # Contains HTML files, including index.html
│   └── dockerfile         # Dockerfile for the frontend application
│
└── docker-compose.yml     # Docker-Compose configuration file
```

## Steps to Containerize the Application

### 1. Dockerfile Setup

Create a `dockerfile` inside the `client/` folder to define how the frontend application will be built and served by Nginx.

**Dockerfile (client/dockerfile):**

```dockerfile
FROM nginx:alpine

COPY ./pages /usr/share/nginx/html

EXPOSE 80
```

### 2. Docker-Compose Setup

In the root directory of your project, create the `docker-compose.yml` file to define the services (frontend and backend). Below is the setup for the frontend application.

**docker-compose.yml:**

```yaml
version: "3.8"

services:
  # Frontend Service
  frontend:
    build:
      context: ./client
      dockerfile: ./client/dockerfile
    ports:
      - "80:80"
    volumes:
      - ./client/pages:/usr/share/nginx/html
```

### 3. Build and Run the Application

After setting up the Dockerfile and Docker-Compose file, you can follow these steps to build and run the application.

1. **Build the containers**

   Open a terminal in the project root and run:

   ```bash
   docker-compose up --build
   ```

   This command builds the Docker images and starts the containers.

2. **Access the application**

   Once the containers are running, open your browser and navigate to `http://localhost` to view the frontend application.

### 4. Hot Reload (Optional)

If you're actively working on the frontend and want changes to reflect immediately without rebuilding the container, use Docker's volume mapping feature. The `volumes` configuration in the `docker-compose.yml` file ensures that changes to the `client/pages` directory on your host machine will be reflected inside the container without rebuilding.

---

## Stopping the Containers

To stop and remove the containers, run the following command:

```bash
docker-compose down
```

This stops the containers and removes them, along with any associated networks and volumes.
