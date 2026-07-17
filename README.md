# 🎓 School Management System

A comprehensive, enterprise-grade school management portal with advanced security features, AI-powered assistance, and complete fee management. This system demonstrates industry best practices in security architecture, role-based access control, and integrated monitoring.

🔗 **[Live Demo](https://school-management-dit2.onrender.com/)** · **[GitHub Repo](https://github.com/sakib1133/Secure-School-Management-Porta)**


## 📋 Project Overview

This project implements a full-featured school management system with:
- **Role-Based Access Control** for Admin, Teacher, and Student users
- **Enterprise-Grade Security** with multi-layered protection mechanisms
- **AI-Powered Chatbot** with NLP, sentiment analysis, and multi-language support
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

### AI & Chatbot
- **NLP** - Natural Language Processing
- **Sentiment Analysis** - Emotion detection
- **Multi-language Support** - English & Hindi
- **Contextual Learning** - Smart responses

### Monitoring
- **Prometheus** - Metrics collection and storage
- **Grafana** - Data visualization and dashboards
- **Node Exporter** - System metrics exporter

### DevOps
- **Docker** - Containerization
- **Docker Compose** - Multi-container orchestration
- **Jenkins** - CI/CD pipeline (ready for implementation)
- **Render** - Cloud deployment support

## 🚀 Quick Start

### Prerequisites
- Docker & Docker Compose
- Node.js 18+ (for local development)
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/school-management-system.git
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

### Default Credentials
- **Admin**: Username: `admin`, Password: (Set via ADMIN_PASSWORD env var)
- **Teacher/Student**: Created via admin dashboard

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

### 2. AI-Powered Chatbot
Advanced natural language processing for intelligent assistance:
- **NLP Intent Detection**: Recognizes user queries with fuzzy matching and contextual understanding
- **Sentiment Analysis**: Detects user emotions and adapts responses accordingly
- **Multi-language Support**: English and Hindi language capabilities
- **Contextual Learning**: Remembers conversation history and provides personalized responses
- **Smart Suggestions**: Proactively offers relevant actions based on user intent
- **Role-Based Responses**: Different response styles for Admin, Teacher, and Student roles

### 3. Complete Fee Management
End-to-end payment system with verification workflow:
- **Razorpay Integration**: Secure online payments with order creation and signature verification
- **OTP Verification**: Email-based OTP for both Razorpay and manual payments
- **Fee Assignment**: Admin can assign fees to students with descriptions and due dates
- **Payment Approval**: Manual payments (UPI/Bank transfer) require admin approval
- **Payment History**: Complete audit trail of all transactions
- **Receipt Generation**: Digital receipts for successful payments
- **School Payment Details**: Configurable UPI ID, QR code, bank details for manual payments

### 4. Role-Based Access Control
Distinct user experiences with secure permission management:
- **Admin Dashboard**: Complete system management (students, teachers, classes, fees, payments)
- **Teacher Dashboard**: Profile management, assigned students, classes, assignments, results
- **Student Dashboard**: Personal information, grades, timetable, subjects, assignments, notifications
- **JWT Authentication**: Role-based token expiration (Admin: 1hr, Teacher: 45min, Student: 30min)
- **Session Management**: Auto-refresh capability, expiry warnings, activity tracking
- **MFA/2FA**: Multi-factor authentication for sensitive operations

### 5. Integrated Monitoring Stack
Production-ready observability with real-time metrics:
- **Prometheus**: Metrics collection with configurable scrape intervals
- **Grafana**: Interactive dashboards for visualization and analysis
- **Node Exporter**: System-level metrics (CPU, memory, disk, network)
- **Custom Metrics**: Application-specific metrics for business KPIs
- **Alerting**: Configurable alerting rules for proactive monitoring
- **Log Aggregation**: Centralized logging for all system events

##  Monitoring Setup

### Prometheus Configuration
- **Configuration File**: `monitoring/prometheus.yml`
- **Scrape Interval**: 15 seconds
- **Targets**: Node.js App, Node Exporter

### Grafana Dashboards
- **System Metrics**: CPU, Memory, Disk usage
- **Application Metrics**: Request rates, Response times, Error rates
- **Security Metrics**: IPS blocks, WAF alerts, Anomaly detection
- **Business KPIs**: Student enrollments, Fee collections, Active sessions

## 🔧 Development

### Project Structure
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

### Local Development
```bash
# Install dependencies
cd App && npm install

# Start development server
npm start

# Or with nodemon for auto-reload
npm run dev
```

## 🔄 CI/CD Pipeline

### Jenkins Pipeline (Ready for Implementation)
The Jenkinsfile is ready for implementation with the following stages:
1. **Code Checkout** - Pull latest code from repository
2. **Security Scan** - Vulnerability assessment and dependency checking
3. **Build** - Create Docker image
4. **Test** - Run automated tests (when implemented)
5. **Deploy** - Push to registry and deploy

### Render Deployment
The project includes `render.yaml` for easy deployment to Render cloud platform:
- Automatic builds from Git repository
- Environment variable management
- Health check configuration
- Free tier support with database persistence

## 🌐 Deployment

### Docker Deployment
```bash
# Start all services
docker-compose up -d

# Stop all services
docker-compose down

# View logs
docker-compose logs -f app

# Scale application (if needed)
docker-compose up -d --scale app=2
```

### Render Deployment
```bash
# Push to GitHub repository
git push origin main

# Connect repository to Render
# Configure environment variables in Render dashboard
# Automatic deployment will trigger on push
```

## 📈 Monitoring & Alerting

### Key Metrics
- **Application**: Response time, Error rate, Throughput, Active sessions
- **Security**: IPS blocks, WAF alerts, Anomaly detection, Failed logins
- **System**: CPU usage, Memory usage, Disk I/O, Network traffic
- **Business**: Student enrollments, Fee collections, Payment status

### Alerting Rules
- High CPU usage (>80%)
- Memory pressure (>90%)
- Application errors (>5%)
- Security alerts (IPS blocks, WAF detections)
- Service downtime

## 🔒 Security Features

### Authentication & Authorization
- **JWT Authentication**: Role-based tokens with expiration
- **Bcrypt Password Hashing**: Secure password storage
- **MFA/2FA**: Multi-factor authentication for sensitive operations
- **Role-Based Access Control**: Admin, Teacher, Student permissions

### Protection Mechanisms
- **IPS**: Brute-force protection with IP blocking
- **ADS**: Anomaly detection for mass data fetch and rapid requests
- **WAF**: SQL injection, XSS, and command injection detection
- **Anti-Phishing**: Domain validation and suspicious pattern detection
- **App Cloning Protection**: User-agent validation and signature verification

### Data Security
- **AES-256-CBC Encryption**: All sensitive data encrypted at rest
- **Environment Variables**: Secure configuration management
- **Security Headers**: Helmet.js for standard security headers
- **CORS Protection**: Whitelisted origins only
- **Rate Limiting**: Configurable rate limits per endpoint

### Logging & Monitoring
- **Comprehensive Logging**: All security events logged to dedicated files
- **Notification Alerts**: Email, Slack, Discord, Teams integration
- **Session Tracking**: Activity monitoring and expiry warnings
- **Audit Trail**: Complete audit trail for all user actions

## 📚 API Documentation

### Authentication Endpoints
- `POST /api/login` - User login with role selection
- `POST /api/logout` - User logout and session invalidation
- `POST /api/refresh-token` - Refresh JWT token
- `GET /api/session-info` - Get current session details

### User Management
- `GET /api/me` - Get current user profile
- `PUT /api/admin/profile` - Update admin profile
- `POST /api/admin/change-password` - Change password
- `POST /api/2fa/send-otp` - Send 2FA OTP
- `POST /api/2fa/verify-otp` - Verify 2FA OTP

### Student Management
- `GET /api/admin/students` - Get all students
- `POST /api/admin/students` - Create new student
- `PUT /students/:id` - Update student details
- `DELETE /students/:id` - Delete student
- `GET /students/me` - Get student's own profile

### Teacher Management
- `GET /api/admin/get-teachers` - Get all teachers
- `POST /api/admin/create-teacher` - Create new teacher
- `PUT /api/admin/update-teacher/:id` - Update teacher
- `DELETE /api/admin/delete-teacher/:id` - Delete teacher
- `GET /api/teacher/profile` - Get teacher's own profile

### Fee Management
- `POST /api/fees/create` - Assign fee to student
- `GET /api/fees/student` - Get student's fees
- `GET /api/fees/all` - Get all fees (admin)
- `DELETE /api/fees/:id` - Delete fee
- `POST /api/fees/send-otp` - Send fee OTP
- `POST /api/fees/verify-otp` - Verify fee OTP
- `POST /api/fees/mark-paid` - Mark manual payment
- `GET /api/fees/payments/history` - Get payment history

### Payment System
- `POST /api/payments/create-order` - Create Razorpay order
- `POST /api/payments/verify` - Verify Razorpay payment
- `GET /api/payments/my-payments` - Get user's payments
- `GET /api/payments/receipt/:paymentId` - Get payment receipt
- `POST /api/payments/send-otp` - Send payment OTP
- `POST /api/payments/verify-otp` - Verify payment OTP

### Chatbot Services
- `POST /api/chatbot` - Internal chatbot interaction
- `POST /api/login-chatbot` - Login page chatbot
- `GET /api/admin/chatbot-logs` - Get chatbot logs (admin)

### Admin Endpoints
- `GET /api/admin/payments` - Get all payments with filters
- `GET /api/admin/payments/summary` - Get payment summary
- `GET /api/admin/payment-requests` - Get pending payment requests
- `POST /api/admin/approve-payment` - Approve manual payment
- `POST /api/admin/reject-payment` - Reject manual payment
- `GET /api/admin/session-stats` - Get session statistics

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request



## 🙋‍♂️ Support

- **Issues**: [GitHub Issues](https://github.com/sakib1133/school-management-system/issues)
- **Discussions**: [GitHub Discussions](https://github.com/sakib1133/school-management-system/discussions)
- **Email**: sakibmalik5347@gmail.com

## 🏆 Acknowledgments

- [Express.js](https://expressjs.com/) - Web framework
- [SQLite](https://www.sqlite.org/) - Database engine
- [Razorpay](https://razorpay.com/) - Payment gateway
- [Prometheus](https://prometheus.io/) - Monitoring system
- [Grafana](https://grafana.com/) - Visualization platform
- [Docker](https://www.docker.com/) - Container platform
- [Node.js](https://nodejs.org/) - JavaScript runtime

## 🎯 Future Enhancements

- [ ] Implement comprehensive unit and integration tests
- [ ] Add API documentation with Swagger/OpenAPI
- [ ] Refactor monolithic backend into modular architecture
- [ ] Implement database migrations system
- [ ] Add PostgreSQL support for production scalability
- [ ] Implement automated CI/CD pipeline in Jenkins
- [ ] Add Kubernetes manifests for orchestration
- [ ] Implement real-time notifications with WebSockets
- [ ] Add mobile application support
- [ ] Implement advanced analytics and reporting

---

**⭐ Star this repository if it helped you!**

**🔄 Fork and contribute to make it better!**
