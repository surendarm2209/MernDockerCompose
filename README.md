 MERN Stack Application
Before running any containers, we need to create a custom bridge network so that all containers can communicate with each other.
1. Create the custom network: To allow all the containers to communicate, run the following command to create a custom bridge network: docker network create demo
2. Build the client (Frontend):
    * Navigate to the frontend directory and create a Docker image for the client: cd mern/frontend
    * docker build -t mern-frontend .
    * 
3. Run the client container: After building the Docker image for the frontend, you can run the container as follows: docker run --name=frontend --network=demo -d -p 5173:5173 mern-frontend
4. 
5. Verify the client is running: Open your browser and navigate to: http://localhost:5173
6.  This should display your React frontend.
7. Run the MongoDB container:
    * For MongoDB, we use the official MongoDB image and mount the data to a local directory to ensure persistence: docker run --network=demo --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongodb:latest
    * 
8. Build the server (Backend):
    * Navigate to the backend directory and build the Docker image for the backend: cd mern/backend
    * docker build -t mern-backend .
    * 
9. Run the server container: After building the backend Docker image, you can run the backend container: docker run --name=backend --network=demo -d -p 5050:5050 mern-backend
10. Using Docker Compose: If you'd like to manage everything using Docker Compose, you can start all the containers with the following command: docker compose up -d
11. This setup ensures that your frontend, backend, and MongoDB containers can communicate via the custom network (demo), and the necessary Dockerfiles are used for both the frontend and backend.
