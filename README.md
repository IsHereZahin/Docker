# Docker Commands for Node.js Application

This README provides a collection of essential Docker commands for working with Node.js applications. These commands will guide you through building, running, and managing Docker containers for your projects.

## 1. Setup

#### Install Docker  
To get started, download and install Docker from the official website:  
🔗 [Docker Official Site](https://www.docker.com/)  

#### Creating a Dockerfile  
Once Docker is installed, navigate to the root directory of your project and create a `Dockerfile`.  
This file defines the environment and dependencies for your containerized application.  

Dockerfile Example
Below is a sample `Dockerfile` for setting up a Node.js application: 
    
    Dockerfile

Dockerfile Semple

    FROM node:22
    
    WORKDIR /app
    
    COPY . .
    
    RUN npm install
    
    EXPOSE 5001 
    
    CMD [ "node", "app.js" ]
  
<details>
  <summary>Click to expand Dockerfile Explanation</summary>

### 1️⃣ `FROM node:22`  
- Specifies the base image as Node.js version 22.  
- Ensures a consistent runtime environment for the application.  

### 2️⃣ `WORKDIR /app`  
- Sets `/app` as the working directory inside the container.  
- All subsequent commands will be executed within this directory.  

### 3️⃣ `COPY . .`  
- Copies all files from the project directory (host machine) to the container's `/app` directory.  
- Ensures that the application code and dependencies are available inside the container.  

### 4️⃣ `RUN npm install`  
- Installs all dependencies defined in `package.json`.  
- This step ensures that required Node.js packages are available for the application.  

### 5️⃣ `EXPOSE 5001`  
- Informs Docker that the application inside the container will use port **5001**.  
- This does **not** automatically publish the port but serves as documentation for users running the container.  

### 6️⃣ `CMD ["node", "app.js"]`  
- Defines the default command that will be executed when the container starts.  
- Runs `node app.js` to launch the application.  

---

### 📌 Summary  
This `Dockerfile` creates a reproducible and isolated environment for a Node.js application.  
It ensures dependencies are installed, exposes the correct port, and defines how the application should start inside the container. 🚀  

</details>



## 3. Build and Run Docker Image
#### Build Docker Image
    docker build .  
Build the Docker image from the current directory

#### Run Docker Image
    docker run IMAGE_ID
Run the Docker image using its ID

#### Build Docker Image with a Custom Tag
    docker build -t javascript_app:v1 . 
Build image with name "javascript_app" and tag "v1"

#### Run Docker Image with Custom Tag
    docker run javascript_app:v1  
Run the image with the specified tag

## 4. Stop and Start Containers
#### Stop a Running Container
    docker container stop e1f45f6fe891  
Stop the container by its ID
(You can also use the container's name instead of the ID)

#### Start a Stopped Container
    docker container start e1f45f6fe891  
Start the container using its ID

## 5. Clean Up Containers and Images
#### Remove All Stopped Containers
    docker container prune

#### Remove Unused Docker Images
    docker image prune -a
(a for creating forces if normally not removed)



## 6. Run with Custom Container Name
#### Run Docker Container with Specific Name
    docker run -p 5001:5001 --name node_app_container --rm (image_name_or_id)  
Run with a specific container name

## Additional Commands
#### Change Port Mapping and Run Docker Container
    docker run -p 5002:5001 node_app:v1

#### Run and Automatically Remove Container
    docker run -p 5003:5001 --rm 48ed96624269  
Run and remove the container once stopped (48ed96624269 = container id or name)

#### Stop a Running Container (Full ID)
    docker container stop a187c6aec56572b2  
Stop the container by its full ID

#### Run and Build Node.js Application Docker Image
    docker build -t node_app:v1 .  
Build the node application image

      docker run -p 5001:5001 node_app:v1  
Run the container, mapping port 5001



