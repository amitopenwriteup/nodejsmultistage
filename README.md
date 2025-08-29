

```markdown
# Node.js Multi-Stage Docker Project

This project demonstrates a **Node.js application** containerized using a **multi-stage Docker build**.  
The multi-stage build helps reduce image size by separating the build stage from the runtime stage.  

---

## 📂 Project Structure
```

.
├── Dockerfile
├── package.json
├── cloudbuild.yaml   # (optional: for GCP Cloud Build deployment)
├── public/           # static files
├── k8s/              # Kubernetes manifests
├── src/              # application source code
└── dist/             # compiled output after build

````

---

## 🐳 Dockerfile Breakdown

### Stage 1: Build Stage
- Uses **node:18** as the build environment.
- Installs dependencies.
- Builds the app into `/app/dist`.

### Stage 2: Production Stage
- Uses a **lightweight node:18-alpine** base image.
- Copies only the build artifacts (`/dist`) and `node_modules` from the build stage.
- Exposes port **3000**.
- Runs the app with:
  ```bash
  node dist/server.js
````

---

## 🚀 Getting Started

### 1. Build Docker Image

```bash
docker build -t my-node-app .
```

### 2. Run Container

```bash
docker run -p 3000:3000 my-node-app
```

App will be available at 👉 [http://localhost:3000](http://localhost:3000)

---

## ☁️ Deployment Options

* **Kubernetes**: Use the manifests in the `k8s/` folder.
* **Google Cloud Build**: Use `cloudbuild.yaml` for CI/CD pipeline integration.
* **Docker Hub / Artifact Registry**: Push your image for production use.

---

## 🛠 Scripts

* `npm install` → Install dependencies
* `npm run build` → Build the application
* `npm start` → Start app (in local dev mode)

---

## 📌 Notes

* The multi-stage build keeps the final image **lightweight**.
* Ensure that your **dist/server.js** file exists after build.
* Add environment variables as needed before deployment.

---

## 👤 Author

**amitopenwriteup**
📧 [amit@openwriteup.com](mailto:amit@openwriteup.com)

```

---

