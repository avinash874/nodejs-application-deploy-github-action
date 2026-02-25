# Want to make this
✅ Create a Node.js app
✅ Push to GitHub
✅ Add GitHub Actions (CI/CD)
✅ Deploy on Render (instead of Hostinger)
✅ Use Docker

# 🚀 STEP 1: Fix Your Project Structure
First, fix small issues in your code.

✅ 1. Fix package.json
You cannot have "type" twice.
Use this:
```fs
{
  "name": "nodejs-application-deploy-github-action",
  "version": "1.0.0",
  "description": "Node.js CI/CD Demo",
  "license": "ISC",
  "type": "module",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^5.2.1"
  }
}
```

# Your Dockerfile
```fs
FROM node:22-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
CMD ["node", "index.js"
```

# 🚀 STEP 2: Test Locally
🔹 Run without Docker
```fs
npm install
npm start
```

# 🔹 Run with Docker

Build image:
```fs
docker build -t node-app .
```

Run container:
```fs
docker run -p 8080:8080 node-app
```

# 🚀 STEP 3: Push to GitHub
🔹 1. Create Repo on GitHub

Go to:
👉 https://github.com

Click → New Repository

# 🚀 STEP 4: Add GitHub Actions (CI/CD)
Now we create automation.
Create folder:

```fs
.github/workflows/ci.yml
```

```fs
name: Node CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 22

      - name: Install Dependencies
        run: npm install

      - name: Run Application Test
        run: echo "App build successful!"
```
Now whenever you push → GitHub automatically runs CI.

# 🚀 STEP 5: Deploy on Render (Instead of Hostinger)
Now production deployment.

# 🚀 STEP 6: Auto Deploy on Every Push

* Render automatically redeploys when:
You push new code to main branch
So flow becomes:

```fs
You push code →
GitHub →
GitHub Actions runs →
Render auto redeploys →
Live site updated
```
This is REAL CI/CD 🔥

# 🔥 Complete Architecture
```fs
Local Development
        ↓
GitHub Repo
        ↓
GitHub Actions (CI)
        ↓
Render (CD - Deployment)
        ↓
Live Production URL
```

# 🧠 What You Learned
This project teaches you:

Node.js production setup
Docker
Git
GitHub Actions
CI/CD
Cloud deployment
Environment variables
Production port handlin