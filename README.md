<div align="center">
  <h1>🏛️ Smart Public Service CRM</h1>
  <p><i>A modern civic complaint and grievance redressal platform.</i></p>

  [![Node](https://img.shields.io/badge/node-18+-green?style=for-the-badge&logo=node.js)](https://nodejs.org/)
  [![React](https://img.shields.io/badge/react-18-blue?style=for-the-badge&logo=react)](https://react.dev/)
  [![TypeScript](https://img.shields.io/badge/typescript-5.x-3178C6?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
  [![Docker](https://img.shields.io/badge/docker-enabled-blue?style=for-the-badge&logo=docker)](https://www.docker.com/)
  [![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg?style=for-the-badge)](./LICENSE)

  <br />

  **🚀 [Try the Live Demo](https://public-service-crm.vercel.app/login)**
</div>

<br />

<div align="center">
  <img src="./docs/screenshot.png" alt="Smart CRM Interface" width="800" />
</div>

<br />

## 📖 Overview

Municipal complaint handling is often fragmented and opaque: citizens do not get timely updates, officers lack prioritization support, and administrators struggle to identify systemic trends. 

**Smart Public Service CRM** addresses this by providing a cohesive platform that empowers citizens, officers, and administrators with real-time updates, AI-assisted operations, and actionable insights.

---

## ✨ Core Capabilities

- 📝 **Complaint Lifecycle Management**: Seamlessly create, track, assign, update, and close complaints.
- 🔐 **Role-Based Access Control (RBAC)**: Distinct dashboards and permissions for citizens, officers, and administrators.
- 🤖 **AI-Assisted Operations**: Leverage AI for complaint classification, prioritization, and an intelligent governance copilot.
- ⚡ **Real-Time Notifications**: Get instant updates across operational dashboards powered by Socket.IO.
- 📊 **Public Transparency Portal**: Publicly accessible and aggregated data, including CSV exports for open governance.
- 📎 **Attachment Uploads**: Secure, presigned upload mechanisms using S3-compatible storage.
- 📈 **Predictive Analytics**: Admin-facing hooks and predictive endpoints for smarter decision-making.

---

## 👥 Product Roles & Workflows

| Role | Capabilities |
|------|-------------|
| 🧑‍🤝‍🧑 **Citizens** | • Register / Login <br> • Submit complaints with details & evidence <br> • Track progress and receive status updates |
| 👮 **Officers** | • View and manage assigned complaints <br> • Update statuses and add operational notes <br> • Resolve issues within SLA windows |
| 👑 **Administrators** | • Oversee city-wide complaint operations <br> • Monitor trends and department performance <br> • Utilize copilot and prediction endpoints |

---

## 🏗️ Architecture & Tech Stack

### 🧩 Architecture Overview
1. **Frontend (`frontend/`)**: React + Vite client offering role-aware dashboards.
2. **Backend API (`backend/`)**: Express + TypeScript REST APIs managing auth, complaints, uploads, and analytics.
3. **Data Layer**: PostgreSQL (system of record), Redis (queue/cache), MinIO/S3 (object storage).
4. **Real-time & Jobs**: Socket.IO for live interactions and BullMQ for robust background processing.

### 💻 Technology Stack
- **Frontend**: React 18, Vite, TypeScript, React Router, Recharts, Socket.IO Client, Leaflet
- **Backend**: Node.js, Express, TypeScript, Prisma ORM, BullMQ, Socket.IO
- **Infrastructure**: PostgreSQL, Redis, MinIO, Docker Compose

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- npm or yarn
- Docker & Docker Compose (highly recommended)

### 🐳 Option A: Docker Compose (Recommended)
Launch the entire stack with a single command:
```bash
docker compose up --build
```
*Services Started:*
- **Frontend**: `http://localhost:5173`
- **Backend API**: `http://localhost:5001`
- **PostgreSQL**: `localhost:5433`
- **Redis**: `localhost:6379`
- **MinIO**: `http://localhost:9000`

### 💻 Option B: Local Development

1. **Start Infrastructure Services**:
   ```bash
   docker compose up postgres redis minio -d
   ```
2. **Setup Backend**:
   ```bash
   cd backend
   npm install
   npm run prisma:generate
   npm run prisma:migrate
   npm run dev
   ```
3. **Setup Frontend** *(in a new terminal)*:
   ```bash
   cd frontend
   npm install
   npm run dev
   ```
4. *(Optional)* **Generate Demo Data**:
   ```bash
   cd backend && npm run seed:demo
   ```

---

## ⚙️ Configuration

Create `.env` files based on the `.env.example` templates. 

**Backend (`backend/.env`):**
```env
PORT=5000
NODE_ENV=development
CORS_ORIGIN=http://localhost:5173
JWT_SECRET=replace-me
DATABASE_URL=postgresql://postgres:postgres@localhost:5433/civiccrm
REDIS_URL=redis://localhost:6379
AWS_REGION=us-east-1
AWS_BUCKET=smart-crm-uploads
AWS_ACCESS_KEY_ID=minioadmin
AWS_SECRET_ACCESS_KEY=minioadmin
AWS_S3_ENDPOINT=http://localhost:9000
```

**Frontend (`frontend/.env`):**
```env
VITE_API_URL=http://localhost:5001
```

---

## 🛠️ Testing & Quality

- **Backend Testing**: `cd backend && npm test`
- **Frontend Build Check**: `cd frontend && npm run build`

---

## ☁️ Deployment & Observability

**Hardening for Production**:
- Use Managed PostgreSQL and Redis.
- Secure S3 buckets with proper lifecycle policies.
- Utilize HTTPS termination and reverse proxies (e.g., Nginx, Traefik).
- Manage secrets via secure vaults (e.g., AWS Secrets Manager, HashiCorp Vault).

**Observability Built-in**:
- **Metrics**: Prometheus-style endpoint at `GET /api/metrics/metrics`
- **Logging**: Structured backend logs.
- **Error Tracking**: Ready for Sentry DSN integration.

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:
1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes with clear, descriptive messages.
4. Run all tests and build checks locally.
5. Open a Pull Request with context and validation details.

---

## 📄 License

This project is licensed under the [MIT License](./LICENSE).

---

## 👨‍💻 Maintainers

- **Abhnish**: abhnish.1289@gmail.com
- **Chinmay**: dev24.chinmay@gmail.com
- **Naman**: namanroy9@gmail.com

<p align="center"><i>Built for practical, transparent, and accountable public service delivery.</i></p>
