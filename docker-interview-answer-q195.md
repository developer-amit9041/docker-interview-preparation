# Q195. How would you ensure MongoDB is ready before the Node.js backend connects to it?

## English Definition
Use a Docker Compose health check to verify MongoDB is responding, then configure the backend to depend on MongoDB with `condition: service_healthy`. The Node.js application should also handle connection failures and retries.

## 1. Understand the Problem
A container being started does not mean the application inside it is ready. MongoDB may still be initializing when Node.js tries to connect. This is a startup race condition.

## 2. Docker Compose Configuration

```yaml
services:
  mongo:
    image: mongo:7
    volumes:
      - mongo_data:/data/db
    healthcheck:
      test: ["CMD", "mongosh", "--quiet", "127.0.0.1:27017/test", "--eval", "db.adminCommand('ping').ok"]
      interval: 5s
      timeout: 3s
      retries: 10
      start_period: 10s

  backend:
    build: ./backend
    environment:
      MONGODB_URI: mongodb://mongo:27017/myapp
    depends_on:
      mongo:
        condition: service_healthy
    restart: unless-stopped

volumes:
  mongo_data:
```

## 3. How It Works
1. Compose starts MongoDB.
2. The health check runs `mongosh` and executes a ping command.
3. If MongoDB is not ready, the check fails and Compose keeps checking.
4. Once MongoDB reports healthy, Compose starts the backend.
5. The backend connects using `mongodb://mongo:27017/myapp`.

The example assumes the official MongoDB 7 image, which includes `mongosh`. The ping succeeds when `db.adminCommand('ping').ok` returns 1.

## 4. Why Not Only depends_on?

Short syntax:

```yaml
depends_on:
  - mongo
```

This controls startup order but does not wait for MongoDB readiness.

Health-aware syntax:

```yaml
depends_on:
  mongo:
    condition: service_healthy
```

This waits for the dependency's health check to pass before starting the backend.

## 5. Node.js Connection Handling

Example using Mongoose:

```js
const mongoose = require("mongoose");

async function connectDatabase() {
  const uri = process.env.MONGODB_URI;
  if (!uri) throw new Error("MONGODB_URI is not configured");

  await mongoose.connect(uri, {
    serverSelectionTimeoutMS: 5000,
  });

  console.log("MongoDB connected successfully");
}

connectDatabase().catch((err) => {
  console.error("MongoDB connection failed:", err.message);
  process.exit(1);
});
```

Here the process exits on initial connection failure; `restart: unless-stopped` allows Docker to restart the backend container. For more controlled production behavior, use bounded or exponential-backoff retries. Avoid a tight infinite retry loop.

A Compose health check helps coordinate startup, but MongoDB can still become unavailable later. Handle runtime disconnects and reconnection too.

## 6. Run and Verify

```bash
docker compose up -d --build
docker compose ps
docker compose logs -f mongo
docker compose logs -f backend
docker inspect --format='{{json .State.Health}}' <mongo_container_name>
```

## 7. Common Mistakes
- **Only using short depends_on:** it does not guarantee readiness; use `condition: service_healthy`.
- **Checking only whether the container is running:** verify MongoDB responds to a ping.
- **Using localhost from the backend:** localhost refers to the backend container itself; use `mongo:27017` when both services share a network and the Compose service is named `mongo`.
- **Assuming readiness means permanent availability:** handle later connection failures too.

## 8. Interview-Ready Answer
“I would configure a MongoDB health check in Docker Compose and set the Node.js backend's depends_on condition to service_healthy. The health check can use mongosh to execute a ping command. Compose waits for MongoDB to become healthy before starting the backend. I would also implement connection-error handling and retry logic because the database can become unavailable after startup.”

## Quick Revision
- **Problem:** Started container does not mean ready application.
- **Health check:** Verifies MongoDB is responding.
- **service_healthy:** Waits for the dependency's health check to pass.
- **Short depends_on:** Startup ordering only.
- **Connection URI:** `mongodb://mongo:27017/myapp`.
- **Reliability:** Handle runtime failures and retry safely.

```text
Compose starts MongoDB
        |
        v
Health check runs ping
        |
   Healthy?
   /      \\
 No        Yes
 |          |
Retry    Start backend
             |
             v
    Connect to mongo:27017
```
