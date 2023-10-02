# Docker REST API with MongoDB

## Step 1: Project Initialization
To initialize the project, follow these commands in your terminal, ensuring that you are in the root directory:

```shell
mkdir docker_rest_api && cd docker_rest_api && npm init -y

## Step 2: Install Dependencies
Navigate to the project folder and install the necessary dependencies:

```shell
npm install express body-parser mongodb mongoose

These libraries are essential for building the backend of our application. Express handles routes and middleware, body-parser helps with request data, and MongoDB/Mongoose enable database operations.

## Step 3: Database Setup
Under the docker_rest_api directory, there is a db.js file. This file contains code to connect to MongoDB using your credentials. On successful connection, a success message is logged; otherwise, an error message is displayed.

## Step 4: Define Models and Schemas
In this step, we will create a user collection in MongoDB based on the schema defined in user.js. The schema requires mandatory fields: name and role, both of type string. Using this schema, we create a User model, allowing CRUD operations on user data.

## Step 5: Application Routes
In the app.js file under the docker_rest_api directory, we define application routes to enable CRUD functionalities. The application listens on port 5000 and logs a message when successfully booted up.

## Step 6: Docker Configuration
Create two files, Dockerfile and docker-compose.yml. The Dockerfile contains instructions to create a Docker image for your application. The docker-compose.yml file defines and runs multi-container Docker applications, setting up both the application and MongoDB. With Docker Compose, deployment becomes more efficient.

## Step 7: Run Application
To run the application and test CRUD operations using Postman, follow these steps:

Run the following command to start the application using Docker Compose:

```shell
docker compose up -d

This command pulls the MongoDB Docker image, builds the custom Docker image defined in the Dockerfile, and starts both services.

Verify that the Docker containers are running:
```shell
docker ps


You should see two running containers.

1. Use Postman to create a new user and retrieve all users:

- Create a new collection in Postman.
- Create a POST request to localhost:5000/users with the following JSON body:
```json
Copy code
{
  "name": "Tony",
  "role": "Developer"
}
- Send the request.

2. To verify the user has been added:

- Visit localhost:5000/users in your browser.
- Check the MongoDB Docker container for the newly created user:

```shell
docker exec -it mongosh -u "root" -p "example"

db.users.find().pretty()