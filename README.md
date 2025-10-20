# 🌀 Unbound — A Modern Social Platform

> Built collaboratively by [Ajar (Muhammad Azdhar Syahputra)](https://github.com/azdharsyahputra) and [Co-Creator](), **Unbound** is a fully modular, event-driven social media platform built with a modern polyglot microservice architecture.  
>
> The goal: create a scalable, intelligent, and developer-friendly social platform — powered by Go, Rust, Python, React, and gRPC.

---

## 🚀 Tech Stack Overview

| Layer | Stack | Description |
|:------|:------|:------------|
| **Frontend** | React + Vite + TypeScript + shadcn/ui | Web client with a clean, modern component library |
| **Gateway / BFF** | Go (Fiber / Chi + gRPC Client) | Main API entry point connecting frontend to backend services |
| **Microservices** | Go + Rust (tonic, sqlx) | Core logic (Auth, User, Post, Feed, Graph, Notification, Search) |
| **Machine Learning** | Python (LightGBM / ONNX Runtime) | Handles FYP (For-You-Page) ranking and recommendations |
| **Event Bus** | Kafka | Asynchronous event propagation between services |
| **Datastores** | PostgreSQL + Redis + MinIO + ClickHouse | Core DB, caching, media storage, analytics |
| **Infrastructure** | Docker Compose → Kubernetes (Helm / ArgoCD) | Local development and production deployment |
| **Observability** | Prometheus + Grafana + Jaeger | Metrics, monitoring, and tracing |

---

## 🧩 Project Structure

```
unbound/
├── web/               # React frontend (Vite + shadcn/ui)
├── gateway/           # Go API Gateway / BFF
├── services/          # Core microservices
│   ├── auth/          # Authentication & token management (Go)
│   ├── user/          # User profiles & relationships (Go)
│   ├── post/          # Posting, likes, comments (Rust)
│   ├── feed/          # Timeline & ranking logic (Rust)
│   ├── graph/         # Social graph & recommendations (Rust)
│   ├── notif/         # Notifications (Go)
│   └── search/        # Search indexing (Go)
├── ml/                # Python ML workers (FYP / Ranking)
├── proto/             # gRPC schema definitions (shared contracts)
├── infra/             # Docker, K8s manifests, monitoring setup
├── scripts/           # Build & deployment helper scripts
├── .env.example       # Default environment variables
├── docker-compose.yml # Local dev orchestration
└── README.md
```

---

## ⚙️ Local Development Setup

### 1. Clone the Repository

```bash
git clone https://github.com/azdharsyahputra/unbound.git
cd unbound
```

### 2. Copy Environment Variables

```bash
cp .env.example .env
```

Fill in your `.env` file with your local settings:

```env
POSTGRES_URL=postgres://unbound:password@localhost:5432/unbound
REDIS_URL=redis://localhost:6379
KAFKA_BROKER=localhost:9092
MINIO_URL=http://localhost:9000
JWT_SECRET=supersecret
```

### 3. Run Local Services (Docker Compose)

```bash
docker-compose up --build
```

This will:
- Start PostgreSQL, Redis, Kafka, and MinIO  
- Build all Go/Rust services  
- Run the Python ML worker in the background  
- Serve the web client at [http://localhost:5173](http://localhost:5173)

---

## 🧠 Development Philosophy

- 🧩 **Microservice-first:** Each module scales independently and communicates via gRPC or Kafka.  
- ⚡ **gRPC over REST:** All inter-service communication uses gRPC for high performance and strict contracts.  
- 📨 **Event-driven backbone:** Kafka connects services asynchronously (`post.created`, `follow.created`, etc).  
- 🧠 **ML-powered feeds:** Python ML workers continuously train ranking models (LightGBM → ONNX).  
- 🎨 **Modern frontend:** React + shadcn/ui for an elegant, responsive interface.  

---

## 🤝 Creators

| Name | Role | GitHub |
|:------|:------|:-------|
| **Muhammad Azdhar Syahputra** | Backend Systems & Architecture | [@azdharsyahputra](https://github.com/azdharsyahputra) |
| **[Co-Creator Name]** | Frontend / ML Engineering | *(add your partner’s GitHub link here)* |

> Built collaboratively with equal roles — no lead, no hierarchy.  
> Every commit is a shared step toward something unbound. 🌌

---

## 🪄 License

**MIT License** © 2025 [Ajar & Co-Creator](https://github.com/azdharsyahputra)

---

> _"Build clean. Build fast. Stay unbound."_ — 2025
