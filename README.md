# 🌐 Unbound — The Social for the Unrestricted Mind

**Unbound** is a next-generation social media platform built for *authentic expression, freedom, and connection without boundaries.*  
Still in early development stage — our mission is to create a space where creativity and individuality thrive without algorithmic noise.

---

## 🚧 Current Status
> **Phase:** Early Development (Pre-Alpha)  
> **Goal:** Core microservices setup + basic frontend integration  
> **Stack:** React • Go • Rust • Python (ML/FYP) • gRPC • Kafka

---

## 🧱 Architecture Overview

Unbound is built using a **microservice architecture** with gRPC and Kafka as the backbone for communication and event streaming.

```
Frontend (React)
       ↓
API Gateway (Go)
       ↓
+-----------------------------+
|  Auth Service (Rust)        |
|  Feed Service (Go)          |
|  User Service (Rust/Go)     |
|  ML Recommender (Python)    |
|  Notification Service (Go)  |
+-----------------------------+
       ↓
Kafka Bus ↔ gRPC ↔ SQL/NoSQL DB
```

**Highlights:**
- 🧩 **Modular Services** — scalable and language-agnostic.  
- ⚡ **gRPC** — fast binary communication between services.  
- 🧠 **Machine Learning (Python)** — personalized FYP system.  
- 🕸️ **Kafka Streams** — event-driven feed updates and analytics.  

---

## 🧠 Core Ideas
- **Freedom First:** No forced algorithm. Chronological and discovery feeds coexist.  
- **Authentic Voice:** Multi-persona system (public, private, anonymous).  
- **Decentralization Ready:** Designed with Web3-compatible architecture in mind.  
- **Own Your Data:** User content portability and privacy control.

---

## 🧩 Tech Stack

| Layer | Technology |
|-------|-------------|
| **Frontend** | React + Tailwind + shadcn/ui |
| **Backend (API)** | Go (Gin / Fiber) |
| **Heavy Logic Services** | Rust (Axum / Actix) |
| **ML / Recommendation** | Python (FastAPI + TensorFlow / PyTorch) |
| **Communication** | gRPC + Kafka |
| **Database** | PostgreSQL / MongoDB (still evaluating) |
| **Auth** | JWT + OAuth2 |

---

## 📦 Current Repositories

| Service | Language | Status |
|----------|-----------|---------|
| `unbound-frontend` | React | 🚧 In Progress |
| `unbound-auth` | Rust | 🧱 Setup Phase |
| `unbound-feed` | Go | 🧩 Designing schema |
| `unbound-ml` | Python | 🧠 Research stage |
| `unbound-notify` | Go | ⏳ Planned |

---

## 🧰 Development Setup

### Prerequisites
- Node.js 20+
- Go 1.22+
- Rust (latest stable)
- Python 3.11+
- Kafka + Zookeeper (Docker)
- PostgreSQL or MongoDB

### Setup (local dev)
```bash
# Clone repo
git clone https://github.com/azdharsyahputra/unbound.git
cd unbound

# Run frontend
cd unbound-frontend
npm install && npm run dev

# Run backend service
cd ../unbound-feed
go run main.go
```

---

## 🧪 Planned Milestones

| Phase | Description | ETA |
|--------|--------------|------|
| **Phase 1** | Core service scaffolding, gRPC + Kafka integration | Nov 2025 |
| **Phase 2** | FYP ML model prototype + auth integration | Dec 2025 |
| **Phase 3** | Frontend + feed UI integration | Jan 2026 |
| **Phase 4** | Closed Alpha release | Q1 2026 |

---

## 🧑‍💻 Contributors
| Name | Role |
|------|------|
| **Ajar (Muhammad Azdhar Syahputra)** | Founder / Full-Stack Engineer |
| **(TBD)** | Co-developer / Backend Support |

---

## 💬 Vision Statement
> “Unbound isn’t just another social app — it’s a rebellion against constraint.  
> A place where expression flows freely, and your voice isn’t lost in the noise.”

---

## 🪪 License
MIT License © 2025 Muhammad Azdhar Syahputra  
Feel free to fork, learn, and contribute.

---

## 🧭 Links
- 🌍 [Website (coming soon)](https://unbound.social)
- 📘 [Docs (TBA)](https://docs.unbound.social)
- 🧠 [Design Notes / Figma (TBA)](https://figma.com/unbound)
