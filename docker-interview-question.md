# Docker Interview Questions — Topic-wise (180 Questions)

This is the original 180-question list, organized into 13 topics from fundamentals to scenario-based interview questions.

### 🔥 1. Docker Fundamentals

1. Docker kya hai?
2. Docker ki need kyu hoti hai?
3. Docker aur Virtual Machine (VM) mein kya difference hai?
4. Docker Container kya hota hai?
5. Docker Image kya hoti hai?
6. Docker Image aur Container mein kya difference hai?
7. Docker Engine kya hai?
8. Docker Architecture kya hai?
9. Docker Client kya hai?
10. Docker Daemon kya hai?
11. Docker Registry kya hoti hai?
12. Docker Hub kya hai?
13. Docker ke main benefits kya hain?
14. Containerization kya hoti hai?
15. Docker kaise internally kaam karta hai?

### 🔥 2. Docker Commands

16. Docker container kaise run karte hain?
17. `docker run` kya karta hai?
18. `docker ps` kya karta hai?
19. `docker ps -a` kya karta hai?
20. Container ko stop kaise karte hain?
21. Container ko start kaise karte hain?
22. Container restart kaise karte hain?
23. Container delete kaise karte hain?
24. Docker image kaise list karte hain?
25. Docker image ko delete kaise karte hain?
26. Running container ke andar kaise enter karte hain?
27. Container ke logs kaise check karte hain?
28. Container ke andar command kaise execute karte hain?
29. Docker container ka port kaise expose/map karte hain?
30. Docker image ko pull kaise karte hain?
31. Docker image ko push kaise karte hain?
32. Docker image build kaise karte hain?
33. `docker exec` vs `docker attach`?
34. `docker stop` vs `docker kill`?
35. `docker rm` vs `docker rmi`?

### 🔥 3. Dockerfile

36. Dockerfile kya hoti hai?
37. Dockerfile kyu use karte hain?
38. Dockerfile ka basic structure kya hota hai?
39. `FROM` instruction kya karta hai?
40. `RUN` kya karta hai?
41. `CMD` kya karta hai?
42. `ENTRYPOINT` kya karta hai?
43. `COPY` vs `ADD`?
44. `WORKDIR` kya karta hai?
45. `EXPOSE` kya karta hai?
46. `ENV` kya karta hai?
47. `ARG` kya hota hai?
48. `ENV` vs `ARG`?
49. `USER` instruction kya karta hai?
50. `VOLUME` kya karta hai?
51. Dockerfile mein multiple `RUN` kyu avoid karte hain?
52. Dockerfile ko optimize kaise karte hain?
53. `.dockerignore` kya hai?
54. Dockerfile mein comments kaise likhte hain?
55. Dockerfile mein Node.js application kaise containerize karenge?

### 🔥 4. Docker Image

56. Docker image kaise create hoti hai?
57. Docker image ke layers kya hote hain?
58. Docker image layers kaise kaam karti hain?
59. Image size kaise reduce karenge?
60. Docker image caching kya hoti hai?
61. Docker image ko tag kaise karte hain?
62. Docker image ko Docker Hub par kaise push karenge?
63. Docker image aur Docker container ka relationship kya hai?
64. Base image kya hoti hai?
65. Alpine image kya hoti hai?
66. Alpine image use karne ke advantages kya hain?
67. Docker image ko inspect kaise karenge?
68. Dangling images kya hoti hain?
69. Docker image pruning kya hoti hai?

### 🔥 5. Container

70. Container lifecycle kya hota hai?
71. Container restart hone par data ka kya hota hai?
72. Container ke andar files kaise copy karenge?
73. Container se host machine mein file kaise copy karenge?
74. Container networking kya hoti hai?
75. Container mein environment variables kaise pass karenge?
76. Container ko background mein kaise run karenge?
77. Detached mode `-d` kya hota hai?
78. Interactive mode `-it` kya hota hai?
79. Container health check kya hota hai?
80. `HEALTHCHECK` kya karta hai?

### 🔥 6. Docker Volumes

81. Docker Volume kya hai?
82. Volume ki need kyu hoti hai?
83. Container delete hone par data kaise preserve karenge?
84. Docker Volume vs Bind Mount?
85. Named Volume kya hota hai?
86. Anonymous Volume kya hota hai?
87. Volume create kaise karenge?
88. Volume ko container ke saath kaise attach karenge?
89. MongoDB ke data ko Docker mein kaise persist karenge?

### 🔥 7. Docker Networking

90. Docker Network kya hota hai?
91. Docker ke different network drivers kaunse hain?
92. Bridge network kya hai?
93. Host network kya hai?
94. None network kya hai?
95. Container-to-container communication kaise hoti hai?
96. Docker container ek dusre ko hostname se kaise access karte hain?
97. Docker mein port mapping kya hoti hai?
98. `EXPOSE 5000` aur `-p 5000:5000` mein difference?
99. Docker network create kaise karenge?
100. Same Docker network mein React aur Node containers kaise communicate karenge?

### 🔥 8. Docker Compose ⭐ Very Important

101. Docker Compose kya hai?
102. Docker Compose kyu use karte hain?
103. `docker-compose.yml` kya hoti hai?
104. Docker Compose aur Docker mein kya difference hai?
105. Docker Compose se multiple containers kaise run karenge?
106. `services` kya hota hai?
107. `ports` kya hota hai?
108. `environment` kya hota hai?
109. `volumes` kya hota hai?
110. `networks` kya hota hai?
111. `depends_on` kya karta hai?
112. Docker Compose mein MongoDB kaise setup karenge?
113. Docker Compose mein Node.js + MongoDB kaise connect karenge?
114. Docker Compose mein React + Node + MongoDB kaise setup karenge?
115. `docker compose up` vs `docker compose up -d`?
116. `docker compose down` kya karta hai?
117. `docker compose build` kya karta hai?
118. `docker compose restart` kya karta hai?
119. Docker Compose mein environment variables kaise manage karenge?
120. Docker Compose mein volume persistence kaise implement karenge?

### 🔥 9. Docker + MERN ⭐⭐⭐

121. MERN application ko Dockerize kaise karenge?
122. React application ke liye Dockerfile kaise banayenge?
123. Node.js/Express application ke liye Dockerfile kaise banayenge?
124. MongoDB ko Docker container mein kaise run karenge?
125. React container Node container ko kaise access karega?
126. Node container MongoDB container ko kaise access karega?
127. `localhost` Docker container mein problem kyu karta hai?
128. MERN application ke liye Docker Compose kaise likhenge?
129. Docker mein MongoDB data persist kaise karenge?
130. MERN application mein environment variables kaise manage karenge?
131. Docker mein frontend aur backend ko separate containers mein kyu rakhte hain?
132. Dockerized MERN app ko AWS EC2 par kaise deploy karenge?
133. Dockerized MERN application ke saamne Nginx kaise use karenge?
134. Docker + Nginx + Node.js architecture explain karo.
135. Dockerized MERN application ko Kubernetes par kaise deploy karenge?

### 🔥 10. Docker Security

136. Docker containers ko secure kaise karenge?
137. Container ko root user ke bina kaise run karenge?
138. Docker secrets kya hote hain?
139. Docker mein passwords/secrets kaise manage karenge?
140. Docker image vulnerabilities kya hoti hain?
141. Docker image scan kaise karenge?
142. Container security ke best practices kya hain?
143. Docker socket kya hai?
144. Docker socket expose karna risky kyu hai?

### 🔥 11. Docker Performance & Optimization

145. Docker image size kaise reduce karenge?
146. Multi-stage Docker build kya hota hai?
147. Multi-stage build kyu use karte hain?
148. Docker build cache kya hota hai?
149. Docker container memory limit kaise set karenge?
150. Docker CPU limit kaise set karenge?
151. Docker containers ke resource usage ko kaise monitor karenge?
152. Docker image ko optimize kaise karenge?
153. Production Dockerfile aur development Dockerfile mein kya difference hai?

### 🔥 12. Advanced / Production Questions

154. Docker Swarm kya hai?
155. Docker Swarm vs Kubernetes?
156. Docker Compose vs Kubernetes?
157. Docker orchestration kya hoti hai?
158. Container orchestration ki need kyu hoti hai?
159. Docker mein scaling kaise karenge?
160. Horizontal scaling kya hoti hai?
161. Docker mein rolling update kya hota hai?
162. Container health check kyu important hai?
163. Docker logging kaise manage karenge?
164. Docker container crash hone par kya hota hai?
165. Container automatically restart kaise karte hain?
166. Restart policies kya hoti hain?
167. `restart: always` kya karta hai?
168. Docker production mein kaise use karte hain?
169. Docker CI/CD pipeline mein kaise use hota hai?
170. GitHub Actions + Docker kaise integrate karenge?

### 🔥 13. Scenario-Based Questions ⭐⭐⭐

171. **Container mein Node.js application chal rahi hai but MongoDB connect nahi ho raha. Debug kaise karoge?**
172. **Docker container immediately exit ho raha hai. Reason kaise find karoge?**
173. **Application local machine par chal rahi hai but Docker mein nahi. Kya check karoge?**
174. **Container ke andar `localhost` kaam kyu nahi kar raha?**
175. **Docker image bahut large hai. Size kaise reduce karoge?**
176. **Container restart hone ke baad MongoDB ka data disappear ho gaya. Fix kaise karoge?**
177. **Docker container mein port accessible nahi hai. Kya check karoge?**
178. **Two containers ek dusre se communicate nahi kar rahe. Kaise debug karoge?**
179. **Docker build bahut slow hai. Kaise optimize karoge?**
180. **Production mein Docker container baar-baar crash ho raha hai. Kaise debug karoge?**
