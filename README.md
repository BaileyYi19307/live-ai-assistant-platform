# Real-Time LLM Ops Platform

End-to-end infrastructure for deploying and operating a low-latency, real-time AI system supporting chat, voice, and tool invocation workloads. Built to simulate production-grade DevOps workflows: containerization, CI/CD, observability, scaling, and reliability.

---

## Architecture

- **Backend**: Python (FastAPI) for real-time API + WebSocket handling  
- **Worker / Tools Layer**: Node.js (via MCP tools)  
- **Vector Search**: FAISS (CPU)  
- **Cache**: Redis  
- **Database**: Postgres  
- **Infrastructure**: AWS (ECS Fargate) or GCP (Cloud Run)  
- **Storage**: S3 / GCS  
- **Networking**: ALB (WebSocket upgrade), TLS, VPC  

---

## Features

### Real-Time System
- WebSocket-based chat with streaming responses  
- Simulated voice + tool invocation workloads  
- Concurrent session handling  

### Containerization
- Multi-stage Docker builds (Python 3.12 + Node.js 20)  
- Optimized image size and dependency layering  

### CI/CD Pipeline
- Lint → Test → Build → Deploy workflow  
- Staging environment with smoke tests  
- Manual promotion to production  

### Infrastructure as Code
Terraform-managed infrastructure:
- ECS Fargate / Cloud Run  
- Redis + Postgres  
- Object storage (S3/GCS)  
- CDN, DNS, TLS  

### Observability
- Structured JSON logging  
- Prometheus metrics:
  - request latency  
  - LLM time-to-first-byte (TTFB)  
  - tool execution time  
  - concurrent connections  
- Grafana dashboards  
- PagerDuty-style alerting with runbooks  

### Security
- Migration from `.env` → Secrets Manager / Vault  
- Key rotation  
- Per-tenant credential isolation  

### Networking
- TLS termination  
- WebSocket upgrade via load balancer  
- CORS policies  
- Rate limiting + DDoS protection  
- VPC with private subnets  

### Load Testing
- k6 / Locust simulations:
  - concurrent chat sessions  
  - voice-like streaming  
  - tool invocation bursts  

### Reliability
- Incident response runbooks  
- Rollback procedures  
- Disaster recovery (DR) strategy  
- On-call simulation  

---

## Example Results

- Sustained **X concurrent connections** under load  
- Reduced P95 latency from **X ms → X ms**  
- Maintained stable throughput under simulated voice + chat workloads  

---

## How to Run Locally

```bash
# build and run services
docker compose up --build

# run tests
pytest

# run load test
k6 run load-test.js
```

---
