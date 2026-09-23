# 🎓 Fluxion Math — Adaptive AP Calculus Learning Engine

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28%2B-FF4B4B.svg)](https://streamlit.io/)
[![Supabase](https://img.shields.io/badge/Database-Supabase%20PostgreSQL-3ECF8E.svg)](https://supabase.com/)
[![Security](https://img.shields.io/badge/Auth-Bcrypt%20Salted-green.svg)](https://en.wikipedia.org/wiki/Bcrypt)

**Fluxion Math** is an open-access, cloud-connected adaptive learning engine designed to expand Advanced Placement (AP) STEM education among youth in Uzbekistan and beyond. By combining data-driven performance analytics, strict security protocols, and adaptive question queuing, Fluxion Math empowers students to master AP Calculus efficiently—even in regions where AP coursework is traditionally inaccessible.

---

## 🚀 The Mission

In many developing regions, Advanced Placement courses remain uncommon, leaving talented youth without structured pathways to world-class STEM preparation. **Fluxion Math** was built to break that barrier. By offering a free, high-rigor, adaptive learning environment, the platform helps local students build conceptual mastery, accelerate their learning pace, and compete on the international academic stage.

---

## 🌟 Key Features

### 🧠 1. Rule-Based Adaptive Algorithm
* **Weak Topic Prioritization:** The engine queries historical attempt data in real time. If a student's performance in any of the 10 AP Calculus units drops below **60%**, the platform dynamically reshuffles the queue to target those weak points.
* **Latency & Pacing Alerts:** Custom JavaScript timing components monitor per-question response speeds. Correct answers taking longer than **90 seconds** trigger pacing warnings in the analytics dashboard to help students adapt to the College Board's strict exam time constraints.

### ⏱️ 2. Dual Testing Environments
* **Practice Mode:** Untimed, low-pressure environment featuring instant feedback and premium UI audio chimes for correct/incorrect answers to reinforce learning.
* **Exam Mode:** High-stakes environment mimicking real AP conditions. Features a strict 15-minute countdown, hidden feedback until submission, and a subtle 60-second mechanical heartbeat timer to simulate exam pressure.

### 🔒 3. Enterprise-Grade Security Architecture
* **Bcrypt Password Hashing:** User credentials are encrypted using salted `bcrypt` hashing to ensure banking-level data security.
* **State-Independent Brute-Force Protection:** Failed login attempts and strict 5-minute lockouts are written directly to the Supabase database (UTC-synced), making them impossible to bypass via browser refreshes or incognito mode.
* **Strict Input Sanitization:** Regex-based safelisting on registration fields neutralizes Cross-Site Scripting (XSS) injection attempts.

### 🏆 4. Gamification & Student Habit Building
* **Timezone-Aware Streaks & Leaderboards:** Powered by `zoneinfo`, daily streaks and monthly leaderboards mathematically roll over exactly at midnight Uzbekistan time (`Asia/Tashkent`), regardless of server UTC time.
* **Mastery Trophy Case:** Dynamically calculates accuracy across all units. Reaching **≥80% accuracy** unlocks Champagne Gold trophy badges.
* **Starred Question Vault:** Allows students to bookmark challenging questions post-quiz and generate custom dynamic review sessions using only saved items.
* **Skill Radar Charts:** Automatically generates personalized spider-web mastery charts (optimized with automatic garbage collection to prevent server memory leaks).

### 👑 5. Administrator Analytics Dashboard
* **Global Performance Overview:** Tracks total registered students, global questions answered, and aggregate platform accuracy.
* **Student Leaderboard & Weakness Tracking:** Displays student progress, total XP, and identifies each student's weakest unit for targeted educational guidance.

---

## 🛠️ Tech Stack & Architecture

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Frontend Framework** | `Streamlit` | Interactive web UI styled with custom ambient SaaS CSS injection. |
| **Database** | `Supabase (PostgreSQL)` | Cloud relational database configured for massive scale (100,000+ row limits). |
| **Authentication** | `Bcrypt` | Custom-built, salted password hashing and database-backed lockout sessions. |
| **Analytics & Visualization** | `Pandas`, `Matplotlib` | Memory-optimized trend aggregation, accuracy tracking, and polar charts. |
| **Timezone Management** | `ZoneInfo` | Shifts UTC database timestamps to local (`Asia/Tashkent`) timeframes. |
| **Caching Optimization** | `@st.cache_data` | Server-side data memoization to eliminate redundant database queries. |

---

## 📁 Repository Structure

```text
├── .streamlit/
│   └── secrets.toml        # Environment variables (Database URL/Keys)
├── app.py                  # Core application logic, routing, and UI views
├── seed_all_units.py       # Cloud database bulk question bank importer
├── requirements.txt        # Production Python dependencies
└── README.md               # Documentation & project overview
