# 🎓 School Management System

A comprehensive, enterprise-grade school management portal with advanced security features, and complete fee management. This system demonstrates industry best practices in security architecture, role-based access control, and integrated monitoring.

🔗 **[Live Demo](https://school-management-dit2.onrender.com/)** · **[GitHub Repo](https://github.com/sakib1133/Secure-School-Management-Porta)**


## 📋 Project Overview

This project implements a full-featured school management system with:
- **Role-Based Access Control** for Admin, Teacher, and Student users
- **Enterprise-Grade Security** with multi-layered protection mechanisms
- **Complete Fee Management** with Razorpay integration and OTP verification
- **Integrated Monitoring Stack** with Prometheus, Grafana, and Node Exporter
- **Docker Compose** for containerized deployment
- **CI/CD Ready** with Jenkins pipeline support

## 🏗️ Architecture

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

## 🛠️ Tech Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **SQLite3** - Database with 19+ tables
- **bcrypt** - Password hashing
- **jsonwebtoken** - JWT authentication
- **nodemailer** - Email notifications
- **razorpay** - Payment gateway integration

### Frontend
- **HTML5/CSS3** - Modern responsive UI
- **Vanilla JavaScript** - Client-side logic
- **Font Awesome** - Icon library
- **Material Icons** - Google Material Design icons

### Security
- **Helmet.js** - Security headers
- **express-rate-limit** - Rate limiting
- **AES-256-CBC** - Data encryption
- **JWT** - Token-based authentication
- **MFA/2FA** - Multi-factor authentication

### Monitoring
- **Prometheus** - Metrics collection and storage
- **Grafana** - Data visualization and dashboards
- **Node Exporter** - System metrics exporter

### DevOps
- **Docker** - Containerization
- **Docker Compose** - Multi-container orchestration
- **Jenkins** - CI/CD pipeline (ready for implementation)
- **Render** - Cloud deployment support

### 🚀 Quick 

## Project Structure
```
├── App/                    # Main application directory
│   ├── public/             # Frontend files
│   │   ├── index.html      # Landing page
│   │   ├── login.html      # Login page with chatbot
│   │   ├── dashboard.html  # Admin dashboard
│   │   ├── student/        # Student-specific pages
│   │   ├── teacher/        # Teacher-specific pages
│   │   ├── css/            # Stylesheets
│   │   └── js/             # JavaScript modules
│   ├── utils/              # Service modules
│   │   ├── chatbotService.js        # Main chatbot logic
│   │   ├── navigationChatbotService.js  # Navigation chatbot
│   │   └── notificationService.js     # Security notifications
│   ├── prompts/            # AI system prompts
│   │   ├── admin.txt       # Admin chatbot prompt
│   │   ├── teacher.txt     # Teacher chatbot prompt
│   │   └── student.txt     # Student chatbot prompt
│   ├── data/               # Database storage
│   ├── logs/               # Application logs
│   ├── uploads/            # File uploads
│   ├── app.js              # Main application (7978 lines)
│   └── package.json        # Dependencies
├── monitoring/             # Monitoring configuration
│   └── prometheus.yml      # Prometheus config
├── Dockerfile              # Application container
├── docker-compose.yml      # Multi-container setup
├── render.yaml             # Render deployment config
└── Jenkinsfile             # CI/CD pipeline (ready for implementation)
```


## Prerequisites
- Docker & Docker Compose
- Node.js 18+ (for local development)
- Git

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/sakib1133/school-management-system.git
   cd school-management-system
   ```

2. **Environment Setup**
   ```bash
   # Copy and configure environment variables
   cp App/.env.example App/.env
   # Edit .env with your configuration (JWT_SECRET, SESSION_SECRET, ENCRYPTION_KEY)
   ```

3. **Start the Application**
   ```bash
   # Using Docker Compose (Recommended)
   docker-compose up -d

   # Or for local development
   cd App
   npm install
   npm start
   ```

4. **Access Services**
   - **School Portal**: http://localhost:3000
   - **Prometheus**: http://localhost:9090
   - **Grafana**: http://localhost:3002
   - **Node Exporter**: http://localhost:9100
   - **Jenkins**: http://localhost:8081

5. **Default Credentials**
- **Admin**: Username: `admin`, Password: admin@321/admin@123
- **Teacher/Student**: Make your own udner stundent/teacher management after    admin login

## � Key Strengths

### 1. Enterprise-Grade Security
Multi-layered protection system with defense-in-depth approach:
- **IPS (Intrusion Prevention System)**: Brute-force protection with IP blocking after 5 failed attempts (15min block duration)
- **ADS (Anomaly Detection System)**: Detects mass data fetch (>50 records), rapid requests (>10/min), and bulk operations
- **WAF (Web Application Firewall)**: SQL injection, XSS, and command injection detection with regex patterns
- **Anti-Phishing**: Domain validation, origin/referer checking, suspicious pattern detection
- **App Cloning Protection**: User-agent validation, request timing analysis, signature verification
- **AES-256-CBC Encryption**: All sensitive data (names, emails, phone, addresses) encrypted at rest
- **Comprehensive Logging**: Security events logged to dedicated files with notification alerts via Email, Slack, Discord, Teams

### 2. Complete Fee Management
End-to-end payment system with verification workflow:
- **Razorpay Integration**: Secure online payments with order creation and signature verification
- **OTP Verification**: Email-based OTP for both Razorpay and manual payments
- **Fee Assignment**: Admin can assign fees to students with descriptions and due dates
- **Payment Approval**: Manual payments (UPI/Bank transfer) require admin approval
- **Payment History**: Complete audit trail of all transactions
- **Receipt Generation**: Digital receipts for successful payments
- **School Payment Details**: Configurable UPI ID, QR code, bank details for manual payments

### 3. Role-Based Access Control
Distinct user experiences with secure permission management:
- **Admin Dashboard**: Complete system management (students, teachers, classes, fees, payments)
- **Teacher Dashboard**: Profile management, assigned students, classes, assignments, results
- **Student Dashboard**: Personal information, grades, timetable, subjects, assignments, notifications
- **JWT Authentication**: Role-based token expiration (Admin: 1hr, Teacher: 45min, Student: 30min)
- **Session Management**: Auto-refresh capability, expiry warnings, activity tracking
- **MFA/2FA**: Multi-factor authentication for sensitive operations



## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


## 🎯 Future Enhancements

- [ ] Implement comprehensive unit and integration tests
- [ ] Add API documentation with Swagger/OpenAPI
- [ ] Refactor monolithic backend into modular architecture
- [ ] Implement database migrations system
- [ ] Add PostgreSQL support for production scalability
- [ ] Add Kubernetes manifests for orchestration
- [ ] Implement real-time notifications with WebSockets
- [ ] Add mobile application support
- [ ] Implement advanced analytics and reporting



## 🙋‍♂️ Support

- **Issues**: [GitHub Issues](https://github.com/sakib1133/school-management-system/issues)
- **Discussions**: [GitHub Discussions](https://github.com/sakib1133/school-management-system/discussions)
- **Email**: sakibmalik5347@gmail.com


---

**⭐ Star this repository if it helped you!**

**🔄 Fork and contribute to make it better!**

## Author

**Mohd Sakib Malik**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/mohd-sakib-malik-97ab4a283/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black)](https://github.com/sakib1133)
[![LeetCode](https://img.shields.io/badge/LeetCode-Profile-orange)](https://leetcode.com/u/sakib_malik79/)
