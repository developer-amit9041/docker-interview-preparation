# Docker Interview Questions — Topic-wise (180 Questions)

All questions are written in English and organized into 13 interview-preparation topics.

### 1. Docker Fundamentals
1. What is Docker?
2. Why do we need Docker?
3. What is the difference between Docker and a Virtual Machine (VM)?
4. What is a Docker container?
5. What is a Docker image?
6. What is the difference between a Docker image and a container?
7. What is Docker Engine?
8. What is Docker architecture?
9. What is the Docker client?
10. What is the Docker daemon?
11. What is a Docker registry?
12. What is Docker Hub?
13. What are the main benefits of Docker?
14. What is containerization?
15. How does Docker work internally?

### 2. Docker Commands
16. How do you run a Docker container?
17. What does the `docker run` command do?
18. What does the `docker ps` command do?
19. What does the `docker ps -a` command do?
20. How do you stop a container?
21. How do you start a container?
22. How do you restart a container?
23. How do you remove a container?
24. How do you list Docker images?
25. How do you remove a Docker image?
26. How do you enter a running container?
27. How do you check container logs?
28. How do you execute a command inside a container?
29. How do you expose or map a container port?
30. How do you pull a Docker image?
31. How do you push a Docker image?
32. How do you build a Docker image?
33. What is the difference between `docker exec` and `docker attach`?
34. What is the difference between `docker stop` and `docker kill`?
35. What is the difference between `docker rm` and `docker rmi`?

### 3. Dockerfile
36. What is a Dockerfile?
37. Why do we use a Dockerfile?
38. What is the basic structure of a Dockerfile?
39. What does the `FROM` instruction do?
40. What does the `RUN` instruction do?
41. What does the `CMD` instruction do?
42. What does the `ENTRYPOINT` instruction do?
43. What is the difference between `COPY` and `ADD`?
44. What does the `WORKDIR` instruction do?
45. What does the `EXPOSE` instruction do?
46. What does the `ENV` instruction do?
47. What is the `ARG` instruction?
48. What is the difference between `ENV` and `ARG`?
49. What does the `USER` instruction do?
50. What does the `VOLUME` instruction do?
51. Why should unnecessary multiple `RUN` instructions be avoided?
52. How do you optimize a Dockerfile?
53. What is a `.dockerignore` file?
54. How do you write comments in a Dockerfile?
55. How do you containerize a Node.js application using a Dockerfile?

### 4. Docker Images
56. How is a Docker image created?
57. What are Docker image layers?
58. How do Docker image layers work?
59. How do you reduce Docker image size?
60. What is Docker image caching?
61. How do you tag a Docker image?
62. How do you push a Docker image to Docker Hub?
63. What is the relationship between a Docker image and a container?
64. What is a base image?
65. What is an Alpine image?
66. What are the advantages of using Alpine images?
67. How do you inspect a Docker image?
68. What are dangling images?
69. What is Docker image pruning?

### 5. Containers
70. What is the container lifecycle?
71. What happens to data when a container is restarted?
72. How do you copy files into a container?
73. How do you copy files from a container to the host machine?
74. What is container networking?
75. How do you pass environment variables to a container?
76. How do you run a container in the background?
77. What does detached mode (`-d`) mean?
78. What does interactive mode (`-it`) mean?
79. What is a container health check?
80. What does the `HEALTHCHECK` instruction do?

### 6. Docker Volumes
81. What is a Docker volume?
82. Why do we need volumes?
83. How can you preserve data when a container is deleted?
84. What is the difference between a Docker volume and a bind mount?
85. What is a named volume?
86. What is an anonymous volume?
87. How do you create a volume?
88. How do you attach a volume to a container?
89. How do you persist MongoDB data in Docker?

### 7. Docker Networking
90. What is a Docker network?
91. What are the different Docker network drivers?
92. What is a bridge network?
93. What is host networking?
94. What is a none network?
95. How does container-to-container communication work?
96. How can Docker containers access each other by hostname?
97. What is port mapping in Docker?
98. What is the difference between `EXPOSE 5000` and `-p 5000:5000`?
99. How do you create a Docker network?
100. How can React and Node.js containers communicate on the same Docker network?

### 8. Docker Compose
101. What is Docker Compose?
102. Why do we use Docker Compose?
103. What is a `docker-compose.yml` file?
104. What is the difference between Docker Compose and Docker?
105. How do you run multiple containers using Docker Compose?
106. What does `services` mean in Docker Compose?
107. What does `ports` mean in Docker Compose?
108. What does `environment` mean in Docker Compose?
109. What does `volumes` mean in Docker Compose?
110. What does `networks` mean in Docker Compose?
111. What does `depends_on` do?
112. How do you set up MongoDB using Docker Compose?
113. How do you connect a Node.js application to MongoDB using Docker Compose?
114. How do you set up React, Node.js, and MongoDB using Docker Compose?
115. What is the difference between `docker compose up` and `docker compose up -d`?
116. What does `docker compose down` do?
117. What does `docker compose build` do?
118. What does `docker compose restart` do?
119. How do you manage environment variables in Docker Compose?
120. How do you implement volume persistence in Docker Compose?

### 9. Docker + MERN Stack
121. How do you Dockerize a MERN application?
122. How do you create a Dockerfile for a React application?
123. How do you create a Dockerfile for a Node.js/Express application?
124. How do you run MongoDB in a Docker container?
125. How can a React container access a Node.js container?
126. How can a Node.js container connect to a MongoDB container?
127. Why can using `localhost` cause problems inside Docker containers?
128. How do you write a Docker Compose file for a MERN application?
129. How do you persist MongoDB data in Docker?
130. How do you manage environment variables in a Dockerized MERN application?
131. Why are the frontend and backend usually placed in separate containers?
132. How do you deploy a Dockerized MERN application to AWS EC2?
133. How do you use Nginx in front of a Dockerized MERN application?
134. Explain the architecture of Docker, Nginx, and Node.js.
135. How do you deploy a Dockerized MERN application to Kubernetes?

### 10. Docker Security
136. How do you secure Docker containers?
137. How do you run a container without using the root user?
138. What are Docker secrets?
139. How do you manage passwords and secrets in Docker?
140. What are Docker image vulnerabilities?
141. How do you scan a Docker image for vulnerabilities?
142. What are the best practices for container security?
143. What is the Docker socket?
144. Why is exposing the Docker socket risky?

### 11. Docker Performance and Optimization
145. How do you reduce Docker image size?
146. What is a multi-stage Docker build?
147. Why do we use multi-stage builds?
148. What is the Docker build cache?
149. How do you set a memory limit for a Docker container?
150. How do you set a CPU limit for a Docker container?
151. How do you monitor Docker container resource usage?
152. How do you optimize a Docker image?
153. What is the difference between a production Dockerfile and a development Dockerfile?

### 12. Advanced and Production Questions
154. What is Docker Swarm?
155. What is the difference between Docker Swarm and Kubernetes?
156. What is the difference between Docker Compose and Kubernetes?
157. What is Docker orchestration?
158. Why do we need container orchestration?
159. How do you scale services in Docker?
160. What is horizontal scaling?
161. What is a rolling update in container deployments?
162. Why are container health checks important?
163. How do you manage Docker logging?
164. What happens when a Docker container crashes?
165. How do you configure a container to restart automatically?
166. What are Docker restart policies?
167. What does `restart: always` do?
168. How is Docker used in production?
169. How is Docker used in a CI/CD pipeline?
170. How do you integrate Docker with GitHub Actions?

### 13. Scenario-Based Questions
171. A Node.js application inside a container cannot connect to MongoDB. How would you debug the issue?
172. A Docker container exits immediately after starting. How would you find the cause?
173. An application works on the local machine but fails in Docker. What would you check?
174. Why might `localhost` not work as expected inside a Docker container?
175. A Docker image is too large. How would you reduce its size?
176. MongoDB data disappears after a container restarts. How would you fix the issue?
177. A port is not accessible on a Docker container. What would you check?
178. Two containers cannot communicate with each other. How would you debug the issue?
179. Docker image builds are very slow. How would you optimize them?
180. A Docker container keeps crashing in production. How would you debug it?

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
