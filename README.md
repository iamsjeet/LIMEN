# LIMEN — Decision Intelligence System

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-Backend-green)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue)
![Status](https://img.shields.io/badge/Status-Active-success)
![License](https://img.shields.io/badge/License-MIT-yellow)

> A real-time decision intelligence engine that learns user preferences through pairwise comparisons and continuously refines rankings using an adaptive ELO-based model.

---

# 🎯 WHAT IS LIMEN?

Most recommendation systems passively observe:

- clicks  
- purchases  
- browsing behavior  

**Limen takes a fundamentally different approach.**

> It learns directly from decisions.

---

## 🔁 CORE LOOP
Compare → Choose → Update → Learn → Repeat

Every interaction improves the system instantly.

---

# ❓ PROBLEM IT SOLVES

Traditional recommendation systems:

- ❌ Cold start problem  
- ❌ Slow adaptation  
- ❌ Black-box decision making  

### Limen solves this by:

- ⚡ Real-time learning  
- 🧠 No prior data required  
- 🔍 Transparent ranking system  
- 🔁 Continuous adaptation  

---

# ⚙️ CORE FEATURES (V1 → V2)

---

## 🔥 A. Pairwise Comparison Engine

### Flow:
- User sees **Item A vs Item B**
- Selects one
- Confirms decision

### Features:
- Randomized pair selection  
- Duplicate pair prevention  
- Category-based filtering  
- Difficulty balancing (similar ELO items)  

### Edge Cases:
- Same item repeated → prevented  
- Rapid clicking → debounce + confirmation  
- No available pairs → fallback to broader category  

---

## 🔥 B. ELO Rating System (CORE ENGINE)

### Formula:
R_new = R_old + K(S − E)

### Expected Score:
E = 1 / (1 + 10^((R_opponent − R_player)/400))

---

### Components:
- `R_old` → current rating  
- `S` → actual outcome (1 or 0)  
- `E` → expected probability  
- `K` → learning rate  

---

### Features:
- Dynamic K-factor  
  - New items → high K (fast learning)  
  - Stable items → low K (stability)  

- Dual rating system:
  - Global rating  
  - Per-user rating  

---

### Edge Cases:
- New items → initialized at baseline (e.g., 1000)  
- Large rating gaps → capped updates  
- Rating inflation → normalization  

---

## 🔥 C. Personalization Layer

Each user has:

- Personal ELO  
- Interaction count  

---

### Final Score:
Final Score = w1 * Personal + w2 * Global

---

### Dynamic Weighting:
- New users → rely more on global  
- Active users → rely more on personal  

---

### Edge Cases:
- Low interaction → prevent overfitting  
- Inconsistent behavior → smooth updates  

---

## 🔥 D. Smart Pair Selection System

### Goals:
- Meaningful comparisons  
- Faster learning  
- Balanced exposure  

---

### Strategies:
- Similar ELO pairing  
- Exploration vs exploitation  
- Category clustering  

---

### Edge Cases:
- Repetitive pairs → avoided  
- User fatigue → variation introduced  
- Dead items → reintroduced periodically  

---

## 🔥 E. Insights Engine (Decision Intelligence Layer)

Transforms raw data into meaningful insights.

---

### Outputs:

#### 1. Preference Profile
- Category distribution  
- Item-type preference  

#### 2. Decision Patterns
- Premium vs budget  
- Minimal vs complex  
- Brand bias  

#### 3. Ranking Evolution
- Time-series rating changes  

#### 4. Confidence Score
- Stability of user preferences  

---

### Edge Cases:
- Sparse data → “Learning…” state  
- Conflicting signals → mixed insights  

---

## 🔥 F. Analytics Dashboard

### Sections:
- Global ranking leaderboard  
- User preference breakdown  
- Comparison history  
- Top-performing items  

---

### Advanced Insights:
- Trend detection  
- Category dominance  
- Behavioral analysis  

---

## 🔥 G. Admin / System Layer

### Features:
- Add / remove items  
- CSV-based bulk import  
- Reset ratings  
- Monitor system behavior  

---

### Edge Cases:
- Duplicate items → detection + merge  
- Data corruption → fallback recovery  

---

## 🔥 H. Data Pipeline
User Action
↓
API Layer (FastAPI)
↓
Service Layer (Business Logic)
↓
ELO Engine + Personalization
↓
Database (PostgreSQL)
↓
Analytics Layer

---

# 🧱 SYSTEM ARCHITECTURE
Frontend (React)
↓
FastAPI (API Layer)
↓
Service Layer (ELO + Logic)
↓
Database (PostgreSQL)

---

### Optional Enhancements:
- Redis (caching & fast retrieval)

---

# 🎨 UI SYSTEM

### Theme:
- Dark base  
- Muted green  
- Soft lime highlights  

---

### Core UX:

#### Compare Page:
- A vs B layout  
- Winner glow  
- Loser fade  
- ELO change preview  

#### Dashboard:
- Insights  
- Patterns  
- Charts  

---

# 🧠 ADVANCED FEATURES

---

## 🔥 Confidence Score
Measures preference stability using:
- number of comparisons  
- consistency  

---

## 🔥 Time Decay
Older interactions lose influence over time.

---

## 🔥 Diversity Injection
Occasionally surfaces unexpected items.

---

## 🔥 Bias Detection
Detects repetitive or skewed user behavior.

---

# ⚠️ EDGE CASE HANDLING

---

### User Behavior:
- Random clicking → inconsistency detection  
- Rapid input → ignored / debounced  

---

### Data:
- Sparse data → fallback to global  
- Extreme ratings → capped  

---

### System:
- No comparisons → seeded initialization  
- API failures → retry logic  

---

# 🛠️ TECH STACK

### Backend:
- Python  
- FastAPI  

### Database:
- PostgreSQL  

### ORM:
- SQLAlchemy  

### Authentication:
- JWT  
- bcrypt  

### Frontend:
- React  

### Data Handling:
- CSV ingestion  

---

# 🚀 API OVERVIEW
POST /auth/register
POST /auth/login
POST /products
POST /comparisons
GET /recommendations
GET /admin/analytics/*

---

# 💡 WHAT MAKES LIMEN DIFFERENT

This is NOT a CRUD or tutorial project.

It focuses on:

- Real-time learning systems  
- Adaptive ranking algorithms  
- Behavioral intelligence  
- Dynamic decision modeling  

---

> Most systems recommend based on history.  
> **Limen learns from decisions.**

---

# 🔮 FUTURE SCOPE

- A/B testing ranking strategies  
- Distributed scaling  
- Advanced visualization  
- Multi-user collaborative learning  

---

# 📌 FINAL THOUGHT

Limen is not just a recommendation system.

> It is a system that **understands user preferences by observing decisions in motion.**

---

# ⭐ If you found this interesting, consider starring the repo!
