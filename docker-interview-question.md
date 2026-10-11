### 14. Docker: Real-World MERN Deployment Questions

These questions focus on how Docker is used to build, run, connect, and deploy a MERN application in real-world projects. They complement the Kubernetes deployment questions by focusing on containers, Dockerfiles, Docker Compose, networking, persistence, and production operations.

181. How would you Dockerize a complete MERN application for local development?
182. How would you design the Docker architecture for React, Node.js/Express, and MongoDB?
183. Would you use one container or separate containers for the frontend, backend, and database? Why?
184. How would you write a production-ready Dockerfile for a React frontend?
185. How would you write a production-ready Dockerfile for a Node.js/Express backend?
186. Why would you use a multi-stage build for a React application?
187. How would you serve a React production build using Nginx in Docker?
188. How would you configure Nginx to route frontend requests and proxy `/api` requests to the backend container?
189. How would you create a `compose.yaml` file for a React, Node.js, and MongoDB application?
190. How would the Node.js container connect to MongoDB through Docker Compose?
191. Why should the backend use the MongoDB service name instead of `localhost` in its connection string?
192. How would you expose the frontend to users while keeping MongoDB inaccessible from the public host?
193. How would you configure frontend and backend ports in a Dockerized MERN application?
194. How would you pass backend environment variables using Docker Compose?
195. Where would you store MongoDB credentials and other sensitive configuration in production?
196. How would you persist MongoDB data when its container is recreated or removed?
197. What is the difference between using a named volume and a bind mount for MongoDB in development and production?
198. How would you make sure the backend starts only after MongoDB is ready to accept connections?
199. Why is `depends_on` alone not always sufficient to guarantee that MongoDB is ready?
200. How would you add a health check to the Node.js backend or MongoDB service?
201. How would you rebuild and redeploy only the backend after changing Node.js code?
202. How would you use Docker Compose watch mode, bind mounts, or another workflow for backend hot reloading during development?
203. How would you keep development and production Docker Compose configurations separate?
204. How would you reduce the size and build time of Docker images for a MERN application?
205. How would you use `.dockerignore` to prevent files such as `node_modules`, `.env`, and Git history from entering the build context?
206. How would you tag and push frontend and backend images to Docker Hub or a container registry?
207. How would you deploy a Dockerized MERN application on an AWS EC2 instance?
208. How would you configure HTTPS and reverse proxying for a Dockerized MERN application in production?
209. How would you update a running MERN application with a new image while minimizing downtime?
210. How would you troubleshoot a backend container that cannot connect to MongoDB?
211. How would you debug a React frontend that works locally but cannot reach the backend after being containerized?
212. How would you investigate a container that repeatedly exits or restarts?
213. How would you debug a port-mapping problem when the application is running inside a container?
214. How would you inspect container logs, health status, and resource usage when a production issue occurs?
215. What would you change before moving a Dockerized MERN application from development to production?

### 14. MERN and Docker: Real-World Questions

These questions are especially important for a MERN developer because interviewers may ask how Docker is used in practical application development, containerization, networking, and production deployments.

181. How would you Dockerize a complete MERN application?

182. How would you create a Dockerfile for a React frontend?

183. How would you create a Dockerfile for a Node.js/Express backend?

184. How would you run MongoDB in a Docker container for a MERN application?

185. How would you run React, Node.js, and MongoDB as separate Docker containers?

186. Why would you use separate containers for the frontend, backend, and database?

187. How would you connect a React frontend container to a Node.js backend container?

188. How would the Node.js backend connect to MongoDB in Docker?

189. Why does `localhost` cause connection problems between Docker containers?

190. How would you configure environment variables for a Dockerized MERN application?

191. How would you store MongoDB credentials and other sensitive information securely?

192. How would you persist MongoDB data when a container is stopped, removed, or recreated?

193. How would you write a Docker Compose file for a complete MERN application?

194. How would you configure service names, ports, networks, and volumes in Docker Compose?

195. How would you ensure MongoDB is ready before the Node.js backend connects to it?

196. How would you use Nginx as a reverse proxy for a Dockerized MERN application?

197. How would you serve a React production build using Nginx inside Docker?

198. How would you optimize Docker images for a React and Node.js application using multi-stage builds?

199. How would you separate development and production configurations for a Dockerized MERN application?

200. How would you deploy a Dockerized MERN application on an AWS EC2 instance?

201. How would you push MERN application images to Docker Hub and run them on another server?

202. How would you update a Dockerized MERN application with a new version?

203. How would you configure container restart policies and health checks for a MERN application?

204. How would you troubleshoot a Node.js container that cannot connect to MongoDB?

205. How would you debug a React frontend that cannot communicate with the backend after Docker deployment?

206. How would you troubleshoot a Docker container that keeps restarting or exits immediately?

207. How would you configure HTTPS for a Dockerized MERN application in production?

208. How would you design a production-ready architecture for React, Node.js, and MongoDB using Docker?
