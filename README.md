# 🌀 Unbound — A Modern Social Platform

> Built collaboratively by [Muhammad Azdhar Syahputra (Ajar)](https://github.com/azdharsyahputra) and [Panji Gunawan](https://github.com/gundz204), **Unbound** is a fully modular, event-driven social media platform built with a modern polyglot microservice architecture.  
>
> The goal: create a scalable, intelligent, and developer-friendly social platform — powered by Go, Rust, Python, React, and gRPC.

---

## 🚀 Tech Stack Overview

| Layer | Stack | Description |
|:------|:------|:------------|
| **Frontend** | React + Vite + TypeScript + shadcn/ui *(TBD)* | Web client with a clean, modern component library |
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
- 🧱 **Backend-first foundation:** Core system built from backend up — architecture, event bus, and model pipeline first, frontend follows later.

---

## 🧪 Core Services Overview

| Service | Language | Description |
|:---------|:----------|:-------------|
| **Auth Service** | Go | Handles user authentication, sessions, and JWTs |
| **User Service** | Go | Manages profiles, bios, and relationships |
| **Post Service** | Rust | Responsible for creating, deleting, and processing posts/media |
| **Feed Service** | Rust | Generates personalized timelines and feed caching |
| **Graph Service** | Rust | Manages social graph (follows, mutuals, suggestions) |
| **Notification Service** | Go | Real-time user notifications (in-app & push) |
| **Search Service** | Go | Indexes posts and users for fast lookups |
| **ML Worker** | Python | Performs training and scoring for FYP recommendations |

---

## 🧭 Communication Pattern

```
[ React (Frontend) ]
        ↓  (REST/GraphQL)
[ Gateway (Go) ]
        ↓  (gRPC)
 ┌─────────────────────────────┐
 │  User / Post / Feed / Auth  │
 │  Graph / Notif / Search     │
 └─────────────────────────────┘
        ↓
     [ Kafka Bus ]
        ↓
   [ ML Worker (Python) ]
```

---

## 🔧 Tooling & Utilities

| Purpose | Tool |
|:---------|:------|
| Build automation | Makefile / Taskfile |
| Proto management | Buf.build (`/proto`) |
| Hot reload | Air (Go) / Cargo watch (Rust) |
| Observability | OpenTelemetry + Jaeger |
| Container orchestration | Docker Compose (dev) / Kubernetes (prod) |
| CI/CD (planned) | GitHub Actions + ArgoCD |

---

## 🧱 Development Milestones

- [x] Core repository setup (monorepo)
- [ ] Docker Compose base environment
- [ ] Gateway skeleton (Go)
- [ ] Auth & User service prototypes
- [ ] Feed & Post microservices (Rust)
- [ ] Kafka integration for async events
- [ ] ML Worker (Python + ONNX export)
- [ ] Frontend (React) UI skeleton *(TBD)*
- [ ] Deployment via Kubernetes

---

## 🧭 Future Goals

- [ ] GraphQL Gateway layer for combined queries  
- [ ] FYP personalization with online learning  
- [ ] Full observability stack (Prometheus, Grafana, Jaeger)  
- [ ] ElasticSearch or Meilisearch integration  
- [ ] Real-time WebSocket notifications  
- [ ] Media upload via MinIO presigned URLs  
- [ ] Multi-region deployment & horizontal scaling  

---

## 🤝 Creators

| Name | Role | GitHub |
|:------|:------|:-------|
| **Muhammad Azdhar Syahputra (Ajar)** | Backend Systems & Architecture | [@azdharsyahputra](https://github.com/azdharsyahputra) |
| **Panji Gunawan** | Backend Systems & Architecture | [@gundz204](https://github.com/gundz204) |
| **(TBD)** | Frontend Engineering & Product Design | — |

> Both co-founders and equal collaborators — backend-first builders shaping a distributed social system.  
> Frontend architecture TBD (will be defined post-core service stabilization).  
> Every commit is a shared step toward something unbound. 🌌

---

## 🪄 License

**MIT License** © 2025 [Muhammad Azdhar Syahputra & Panji Gunawan](https://github.com/azdharsyahputra)

---

## 💬 Notes

- This project uses a **monorepo structure** for fast iteration.  
- In production, services (Feed, Post, Graph) can be separated into individual repositories.  
- All gRPC schemas live inside `/proto` and are generated using Buf.  
- Feel free to open issues, discussions, or pull requests — everything here is transparent and collaborative.  

---

> _"Build clean. Build fast. Stay unbound."_ — 2025
