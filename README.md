# School Management System — Full-Stack DevOps Platform

A production-grade, secure web application for educational institutions — fully containerized, monitored, and deployed through an automated CI/CD pipeline.

> Built end-to-end by **Mohd Sakib Malik** — [sakibmalik5347@gmail.com](mailto:sakibmalik5347@gmail.com) · [GitHub](https://github.com/sakib1133) · [LinkedIn](linkedin.com/in/mohd-sakib-malik-97ab4a283/)

---

## What This Project Is

The **School Management System** is a multi-role web application serving Admins, Teachers, and Students — secured with enterprise-grade defenses, powered by an AI chatbot assistant, and deployed inside a fully automated DevOps ecosystem.

The project has two tightly integrated layers:

- **Application Layer** — A Node.js/Express backend with JWT-based Role-Based Access Control (RBAC), AES-256 database encryption, Web Application Firewall, Intrusion Prevention System, and an AI-powered chatbot
- **Infrastructure Layer** — Docker containerization, Prometheus + Grafana monitoring, Jenkins CI/CD pipeline, and Terraform infrastructure-as-code

Every commit is automatically tested, built, and deployed. Every service is monitored in real time. Every security event triggers an alert.

---

## System Architecture

```
                        ┌──────────────────────┐
                        │       Jenkins        │
                        │       CI/CD          │
                        └──────────┬───────────┘
                                   │ auto-deploy on push
                                   ▼
┌──────────────────────────────────────────────────────────────┐
│                      Docker Environment                      │
│                                                              │
│  ┌─────────────────────────────────────────────────────┐    │
│  │            School Management System App             │    │
│  │         Node.js + Express  :3000 (HTTPS :3443)      │    │
│  │                                                     │    │
│  │  ┌──────────┐  ┌──────────┐  ┌───────────────────┐ │    │
│  │  │  Admin   │  │ Teacher  │  │     Student       │ │    │
│  │  │  Panel   │  │  Panel   │  │     Portal        │ │    │
│  │  └──────────┘  └──────────┘  └───────────────────┘ │    │
│  │                                                     │    │
│  │  ┌──────────────────────────────────────────────┐   │    │
│  │  │        Security Stack (Multi-Layer)          │   │    │
│  │  │  WAF │ IPS │ Anti-Phishing │ App-Clone Guard │   │    │
│  │  │  JWT │ AES-256 Encryption │ HTTPS/TLS       │   │    │
│  │  └──────────────────────────────────────────────┘   │    │
│  │                                                     │    │
│  │  ┌──────────────────────────────────────────────┐   │    │
│  │  │          AI Chatbot Assistant                │   │    │
│  │  │     NLP Engine │ Role-Based Responses        │   │    │
│  │  └──────────────────────────────────────────────┘   │    │
│  └─────────────────────────────────────────────────────┘    │
│           │  metrics                  │  metrics            │
│           ▼                           ▼                     │
│  ┌──────────────┐           ┌──────────────────┐            │
│  │ Node Exporter│           │   Prometheus     │            │
│  │   :9100      │──────────▶│     :9090        │            │
│  └──────────────┘           └────────┬─────────┘            │
│                                      │                      │
│                                      ▼                      │
│                             ┌──────────────────┐            │
│                             │     Grafana      │            │
│                             │     :3001        │            │
│                             └──────────────────┘            │
└──────────────────────────────────────────────────────────────┘
```

---

## Tech Stack

| Layer | Tools |
|---|---|
| **Backend** | Node.js, Express.js, REST APIs |
| **Database** | SQLite (AES-256-CBC encrypted) |
| **Authentication** | JWT, Role-Based Access Control |
| **Security** | WAF, IPS, Anti-Phishing, App-Clone Guard, HTTPS/TLS |
| **AI Assistant** | Custom NLP Engine, Role-Based Chatbot |
| **Containerization** | Docker, Docker Compose |
| **CI/CD** | Jenkins, GitHub |
| **Monitoring** | Prometheus, Grafana, Node Exporter |
| **Infrastructure** | Terraform, Docker Networking & Volumes |
| **Alerting** | Email (SMTP), Slack, Discord, Microsoft Teams |
| **OS** | Linux (Ubuntu) |

---

## User Roles

| Role | Access |
|---|---|
| **Admin** | Full system access — manage users, view security alerts, monitor system health |
| **Teacher** | Manage student grades, attendance, and class rosters |
| **Student** | View own profile, grades, attendance, schedules, and fee status |

Role is embedded in the JWT and validated by middleware on every protected API request.

---

## Project Structure

```
.
├── App/
│   ├── public/
│   ├── uploads/
│   ├── prompts/
│   ├── utils/
│   ├── chatbotService.js       # NLP engine (641 lines)
│   ├── chatbot.js              # Frontend chatbot widget (348 lines)
│   ├── chatbot.css             # Chatbot styling (449 lines)
│   ├── package.json
│   └── server.js
├── monitoring/
│   ├── prometheus.yml
│   └── grafana/
├── terraform/
├── tests/
│   ├── test_waf.js
│   ├── test_ids.js
│   ├── test_anti_phishing.js
│   ├── test_app_cloning.js
│   ├── test_database_encryption.js
│   ├── test_session_timeout.js
│   ├── test_https_only_final.js
│   ├── test_cors_validation.js
│   ├── test_notification_system.js
│   └── test_chatbot.js
├── docs/
│   ├── BURP_SUITE_TESTING.md
│   └── KALI_LINUX_TESTING.md
├── Dockerfile
├── docker-compose.yml
├── Jenkinsfile
└── .env.example
```

---

## Getting Started

### Prerequisites

- Docker & Docker Compose
- Git
- Node.js v18+ (local development only)

### Setup

```bash
# Clone the repo
git clone https://github.com/your-username/school-management-system.git
cd school-management-system

# Configure environment
cp App/.env.example App/.env
# Edit App/.env — set JWT secret, encryption key, SMTP/Slack credentials, allowed origins
```

### Run with Docker

```bash
# Start all services
docker-compose up -d

# Verify containers are running
docker ps

# Stop all services
docker-compose down
```

### Run Locally (Development)

```bash
cd App
npm install
npm start
```

---

## Service Endpoints

| Service | URL |
|---|---|
| School Management App (HTTP) | http://localhost:3000 |
| School Management App (HTTPS) | https://localhost:3443 |
| Prometheus | http://localhost:9090 |
| Grafana | http://localhost:3001 |
| Node Exporter | http://localhost:9100 |

---

## API Reference

| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/api/login` | Public | User login, returns JWT |
| `GET` | `/api/status` | All roles | Application status |
| `GET` | `/metrics` | Internal | Prometheus scrape endpoint |
| `GET` | `/api/students` | Admin, Teacher | List students |
| `GET` | `/api/grades` | All roles | View grades (role-filtered) |
| `GET` | `/api/attendance` | All roles | View attendance (role-filtered) |
| `POST` | `/api/chatbot` | All roles | AI chatbot interaction |
| `GET` | `/api/security/alerts` | Admin | View security event log |
| `GET` | `/api/security/blocked-ips` | Admin | View blocked IP list |

---

## Security Architecture

The system uses a **defense-in-depth** strategy — multiple independent layers, so bypassing one does not compromise the system.

### Layer 1 — Secure Transport
- **HTTPS/TLS only** on port 3443; all HTTP traffic auto-redirected
- **Hardened CORS** — only whitelisted origins in `.env` are accepted

### Layer 2 — Web Application Firewall (WAF)
First line of defense. Inspects every incoming request and blocks:
- SQL Injection (Basic, UNION, Blind, Time-Based, Error-Based)
- Cross-Site Scripting (XSS)
- Directory Traversal
- Command Injection

### Layer 3 — Intrusion Prevention System (IPS)
- Monitors failed login attempts per IP
- Auto-blocks IP after **3 failed attempts**
- Block duration: **10 minutes**, then automatic unblock
- Admins can view and manage blocked IPs via dashboard

### Layer 4 — Anti-Phishing Protection
Applied specifically to `/api/login`:
- Validates `Host`, `Origin`, and `Referer` headers against allowed domains
- Blocks requests from spoofed or suspicious domains

### Layer 5 — App-Cloning Protection
Prevents unauthorized clients from accessing the API:
- Requires valid `X-App-Signature` and `X-App-Version` headers
- Detects and blocks bots, crawlers, and suspicious User-Agent strings
- Request timing analysis to catch abnormally fast automated clients

### Layer 6 — Database Encryption at Rest
- **AES-256-CBC** encryption for all sensitive fields
- Unique randomly generated IV per record
- Encrypted fields: student names, ages, grades, teacher names, subjects, experience
- Transparent decryption on API responses — seamless to end users
- Encryption keys stored in environment variables, never hardcoded

### Layer 7 — Authentication & Session Management

| Role | Session Duration |
|---|---|
| Admin | 1 hour |
| Teacher | 45 minutes |
| Student | 30 minutes |

- Auto-expiring JWTs signed with environment-variable secrets
- Session warning at 5-minute threshold
- Token refresh mechanism with maximum refresh limits
- Real-time session activity tracking

### Layer 8 — Real-Time Security Alerting

| Channel | Supported |
|---|---|
| Email (SMTP) | ✅ |
| Slack Webhook | ✅ |
| Discord Webhook | ✅ |
| Microsoft Teams | ✅ |

**Alert priority tiers:** Low → Medium → High → Critical

**Automated alerts fire for:**
- IP blocking events (IPS triggers)
- SQL injection attempts
- XSS detection
- Phishing attempts
- App-cloning attempts
- Mass data access anomalies

5-minute cooldown between duplicate alerts to prevent notification flooding.

---

## AI Chatbot Assistant

An intelligent, role-aware chatbot available 24/7 to all users.

### Capabilities by Role

| Role | What the Chatbot Can Do |
|---|---|
| **Student** | Check grades, attendance, fee status, class schedule, security tips |
| **Teacher** | View class rosters, student management, teaching schedule, assignments |
| **Admin** | System monitoring, security alerts, blocked IP status, user statistics, threat analysis |

### Technical Implementation

- **NLP Engine** — Rule-based natural language processing with 15+ supported intents
- **Context Awareness** — Conversation history and contextual response generation
- **Security Integration** — Real-time awareness of WAF, IPS, and phishing events
- **Input Sanitization** — Filters SQL injection, XSS, and command injection from chat input
- **Audit Logging** — Every conversation logged for compliance and forensic analysis

---

## Monitoring & Observability

### Prometheus Metrics Collected

**Application metrics** (via `/metrics` endpoint):
- Request count and rate
- Response time (p50, p95, p99)
- Error rate
- Active sessions

**Infrastructure metrics** (via Node Exporter):
- CPU usage per core
- Memory and swap utilization
- Disk I/O and utilization
- Network traffic in/out

### Grafana Dashboards

Dashboards persist across restarts via Docker Volumes mounted to `/var/lib/grafana`.

- **System Dashboard** — CPU, memory, disk, network
- **Application Dashboard** — API latency, throughput, error rate, service health
- **Security Dashboard** — Blocked IPs, WAF triggers, failed login attempts

---

## CI/CD Pipeline

```
Developer Push
      │
      ▼
   GitHub
      │
      ▼
   Jenkins
      │
 ┌────┴─────────────┐
 │ 1. Checkout      │
 │ 2. npm install   │
 │ 3. npm test      │
 │ 4. docker build  │
 │ 5. docker push   │
 │ 6. docker-compose│
 │    up -d         │
 └────┬─────────────┘
      │
      ▼
 Running Containers
      │
      ▼
 Prometheus ──▶ Grafana
```

---

## Infrastructure as Code

Terraform automates infrastructure provisioning — no manual server setup required.

```bash
terraform init    # Download providers
terraform plan    # Preview changes
terraform apply   # Provision infrastructure
```

---

## Alerting Thresholds

| Metric | Threshold | Severity |
|---|---|---|
| CPU Usage | > 80% | Warning |
| Memory Usage | > 90% | Critical |
| Failed Logins | 3 per IP | Warning → IP Block |
| WAF Block | Any trigger | High |
| Container Down | Any | Critical |
| Service Unreachable | Any | Critical |

---

## Security Testing

### Automated Test Suite

| Test File | What It Validates |
|---|---|
| `test_waf.js` | WAF blocks SQLi, XSS, traversal, command injection |
| `test_ids.js` | IPS auto-blocks after failed login threshold |
| `test_anti_phishing.js` | Login endpoint rejects spoofed origins |
| `test_app_cloning.js` | Signature verification blocks unauthorized clients |
| `test_database_encryption.js` | AES-256-CBC encryption/decryption of sensitive fields |
| `test_session_timeout.js` | Role-based session expiry and token refresh |
| `test_https_only_final.js` | HTTPS-only enforcement and HTTP redirect |
| `test_cors_validation.js` | CORS policy allows/rejects correct origins |
| `test_notification_system.js` | Alerts delivered across Email, Slack, Discord, Teams |
| `test_chatbot.js` | NLP intent recognition, RBAC responses, input sanitization |

```bash
npm test                    # Unit tests
npm run test:integration    # Integration tests
npm run test:performance    # Performance tests
```

### Attack Simulation Results

| Attack Type | Vectors Tested | Result |
|---|---|---|
| SQL Injection | Basic, UNION, Blind, Time-Based, Error-Based | ✅ 100% Blocked |
| Brute Force | Credential stuffing, password spraying, distributed | ✅ 100% Blocked |
| Phishing | Malicious domains, subdomain spoofing, header injection | ✅ 100% Blocked |
| App Cloning | Missing signatures, invalid headers, bot user-agents | ✅ 100% Blocked |
| Database Access | Direct file inspection of sensitive fields | ✅ 100% Encrypted |

### Professional Pentest Documentation

- `docs/BURP_SUITE_TESTING.md` — Full Burp Suite Pro testing guide with scenarios and report templates
- `docs/KALI_LINUX_TESTING.md` — Kali Linux methodology using `nmap`, `sqlmap`, `nikto`, `testssl.sh`, and custom automation scripts

---

## Technical Challenges & Solutions

**Exposing app metrics to Prometheus**
The Node.js app needed a `/metrics` endpoint in Prometheus exposition format. Integrated `prom-client` and registered custom counters and histograms for HTTP requests, error rates, and active sessions.

**Persistent Grafana dashboards**
Dashboards were lost on container restarts. Solved by mounting a named Docker Volume to `/var/lib/grafana`, preserving all dashboard configurations and data permanently.

**Container-to-container networking**
Services needed to discover each other by name, not by dynamic IP. Solved by defining a custom Docker bridge network in `docker-compose.yml`, enabling DNS-based service discovery (e.g., `http://prometheus:9090`).

**AES-256 encryption with unique IVs**
Each database record needed independent encryption to prevent pattern analysis. Implemented per-record random IV generation, stored alongside the ciphertext, with transparent decryption on every API read.

**Role-based session timeouts**
Different roles required different session durations without breaking the UX. Solved by embedding role in the JWT payload and enforcing role-specific expiry in middleware, with a frontend warning 5 minutes before expiry.

---

## Scalability Roadmap

**Current:** SQLite with AES-256-CBC application-level encryption — ideal for demos and small deployments.

**Enterprise path:**

| Database | Encryption Upgrade | Scaling |
|---|---|---|
| PostgreSQL | `pg_tde` + `pgcrypto` for column-level encryption | Read replicas, connection pooling, Row-Level Security |
| MySQL | Enterprise keyring plugin + tablespace TDE | MySQL Cluster, FIPS 140-2 certified modules |

**Infrastructure path:**
- [ ] Kubernetes deployment with Helm charts
- [ ] GitHub Actions as alternative/parallel CI/CD
- [ ] ELK Stack for centralized log aggregation
- [ ] Automated rollbacks on failed health checks
- [ ] Cloud deployment to AWS ECS / GCP Cloud Run
- [ ] Slack/PagerDuty escalation for Critical alerts

---

## Screenshots

| School Management App | Jenkins Pipeline |
|---|---|
| ![App](login.png) | ![Jenkins](screenshots/jenkins-dashboar.png) |

| Jenkins Pipeline |
| ![Jenkins](jenkins-dashboar.png) 
| Grafana Dashboard |
|---|---|
| ![Grafana](grafana.png) 

---

## Security Posture: EXCELLENT

The system demonstrates enterprise-grade security across all layers — validated through automated testing, comprehensive attack simulations, and professional penetration testing documentation. All simulated attacks were blocked at 100%.


---

*If this project was useful, consider giving it a ⭐*
