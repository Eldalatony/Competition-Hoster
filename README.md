# WPT - Backend & Database Review

📅 **Last Updated:** *February 19, 2025*  
📌 **Project Scope:** *Full-stack platform for hosting padel tournaments with automated fixtures, scoring, and team management.*

---

## **📌 Database Schema (MySQL)**
### **Key Design Points:**
- **Normalization:** Data is structured efficiently to prevent redundancy.
- **Referential Integrity:** Foreign keys maintain relationships.
- **Performance Enhancements:** Indexed key fields, optimized queries.
- **Scalability:** Flexible schema to add new game modes (Mexicano, Leagues, etc.) later.

### **🗃️ Tables Overview:**
| **Table Name**           | **Description** |
|-------------------------|------------------------------------------------------------|
| **Users**               | Stores all registered users (Members & Admins). |
| **Admin**               | Special user type with tournament management privileges. |
| **Team**                | A group of users competing together in a tournament. |
| **Competition**         | Hosted by admins; defines tournament type and settings. |
| **Fixtures**            | Matches within competitons; stores scores and results. |
| **CompetitionDetails**  | Stores additional metadata about competitions. |
| **CompetitionFinancials** | Handles entry fees, prize pool, and revenue calculations. |
| **PrizeDistribution**   | Determines how prizes are split between winning teams. |
| **TeamStatistics**      | Tracks wins, losses, and performance metrics. |

---

## **📌 Backend Architecture & APIs**
### **🔹 1. Authorization API**
**📌 Purpose:** Handles user authentication & role-based access control.  
**📍 Key Features:**
- 🔑 **JWT Authentication** (secure login).
- 📧 **OAuth Support** (Google login).
- 🔄 **Signup/Login** (auto-assigns new users as "Members").
- 🔐 **Phone & email verification.**
- 🔄 **Forgot Password & Reset Functionality.**
- 🔄 **Deletion & Ban Functionality.**

---

### **🔹 2. Tournament API**
**📌 Purpose:** Manages all tournament operations.  
**📍 Key Features:**
- 🏆 **Members can create or join teams.**
- 🔢 **Fixture generation** (automatic scheduling of matches).
- 🎯 **Match results entered by admin** → triggers MySQL auto-score updates.
- 🚀 **Group stage auto-calculations** → Top 2 advance.
- 🎲 **Knockout stage matchups auto-generated.**
- 🏁 **Competition ends when final match is played.**

---

### **🔹 3. Public API**
**📌 Purpose:** Handles homepage and non-competition-related content.  
**📍 Key Features:**
- 📰 **Fetch competition history & winners.**
- 🏟️ **Public pages showing upcoming tournaments.**
- 📢 **Announcements & News.**

---

### **🔹 4. Admin API**
**📌 Purpose:** Provides full **admin control** over competitions & platform.  
**📍 Key Features:**
- 🏆 **Create and Host Competition**
- 🎯 **Handle financials & prize distribution.**
- ⚙️ **Access all other APIs for full control.**
- 🎯 **Manage users

---

### **🔹 5. Azure Functions API (Serverless Automation)**
**📌 Purpose:** Automates backend tasks.  
**📍 Key Features:**
- 📧 **Send tournament-related emails.**
- 🏁 **Trigger notifications when a new match is available.**
- 🔄 **Update competition status automatically.**

---

### **🔹 6. Azure Cache API (Performance Optimization)**
**📌 Purpose:** Uses **Azure Cache for Redis** to improve efficiency.  
**📍 Key Features:**
- 🚀 **Reduces database queries for repeated requests.**
- ⚡ **Caches leaderboard, fixture schedules, and team stats.**

---

### **🔹 7. Azure Analytics API (Dashboard & Real-Time Updates)**
**📌 Purpose:** Enhances **Admin Dashboard** with analytics & real-time score updates.  
**📍 Key Features:**
- 📊 **Tracks tournament financials & user activity.**
- 🎯 **Real-time score updates during matches.**
- 🏆 **Performance tracking for teams.**

---

## **📌 Notifications System**
📩 **Notification Type:** **Email (No in-app notifications for now)**  
📍 **Triggers:**
- ✅ **Tournament joined** → Confirmation email.
- 🎯 **New match available** → Email notification.
- 🏆 **Tournament completed** → Winners & prize details sent.

---

## **📌 Deployment & DevOps**
- **Backend:** Flask (Python) running on **Azure App Services**.
- **Database:** MySQL on **Azure Database for MySQL**.
- **Cache:** **Azure Cache for Redis** (for performance improvements).
- **Automation:** **Azure Functions** for sending emails & updates.
- **Real-time Updates:** **Azure Analytics API** (for tournament scores).

---

## **✅ Final Summary**
| **Component** | **Status** |
|--------------|----------|
| **Database Schema** | ✅ Finalized |
| **API Structure** | ✅ Defined |
| **Authorization System** | ✅ Secured with JWT & OAuth |
| **Tournament System** | ✅ Auto-fixtures & knockout handling |
| **Admin Dashboard** | ✅ Connected to all APIs |
| **Azure Enhancements** | ✅ Cache, Automation, Analytics added |
| **Notifications** | ✅ Email-based alerts |
| **Deployment Plan** | ✅ Set for Azure Cloud |

---

## **🚀 Ready for Development!**  
This document will serve as our blueprint for building the **WPT Backend** efficiently. 💪 Let’s start coding! 🏗️🔥
