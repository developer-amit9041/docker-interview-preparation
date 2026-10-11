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


---

## Q2. Why do we need Docker?

### 1. English Definition

Docker is needed to package applications and their dependencies into portable containers, reduce environment-related issues, simplify deployment, isolate workloads, and support consistent development, testing, and production environments.

### 2. Hindi Definition

Docker ki zaroorat applications aur unki dependencies ko ek portable container mein package karne ke liye hoti hai, jisse deployment aasaan hota hai aur alag-alag environments mein application chalane se judi problems kam hoti hain.

### 3. Hinglish Explanation

Maan lo aapki MERN application aapke laptop par sahi chalti hai, lekin production server par Node.js version, installed packages, ya configuration alag hone ki wajah se fail ho jaati hai. Is situation ko aksar **“it works on my machine”** problem kaha jata hai.

Docker application ke liye required runtime aur dependencies ko image mein package karne mein help karta hai. Isse team development, testing aur production mein ek consistent setup use kar sakti hai.

Docker ke main use cases:

- **Environment consistency:** Different environments mein configuration differences kam karna.
- **Portability:** Container image ko compatible Docker environments par run karna.
- **Isolation:** Applications ko separate containers mein run karna.
- **Faster deployment:** Repeatable build aur deployment process banana.
- **Scaling:** Zaroorat ke hisaab se application ke multiple container instances run karna.
- **CI/CD support:** Automated testing aur deployment pipelines mein containers use karna.

### 4. Practical Example / Code

Suppose aapki Node.js application ko Node.js 20 chahiye. Dockerfile mein version specify karein:

```dockerfile
FROM node:20

WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .

EXPOSE 5000
CMD ["node", "server.js"]
```

Build aur run:

```bash
docker build -t my-node-app .
docker run -d -p 5000:5000 --name my-node-container my-node-app
```

Ab image ke andar Node.js 20 runtime specify hai, isliye compatible Docker environments par application ko same runtime ke saath chalana easier hota hai. Application ko sahi tarah configure karna aur required external services dena phir bhi zaroori hai.

### 5. Architecture Diagram

```text
          Application Source Code
                    |
                    v
            Dockerfile + Dependencies
                    |
                    v
               Docker Image
                    |
          +---------+---------+
          |         |         |
          v         v         v
       Dev Env   Test Env   Production
       Container Container  Container
          |         |         |
          +---- Consistent setup ----+
```

### 6. Practical Command / Configuration

**Check the Node.js version inside a container:**

```bash
docker run --rm node:20 node --version
```

**Build your application image:**

```bash
docker build -t my-node-app .
```

**Run it with a published port:**

```bash
docker run -d -p 5000:5000 --name my-node-container my-node-app
```

**Check container status and logs:**

```bash
docker ps
docker logs my-node-container
```

### 7. Summary Table

| Why Docker is needed | Benefit |
|---|---|
| Environment consistency | Reduces “works on my machine” issues |
| Portability | Runs the same image in compatible environments |
| Isolation | Separates application processes and dependencies |
| Deployment | Makes releases more repeatable |
| Scaling | Allows multiple container instances |
| CI/CD | Supports automated build, test, and deployment workflows |

**Interview-ready summary:**

> We use Docker to package applications with their dependencies, reduce environment inconsistencies, simplify deployment, isolate workloads, and make application delivery more repeatable across development, testing, and production.


---

## Q3. What is the difference between Docker and a Virtual Machine (VM)?

### 1. English Definition
Docker runs applications in lightweight containers that share the host OS kernel (on Linux). A virtual machine runs a separate guest operating system on virtual hardware managed by a hypervisor.

### 2. Hindi Definition
Docker application ko container mein chalata hai jo Linux host ka kernel share karta hai. Virtual Machine apna alag guest operating system virtual hardware par chalati hai.

### 3. Hinglish Explanation
Maan lo aapko Node.js application run karni hai. Docker container mein application aur uski dependencies hoti hain, lekin har container ko complete OS boot nahi karna padta. VM mein guest OS bhi hota hai, jaise Ubuntu ya Windows. Isliye containers aam taur par lightweight aur jaldi start hote hain; VMs separate OS environments ke liye useful hoti hain.

Note: Docker Desktop on Windows/macOS may use a Linux VM behind the scenes to run Linux containers.

### 4. Practical Example / Code
Run Node.js in a temporary container:

```bash
docker run --rm node:20 node --version
```

A VM example is an Ubuntu virtual machine created using Hyper-V, VMware, or VirtualBox, with Node.js installed inside its guest OS.

### 5. Architecture Diagram

```text
Docker:
+---------------------------+
| App A       | App B       |
| Container   | Container   |
+---------------------------+
| Docker Engine / Runtime   |
| Host OS Kernel            |
+---------------------------+
| Host Machine              |
+---------------------------+

Virtual Machines:
+---------------------------+
| App A       | App B       |
| Libraries   | Libraries   |
| Guest OS    | Guest OS    |
+---------------------------+
| Hypervisor                 |
+---------------------------+
| Host Machine              |
+---------------------------+
```

### 6. Practical Command / Configuration

```bash
docker run --rm node:20 node --version
```

For a VM, allocate virtual CPU, memory, storage, and a guest OS image in a hypervisor before installing and running the application.

### 7. Summary Table

| Feature | Docker Container | Virtual Machine |
|---|---|---|
| OS | Shares host kernel on Linux | Has its own guest OS |
| Startup | Usually faster | Usually slower due to OS boot |
| Resource usage | Usually lower | Usually higher |
| Size | Typically smaller | Typically larger |
| Isolation | Container-level isolation | Separate guest OS; different isolation boundary |
| Best suited for | Packaging and deploying apps | Separate OS environments |

**Interview-ready summary:**

> Docker containers share the host OS kernel and are generally lightweight and fast to start. Virtual machines run separate guest operating systems on a hypervisor, typically using more resources while offering greater guest-OS flexibility.


---

## Q4. What is a Docker container?

### 1. English Definition

A Docker container is an isolated runtime environment created from a Docker image. It runs an application and its required processes and dependencies while sharing the host OS kernel on Linux.

### 2. Hindi Definition

Docker container ek isolated runtime environment hota hai, jo Docker image se create hota hai. Iske andar application aur uske required processes run hote hain, aur Linux par container host operating system ka kernel share karta hai.

### 3. Hinglish Explanation

Container ko application chalane ke liye ek isolated environment samjho.

Example: Aapki MERN application mein Node.js backend hai. Aap backend ko Docker image se container ke andar run kar sakte ho. Container ke andar application ka process chalta hai aur uske liye required dependencies available hoti hain.

Yaad rakhein:

- **Image** ek template hai.
- **Container** image se create hua runtime instance hai.
- Ek hi image se multiple containers create kiye ja sakte hain.
- Container stop ya delete karne se uske writable layer ka data generally persist nahi karta. Persistent data ke liye volume ya bind mount use karein.

### 4. Practical Example / Code

Run a Node.js container:

```bash
docker run -d --name my-node-container -p 5000:5000 node:20
```

This starts a container from the Node.js 20 image. The base image's default command starts Node.js, so a real web application would normally use your application image built from a Dockerfile.

Build and run your own Node.js app:

```bash
docker build -t my-node-app .
docker run -d --name my-app -p 5000:5000 my-node-app
```

### 5. Architecture Diagram

```text
       Docker Image
   (app + dependencies)
              |
        docker run
              |
              v
   +----------------------+
   |   Docker Container   |
   |                      |
   |  Node.js Application |
   |  Required Libraries  |
   |  Writable Layer      |
   +----------------------+
              |
       Host OS Kernel
       (Linux example)
```

### 6. Practical Command / Configuration

**List running containers:**

```bash
docker ps
```

**List all containers, including stopped ones:**

```bash
docker ps -a
```

**View logs:**

```bash
docker logs my-app
```

**Stop the container:**

```bash
docker stop my-app
```

**Remove the stopped container:**

```bash
docker rm my-app
```

### 7. Summary Table

| Term | Meaning |
|---|---|
| Docker container | Isolated runtime environment for an application |
| Created from | Docker image |
| Contains | Application process and required runtime dependencies |
| Kernel | Shares the host kernel on Linux |
| Persistence | Use volumes or bind mounts for data that must survive container removal |
| Multiple instances | Multiple containers can be created from one image |

**Interview-ready summary:**

> A Docker container is an isolated runtime instance created from a Docker image. It runs an application with its required dependencies and shares the host OS kernel on Linux, making it generally lightweight and portable.


---

## Q5. What is a Docker image?

### 1. English Definition

A Docker image is a read-only template used to create Docker containers. It contains the application code, runtime, libraries, dependencies, and configuration needed to run an application.

### 2. Hindi Definition

Docker image ek read-only template hoti hai, jiska use Docker containers create karne ke liye hota hai. Ismein application code, runtime, libraries aur required dependencies ho sakti hain.

### 3. Hinglish Explanation

Image ko application ka packaged blueprint samjho, aur container ko us blueprint se bana hua running instance.

For example, aap Node.js application ki image banate ho. Us image mein Node.js runtime, aapka application code aur required packages include ho sakte hain. Isi ek image se aap development, testing ya production ke liye multiple containers create kar sakte ho.

**Remember:**
- **Dockerfile:** Image banane ke instructions.
- **Docker image:** Built template.
- **Docker container:** Image se create hua runtime instance.

Images layered hoti hain, isliye unchanged layers ko reuse kiya ja sakta hai. Image build karne ke baad usse Docker Hub ya private registry mein store aur share bhi kar sakte hain.

### 4. Practical Example / Code

Example Dockerfile for a Node.js application:

```dockerfile
FROM node:20
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

Build the image:

```bash
docker build -t my-node-app:1.0 .
```

List local images:

```bash
docker images
```

Create a container from the image:

```bash
docker run -d --name my-app -p 5000:5000 my-node-app:1.0
```

Note: The project should have a valid `package.json` with a `start` script, and the application should listen on port 5000.

### 5. Architecture Diagram

```text
          Dockerfile
      (build instructions)
               |
         docker build
               |
               v
       +------------------+
       |   Docker Image   |
       | App Code         |
       | Runtime          |
       | Dependencies     |
       +------------------+
               |
          docker run
               |
               v
       +------------------+
       | Docker Container |
       | Running App      |
       +------------------+
```

### 6. Practical Command / Configuration

**Pull an image from a registry:**

```bash
docker pull node:20
```

**Inspect image details:**

```bash
docker image inspect node:20
```

**Remove a local image (after removing containers that use it, if necessary):**

```bash
docker image rm my-node-app:1.0
```

### 7. Summary Table

| Term | Meaning |
|---|---|
| Docker image | Read-only template for creating containers |
| Created using | Usually a Dockerfile and `docker build` |
| Contains | Application files, runtime, dependencies and configuration |
| Runs directly? | No; a container is created to run the application |
| Reusable | One image can create multiple containers |
| Stored in | Local image cache or a container registry |

**Interview-ready summary:**

> A Docker image is a read-only, layered template that packages an application and its required runtime dependencies. Docker uses the image to create one or more containers.


---

## Q6. What is the difference between a Docker image and a container?

### 1. English Definition

A Docker image is a read-only, layered template used to create containers. A Docker container is a runtime instance of an image, with an isolated process environment and a writable container layer.

### 2. Hindi Definition

Docker image ek read-only template hoti hai, jisse container create hota hai. Docker container us image ka runtime instance hota hai, jisme application run karti hai aur apni writable layer mein changes kar sakti hai.

### 3. Hinglish Explanation

Easy example se samjho:

- **Image = blueprint / recipe**
- **Container = us blueprint se bana hua running application environment**

Jaise ek hi Docker image se aap development aur testing ke liye alag-alag containers bana sakte ho. Image khud template hoti hai; container ke andar application ka process run karta hai.

Container ke writable layer mein kiye gaye changes image ko automatically modify nahi karte. Container remove karne par writable-layer data generally lost ho sakta hai, isliye persistent data ke liye volumes ya bind mounts use karte hain.

### 4. Practical Example / Code

Pull an image:

```bash
docker pull node:20
```

Create two containers from the same image:

```bash
docker run -d --name node-app-1 node:20
docker run -d --name node-app-2 node:20
```

These commands create two containers from the same image. Since the default Node image command may exit when no process is kept running, use this version to keep both containers running for demonstration:

```bash
docker run -d --name node-app-1 node:20 sleep infinity
docker run -d --name node-app-2 node:20 sleep infinity
```

Check containers and images:

```bash
docker ps
docker images
```

### 5. Architecture Diagram

```text
              Docker Image
            (read-only template)
                    |
           +--------+--------+
           |                 |
       docker run        docker run
           |                 |
           v                 v
   +---------------+  +---------------+
   |  Container 1  |  |  Container 2  |
   | Writable layer|  | Writable layer|
   | Process / App |  | Process / App |
   +---------------+  +---------------+
```

### 6. Practical Command / Configuration

**See local images:**

```bash
docker images
```

**See running containers:**

```bash
docker ps
```

**See all containers, including stopped ones:**

```bash
docker ps -a
```

**Inspect an image or container:**

```bash
docker image inspect node:20
docker container inspect node-app-1
```

### 7. Summary Table

| Feature | Docker Image | Docker Container |
|---|---|---|
| Meaning | Read-only template | Runtime instance of an image |
| Purpose | Used to create containers | Runs the application process |
| State | Image layers are immutable | Has a writable container layer |
| Created by | Usually `docker build` or `docker pull` | `docker run` or `docker create` |
| Instances | One image can create many containers | Each container is a separate instance |
| Persistence | Image layers are reusable | Writable-layer data may be lost when removed; use volumes for persistent data |

**Interview-ready summary:**

> A Docker image is a read-only template, whereas a Docker container is a runtime instance created from that image. One image can be used to create multiple independent containers.


---

## Q7. What is Docker Engine?

### 1. English Definition

Docker Engine is the core containerization technology that builds and runs Docker containers. It includes the Docker daemon, a REST API, and the Docker CLI.

### 2. Hindi Definition

Docker Engine Docker ka core software hai jo containers ko build, create aur run karne ka kaam karta hai. Ismein Docker daemon, REST API aur Docker CLI jaise components hote hain.

### 3. Hinglish Explanation

Docker Engine ko Docker ka main execution system samjho. Jab aap terminal mein `docker run` command dete ho, Docker CLI request ko Docker Engine ke API ke through daemon tak pahunchata hai. Daemon image check/pull karta hai, container create karta hai aur uske lifecycle ko manage karta hai.

**Main components:**
- **Docker CLI:** Woh command-line tool jahan aap `docker run`, `docker build` jaise commands likhte ho.
- **Docker daemon (`dockerd`):** Background service jo images, containers, networks aur volumes manage karti hai.
- **REST API:** CLI aur daemon ke beech communication interface.

### 4. Practical Example / Code

Build an image:

```bash
docker build -t my-node-app .
```

Run a container:

```bash
docker run -d --name my-app -p 5000:5000 my-node-app
```

In commands ko execute karte waqt CLI Docker Engine se request karta hai; daemon image build karne ya container run karne ka kaam manage karta hai.

### 5. Architecture Diagram

```text
        User / Terminal
               |
           Docker CLI
               |
        REST API request
               |
               v
       Docker Daemon
          (dockerd)
               |
      +--------+---------+
      |        |         |
    Images  Containers  Networks
               |
        Host OS / Kernel
```

### 6. Practical Command / Configuration

**Check Docker Engine version:**

```bash
docker version
```

**Check daemon and installation details:**

```bash
docker info
```

**Check whether the Docker service is active on a typical Linux system using systemd:**

```bash
sudo systemctl status docker
```

Note: The last command applies to many Linux installations. Docker Desktop on Windows/macOS manages its engine differently.

### 7. Summary Table

| Component | Responsibility |
|---|---|
| Docker CLI | Accepts commands from the user |
| Docker REST API | Provides the interface for communicating with the daemon |
| Docker daemon (`dockerd`) | Manages images, containers, networks and volumes |
| Docker Engine | Core technology that builds and runs containers |

**Interview-ready summary:**

> Docker Engine is the core technology used to build and run containers. It includes the Docker daemon, REST API, and CLI, which work together to manage containerized applications.


---

## Q8. What is Docker architecture?

### 1. English Definition

Docker architecture is a client-server architecture in which the Docker CLI communicates with the Docker daemon through a REST API. The daemon manages Docker objects such as images, containers, networks, and volumes.

### 2. Hindi Definition

Docker architecture ek client-server model par based hoti hai. Docker CLI commands bhejta hai, REST API ke through request Docker daemon tak pahunchti hai, aur daemon images, containers, networks aur volumes ko manage karta hai.

### 3. Hinglish Explanation

Docker architecture ko request ke flow se samjho:

1. Aap terminal mein command likhte ho, jaise `docker run nginx`.
2. Docker CLI command ko Docker Engine API ke through daemon tak bhejta hai.
3. Docker daemon required image local machine par check karta hai. Image na mile toh registry se pull kar sakta hai.
4. Daemon container create aur start karta hai.
5. Container application ko run karta hai.

**Main components:**
- **Docker Client (CLI):** User commands accept karta hai.
- **Docker Daemon (`dockerd`):** Docker objects aur container lifecycle manage karta hai.
- **Docker Registry:** Docker images store aur distribute karti hai, jaise Docker Hub.
- **Docker Objects:** Images, containers, networks aur volumes.

### 4. Practical Example / Code

Run an Nginx container:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Docker image ko local cache mein check karega; agar zaroorat ho toh registry se pull karega, phir container start karega. Browser mein `http://localhost:8080` open karke Nginx page check kar sakte ho.

Check the running container:

```bash
docker ps
```

### 5. Architecture Diagram

```text
              User / Terminal
                     |
                     v
              Docker CLI
                     |
              REST API request
                     |
                     v
             Docker Daemon
                (dockerd)
          _________|___________
         |         |           |
         v         v           v
      Images   Containers   Networks/Volumes
         |
         | image pull / push
         v
    Docker Registry
      (e.g. Docker Hub)
```

### 6. Practical Command / Configuration

**Run a container:**

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

**List containers:**

```bash
docker ps
```

**List local images:**

```bash
docker images
```

**Inspect Docker Engine details:**

```bash
docker info
```

### 7. Summary Table

| Component | Responsibility |
|---|---|
| Docker Client / CLI | User commands bhejta hai |
| REST API | Client aur daemon ke beech communication |
| Docker Daemon | Docker objects aur container lifecycle manage karta hai |
| Docker Registry | Images store aur distribute karti hai |
| Docker Image | Container create karne ka template |
| Docker Container | Application run karne wala isolated environment |
| Networks / Volumes | Container communication aur persistent data support karte hain |

**Interview-ready summary:**

> Docker uses a client-server architecture. The Docker CLI sends requests through the Docker Engine API to the Docker daemon, which manages images, containers, networks, and volumes and can communicate with registries to pull or push images.


---

## Q9. What is the Docker client?

### 1. English Definition

The Docker client is the command-line interface (CLI) that lets users interact with Docker. It sends commands to the Docker daemon through the Docker Engine API.

### 2. Hindi Definition

Docker client ek command-line tool hai jiske through user Docker ko commands deta hai. Ye commands Docker Engine API ke zariye Docker daemon tak pahunchti hain.

### 3. Hinglish Explanation

Docker client ko woh tool samjho jahan aap Docker commands type karte ho, jaise `docker run`, `docker build`, aur `docker ps`.

Client khud container ko directly run nahi karta. Ye request Docker daemon ko bhejta hai, aur daemon requested operation manage karta hai.

**Flow:** User → Docker CLI → Docker Engine API → Docker daemon → Docker operation.

### 4. Practical Example / Code

Run this command in your terminal:

```bash
docker ps
```

Docker CLI daemon se running containers ki list maangta hai.

Build an image:

```bash
docker build -t my-node-app .
```

Yahan CLI build request bhejta hai; image build karne ka kaam Docker Engine/daemon manage karta hai.

### 5. Architecture Diagram

```text
       User types command
              |
              v
         Docker CLI
         (Client)
              |
        Docker Engine API
              |
              v
        Docker Daemon
          (dockerd)
              |
              v
    Images / Containers / Networks
```

### 6. Practical Command / Configuration

**Check the client and server versions:**

```bash
docker version
```

**Ask the daemon to list running containers:**

```bash
docker ps
```

**Check Docker Engine information:**

```bash
docker info
```

### 7. Summary Table

| Component | Responsibility |
|---|---|
| Docker client / CLI | Commands accept karta hai aur requests bhejta hai |
| Docker Engine API | Client aur daemon ke beech interface |
| Docker daemon | Requests ke according Docker resources manage karta hai |
| Example commands | `docker run`, `docker build`, `docker ps` |

**Interview-ready summary:**

> The Docker client is the CLI used to interact with Docker. It sends requests through the Docker Engine API to the Docker daemon, which performs operations such as building images and managing containers.


---

## Q10. What is the Docker daemon?

### 1. English Definition

The Docker daemon (`dockerd`) is a background service that manages Docker objects such as images, containers, networks, and volumes. It receives requests through the Docker Engine API and performs the requested operations.

### 2. Hindi Definition

Docker daemon ek background service hai jo Docker images, containers, networks aur volumes ko manage karti hai. Ye Docker Engine API ke through requests receive karke required operations perform karti hai.

### 3. Hinglish Explanation

Docker daemon ko Docker ka background manager samjho. Aap terminal mein `docker run nginx` command dete ho. Docker client request bhejta hai, aur daemon image check/pull karke container create aur start karne ka kaam manage karta hai.

**Yaad rakho:**
- **Docker Client:** Command bhejta hai.
- **Docker Daemon (`dockerd`):** Request process karke Docker resources manage karta hai.
- **Docker Engine API:** Client aur daemon ke beech communication interface hai.

Daemon background mein run karta hai; isliye terminal mein har operation ko manually manage karne ki zaroorat nahi hoti.

### 4. Practical Example / Code

Start an Nginx container:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Is request ko Docker client daemon tak bhejta hai. Daemon zaroorat padne par image pull karta hai, phir container create aur start karta hai.

Check the running container:

```bash
docker ps
```

### 5. Architecture Diagram

```text
       User / Terminal
              |
              v
         Docker CLI
              |
        Docker Engine API
              |
              v
      Docker Daemon (dockerd)
              |
     +--------+---------+
     |        |         |
   Images  Containers  Networks
                         |
                      Volumes
```

### 6. Practical Command / Configuration

**Check Docker daemon / Engine details:**

```bash
docker info
```

**On many Linux systems using systemd, check the Docker service:**

```bash
sudo systemctl status docker
```

**On those Linux systems, start the service if needed:**

```bash
sudo systemctl start docker
```

Note: Docker Desktop on Windows/macOS manages the Docker Engine differently, so these systemd commands may not apply.

### 7. Summary Table

| Component | Responsibility |
|---|---|
| Docker Client | Commands send karta hai |
| Docker Engine API | Client requests daemon tak pahunchati hai |
| Docker Daemon (`dockerd`) | Images, containers, networks aur volumes manage karta hai |
| Runs as | Background service/process |
| Example operation | Container create/start karna |

**Interview-ready summary:**

> The Docker daemon, also called `dockerd`, is the background service responsible for managing Docker images, containers, networks, and volumes. It receives requests through the Docker Engine API and carries out the requested operations.


---

## Q11. What is a Docker registry?

### 1. English Definition

A Docker registry is a service that stores and distributes Docker images. Users can push images to a registry and pull images from it to build and deploy containerized applications.

### 2. Hindi Definition

Docker registry ek service hai jahan Docker images store aur share ki jaati hain. Developers images ko registry mein push kar sakte hain aur deployment ke time wahan se pull kar sakte hain.

### 3. Hinglish Explanation

Registry ko Docker images ka online store samjho. Example ke liye Docker Hub ek public registry hai.

Maan lo aapne apni MERN backend ki image local machine par build ki. Ab aap us image ko Docker Hub par push kar sakte ho. Phir AWS server ya doosri machine par us image ko pull karke container run kar sakte ho.

**Important difference:**
- **Image:** Application ka packaged template.
- **Container:** Image se bana runtime instance.
- **Registry:** Images ko store aur distribute karne ki service.
- **Repository:** Registry ke andar related image names/tags ka collection.

Registries public ya private ho sakti hain. Private registry mein access ke liye authentication aur permissions ki zaroorat ho sakti hai.

### 4. Practical Example / Code

**Step 1: Sign in to Docker Hub from the CLI.**

```bash
docker login
```

**Step 2: Tag your local image using your Docker Hub username.**

```bash
docker tag my-node-app:1.0 YOUR_DOCKERHUB_USERNAME/my-node-app:1.0
```

Replace `YOUR_DOCKERHUB_USERNAME` with your actual username.

**Step 3: Push the image to the registry.**

```bash
docker push YOUR_DOCKERHUB_USERNAME/my-node-app:1.0
```

**Step 4: Pull it on another machine.**

```bash
docker pull YOUR_DOCKERHUB_USERNAME/my-node-app:1.0
```

Then create a container from the pulled image with `docker run`.

### 5. Architecture Diagram

```text
 Developer Machine                    Server / AWS
 +------------------+                +------------------+
 | Build Docker     |                | Pull Docker      |
 | Image            |                | Image            |
 +--------+---------+                +---------^--------+
          |                                    |
       docker push                         docker pull
          |                                    |
          v                                    |
      +---------------------------------------------+
      |               Docker Registry               |
      |     Stores and distributes Docker images   |
      |              (e.g. Docker Hub)              |
      +---------------------------------------------+
```

### 6. Practical Command / Configuration

**Sign in:**

```bash
docker login
```

**Push an image:**

```bash
docker push YOUR_DOCKERHUB_USERNAME/my-node-app:1.0
```

**Pull an image:**

```bash
docker pull YOUR_DOCKERHUB_USERNAME/my-node-app:1.0
```

**List local images:**

```bash
docker images
```

### 7. Summary Table

| Term | Meaning |
|---|---|
| Docker registry | Service to store and distribute images |
| Docker Hub | A widely used public registry with private-repository options |
| Push | Upload an image to a registry |
| Pull | Download an image from a registry |
| Docker repository | Collection of image versions/tags under a repository name |
| Use case | Share images and deploy the same image across environments |

**Interview-ready summary:**

> A Docker registry is a service that stores and distributes Docker images. Developers push images to a registry and pull them on other machines or servers to run containers consistently.


---

## Q12. What is Docker Hub?

### 1. English Definition

Docker Hub is a cloud-based container registry where users can find, download, store, and share Docker images. It hosts official images, community images, and private repositories.

### 2. Hindi Definition

Docker Hub ek online container registry hai jahan developers Docker images ko search, download, store aur share kar sakte hain. Ismein official images, community images aur private repositories available hoti hain.

### 3. Hinglish Explanation

Docker Hub ko Docker images ka online store samjho. Jaise aap Node.js install karne ke liye official Node.js image pull kar sakte ho, ya apni application ki image upload karke AWS server par download kar sakte ho.

Example:
- `node:20` — Node.js image.
- `nginx` — Nginx web server image.
- `docker push` — apni image Docker Hub par upload karna.
- `docker pull` — Docker Hub se image download karna.

Docker Hub ek **Docker registry** hai. Har registry Docker Hub nahi hoti; organizations apni private registry bhi chala sakti hain.

### 4. Practical Example / Code

**Step 1: Pull an image from Docker Hub.**

```bash
docker pull node:20
```

**Step 2: Build your application image (assuming a Dockerfile exists).**

```bash
docker build -t my-node-app:1.0 .
```

**Step 3: Log in to Docker Hub.**

```bash
docker login
```

**Step 4: Tag your image with your Docker Hub username.**

```bash
docker tag my-node-app:1.0 YOUR_DOCKERHUB_USERNAME/my-node-app:1.0
```

**Step 5: Push the image.**

```bash
docker push YOUR_DOCKERHUB_USERNAME/my-node-app:1.0
```

Replace `YOUR_DOCKERHUB_USERNAME` with your actual Docker Hub username.

### 5. Architecture Diagram

```text
 Developer / Local Machine
          |
   docker pull / push
          |
          v
   +-------------------+
   |     Docker Hub    |
   |                   |
   | Official Images   |
   | Public Repositories|
   | Private Repositories|
   +-------------------+
          |
   docker pull
          |
          v
     AWS / Server
   Run image as container
```

### 6. Practical Command / Configuration

**Search for images:** Use Docker Hub's website search or run:

```bash
docker search nginx
```

**Pull an image:**

```bash
docker pull nginx
```

**Check local images:**

```bash
docker images
```

**Sign in:**

```bash
docker login
```

### 7. Summary Table

| Term | Meaning |
|---|---|
| Docker Hub | Cloud-based container registry |
| Main purpose | Find, store and share images |
| Official image | Image published or maintained by the relevant official publisher |
| Pull | Download an image |
| Push | Upload an image |
| Private repository | Repository with restricted access |

**Interview-ready summary:**

> Docker Hub is a cloud-based container registry used to find, store, and share Docker images. Developers can pull existing images or push their own images for use on other machines and servers.


---

## Q13. What are the main benefits of Docker?

### 1. English Definition

Docker provides benefits such as portability, consistent environments, lightweight isolation, faster deployment, efficient resource utilization, scalability, and repeatable application delivery.

### 2. Hindi Definition

Docker ke main benefits hain application ko alag-alag environments mein consistently chalana, deployment ko fast banana, resources ka efficient use karna aur applications ko isolated containers mein run karna.

### 3. Hinglish Explanation

Docker ke benefits ko MERN application ke example se samjho:

1. **Portability:** Same image ko laptop, testing server aur AWS par run kar sakte ho, agar compatible environment ho.
2. **Consistency:** Node.js version aur dependencies image mein package ki ja sakti hain, isliye “mere laptop par chal raha hai” wali problem kam hoti hai.
3. **Lightweight:** Containers aam taur par VMs se kam resources use karte hain, kyunki Linux par host kernel share karte hain.
4. **Fast deployment:** Prebuilt image se container quickly start kiya ja sakta hai.
5. **Isolation:** Alag applications ko separate containers mein run kar sakte ho.
6. **Scalability:** Zaroorat ke mutabik same image se additional containers create kar sakte ho; orchestration tools scaling automate kar sakte hain.
7. **CI/CD support:** Build, test aur deployment pipelines mein same image artifact use kiya ja sakta hai.
8. **Reproducibility:** Versioned images se deployment ko repeat karna easier hota hai.

Docker har problem solve nahi karta: persistent storage, secrets, security, monitoring aur orchestration ko properly configure karna phir bhi zaroori hai.

### 4. Practical Example / Code

Build a versioned image:

```bash
docker build -t my-node-app:1.0 .
```

Run the same image as a container:

```bash
docker run -d --name my-app -p 5000:5000 my-node-app:1.0
```

The same tagged image can be pushed to a registry and pulled on a compatible server, helping keep environments consistent.

### 5. Architecture Diagram

```text
      MERN Application
              |
         Dockerfile
              |
         docker build
              |
              v
       Versioned Image
              |
       +------+------+
       |      |      |
       v      v      v
    Laptop  Testing  AWS
   Container Container Container
       |      |      |
       +-- Consistent packaged app --+
```

### 6. Practical Command / Configuration

**Build a versioned image:**

```bash
docker build -t my-node-app:1.0 .
```

**Run it:**

```bash
docker run -d --name my-app -p 5000:5000 my-node-app:1.0
```

**Check resource usage:**

```bash
docker stats
```

**Check running containers:**

```bash
docker ps
```

### 7. Summary Table

| Benefit | Explanation |
|---|---|
| Portability | Same image can run across compatible environments |
| Consistency | Packages runtime and dependencies |
| Lightweight | Typically less overhead than a full VM |
| Fast deployment | Containers can start quickly |
| Isolation | Applications run in separate container environments |
| Scalability | More instances can be created from the same image |
| CI/CD | Supports repeatable build and release pipelines |
| Reproducibility | Versioned images help repeat deployments |

**Interview-ready summary:**

> Docker makes application delivery more consistent and portable by packaging code and dependencies into images. It supports lightweight isolation, faster deployments, efficient resource usage, scaling, and repeatable CI/CD workflows.


---

## Q14. What is containerization?

### 1. English Definition

Containerization is a method of packaging an application and its required dependencies into an isolated container so it can run consistently across compatible environments.

### 2. Hindi Definition

Containerization ek process hai jisme application aur uski required dependencies ko container mein package kiya jata hai, taaki application different compatible environments mein consistently run kar sake.

### 3. Hinglish Explanation

Maan lo aapki MERN application local machine par sahi chal rahi hai, lekin testing ya production server par dependency versions ki wajah se issue aa raha hai.

Containerization mein aap application code, runtime aur required dependencies ko image mein package karte ho. Phir us image se container create karke application run kar sakte ho.

**Simple difference:**
- **Containerization:** Application ko container mein package aur isolate karne ka approach.
- **Docker:** Containerization ke liye commonly used platform/tooling.
- **Container:** Packaged application ko run karne wala isolated environment.

Linux containers aam taur par host OS kernel share karte hain, isliye ye full virtual machines se generally lightweight hote hain.

### 4. Practical Example / Code

A Node.js application's Dockerfile can package its runtime and dependencies:

```dockerfile
FROM node:20
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

Build an image and run a container:

```bash
docker build -t my-node-app:1.0 .
docker run -d --name my-app -p 5000:5000 my-node-app:1.0
```

Assumption: The project has a valid `package.json` with a `start` script, and the app listens on port 5000.

### 5. Architecture Diagram

```text
      Application Code
             +
      Runtime / Libraries
             |
             v
       Dockerfile
             |
        docker build
             |
             v
        Docker Image
             |
         docker run
             |
             v
     Isolated Container
       Running App
             |
       Compatible Host OS
```

### 6. Practical Command / Configuration

**Build the packaged image:**

```bash
docker build -t my-node-app:1.0 .
```

**Run the container:**

```bash
docker run -d --name my-app -p 5000:5000 my-node-app:1.0
```

**Check the running container:**

```bash
docker ps
```

### 7. Summary Table

| Term | Meaning |
|---|---|
| Containerization | Packaging and isolating an application with its dependencies |
| Docker | A platform used to build and run containers |
| Docker image | Packaged, reusable template |
| Docker container | Runtime instance of an image |
| Main benefit | Consistent application delivery across compatible environments |
| Kernel | Linux containers generally share the host kernel |

**Interview-ready summary:**

> Containerization is the process of packaging an application and its dependencies into an isolated container so it can run consistently across compatible environments, improving portability and deployment reliability.


---

## Q15. How does Docker work internally?

### 1. English Definition

Docker works through a client-server architecture. The Docker CLI sends requests to the Docker daemon through the Docker Engine API, and the daemon builds images, creates and manages containers, and works with registries. On Linux, containers use kernel features such as namespaces and control groups (cgroups) for isolation and resource management.

### 2. Hindi Definition

Docker client-server architecture par kaam karta hai. CLI se command daemon tak API ke through jaati hai. Docker daemon images build/pull karta hai, containers create aur manage karta hai. Linux par namespaces isolation aur cgroups resource limits manage karne mein help karte hain.

### 3. Hinglish Explanation

Maan lo aap command chalate ho:

`docker run -d -p 8080:80 nginx`

Internally broadly ye steps hote hain:

1. **CLI request:** Docker CLI command ko Docker Engine API ke through daemon tak bhejta hai.
2. **Image lookup:** Daemon local image cache check karta hai. Image nahi milti toh configured registry se pull kar sakta hai.
3. **Container setup:** Daemon image ke layers ke upar container ki writable layer configure karta hai.
4. **Isolation:** Linux par namespaces container ke process, network aur filesystem view ko isolate karte hain; cgroups resource usage ko control/measure karne mein help karte hain.
5. **Networking and ports:** Docker network configure karta hai aur `-p 8080:80` ke liye host port ko container port se publish karta hai.
6. **Process start:** Container ke configured command ko start kiya jata hai; yahan Nginx process run hota hai.

Important: Container ek lightweight isolated process environment hai, full virtual machine nahi. Containerization ke implementation details OS aur Docker configuration ke hisaab se differ kar sakte hain.

### 4. Practical Example / Code

Run Nginx:

```bash
docker run -d --name web -p 8080:80 nginx
```

Check the container:

```bash
docker ps
docker logs web
```

Inspect its configuration:

```bash
docker inspect web
```

Open `http://localhost:8080` in a browser to see the Nginx welcome page when the container starts successfully.

### 5. Architecture Diagram

```text
           User command
                |
                v
           Docker CLI
                |
        Docker Engine API
                |
                v
         Docker Daemon
           (dockerd)
                |
        +-------+--------+
        |                |
   Find / pull       Create container
   image             + writable layer
        |                |
        v                v
 Docker Registry     Namespaces / cgroups
                         |
                   Network + port mapping
                         |
                         v
                   Start app process
                      (Nginx)
```

### 6. Practical Command / Configuration

**Run a container with a published port:**

```bash
docker run -d --name web -p 8080:80 nginx
```

**Inspect its configuration and state:**

```bash
docker inspect web
```

**View resource usage:**

```bash
docker stats web
```

**View logs:**

```bash
docker logs web
```

### 7. Summary Table

| Component / Feature | Role |
|---|---|
| Docker CLI | User commands bhejta hai |
| Docker daemon | Docker resources aur lifecycle manage karta hai |
| Image layers | Packaged application files provide karti hain |
| Writable container layer | Container ke runtime filesystem changes store karti hai |
| Namespaces | Linux par process/network/mount jaise views isolate karte hain |
| cgroups | Linux par resource usage control/measure karte hain |
| Networking | Containers ko connect karta hai aur ports publish kar sakta hai |
| Registry | Images pull/push karne ki service |

**Interview-ready summary:**

> Docker CLI sends requests to the Docker daemon through the Engine API. The daemon obtains the image, configures the container's filesystem, isolation, networking, and resource controls, then starts the application process. On Linux, namespaces and cgroups provide key isolation and resource-management mechanisms.


---

### 2. Docker Commands

## Q16. How do you run a Docker container?

### 1. English Definition

You can run a Docker container using the `docker run` command followed by an image name. Docker creates a container from the image and starts its configured process.

### 2. Hindi Definition

Docker container run karne ke liye `docker run` command ke saath image ka naam dete hain. Docker us image se container create karke uska configured process start karta hai.

### 3. Hinglish Explanation

Sabse simple command hai:

`docker run nginx`

Agar Nginx image local machine par available nahi hai, Docker use registry se pull kar sakta hai. Uske baad container create karke Nginx start karta hai.

Common options:
- `-d`: container ko background mein run karta hai.
- `--name`: container ka custom naam set karta hai.
- `-p HOST_PORT:CONTAINER_PORT`: host port ko container port par publish karta hai.
- `--rm`: container exit hone ke baad automatically remove karta hai.

### 4. Practical Example / Code

**Run Nginx in the foreground:**

```bash
docker run nginx
```

**Run it in the background and publish port 8080:**

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Open `http://localhost:8080` to view the Nginx page if the container starts successfully.

**Run a temporary container and remove it when it exits:**

```bash
docker run --rm hello-world
```

### 5. Architecture Diagram

```text
       docker run nginx
              |
              v
        Docker CLI
              |
        Docker Daemon
              |
       Check / pull image
              |
       Create container
              |
       Start container process
              |
              v
        Running container
```

### 6. Practical Command / Configuration

**Check running containers:**

```bash
docker ps
```

**Check all containers, including stopped ones:**

```bash
docker ps -a
```

**View logs:**

```bash
docker logs my-nginx
```

**Stop the container:**

```bash
docker stop my-nginx
```

### 7. Summary Table

| Command / Option | Purpose |
|---|---|
| `docker run nginx` | Creates and starts a container from the Nginx image |
| `-d` | Runs in detached/background mode |
| `--name my-nginx` | Sets the container name |
| `-p 8080:80` | Publishes host port 8080 to container port 80 |
| `--rm` | Removes the container after it exits |
| `docker ps` | Lists running containers |

**Interview-ready summary:**

> A Docker container is run using `docker run IMAGE_NAME`. Docker obtains the image if needed, creates a container, and starts its configured process. Options such as `-d`, `--name`, and `-p` control how the container runs.


---

## Q17. What does the `docker run` command do?

### 1. English Definition

The `docker run` command creates and starts a new container from a specified Docker image. It can also configure options such as the container name, port mapping, environment variables, volume mounts, and detached mode.

### 2. Hindi Definition

`docker run` command ka use Docker image se ek naya container create karne aur use start karne ke liye hota hai. Is command ke through hum port mapping, container name, environment variables aur volumes jaise options bhi set kar sakte hain.

### 3. Hinglish Explanation

Amit, simple words mein samjho:

- **Image** application chalane ka template hoti hai.
- **Container** us image se create hua isolated environment hota hai.
- `docker run` image se container banata hai aur uske andar configured process start karta hai.

Agar image local system par nahi milti, to Docker daemon configured registry se image pull karne ki koshish karta hai. Uske baad container create karke start kiya jata hai.

Dhyan rahe: har baar `docker run` execute karne par aam taur par **naya container** create hota hai. Existing stopped container ko dobara start karne ke liye `docker start CONTAINER_NAME` use karte hain.

### 4. Practical Example / Code

Run an Nginx container:

```bash
docker run nginx
```

Run it in the background and map host port 8080 to container port 80:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Meaning of the options:

- `-d`: container ko background mein run karta hai.
- `--name my-nginx`: container ko ek readable name deta hai.
- `-p 8080:80`: host ke port 8080 ko container ke port 80 se map karta hai.
- `nginx`: image ka naam hai.

Ab browser mein `http://localhost:8080` open karke Nginx page check kar sakte hain, agar port available hai aur container successfully start ho gaya hai.

### 5. Architecture Diagram

```text
User runs: docker run nginx
             |
             v
        Docker CLI
             |
             v
       Docker daemon
             |
             v
    Is nginx image available?
       /             \\
     Yes              No
      |                |
      |          Pull image from
      |          configured registry
       \\              /
        v            v
        Create container
                |
                v
         Start container
                |
                v
       Nginx process runs
```

### 6. Practical Commands / Configuration

Check running containers:

```bash
docker ps
```

Check all containers, including stopped ones:

```bash
docker ps -a
```

View container logs:

```bash
docker logs my-nginx
```

Stop the container:

```bash
docker stop my-nginx
```

Start the existing stopped container again:

```bash
docker start my-nginx
```

Remove a container after it has stopped:

```bash
docker rm my-nginx
```

### 7. Summary Table

| Command / Option | Purpose |
|---|---|
| `docker run nginx` | Creates and starts a container from the Nginx image |
| `-d` | Runs the container in the background |
| `--name my-nginx` | Assigns a name to the container |
| `-p 8080:80` | Maps host port 8080 to container port 80 |
| `docker start my-nginx` | Starts an existing stopped container |
| `docker ps` | Lists running containers |

**Interview-ready answer:** The `docker run` command creates and starts a new container from a Docker image. It also supports runtime configuration such as port mapping, naming, environment variables, volume mounts, and detached mode.


---

## Q18. What does the `docker ps` command do?

### 1. English Definition

The `docker ps` command lists Docker containers that are currently running. You can use the `-a` option to list all containers, including stopped containers.

### 2. Hindi Definition

`docker ps` command ka use currently running Docker containers ki list dekhne ke liye hota hai. Agar running aur stopped dono tarah ke containers dekhne hain, toh `docker ps -a` use karte hain.

### 3. Hinglish Explanation

Amit, jab aap multiple containers run karte ho, toh `docker ps` se pata chalta hai kaun-kaun se containers abhi running hain. Output mein container ID, image name, command, creation time, status, ports aur container name jaise details milti hain.

Yaad rakho:

- `docker ps` → sirf running containers.
- `docker ps -a` → running, stopped aur other existing containers.
- `docker ps -q` → sirf container IDs.

### 4. Practical Example / Code

Pehle ek Nginx container start karo:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Running containers dekho:

```bash
docker ps
```

Possible output:

```text
CONTAINER ID   IMAGE   COMMAND                  STATUS         PORTS                  NAMES
a1b2c3d4e5f6   nginx   "/docker-entrypoint…"    Up 10 seconds  0.0.0.0:8080->80/tcp   my-nginx
```

Output values example ke liye hain; aapke system par IDs, status aur ports alag ho sakte hain.

Stopped containers samet sabhi containers dekho:

```bash
docker ps -a
```

### 5. Architecture Diagram

```text
User runs: docker ps
        |
        v
    Docker CLI
        |
        v
   Docker daemon
        |
        v
Retrieve container information
        |
        v
Display running containers
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker ps` | Lists running containers |
| `docker ps -a` | Lists all containers, including stopped ones |
| `docker ps -q` | Displays only running container IDs |
| `docker ps --filter "status=exited"` | Filters containers whose status is exited |
| `docker ps --format "{{.Names}} {{.Status}}"` | Displays container names and statuses |

### 7. Summary Table

| Command | What it shows |
|---|---|
| `docker ps` | Running containers only |
| `docker ps -a` | All existing containers |
| `docker ps -q` | IDs of running containers |
| `docker ps --filter "status=exited"` | Containers with exited status |

**Interview-ready answer:** The `docker ps` command lists currently running Docker containers and displays details such as container ID, image, status, ports, and name. Use `docker ps -a` to include stopped containers as well.


---

## Q19. What does the `docker ps -a` command do?

### 1. English Definition

The `docker ps -a` command lists all Docker containers on the host, including running, stopped, and exited containers. It displays details such as container ID, image, status, ports, and name.

### 2. Hindi Definition

`docker ps -a` command ka use system par maujood sabhi Docker containers dekhne ke liye hota hai—chahe container running ho, stopped ho, ya exit ho chuka ho.

### 3. Hinglish Explanation

Amit, `docker ps` aur `docker ps -a` ka main difference yaad rakho:

- `docker ps`: sirf currently running containers dikhata hai.
- `docker ps -a`: running aur stopped/exited containers samet sabhi existing containers dikhata hai.

Maan lo aapne ek Nginx container run kiya aur baad mein stop kar diya. `docker ps` mein woh nahi dikhega, lekin `docker ps -a` mein uska status `Exited` ke saath dikh sakta hai. Stopped container ki information tab tak rehti hai jab tak container remove nahi kiya jata.

### 4. Practical Example / Code

Create and start a container:

```bash
docker run -d --name my-nginx nginx
```

Stop it:

```bash
docker stop my-nginx
```

List only running containers:

```bash
docker ps
```

The stopped container will not appear in this list. To see it, run:

```bash
docker ps -a
```

Example output:

```text
CONTAINER ID   IMAGE   COMMAND                  STATUS                     NAMES
a1b2c3d4e5f6   nginx   "/docker-entrypoint…"    Exited (0) 5 seconds ago   my-nginx
```

Output is illustrative; your container ID and status may differ.

### 5. Architecture Diagram

```text
User runs: docker ps -a
           |
           v
       Docker CLI
           |
           v
      Docker daemon
           |
           v
  Retrieve all existing containers
           |
           v
  Show running + stopped + exited
           containers
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker ps` | Shows running containers only |
| `docker ps -a` | Shows all existing containers |
| `docker ps -a -q` | Shows IDs of all existing containers |
| `docker ps -a --filter "status=exited"` | Filters exited containers |
| `docker start my-nginx` | Starts the existing stopped container |
| `docker rm my-nginx` | Removes a stopped container |

### 7. Summary Table

| Container state | `docker ps` | `docker ps -a` |
|---|---|---|
| Running | Shown | Shown |
| Stopped / Exited | Hidden | Shown |
| Removed | Hidden | Hidden |

**Interview-ready answer:** The `docker ps -a` command lists all existing Docker containers, including running and stopped containers. It is useful for checking a container's status and finding containers that are no longer running.


---

## Q20. How do you stop a container?

### 1. English Definition

You can stop a running Docker container using the `docker stop` command followed by the container name or ID. Docker normally sends a termination signal to the container's main process and waits briefly before forcefully stopping it if necessary.

### 2. Hindi Definition

Running Docker container ko stop karne ke liye `docker stop` command use karte hain. Iske baad container ka naam ya container ID dete hain.

### 3. Hinglish Explanation

Amit, maan lo aapka `my-nginx` naam ka container chal raha hai. Use stop karne ke liye:

```bash
docker stop my-nginx
```

Docker pehle container ke main process ko gracefully terminate hone ka signal deta hai. Agar process configured timeout ke andar stop nahi hota, toh Docker use forcefully stop kar sakta hai.

**Important:** `docker stop` container ko stop karta hai, delete nahi. Stopped container ko baad mein `docker start` se dobara start kar sakte ho.

### 4. Practical Example / Code

Start a container:

```bash
docker run -d --name my-nginx nginx
```

Stop it by name:

```bash
docker stop my-nginx
```

You can also stop it by container ID:

```bash
docker ps
docker stop <container_id>
```

Verify the result:

```bash
docker ps
docker ps -a
```

The container should no longer appear in `docker ps`, but it should appear in `docker ps -a` with a stopped/exited status unless it has been removed.

### 5. Architecture Diagram

```text
docker stop my-nginx
          |
          v
     Docker CLI
          |
          v
    Docker daemon
          |
          v
 Send termination signal
          |
          v
 Container process exits
          |
          v
    Container stopped
    (not deleted)
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker stop my-nginx` | Stops a container by name |
| `docker stop <container_id>` | Stops a container by ID |
| `docker stop -t 30 my-nginx` | Waits up to 30 seconds before forceful termination if needed |
| `docker ps` | Checks currently running containers |
| `docker ps -a` | Checks all existing containers |
| `docker start my-nginx` | Starts the stopped container again |
| `docker kill my-nginx` | Forcefully stops a container |

### 7. Summary Table

| Command | What it does |
|---|---|
| `docker stop` | Gracefully stops a running container, with a timeout |
| `docker kill` | Forcefully stops a container |
| `docker start` | Starts an existing stopped container |
| `docker rm` | Removes a container; normally it must be stopped first |

**Interview-ready answer:** Use `docker stop CONTAINER_NAME` or `docker stop CONTAINER_ID` to stop a running container. Docker requests graceful termination first and may forcefully stop it if the timeout expires. Stopping a container does not delete it.


---

## Q21. How do you start a container?

### 1. English Definition

The `docker start` command starts an existing stopped Docker container. You provide the container name or ID. To create and start a new container from an image, use `docker run` instead.

### 2. Hindi Definition

Pehle se created aur stopped Docker container ko dobara start karne ke liye `docker start` command use karte hain. Is command mein container ka naam ya ID dete hain.

### 3. Hinglish Explanation

Amit, yahan do commands ka difference samajhna important hai:

- `docker start my-nginx`: pehle se bana hua stopped container dobara start karta hai.
- `docker run nginx`: image se naya container create karke start karta hai.

Agar container ko `docker stop` se stop kiya tha, toh use wapas start karne ke liye `docker start` use kar sakte ho. Container remove ho chuka hai, toh usi container ko start nahi kar sakte; naya container create karna hoga.

### 4. Practical Example / Code

Create and start a container:

```bash
docker run -d --name my-nginx nginx
```

Stop the container:

```bash
docker stop my-nginx
```

Start the same container again:

```bash
docker start my-nginx
```

Verify that it is running:

```bash
docker ps
```

You can also use the container ID:

```bash
docker start <container_id>
```

### 5. Architecture Diagram

```text
docker start my-nginx
          |
          v
     Docker CLI
          |
          v
    Docker daemon
          |
          v
 Find existing container
          |
          v
 Start its configured process
          |
          v
   Container running
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker start my-nginx` | Starts an existing stopped container |
| `docker start <container_id>` | Starts a container by ID |
| `docker start -a my-nginx` | Starts the container and attaches to its output |
| `docker ps` | Lists running containers |
| `docker ps -a` | Lists all existing containers |
| `docker run -d --name my-nginx nginx` | Creates and starts a new container |

### 7. Summary Table

| Situation | Command |
|---|---|
| Start an existing stopped container | `docker start my-nginx` |
| Create and start a new container | `docker run -d --name my-nginx nginx` |
| Check running containers | `docker ps` |
| Check all containers | `docker ps -a` |

**Interview-ready answer:** The `docker start` command starts an existing stopped container using its name or ID. Unlike `docker run`, it does not create a new container.


---

## Q22. How do you restart a container?

### 1. English Definition

The `docker restart` command stops and then starts an existing Docker container. You can specify the container by its name or ID.

### 2. Hindi Definition

Docker container ko restart karne ke liye `docker restart` command use karte hain. Yeh existing container ko pehle stop karta hai aur phir dobara start karta hai.

### 3. Hinglish Explanation

Amit, maan lo aapka `my-nginx` container running hai aur aap use restart karna chahte ho. Aapko alag se stop aur start commands chalane ki zaroorat nahi hai. Ek hi command use kar sakte ho:

```bash
docker restart my-nginx
```

Docker container ko stop karke dobara start karega. Container ka writable layer aur configured volumes normally preserve rehte hain, kyunki container delete nahi hota. Application restart ke dauran kuch time ke liye unavailable ho sakti hai.

### 4. Practical Example / Code

Create and run a container:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Restart the container:

```bash
docker restart my-nginx
```

Check its status:

```bash
docker ps
```

You can also restart it using its container ID:

```bash
docker restart <container_id>
```

To configure the wait time before Docker forcefully stops a container that does not stop gracefully:

```bash
docker restart -t 30 my-nginx
```

### 5. Architecture Diagram

```text
docker restart my-nginx
          |
          v
    Docker daemon
          |
          v
  Stop existing container
          |
          v
  Start the same container
          |
          v
    Container running
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker restart my-nginx` | Restarts a container by name |
| `docker restart <container_id>` | Restarts a container by ID |
| `docker restart -t 30 my-nginx` | Uses a 30-second stop timeout before forceful termination if needed |
| `docker stop my-nginx` | Stops the container |
| `docker start my-nginx` | Starts an existing stopped container |
| `docker ps` | Checks currently running containers |

### 7. Summary Table

| Command | Action |
|---|---|
| `docker stop` | Stops a container |
| `docker start` | Starts an existing stopped container |
| `docker restart` | Stops and starts the same container |
| `docker run` | Creates and starts a new container |

**Interview-ready answer:** Use `docker restart CONTAINER_NAME` or `docker restart CONTAINER_ID` to restart a container. Docker stops the existing container and starts it again without creating a new container.


---

## Q23. How do you remove a container?

### 1. English Definition

The `docker rm` command removes an existing Docker container. A container generally must be stopped before it can be removed; use `docker rm -f` only when you intentionally want to force-remove a running container.

### 2. Hindi Definition

Docker container ko remove karne ke liye `docker rm` command use karte hain. Normally, container ko remove karne se pehle stop karna hota hai.

### 3. Hinglish Explanation

Amit, yahan teen commands ka difference samjho:

- `docker stop my-nginx` → container stop karta hai, delete nahi.
- `docker rm my-nginx` → stopped container remove karta hai.
- `docker rm -f my-nginx` → running container ko bhi forcefully stop karke remove kar sakta hai.

Container remove karne par us container ka writable layer aur container metadata delete ho jata hai. Named volumes ko `docker rm` normally delete nahi karta, lekin container ke andar sirf writable layer mein stored data remove ho sakta hai. Zaroori data ko volumes ya backups mein rakho.

### 4. Practical Example / Code

Create a container:

```bash
docker run -d --name my-nginx nginx
```

Stop the container:

```bash
docker stop my-nginx
```

Remove the stopped container:

```bash
docker rm my-nginx
```

Verify that it has been removed:

```bash
docker ps -a
```

To force-remove a running container, if that is intentional:

```bash
docker rm -f my-nginx
```

### 5. Architecture Diagram

```text
docker rm my-nginx
        |
        v
   Docker daemon
        |
        v
 Is container stopped?
      /       \\
    Yes        No
     |          |
     v          v
 Remove it   Command fails
                |
                v
       Stop it, then retry
       (or intentionally use
          docker rm -f)
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker stop my-nginx` | Stops the container |
| `docker rm my-nginx` | Removes a stopped container |
| `docker rm -f my-nginx` | Force-removes a container, including a running one |
| `docker rm -v my-nginx` | Removes the container and anonymous volumes associated with it; named volumes are not removed by this option |
| `docker ps -a` | Lists all existing containers |
| `docker container prune` | Removes all stopped containers after confirmation |

### 7. Summary Table

| Command | Result |
|---|---|
| `docker stop` | Stops but keeps the container |
| `docker rm` | Removes a stopped container |
| `docker rm -f` | Force-removes a container |
| `docker container prune` | Removes all stopped containers |

**Interview-ready answer:** Use `docker rm CONTAINER_NAME` or `docker rm CONTAINER_ID` to remove a stopped container. To remove a running container, `docker rm -f` can be used intentionally. Removing a container is different from stopping it, and important data should be stored in volumes or backed up.


---

## Q24. How do you list Docker images?

### 1. English Definition

The `docker images` command lists Docker images stored locally on the host. The equivalent modern command is `docker image ls`.

### 2. Hindi Definition

Local system par available Docker images ki list dekhne ke liye `docker images` ya `docker image ls` command use karte hain.

### 3. Hinglish Explanation

Amit, image aur container mein difference yaad rakho:

- **Image:** Application run karne ka template.
- **Container:** Image se create hua running ya stopped instance.

Jab aap `docker images` run karte ho, toh local machine par available images ke repository names, tags, image IDs, creation information aur sizes dikhte hain. Is command se registry ki saari images list nahi hoti—sirf local images dikhte hain.

### 4. Practical Example / Code

List local images:

```bash
docker images
```

Equivalent command:

```bash
docker image ls
```

Example output:

```text
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
nginx        latest    a1b2c3d4e5f6   2 days ago     190MB
node         22        f6e5d4c3b2a1   5 days ago     1.1GB
```

The IDs, dates, and sizes above are illustrative and may differ on your system.

If an image is not available locally, pull it first:

```bash
docker pull nginx
docker images
```

### 5. Architecture Diagram

```text
User runs: docker images
          |
          v
      Docker CLI
          |
          v
     Docker daemon
          |
          v
 Read local image inventory
          |
          v
 Display repositories, tags,
 image IDs, and sizes
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker images` | Lists local Docker images |
| `docker image ls` | Modern equivalent to list local images |
| `docker images nginx` | Lists local images matching the nginx repository |
| `docker images -q` | Displays local image IDs |
| `docker pull nginx` | Downloads the Nginx image from a registry |
| `docker image inspect nginx` | Shows detailed metadata for an image |

### 7. Summary Table

| Command | What it shows |
|---|---|
| `docker images` | Local images |
| `docker image ls` | Local images |
| `docker images -q` | Image IDs only |
| `docker pull nginx` | Downloads an image; it does not list images |

**Interview-ready answer:** Use `docker images` or `docker image ls` to list Docker images available locally. The output includes the repository, tag, image ID, creation information, and size. It does not list every image available in a remote registry.


---

## Q25. How do you remove a Docker image?

### 1. English Definition

The `docker rmi` command removes one or more Docker images from the local host. Its modern equivalent is `docker image rm`. An image may not be removable while it is referenced by existing containers; those dependencies may need to be removed first.

### 2. Hindi Definition

Local system se Docker image remove karne ke liye `docker rmi` ya `docker image rm` command use karte hain. Agar kisi existing container ko woh image use karne ke liye reference kiya gaya hai, toh image remove karne se pehle us dependency ko handle karna pad sakta hai.

### 3. Hinglish Explanation

Amit bhai, image aur container alag cheezein hain:

- **Image:** Application ka template.
- **Container:** Image se bana instance.

Example: Agar aapke local system par Nginx image hai aur aap use remove karna chahte ho:

```bash
docker rmi nginx
```

Agar image kisi existing container ke through referenced hai, toh Docker image removal reject kar sakta hai. Zaroorat ho toh container ko stop karke remove karo, phir image remove karo. Dhyan rahe, container remove karne se uske writable layer ka data lose ho sakta hai.

### 4. Practical Example / Code

List local images:

```bash
docker images
```

Check whether a container uses the image:

```bash
docker ps -a
```

If the container is no longer needed, stop and remove it:

```bash
docker stop my-nginx
docker rm my-nginx
```

Remove the image:

```bash
docker rmi nginx
```

Equivalent modern command:

```bash
docker image rm nginx
```

Verify the result:

```bash
docker images
```

### 5. Architecture Diagram

```text
docker rmi nginx
       |
       v
  Docker daemon
       |
       v
Check image references
       |
       v
Can the image be removed?
       |
   Yes | No
       |  \\
       v   v
 Remove   Resolve container
 image    references first
       |
       v
Image no longer listed locally
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker rmi nginx` | Removes a local image by repository/tag |
| `docker image rm nginx` | Modern equivalent to remove an image |
| `docker rmi <image_id>` | Removes an image by ID |
| `docker images` | Lists local images |
| `docker ps -a` | Lists all containers that may reference an image |
| `docker image prune` | Removes dangling images |
| `docker image prune -a` | Removes images not referenced by any container; review carefully before confirming |

### 7. Summary Table

| Command | Action |
|---|---|
| `docker rmi nginx` | Removes a local image |
| `docker image rm nginx` | Same image-removal operation |
| `docker image prune` | Removes dangling images |
| `docker image prune -a` | Removes images not used by any container |

**Interview-ready answer:** Use `docker rmi IMAGE_NAME` or `docker image rm IMAGE_NAME` to remove a local Docker image. If a container references the image, Docker may require you to remove that dependency first. Be careful with prune commands because they can remove multiple images.


---

## Q27. How do you check container logs?

### 1. English Definition

The `docker logs` command displays the logs produced by a container's main process through its standard output (stdout) and standard error (stderr). Options such as `-f` let you follow new log entries in real time.

### 2. Hindi Definition

Docker container ke application logs dekhne ke liye `docker logs` command use karte hain. Isse container ke main process ke stdout aur stderr par aane wale messages dekh sakte hain.

### 3. Hinglish Explanation

Amit bhai, maan lo aapka Node.js backend Docker container mein run ho raha hai aur API error aa rahi hai. Aap container ke logs check karke samajh sakte ho ki application kya output de rahi hai aur error message kya hai.

- `docker logs my-api` → available logs show karta hai.
- `docker logs -f my-api` → naye logs ko real time mein follow karta hai.
- `docker logs --tail 100 my-api` → last 100 log lines dikhata hai.

Note: `docker logs` tabhi useful output dikhayega jab application apne logs stdout/stderr par likhti ho aur container ka logging setup un logs ko capture karta ho. Agar application sirf kisi internal file mein logs likhti hai, toh us file ko alag se inspect karna pad sakta hai.

### 4. Practical Example / Code

Run a sample container:

```bash
docker run -d --name my-nginx nginx
```

View its logs:

```bash
docker logs my-nginx
```

Follow logs live:

```bash
docker logs -f my-nginx
```

Show only the last 100 lines:

```bash
docker logs --tail 100 my-nginx
```

Show logs with timestamps:

```bash
docker logs -t my-nginx
```

Stop following live logs with `Ctrl+C`; this normally stops the log-following command, not the container itself.

### 5. Architecture Diagram

```text
Application runs inside container
              |
              v
Writes messages to stdout / stderr
              |
              v
Docker logging mechanism
              |
              v
docker logs my-nginx
              |
              v
Logs displayed in terminal
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker logs my-nginx` | Displays available container logs |
| `docker logs -f my-nginx` | Follows new log entries live |
| `docker logs --tail 100 my-nginx` | Shows the last 100 lines |
| `docker logs -t my-nginx` | Includes timestamps |
| `docker logs --since 10m my-nginx` | Shows logs from the last 10 minutes |
| `docker logs --until 2026-10-11T12:00:00 my-nginx` | Limits logs to entries before the specified time |

### 7. Summary Table

| Option | Meaning |
|---|---|
| No option | Show available logs |
| `-f` | Follow logs live |
| `--tail 100` | Show last 100 lines |
| `-t` | Include timestamps |
| `--since 10m` | Show recent logs from the specified time window |

**Interview-ready answer:** Use `docker logs CONTAINER_NAME` or `docker logs CONTAINER_ID` to inspect a container's stdout and stderr output. Use `docker logs -f` to follow logs in real time and `docker logs --tail 100` to view only the latest 100 lines.


---

## Q28. How do you execute a command inside a container?

### 1. English Definition

The `docker exec` command runs a command inside an already-running Docker container. It is commonly used for troubleshooting, inspecting files, or opening an interactive shell.

### 2. Hindi Definition

Running Docker container ke andar koi command execute karne ke liye `docker exec` command use karte hain. Isse container ke andar shell open kar sakte hain ya directly koi command chala sakte hain.

### 3. Hinglish Explanation

Amit bhai, maan lo aapka `my-nginx` container already running hai aur aap uske andar files check karna chahte ho. Container ko stop ya recreate karne ki zaroorat nahi hai—`docker exec` use karo.

- `docker exec my-nginx ls` → container ke andar `ls` command run karta hai.
- `docker exec -it my-nginx sh` → interactive shell open karta hai.
- `-i` input open rakhta hai aur `-t` terminal allocate karta hai.

Yaad rakho: `docker exec` ke liye container running hona chahiye. Container ke andar shell available na ho, toh `sh` ya `bash` command fail ho sakti hai.

### 4. Practical Example / Code

Run an Nginx container:

```bash
docker run -d --name my-nginx nginx
```

Execute a command inside it:

```bash
docker exec my-nginx nginx -v
```

Open an interactive shell (if `sh` is available):

```bash
docker exec -it my-nginx sh
```

Once inside the container, you can run commands such as:

```bash
ls
pwd
exit
```

For a container that has Bash installed, you can use:

```bash
docker exec -it my-nginx bash
```

### 5. Architecture Diagram

```text
docker exec -it my-nginx sh
            |
            v
        Docker CLI
            |
            v
       Docker daemon
            |
            v
  Find running container
            |
            v
  Execute shell / command
  inside the container
            |
            v
   Display command output
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker exec my-nginx nginx -v` | Runs a command inside the container |
| `docker exec -it my-nginx sh` | Opens an interactive shell |
| `docker exec -it my-nginx bash` | Opens Bash if installed |
| `docker exec -u root -it my-nginx sh` | Opens a shell as root, if permitted |
| `docker exec -w /etc/nginx my-nginx pwd` | Runs a command from a specified working directory |
| `docker ps` | Checks which containers are running |

### 7. Summary Table

| Option / Command | Purpose |
|---|---|
| `docker exec` | Executes a command in a running container |
| `-i` | Keeps standard input open |
| `-t` | Allocates a terminal |
| `sh` | Opens a shell when available |
| `bash` | Opens Bash when installed |

**Interview-ready answer:** The `docker exec` command runs a new command inside an already-running container. For example, `docker exec -it my-nginx sh` opens an interactive shell when the container has `sh` available. Unlike `docker run`, it does not create a new container.


---

## Q29. How do you expose or map a container port?

### 1. English Definition

You publish a container port to make a containerized application's port accessible through the Docker host, typically using the `-p` or `--publish` option with `docker run`. The Dockerfile `EXPOSE` instruction documents the port an application is intended to listen on, but does not publish it by itself.

### 2. Hindi Definition

Container ke andar chal rahi application ko host machine ke port ke through access karne ke liye `docker run -p` use karte hain. Dockerfile mein `EXPOSE` likhne se port document hota hai, lekin port automatically host par publish nahi hota.

### 3. Hinglish Explanation

Amit bhai, maan lo aapka Nginx container ke andar port `80` par run ho raha hai. Host machine ke browser se use access karne ke liye port mapping kar sakte ho:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Iska meaning:

- `8080` = host machine ka port.
- `80` = container ke andar application ka port.
- `-p 8080:80` = host port 8080 ko container port 80 se map karta hai.

Ab browser mein `http://localhost:8080` open kar sakte ho, provided port 8080 available hai aur container successfully running hai.

**Important difference:**
- `EXPOSE 80` in a Dockerfile: port ka documentation/metadata.
- `-p 8080:80` at runtime: actual port publishing/mapping.

### 4. Practical Example / Code

Run Nginx with host port 8080 mapped to container port 80:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Open:

```text
http://localhost:8080
```

Example Dockerfile:

```dockerfile
FROM nginx
EXPOSE 80
```

The `EXPOSE 80` instruction documents that the image's service is intended to listen on port 80. To publish that port when running the container, still use `-p`, for example:

```bash
docker run -d -p 8080:80 my-nginx-image
```

### 5. Architecture Diagram

```text
Browser / Client
      |
      v
Host machine: port 8080
      |
      | Docker port mapping (-p 8080:80)
      v
Container: port 80
      |
      v
Nginx application
```

### 6. Practical Commands / Configuration

| Command / Instruction | Purpose |
|---|---|
| `docker run -p 8080:80 nginx` | Publishes host port 8080 to container port 80 |
| `docker run -p 80:80 nginx` | Maps host port 80 to container port 80 |
| `docker run -p 127.0.0.1:8080:80 nginx` | Publishes the port only on host loopback |
| `docker run -P nginx` | Publishes ports declared with `EXPOSE` to dynamically assigned host ports |
| `EXPOSE 80` | Documents the container port in a Dockerfile; does not publish it by itself |
| `docker port my-nginx` | Shows published port mappings for a container |

### 7. Summary Table

| Term | Meaning |
|---|---|
| Container port | Port where the application listens inside the container |
| Host port | Port used to access the service through the Docker host |
| `-p HOST:CONTAINER` | Publishes/maps a specific host port to a container port |
| `EXPOSE` | Documents an intended container port; does not publish it by itself |
| `-P` | Publishes exposed ports to dynamically assigned host ports |

**Interview-ready answer:** Use the `-p` or `--publish` option with `docker run` to map a host port to a container port, for example, `docker run -d -p 8080:80 nginx`. The Dockerfile instruction `EXPOSE 80` documents the intended container port but does not publish it on its own.


---

## Q30. How do you pull a Docker image?

### 1. English Definition

The `docker pull` command downloads a Docker image from a container registry, such as Docker Hub, to the local machine. You can specify an image tag to pull a particular version.

### 2. Hindi Definition

Docker registry, jaise Docker Hub, se image ko apne local system par download karne ke liye `docker pull` command use karte hain.

### 3. Hinglish Explanation

Amit bhai, maan lo aapko apne project ke liye Nginx ya Node.js ki image chahiye, lekin woh local machine par available nahi hai. Aap registry se image pull kar sakte ho.

Example:

```bash
docker pull nginx
```

By default, agar tag specify nahi kiya gaya, toh Docker aam taur par `latest` tag use karta hai. Specific version chahiye toh tag mention karo, jaise `nginx:1.27` (agar woh tag registry mein available ho).

**Important:** `docker pull` sirf image download karta hai; container create ya start nahi karta. Container run karne ke liye `docker run` use karo.

### 4. Practical Example / Code

Pull the default Nginx image:

```bash
docker pull nginx
```

Pull a specific tag:

```bash
docker pull nginx:1.27
```

Check locally available images:

```bash
docker images
```

Create and start a container from the downloaded image:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

The exact tag availability may change; choose a tag that exists in the registry and is suitable for your project.

### 5. Architecture Diagram

```text
User runs: docker pull nginx
             |
             v
         Docker CLI
             |
             v
        Docker daemon
             |
             v
   Contact container registry
          (e.g., Docker Hub)
             |
             v
     Download image layers
             |
             v
    Store image locally
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker pull nginx` | Pulls the default Nginx image tag |
| `docker pull nginx:1.27` | Pulls a specified Nginx tag, if available |
| `docker pull node:22` | Pulls the Node.js image with tag 22 |
| `docker images` | Lists local images after pulling |
| `docker image inspect nginx` | Shows details about a local image |
| `docker run nginx` | Creates and starts a container from an image |

### 7. Summary Table

| Command | Action |
|---|---|
| `docker pull nginx` | Downloads an image |
| `docker pull nginx:1.27` | Downloads a specific tag |
| `docker images` | Lists local images |
| `docker run nginx` | Creates and starts a container |

**Interview-ready answer:** Use `docker pull IMAGE_NAME[:TAG]` to download an image from a container registry to your local machine. For example, `docker pull nginx` downloads the default Nginx tag. Pulling an image does not itself create or start a container.


---

## Q31. How do you push a Docker image?

### 1. English Definition

The `docker push` command uploads a tagged Docker image from your local machine to a container registry such as Docker Hub. You generally need permission to push to the destination repository.

### 2. Hindi Definition

Local machine par bani Docker image ko Docker Hub ya kisi doosri container registry mein upload karne ke liye `docker push` command use karte hain.

### 3. Hinglish Explanation

Amit bhai, maan lo aapne apne Node.js backend ki image `mern-backend:1.0` banayi. Ab aap chahte ho ki team ya AWS server us image ko download kar sake. Pehle registry mein login karo, image ko apne repository name se tag karo, phir push karo.

- `docker login` → registry mein authenticate karta hai.
- `docker tag` → existing image ko registry-compatible repository name aur tag deta hai.
- `docker push` → image ke required layers aur manifest registry mein upload karta hai.

**Important:** `docker push` image upload karta hai, container ko run ya deploy nahi karta. Credentials aur registry repository permissions sahi hone chahiye.

### 4. Practical Example / Code

Suppose your Docker Hub username is `mydockeruser` and you have built a local image named `mern-backend:1.0`.

Build the image (run in the folder containing your Dockerfile):

```bash
docker build -t mern-backend:1.0 .
```

Log in:

```bash
docker login
```

Tag the image for your Docker Hub repository:

```bash
docker tag mern-backend:1.0 mydockeruser/mern-backend:1.0
```

Push the tagged image:

```bash
docker push mydockeruser/mern-backend:1.0
```

On another machine, download it:

```bash
docker pull mydockeruser/mern-backend:1.0
```

Replace `mydockeruser` with your actual Docker Hub username and ensure you can push to that repository.

### 5. Architecture Diagram

```text
Dockerfile + application
          |
          v
 docker build -t mern-backend:1.0 .
          |
          v
    Local Docker image
          |
          v
docker tag ... mydockeruser/mern-backend:1.0
          |
          v
       docker login
          |
          v
docker push mydockeruser/mern-backend:1.0
          |
          v
 Docker Hub / container registry
          |
          v
Other machine: docker pull ...
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker build -t mern-backend:1.0 .` | Builds a local image |
| `docker login` | Authenticates to the registry |
| `docker tag mern-backend:1.0 mydockeruser/mern-backend:1.0` | Tags the image for the target repository |
| `docker push mydockeruser/mern-backend:1.0` | Pushes the image to Docker Hub |
| `docker images` | Lists locally available images |
| `docker pull mydockeruser/mern-backend:1.0` | Downloads the pushed image |

### 7. Summary Table

| Command | Action |
|---|---|
| `docker build` | Creates an image locally |
| `docker login` | Signs in to a registry |
| `docker tag` | Assigns a repository name and tag |
| `docker push` | Uploads an image to a registry |
| `docker pull` | Downloads an image from a registry |

**Interview-ready answer:** To push a Docker image, first authenticate with `docker login`, tag the local image for the target registry using `docker tag`, and upload it with `docker push REPOSITORY:TAG`. For example, `docker push mydockeruser/mern-backend:1.0` uploads that tagged image to Docker Hub if you have permission.


---

## Q32. How do you build a Docker image?

### 1. English Definition

The `docker build` command builds a Docker image from a Dockerfile and a build context. The image contains the application code, dependencies, and configuration instructions needed to create a container.

### 2. Hindi Definition

Docker image banane ke liye `docker build` command use karte hain. Is command mein Dockerfile aur build context use hota hai, jisme application code aur required files ho sakti hain.

### 3. Hinglish Explanation

Amit bhai, maan lo aapka Node.js backend project hai. Aap chahte ho ki application Docker container mein run ho. Iske liye pehle Dockerfile likhte hain, phir `docker build` command se image banate hain.

- **Dockerfile:** Image banane ke instructions.
- **Build context:** Files ka woh set jo Docker build process ko available hota hai; aksar current directory `.` hoti hai.
- **Docker image:** Build ka output, jisse baad mein container create kiya ja sakta hai.

### 4. Practical Example / Code

Example Node.js project structure:

```text
mern-backend/
├── Dockerfile
├── package.json
├── package-lock.json
└── server.js
```

Example Dockerfile:

```dockerfile
FROM node:22
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

Build the image from the directory containing the Dockerfile:

```bash
docker build -t mern-backend:1.0 .
```

Meaning:
- `-t mern-backend:1.0`: image ka name aur tag set karta hai.
- `.`: current directory ko build context banata hai.

Check the image:

```bash
docker images
```

Run a container from the image:

```bash
docker run -d --name mern-backend-container -p 5000:5000 mern-backend:1.0
```

This example assumes `package.json` has a working `start` script and the app listens on port 5000. For real projects, add a suitable `.dockerignore` file to exclude items such as `node_modules`, local environment files, and Git metadata from the build context. Avoid copying secrets into the image.

### 5. Architecture Diagram

```text
Application code + dependencies
              |
              v
         Dockerfile
              |
              v
docker build -t mern-backend:1.0 .
              |
              v
       Docker build process
              |
              v
      Docker image created
              |
              v
          docker run
              |
              v
       Running container
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker build -t app:1.0 .` | Builds an image and assigns a name/tag |
| `docker build -f Dockerfile.dev -t app:dev .` | Uses a specific Dockerfile |
| `docker images` | Lists local images |
| `docker image inspect app:1.0` | Shows image metadata |
| `docker run app:1.0` | Creates and starts a container from the image |
| `docker build --no-cache -t app:1.0 .` | Builds without using cached build layers |

### 7. Summary Table

| Item | Purpose |
|---|---|
| Dockerfile | Defines image build instructions |
| Build context | Provides files available to the build |
| `docker build` | Builds the image |
| `-t app:1.0` | Assigns image name and tag |
| `docker run` | Creates and starts a container from the image |

**Interview-ready answer:** We use `docker build -t IMAGE_NAME:TAG .` to build a Docker image from a Dockerfile and the specified build context. For example, `docker build -t mern-backend:1.0 .` creates an image named `mern-backend` with tag `1.0`, which can then be used to run a container.


---

## Q33. What is the difference between `docker exec` and `docker attach`?

### 1. English Definition

`docker exec` runs a new command inside an already-running container, while `docker attach` connects your terminal to the container's existing main process (its standard input, output, and error streams).

### 2. Hindi Definition

`docker exec` running container ke andar ek naya command ya shell chalata hai. `docker attach` container ke already-running main process ke input/output se terminal ko connect karta hai.

### 3. Hinglish Explanation

Amit bhai, main difference yeh hai:

- **`docker exec`**: Container ke andar ek separate command run karna, jaise shell open karke files check karna.
- **`docker attach`**: Container ke main process ka existing output dekhna aur, agar input enabled ho, uske saath interact karna.

Example: Nginx container ke andar shell chahiye toh `docker exec -it my-nginx sh` use karo. Agar container ka main process output dekhna hai, toh `docker attach my-nginx` use kar sakte ho.

**Important:** Attached terminal mein `Ctrl+C` press karna container ke main process ko interrupt kar sakta hai, aur isse container stop ho sakta hai. Sirf detach karna ho toh default key sequence `Ctrl+P`, phir `Ctrl+Q` hai, provided detach keys override nahi ki gayi hain.

### 4. Practical Example / Code

Start an Nginx container:

```bash
docker run -d --name my-nginx nginx
```

Run a separate command inside the running container:

```bash
docker exec my-nginx nginx -v
```

Open an interactive shell, if `sh` is available:

```bash
docker exec -it my-nginx sh
```

Attach to the container's main process streams:

```bash
docker attach my-nginx
```

For a background Nginx container, attaching may not provide an interactive shell; it connects to the main process streams. To detach without stopping the container, use `Ctrl+P` followed by `Ctrl+Q` by default.

### 5. Architecture Diagram

```text
                 Running container
                 /              \\
                /                \\
       docker exec              docker attach
            |                        |
            v                        v
  Start a separate command    Connect to existing
  (e.g. shell or diagnostic)   main process streams
            |                        |
            v                        v
   Separate command output      Main process output
```

### 6. Practical Commands / Configuration

| Command | Purpose |
|---|---|
| `docker exec -it my-nginx sh` | Starts a separate interactive shell inside the container |
| `docker exec my-nginx nginx -v` | Runs a one-off command inside the container |
| `docker attach my-nginx` | Connects terminal to the main process streams |
| `docker logs -f my-nginx` | Follows logs without attaching terminal input to the main process |
| `Ctrl+P`, then `Ctrl+Q` | Detaches from an attached container by default without stopping it |

### 7. Summary Table

| Feature | `docker exec` | `docker attach` |
|---|---|---|
| Main purpose | Runs a new command | Connects to the existing main process |
| Starts a separate command? | Yes | No |
| Common use | Shell, debugging, diagnostic commands | Interacting with or viewing the main process streams |
| Requires a running container? | Yes | Container must be running |
| Safe way to leave session | Exit the shell/command | Default detach sequence: `Ctrl+P`, then `Ctrl+Q` |

**Interview-ready answer:** `docker exec` runs a new command inside a running container, such as opening a shell for debugging. `docker attach` connects to the container's existing main process streams. Use `docker exec` when you need a separate shell or command without attaching to the main process.
