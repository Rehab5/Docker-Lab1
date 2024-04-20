# ITI - Docker Lab 🐋

## Task 1: Working with Docker Hello-world Image
### Objective
Learn how to run a container using the hello-world image and manage containers and images.

### Steps
#### 1. Run a Container with hello-world Image
```bash
docker run hello-world
```
#### 2. Check Container Status and Explain
```bash
docker ps -a 
it created and runs display message
Digest: sha256:a26bff933ddc26d5cdf7faa98b4ae1e3ec20c4985e6f87ac0973052224d24302
Status: Downloaded newer image for hello-world:latest

```
#### 3. Start the Stopped Container
```bash
docker start [conatiner-name]
```
#### 4. Remove the Container
```bash
docker rm [conatiner-name]
```
#### 5. Remove the Image
```bash
docker rmi hello-world
```
-----------------------------------------

## Task 2: Running Container with Ubuntu Image
### Objective
Run an Ubuntu container in interactive mode, create a file inside it, and manage containers.

### Steps
#### 1. Run Ubuntu Container in Interactive Mode
```bash
docker run -it  ubuntu
```
#### 2. Create a File inside the Container
```bash
mkdir rehab 
cd rehab
vi hello-docker
in hello-docker i can write ant text
to check content
cat hello-docker
```
#### 3. Stop and Remove the Container
```bash
docker stop [container-id-or-name] 7d56036d995b
docker rm [container-id-or-name] 7d56036d995b
```
#### 4. Check File Status
```bash
```
#### 5. What happened to hello-docker file?

```bash
as ubuntu container is removed the file is removed
```
#### 6. Remove All Stopped Containers
```bash
docker container prune
```
#### 7. Bonus: Remove All Containers in One Command
```bash
docker rm $(docker ps -a -q)

```

---
## Task 3: Creating a Custom Nginx Docker Image
### Objective
Create a custom Docker image using Nginx and a local HTML file.

### Steps
#### 1. Create a Local HTML File
```
mkdir nginx-custom
cd nginx-custom
nano index.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h2>Hello Docker</h2>
</body>
</html>

```
#### 2. Write Dockerfile and Copy the HTML file to the Docker Image
```bash
nano docker-file
# Use nginx
FROM nginx

# Copy the local HTML file
COPY index.html

```
#### 3. Run Container with New Image
```bash
docker build -t nginx-custom .

```

#### 4. Test the Container, open your browser and navigate to http://localhost:8088 to check if everything is okay
```bash
docker run -d -p 8088:80 7d56036d995b custom-nginx nginx-custom

```

