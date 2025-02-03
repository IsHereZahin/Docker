# Live Auto Update with Docker

This project demonstrates how to set up a Node.js application with live auto-update capabilities using Docker and Nodemon.

## Prerequisites
- [Docker](https://www.docker.com/get-started) installed on your machine
- Basic knowledge of Node.js and Docker

## Setup Instructions

### 1. Update `package.json`
Modify the `scripts` section to use Nodemon for automatic live updates:

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "nodemon -L app.js"  // -L for windows pc
}
```

### 2. Update `Dockerfile`
Ensure Nodemon is globally installed and modify the `CMD` instruction:

```dockerfile
FROM node:22
WORKDIR /app
RUN npm install -g nodemon
COPY package.json .
RUN npm install
COPY . .
EXPOSE 5001
CMD [ "npm", "run", "start"]
```

### 3. Build and Run the Docker Container
Run the following command to build the Docker image:

```sh
docker build -t img_name .
```

Then, run the container with volume mounting for live updates:

```sh
docker run -p 5001:5001 --name container_name --rm -v "D:\Docker\Node\Node:/app" -v "/app/node_modules" img_name
```
<details> 
  <summary>Explanation of the Setup</summary>

## Explanation
- `-v "D:\Docker\Node\Node:/app"` mounts the local project directory to the container, enabling live updates.
- `-v "/app/node_modules"` ensures that dependencies are installed inside the container, avoiding conflicts with the local `node_modules`.
- `--rm` automatically removes the container when stopped.
- `EXPOSE 5001` specifies the port used by the application.
- `CMD [ "npm", "run", "start" ]` ensures that Nodemon continuously watches for file changes.

</details>
