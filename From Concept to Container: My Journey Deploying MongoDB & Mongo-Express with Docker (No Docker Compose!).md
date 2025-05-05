### 🔥 Real-World Skills, Real Results — A Cloud Engineer’s Perspective

In cloud engineering, we often celebrate smooth deployments—but the real growth lies in the challenges we troubleshoot along the way. This project is a perfect example of that. I set out to containerize and connect a backend database (**MongoDB**) and a frontend admin interface (**Mongo Express**) using Docker. The twist? I chose not to use Docker Compose. I wanted to master every part of the networking, environment configuration, and volume persistence manually—because that’s how pros sharpen their edge.

Let’s dive into the steps I followed, the problems I solved, and how I ensured my data persisted—even after destroying and recreating my containers.

---

### 📌 Step 1: Create a Docker Network

First, I created a custom bridge network to allow seamless communication between my containers.

```bash
docker network create jamiu-network
```

---

### 🧱 Step 2: Deploy the MongoDB Container

Here, I launched MongoDB with a mounted volume to persist data. This step ensures that even if the container is deleted, the data will remain intact.

```bash
docker run -d \
  --name mongo-database \
  --network jamiu-network \
  -p 27017:27017 \
  -v mongo-data:/data/db \
  -e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
  -e MONGO_INITDB_ROOT_PASSWORD=secret \
  mongo
```

**Key Takeaway:**
Notice the `-v mongo-data:/data/db` line—that’s the magic of Docker volumes doing the heavy lifting for persistence.

---

### 🌐 Step 3: Deploy Mongo Express

Now, I deployed Mongo Express and connected it to my MongoDB container through the custom network. This acts as a simple frontend for interacting with my database.

```bash
docker run -it -d \
  --network jamiu-network \
  --name mongo-express \
  -p 8085:8081 \
  -e ME_CONFIG_OPTIONS_EDITORTHEME="ambiance" \
  -e ME_CONFIG_MONGODB_SERVER="mongo-database" \
  -e ME_CONFIG_MONGODB_ADMINUSERNAME="mongoadmin" \
  -e ME_CONFIG_MONGODB_ADMINPASSWORD="secret" \
  -e ME_CONFIG_BASICAUTH_USERNAME="user" \
  -e ME_CONFIG_BASICAUTH_PASSWORD="fairly long password" \
  mongo-express
```





Access Mongo Express at:
🌍 **[http://localhost:8085](http://localhost:8085)**


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yr8a8d3grcjl08epuqge.png)

The view for Mongo-express
---

### ⚔️ Real Talk: Troubleshooting Was My Superpower

Was it smooth sailing? Absolutely not.

Mongo Express initially failed to connect. The logs screamed:
`Name does not resolve` and `mongo:27017 Invalid argument`.

The issue? I had incorrectly set the MongoDB hostname. Instead of using `"mongo-database"`—which is the container name and acts as the hostname inside the Docker network—I had used `"mongo"`.

Once I corrected the `ME_CONFIG_MONGODB_SERVER` value to match the actual MongoDB container name, everything clicked.

🧠 **Lesson:** Troubleshooting isn't a skill—it's a *superpower*. It’s what separates a "deployer" from a real **Cloud Engineer**.

---

### 🧪 Step 4: Test Volume Persistence Like a Pro

After confirming the Mongo Express interface was working, I connected to the Mongo shell inside the container and added some test data:

```bash
docker exec -it mongo-database mongosh -u mongoadmin -p secret
```

Inside Mongo shell:

```js
use testdb
db.testcollection.insertOne({ name: "Bakre", skill: "Cloud Engineering" })
db.testcollection.find()
```

Then came the real test.

```bash
# Delete the running container
docker rm -f mongo-database

# Recreate it with the same volume
docker run -d \
  --name mongo-database \
  --network jamiu-network \
  -p 27017:27017 \
  -v mongo-data:/data/db \
  -e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
  -e MONGO_INITDB_ROOT_PASSWORD=secret \
  mongo
```

Connected again...
And guess what? 🎉

```js
db.testcollection.find()
```

The data was still there. My volume was working perfectly. **Data persisted!**

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wb1zgwjrj1zzqb67i2ru.png)
---

### 🚀 Final Thoughts: This Is Cloud Engineering

This project was more than deploying containers. It was about thinking like a professional Cloud Engineer:

* Building infrastructure with intention
* Debugging under pressure
* Validating persistence
* Embracing the long road for deeper mastery

Every Founder, CTO, and DevOps team needs people who don’t just know tools, but understand *systems*. If you're looking for someone who’s not afraid of broken logs, bad connections, or late-night debugging—I’m your guy.

🔧 **Cloud isn’t just my skillset. It’s my mindset.**

Let’s connect.


