# ❤️ VitalTrack — Blood Pressure Tracker

Full-stack BP tracking app with voice input, charts, and health insights.

**Stack:** Java Spring Boot 3.2 + React 18 + MySQL + JWT Auth

---

## 🚀 QUICK START (5 steps)

### Prerequisites
- Java 17+  → https://adoptium.net
- Maven 3.8+ → https://maven.apache.org/download.cgi
- Node.js 18+ → https://nodejs.org
- MySQL 8+ → https://dev.mysql.com/downloads/mysql/

---

### Step 1 — Setup MySQL Database

Open MySQL Workbench or terminal and run:

```sql
-- In MySQL terminal or Workbench:
source /path/to/bp-tracker/database/schema.sql
```

Or manually:
```bash
mysql -u root -p < database/schema.sql
```

This creates the `bp_tracker` database with all tables + demo user.

---

### Step 2 — Configure Database Password

Open `backend/src/main/resources/application.properties` and update:

```properties
spring.datasource.username=root
spring.datasource.password=YOUR_MYSQL_PASSWORD
```

---

### Step 3 — Start the Backend

```bash
cd backend
mvn spring-boot:run
```

✅ Backend runs at: http://localhost:8080
Test it: http://localhost:8080/api/auth/health

---

### Step 4 — Start the Frontend

Open a NEW terminal:
```bash
cd frontend
npm install
npm start
```

✅ Frontend opens at: http://localhost:3000

---

### Step 5 — Login and Start Tracking!

- **URL:** http://localhost:3000
- **Demo account:** username `demo` / password `demo123`
- Or click "Create Account" to register

---

## 📱 Features

| Feature | Description |
|---------|-------------|
| 🔐 Auth | Register/Login with JWT tokens |
| ✍️ Manual Input | Enter BP + pulse with date/time |
| 🎙️ Voice Input | Speak your reading naturally |
| 💬 Text Parse | Type "120 over 80 pulse 72" |
| 📊 Charts | Line graphs for 1d/3d/5d/1w/2w/1m |
| 💡 AI Summary | Category, suggestion, trend, alerts |
| 📋 History | Full table with delete + CSV export |
| 📱 Responsive | Works on mobile browsers |

---

## 🎙️ Voice Input Examples

Say any of these:
- "120 over 80 pulse 72"
- "BP is 135/90"
- "systolic 118 diastolic 76 heart rate 68"
- "one hundred twenty over eighty pulse seventy two"
- "125 by 82 pulse rate 70"

---

## 📡 API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register |
| POST | `/api/auth/login` | Login → JWT |
| POST | `/api/readings` | Save manual reading |
| POST | `/api/readings/parse` | Parse voice/text (preview) |
| POST | `/api/readings/voice-save` | Parse + save in one step |
| GET | `/api/readings?range=1w` | Get readings by range |
| GET | `/api/readings/all` | Get all readings |
| GET | `/api/readings/graph?range=1w` | Graph data |
| GET | `/api/readings/summary?range=1w` | Summary + suggestion |
| DELETE | `/api/readings/{id}` | Delete reading |

**Range values:** `1d`, `3d`, `5d`, `1w`, `2w`, `1m`, `all`

---

## 🩺 BP Categories

| Category | Systolic | Diastolic |
|----------|----------|-----------|
| Normal | < 120 | < 80 |
| Elevated | 120–129 | < 80 |
| High Stage 1 | 130–139 | 80–89 |
| High Stage 2 | ≥ 140 | ≥ 90 |
| Crisis | > 180 | > 120 |

---

## 🏗️ Project Structure

```
bp-tracker/
├── backend/                    ← Spring Boot API
│   ├── src/main/java/com/bptracker/
│   │   ├── controller/         ← REST endpoints
│   │   ├── service/            ← Business logic
│   │   ├── model/              ← JPA entities
│   │   ├── repository/         ← DB queries
│   │   ├── config/             ← Security, JWT filter
│   │   ├── dto/                ← Request/Response objects
│   │   └── util/               ← JWT, VoiceParser
│   └── src/main/resources/
│       └── application.properties
│
├── frontend/                   ← React app
│   └── src/
│       ├── pages/              ← Login, Register, Dashboard, Log, History
│       ├── components/         ← Layout, Sidebar
│       ├── context/            ← AuthContext (JWT state)
│       ├── services/           ← Axios API calls
│       └── utils/              ← BP category helpers
│
├── database/
│   └── schema.sql              ← MySQL setup script
│
├── start.sh                    ← Mac/Linux startup
└── start.bat                   ← Windows startup
```

---

## 🔧 Troubleshooting

**MySQL connection failed?**
→ Check `application.properties` username/password
→ Make sure MySQL service is running

**Port 8080 already in use?**
→ Change `server.port=8081` in `application.properties`
→ Update `frontend/package.json` proxy to `http://localhost:8081`

**Voice not working?**
→ Must use Chrome or Edge (Firefox has limited support)
→ Allow microphone permission when prompted
→ Use HTTPS in production (required for Web Speech API)

**npm install fails?**
→ Delete `node_modules/` and `package-lock.json`, then retry

---

## 📲 Android App

To build the Android app later:
1. Use **Retrofit2** for API calls (same endpoints)
2. Use **Google SpeechRecognizer** for voice
3. Use **MPAndroidChart** for graphs
4. Store JWT token in **EncryptedSharedPreferences**

The Spring Boot backend serves both Web and Android from the same APIs.

---

*Made with ❤️ — VitalTrack BP Monitor*
