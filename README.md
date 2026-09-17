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
```
## 🚀 4. Installation & Setup Guide

### Prerequisites
Ensure the following are installed on your machine:
- [Java Development Kit (JDK) 17+](https://www.oracle.com/java/technologies/downloads/)
- [Apache Maven](https://maven.apache.org/) (or Gradle)
- Git

Verify your environment setup:
```bash
java -version
mvn -version
└── Data Storage
    └── Local SQLite Storage (`vityarthi_portfolio.db`)
```
## 🚀 4. Installation & Setup GuidePrerequisitesEnsure the following are installed on your machine:Java Development Kit (JDK) 17+Apache Maven (or Gradle)GitVerify your environment setup:Bashjava -version
mvn -version
QuickstartClone the repository:Bashgit clone [https://github.com/Abhinav/personal-portfolio-expense-dashboard.git](https://github.com/Abhinav/personal-portfolio-expense-dashboard.git)
cd personal-portfolio-expense-dashboard
Compile and build dependencies:Bashmvn clean compile
Launch the JavaFX Application:Bashmvn javafx:run
Execute Test Suite:Bashmvn test
Test Case,Module,Input Action,Expected Result
## 🧪 5. Testing Instructions
TC-01,Database Manager,Enter expense amount = ₹-500.00,Throws TransactionValidationException cleanly without saving
TC-02,SQL Injection Test,Input ' OR '1'='1 in transaction description,Parameterized PreparedStatement safely escapes input
TC-03,Budget Warning,Category expense hits 80% of monthly limit,System triggers WARNING_80_PERCENT alert indicator
TC-04,Budget Breach,Category expense hits 100% of monthly limit,System triggers BREACH_100_PERCENT alert notification
TC-05,Async Market Fetch,Trigger equity market price refresh,Fetch runs on worker thread; UI renders at smooth 60 FPS
TC-06,Network Failover,Simulate internet connection timeout,Circuit breaker falls back to cached prices in ConcurrentHashMap
TC-07,UI Data Binding,"Log new transaction entry of ₹15,000.00","TableView, PieChart, and LineChart update dynamically"
## 6.Project StructurePlaintextpersonal-portfolio-expense-dashboard/
├── src/
│   ├── main/
│   │   ├── java/com/vityarthi/portfolio/
│   │   │   ├── MainApp.java
│   │   │   ├── controller/
│   │   │   │   └── DashboardController.java
│   │   │   ├── model/
│   │   │   │   ├── Transaction.java
│   │   │   │   └── Asset.java
│   │   │   ├── database/
│   │   │   │   └── DatabaseManager.java
│   │   │   ├── service/
│   │   │   │   └── MarketDataService.java
│   │   │   ├── engine/
│   │   │   │   └── BudgetAlertEngine.java
│   │   │   ├── util/
│   │   │   │   └── ValidationUtils.java
│   │   │   └── exception/
│   │   │       └── TransactionValidationException.java
│   │   └── resources/
│   │       ├── fxml/
│   │       │   └── DashboardView.fxml
│   │       ├── styles/
│   │       │   └── application.css
│   │       └── db/
│   │           └── schema.sql
│   └── test/
│       └── java/com/vityarthi/portfolio/
│           ├── BudgetAlertEngineTest.java
│           └── DatabaseManagerTest.java
├── pom.xml
├── README.md
└── STATEMENT.md
## 🔮 8. Future Enhancements📱 Automated SMS Statement Parsing: Localized regex parsing engine to extract transaction records from bank SMS alerts.🔮 Machine-Learning Expense Prediction: Integration of linear regression algorithms for forecasting end-of-month cash flows.🔒 Encrypted Storage at Rest: Implementation of SQLCipher for transparent AES-256 bit encryption of local .db files.
👨‍💻 9. Candidate & Project InformationProject Title: Personal Portfolio & Real-Time Expense Management DashboardCandidate Name: AbhinavRegistration Number: 25BAI10303Institution: VIT Bhopal UniversityCore Technology: Java 17+, JavaFX, JDBC, SQLite, HikariCP, Jackson Databind, JUnit 5License: MIT
