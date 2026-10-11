# Docker Interview Questions — Topic-wise

This question bank is organized from fundamentals to production scenarios, with a focus on Docker and MERN-stack developer interviews.

## 1. Docker Fundamentals
1. What is Docker?
2. Why do we use Docker?
3. What is containerization?
4. What is a Docker container?
5. What is a Docker image?
6. What is the difference between an image and a container?
7. What is Docker Engine?
8. Explain Docker architecture.
9. What is the Docker client?
10. What is the Docker daemon?
11. What is a Docker registry?
12. What is Docker Hub?
13. What are the main benefits of Docker?
14. How does Docker work internally?
15. What is the difference between Docker and a virtual machine?
16. What is the role of the Linux kernel in containers?
17. What are namespaces and cgroups?
18. Is Docker the same as Kubernetes?
19. What is container isolation?
20. What are common use cases for Docker?

## 2. Essential Docker Commands
21. How do you check the Docker version and system information?
22. What does `docker run` do?
23. What is the difference between `docker ps` and `docker ps -a`?
24. How do you stop, start, and restart a container?
25. How do you remove a container?
26. How do you list and remove images?
27. How do you pull an image from a registry?
28. How do you build an image from a Dockerfile?
29. How do you view container logs?
30. How do you follow logs in real time?
31. How do you execute a command inside a running container?
32. What is the difference between `docker exec` and `docker attach`?
33. What is the difference between `docker stop` and `docker kill`?
34. What is the difference between `docker rm` and `docker rmi`?
35. How do you copy files between a host and a container?
36. What do the `-d` and `-it` flags mean?
37. How do you inspect a container or image?
38. How do you monitor container resource usage?
39. What does `docker system df` show?
40. What do Docker prune commands remove, and what risks do they carry?

## 3. Dockerfile
41. What is a Dockerfile?
42. Explain the common instructions used in a Dockerfile.
43. What does `FROM` do?
44. What is the difference between `RUN`, `CMD`, and `ENTRYPOINT`?
45. What does `WORKDIR` do?
46. What is the difference between `COPY` and `ADD`?
47. What does `EXPOSE` do?
48. Does `EXPOSE` publish a port on the host?
49. What is the difference between `ARG` and `ENV`?
50. What does the `USER` instruction do?
51. What is the purpose of `VOLUME`?
52. What is `.dockerignore` and why is it important?
53. How does Dockerfile instruction order affect build caching?
54. Why should dependency manifests be copied before application source?
55. How do you write a Dockerfile for a Node.js application?
56. How do you run a container as a non-root user?
57. When should you use shell form versus exec form?
58. Can a Dockerfile contain multiple `CMD` instructions?
59. What happens when a runtime command overrides `CMD`?
60. What are common Dockerfile best practices?

## 4. Images and Image Builds
61. What is a base image?
62. What are image layers?
63. How does Docker build cache work?
64. What invalidates a cached build layer?
65. What is a multi-stage build?
66. Why are multi-stage builds useful?
67. How can you reduce Docker image size?
68. What is the difference between Alpine and slim images?
69. What is an image tag?
70. How do you tag and push an image to Docker Hub?
71. What is the difference between a tag and an image digest?
72. What are dangling images?
73. How do you inspect image history?
74. What is the difference between `docker build` and `docker build --no-cache`?
75. How would you make image builds more reproducible?

## 5. Containers and Lifecycle
76. Explain the lifecycle of a Docker container.
77. What happens when the main process inside a container exits?
78. Why does a container sometimes exit immediately?
79. How do you pass environment variables to a container?
80. What is a container restart policy?
81. What is the difference between `always`, `unless-stopped`, and `on-failure`?
82. What is a container health check?
83. How does the `HEALTHCHECK` instruction work?
84. Does a healthy status automatically restart an unhealthy container?
85. How do you set CPU and memory limits?
86. How do you find a container's exit code?
87. How do you rename a container?
88. Can multiple containers be created from the same image?
89. What is the difference between ephemeral containers and persistent data?
90. How do you debug a container without changing its image?

## 6. Volumes and Data Persistence
91. Why do containers need persistent storage?
92. What is a Docker volume?
93. What is the difference between a named and anonymous volume?
94. What is a bind mount?
95. What is the difference between a volume and a bind mount?
96. What is a tmpfs mount?
97. What happens to a named volume when a container is removed?
98. How do you create, inspect, and remove a volume?
99. How do you persist MongoDB data in Docker?
100. Why is a volume not a substitute for a backup?
101. How can file permissions cause volume issues?
102. When should you use a bind mount in development?
103. What does `docker compose down -v` do?
104. How do you back up and restore data stored in a volume?
105. How would you persist uploaded files in a production application?

## 7. Docker Networking
106. What is Docker networking?
107. What are the common Docker network drivers?
108. What is the default bridge network?
109. What is a user-defined bridge network?
110. What are host, none, and overlay networks?
111. What is port publishing or port mapping?
112. What is the difference between `EXPOSE 5000` and `-p 5000:5000`?
113. How do containers communicate with each other?
114. How does DNS-based service discovery work on a user-defined network?
115. Why does `localhost` inside a container not refer to another container?
116. How do you create and inspect a Docker network?
117. How can you connect an existing container to a network?
118. How do you troubleshoot a container networking issue?
119. Should a database container's port always be published to the host?
120. How would you isolate frontend, backend, and database services?

## 8. Docker Compose
121. What is Docker Compose?
122. Why use Compose for a multi-container application?
123. What is a Compose YAML file?
124. What are services, networks, and volumes in Compose?
125. What is the difference between `docker compose up` and `docker compose up -d`?
126. What does `docker compose down` do?
127. What is the purpose of `depends_on`?
128. Does `depends_on` alone guarantee that a database is ready?
129. How can a service health check be used with Compose?
130. How do you provide environment variables to Compose services?
131. How should secrets be handled in Compose?
132. How do you rebuild only a particular service?
133. How do you view logs for one service?
134. How do you execute a command inside a Compose service?
135. How do you persist database data using Compose?
136. How do you configure service-to-service communication?
137. What is the difference between Compose and Docker Swarm?
138. How do you use different Compose configurations for development and production?
139. How do you scale a Compose service, and what limitations should you know?
140. How do you troubleshoot a Compose application that fails to start?

## 9. Docker with MERN Stack
141. How would you Dockerize a MERN application?
142. Why should React, Node.js, and MongoDB usually be separate services?
143. How would you write a Dockerfile for an Express API?
144. How would you build and serve a React frontend using a multi-stage build?
145. How should a Node.js service connect to MongoDB in Compose?
146. Why should a backend container not use `localhost` as the MongoDB hostname?
147. How can browser-side React code reach a backend running in Docker?
148. How do you configure API URLs for development and production?
149. How do you persist MongoDB data in a MERN Docker setup?
150. How should application secrets and environment variables be managed?
151. How would you put Nginx in front of the frontend and backend?
152. How would you deploy a Dockerized MERN app to AWS?
153. How would you manage logs and health checks for a MERN deployment?
154. How would you update the API image without losing database data?
155. What changes are needed to prepare a local Compose setup for production?

## 10. Security and Best Practices
156. Why should containers run as non-root where possible?
157. Why should secrets not be baked into Docker images?
158. Why are Docker build arguments not a secure secret store?
159. What is image vulnerability scanning?
160. How do you keep base images and dependencies secure?
161. Why is exposing the Docker daemon socket dangerous?
162. What is the principle of least privilege for containers?
163. How can Linux capabilities be restricted?
164. How should registry credentials be managed?
165. What security checks belong in a Docker CI/CD pipeline?

## 11. Performance and Production
166. How do you optimize Docker build time?
167. How do you reduce the final image size?
168. What is the difference between development and production images?
169. How do you collect and centralize container logs?
170. How do you monitor container CPU and memory usage?
171. What is container orchestration?
172. What is Docker Swarm?
173. What is the difference between Docker Swarm and Kubernetes?
174. What is a rolling update?
175. How does a load balancer work with multiple application containers?

## 12. AWS, CI/CD, and Kubernetes
176. What is Amazon ECR?
177. How do you push a Docker image to Amazon ECR?
178. What are the differences between deploying containers on EC2, ECS, and EKS?
179. How do you use Docker in a GitHub Actions CI/CD pipeline?
180. What steps would you include in a secure image build-and-deploy pipeline?
181. How does Kubernetes use container images?
182. What are Pods, Deployments, and Services in Kubernetes?
183. How would you roll back a failed container deployment?
184. Where should production database data live when application containers are replaced?
185. What monitoring and alerting would you add to a containerized production system?

## 13. Scenario-Based Questions
186. A Node.js container cannot connect to MongoDB. How would you debug it?
187. A container exits immediately after startup. What would you check?
188. An app works on your laptop but fails in Docker. How would you investigate?
189. A service is running but is not reachable from the host. What would you check?
190. MongoDB data disappears after the container is removed. How would you prevent this?
191. Two containers cannot communicate. How would you troubleshoot the network?
192. A Docker image is several gigabytes in size. How would you reduce it?
193. Docker builds are slow in CI. How would you improve them?
194. A container repeatedly restarts in production. How would you find the root cause?
195. A frontend cannot call the backend when both run in Compose. What might be wrong?
196. A secret was accidentally committed into an image. What immediate steps would you take?
197. A database starts more slowly than the API. How should the application handle this?
198. A new image passes tests but fails after deployment. How would you roll back safely?
199. How would you deploy a MERN app with HTTPS, persistent data, and monitoring?
200. Describe a production Docker issue you solved, how you diagnosed it, and how you prevented recurrence.
