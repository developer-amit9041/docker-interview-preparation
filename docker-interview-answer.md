# Docker Interview Answers

## Q1. What is Docker?

### 1. English Definition

Docker is an open-source platform that enables developers to build, package, and run applications in isolated environments called containers. It packages an application with its required dependencies to help ensure consistent behavior across different environments.

### 2. Hindi Definition

Docker ek open-source platform hai jo applications ko unki required dependencies ke saath containers mein package aur run karne ki suvidha deta hai. Isse application ko different environments mein consistently chalana aasaan hota hai.

### 3. Hinglish Explanation

Maan lo aapne MERN Stack mein ek application banayi hai. Aapke local system par Node.js version 20 hai, lekin server par Node.js version 18 hai. Is wajah se compatibility issues aa sakte hain.

Docker ki help se hum application ko uski required dependencies aur configuration ke saath package kar sakte hain. Phir application ko Docker-supported environments mein run karna easier ho jata hai.

Docker mein do important concepts hain:

- **Docker Image:** Application ko run karne ke liye required files aur configuration ka template.
- **Docker Container:** Docker image se create hua running instance, jisme application execute hoti hai.

### 4. Practical Example / Code

Create a `Dockerfile` for a Node.js application:

```dockerfile
FROM node:20

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5000

CMD ["node", "server.js"]
```

This Dockerfile uses Node.js 20 as the base image, installs the application dependencies, copies the source code, and defines the command to start the application.

### 5. Architecture Diagram

```text
Node.js Application
(source code + package.json)
          |
          v
     Docker Image
(application + dependencies
     + configuration)
          |
          v
    Docker Container
   (running application)
```

### 6. Practical Commands

Run these commands from the directory containing the Dockerfile.

**Step 1: Build the image**

```bash
docker build -t my-node-app .
```

**Step 2: Run the container**

```bash
docker run -d -p 5000:5000 --name my-container my-node-app
```

**Step 3: Check running containers**

```bash
docker ps
```

**Step 4: Check application logs**

```bash
docker logs my-container
```

The option `-p 5000:5000` maps port 5000 on the host to port 5000 in the container. The application should listen on port 5000 and, in a typical container setup, bind to `0.0.0.0` to be reachable through the published port.

### 7. Summary Table

| Term | Meaning |
|---|---|
| Docker | A platform for packaging and running applications in containers |
| Docker Image | A template used to create containers |
| Docker Container | A running or stopped instance created from an image |
| Dockerfile | A set of instructions used to build an image |
| Main benefit | Consistent and portable application environments |

**Interview-ready summary:**

> Docker packages applications and their dependencies into containers, making them portable and consistent across development, testing, and production environments.
