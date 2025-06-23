# 🎧 Spotify Clone – DevSecOps with GitHub Actions & Kubernetes

This project is a full-stack **Spotify Clone** built with Node.js, React, and MongoDB Atlas, deployed on Kubernetes with a modern **DevSecOps pipeline**. It integrates GitHub Actions, Trivy, Semgrep, SonarQube, Prometheus, Grafana, Falco, and OPA Gatekeeper for security and observability.

---

## 🚀 Tech Stack

- **Frontend**: React (Port 3000)
- **Backend**: Node.js (Port 5000)
- **Database**: MongoDB Atlas (Cloud)
- **Container Registry**: GitHub Container Registry (GHCR)
- **CI/CD**: GitHub Actions
- **Infrastructure**: Kubernetes (cloud-hosted)

---

## 🔐 DevSecOps Features

| Feature              | Tool                          |
|---------------------|-------------------------------|
| Lint & Format       | ESLint, Prettier              |
| Static Analysis     | Semgrep, SonarQube            |
| Vulnerability Scan  | Trivy, `npm audit`            |
| CI/CD Pipeline      | GitHub Actions                |
| Image Registry      | GitHub Container Registry     |
| K8s Deployment      | `kubectl apply` via GitHub CI |
| Monitoring          | Prometheus + Grafana          |
| Runtime Security    | Falco (DaemonSet)             |
| Admission Control   | OPA Gatekeeper (Helm + Rego)  |

---

## 📁 Project Structure

```
.
├── backend/                    # Node.js API
├── frontend/                   # React UI
├── k8s/
│   ├── backend-deployment.yaml
│   ├── frontend-deployment.yaml
│   ├── ingress.yaml
│   └── security/
│       ├── constraint-templates/
│       └── constraints/
├── .github/
│   └── workflows/
│       └── devsecops.yml       # Full CI/CD Pipeline
```

---

## ⚙️ GitHub Actions Pipeline

Runs on `main` branch push:
1. ✅ Lint + Dependency Audit (`npm audit`)
2. 🧠 Semgrep (SAST) + SonarQube
3. 🔍 Trivy Image Vulnerability Scans
4. 🐳 Docker Build & Push to GHCR
5. ☸️ Deploy to Kubernetes (`kubectl apply`)
6. 📈 Install Prometheus & Grafana via Helm
7. 🔒 Install Falco (runtime) and Gatekeeper (admission)

---

## 🧪 Monitoring & Security

- **Grafana Dashboards** available post-deploy
- **Falco** alerts for runtime violations (shells, file access)
- **OPA Gatekeeper** blocks pods using:
  - `privileged: true`
  - Can be extended with hostPath + runAsNonRoot constraints

---

## 🔧 Requirements

- Kubernetes cluster (e.g., GKE, EKS, AKS)
- MongoDB Atlas instance
- GitHub Secrets:
  - `GHCR_TOKEN`
  - `SONAR_TOKEN`
  - `GRAFANA_ADMIN_PASSWORD`

---

## 🔍 To Deploy Everything

Just push to `main`:

```bash
git push origin main
```

GitHub Actions will build, scan, and deploy everything automatically.

---


## 🧑‍💻 Author

**ygoncloud**

---

## 📄 License

MIT © 2025 ygoncloud

