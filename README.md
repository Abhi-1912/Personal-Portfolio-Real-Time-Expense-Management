# 📈 Personal Portfolio & Real-Time Expense Management Dashboard

![Project Banner](https://raw.githubusercontent.com/placeholder/portfolio-dashboard-banner.png)

## 📌 1. Project Overview

**Personal Portfolio & Real-Time Expense Management Dashboard** is an event-driven, multi-threaded desktop financial simulator designed specifically for university students and early-career professionals. 

It provides an all-in-one solution to manage daily localized expenditures (e.g., college tuition, campus hostel rent, mess hall fees, transit passes) alongside micro-investment systematic investment plans (SIPs in domestic equities like Reliance, TCS, Infosys, and Nifty ETFs) in **Indian Rupees (₹ INR)**. Built with **Java SE 17+** and **JavaFX**, the system ensures 100% offline privacy and zero third-party cloud dependency via an embedded, parameterized SQLite architecture.

> **🎯 Tagline:** Localized Expense Tracking Meets Real-Time Portfolio Intelligence.

---

## 🔥 2. Key Features

- **📝 Parameterized Transaction Logging:** Record, edit, and categorize daily expenses, income streams, and asset purchases with strict input validation to prevent invalid entries or SQL injection attacks.
- **🧠 Automated Categorization & Ledger Management:** Tracks localized student and personal expense categories:
  - 🎓 Tuition & Academic Fees
  - 🏠 Hostel & Mess Bills
  - 🛒 Grocery & Daily Hauls
  - 🚌 Metro & Campus Transit
  - 📈 Equity & ETF SIP Investments (e.g., Reliance, TCS, Infosys, Nifty ETFs)
  - 🍿 Leisure & Entertainment
  - 📦 Miscellaneous Ledger Entries
- **📊 Dynamic Visual Analytics:** Real-time data visualization featuring JavaFX `PieChart` controls for category distribution and `LineChart` controls to plot net worth velocity over time.
- **⚡ Asynchronous Live Market Ingestion:** Non-blocking background API pipeline using `CompletableFuture` thread pools and Java's native `HttpClient` to update stock/crypto valuations without freezing the user interface.
- **💰 Real-Time Budget Alert Engine:** Evaluates category spending against pre-set monthly limits and issues instant alerts at exact mathematical thresholds:
  - ⚠️ **80% Capacity:** Warning Notification
  - 🚨 **100% Capacity:** Budget Breach Alert
- **🔎 Sortable & Filterable Table Views:** Advanced data table interface utilizing `FilteredList` and `SortedList` wrappers for instant live search across transaction dates, categories, and descriptions.
- **🛡️ High-Performance Local Persistence:** HikariCP connection pooling over SQLite guarantees sub-10ms query execution speed.
- **Circuit Breaker Data Protection:** An in-memory `ConcurrentHashMap` price cache ensures application operational continuity even during network drops.

---

## 🛠️ 3. Technologies & Architecture

### **Tech Stack**
- **Core Language:** Java SE 17+
- **GUI Toolkit:** JavaFX 17+ (FXML, Controls, Charts)
- **Database Engine:** Embedded SQLite 3.x via JDBC
- **Connection Pool:** HikariCP 5.0.1
- **Async Networking:** Java `java.net.http.HttpClient` + `CompletableFuture`
- **JSON Processing:** Jackson Databind (`ObjectMapper`)
- **Testing Framework:** JUnit 5

### **System Architecture (MVC Pattern)**
```text
Personal Portfolio Dashboard
│
├── Presentation Layer (JavaFX FXML View)
│   ├── Dashboard Overview
│   ├── Transaction TableView (FilteredList/SortedList)
│   ├── Interactive Expense PieChart
│   └── Net Worth LineChart
│
├── Controller Layer
│   ├── DashboardController
│   └── Event Handlers (Platform.runLater dispatchers)
│
├── Core Model & Processing Services
│   ├── DatabaseManager (HikariCP / SQLite JDBC)
│   ├── MarketDataService (Async HttpClient & Jackson Parser)
│   ├── BudgetAlertEngine (80% & 100% Threshold Validation)
│   └── TransactionValidationUtils
│
└── Data Storage
    └── Local SQLite Storage (`vityarthi_portfolio.db`)
