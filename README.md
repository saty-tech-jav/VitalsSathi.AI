# ❤️ VitalsSaathi.AI — Blood Pressure Tracker

A full-stack Blood Pressure tracking application with mobile APK support and cloud deployment capability.

## 🛠️ Tech Stack

- **Backend** — Java 24, Spring Boot 3.4, Spring Security, JWT Authentication
- **Database** — MySQL
- **Frontend** — React.js
- **Mobile** — Android APK via Capacitor
- **Cloud** — Railway (Backend) + Vercel (Frontend)

## 📁 Project Structure

```
bp-tracker/
  ├── backend/        → Spring Boot REST API
  ├── frontend/       → React.js Web App
  └── database/       → MySQL Schema
```

## ⚙️ Local Setup

### Prerequisites
- Java JDK 24
- Maven
- MySQL
- Node.js & npm

### Backend Setup

1. Create MySQL database:
```sql
CREATE DATABASE bp_tracker;
```

2. Create `application.properties` in `backend/src/main/resources/`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/bp_tracker
spring.datasource.username=your_username
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
jwt.secret=your_jwt_secret_key
jwt.expiration=86400000
server.port=8080
```

3. Run the backend:
```bash
cd backend
mvn spring-boot:run
```

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

App runs at `http://localhost:3000`

## 🔐 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login and get JWT token |
| GET | `/api/readings` | Get all BP readings |
| POST | `/api/readings` | Add new BP reading |
| DELETE | `/api/readings/{id}` | Delete a reading |

## 📱 Mobile APK

```bash
cd frontend
npm run build
npx cap sync android
npx cap open android
```
Build APK from Android Studio → Build → Build APK

## ☁️ Cloud Deployment

- **Backend** → [Railway](https://railway.app) — set environment variables in Railway dashboard
- **Frontend** → [Vercel](https://vercel.com) — connect GitHub repo and deploy

## 🔒 Security Note

`application.properties` is not included in this repository as it contains sensitive credentials. Create it locally using the template above.

---
Built with ❤️ using Spring Boot + React
