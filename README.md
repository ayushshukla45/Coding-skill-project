# 🚀 Quant-Grade Stock Trading Optimizer

### Graph Theory + Dynamic Programming + Full-Stack System Design

A production-grade **MERN application** that computes the **globally optimal trading strategy** for a given stock price series using **Dynamic Programming over a Directed Acyclic Graph (DAG)**.

Designed to demonstrate **algorithmic depth + system design + clean engineering practices**.

---

## 🧠 Core Idea

This project transforms the classical **k-transactions stock problem** into a **state-space graph optimization problem**, where:

* Each state = `(day, transactions_used, holding_state)`
* The system forms a **DAG**
* The optimal strategy is found via **DP + path reconstruction**

This bridges:

> **LeetCode DP → Real-world decision system**

---

## ✨ Key Highlights

* 🔥 **3D Dynamic Programming Engine** — O(n × k)
* 📊 **Graph-based State Modeling (DAG)**
* 🧭 **Optimal Trade Path Reconstruction**
* 📈 **Interactive Trading Visualization**
* 💰 **Per-Trade Profit Breakdown**
* ⚙️ **Configurable Constraints (k, fee, window)**
* 💾 **Scenario Persistence (MongoDB)**
* 🧩 **Offline DP fallback (client-side engine)**

---

## 🏗️ System Architecture

### 🔹 Frontend

* React 18 (Vite)
* Recharts (Data Visualization)
* Component-driven architecture
* Custom CSS (No UI frameworks)

### 🔹 Backend

* Node.js + Express
* REST API design
* Mongoose ORM
* Clean controller-service separation

### 🔹 Database

* MongoDB (Scenario storage)
* Optimized schema for replaying strategies

---

## 📐 Algorithm Breakdown

### State Definition

```
dp[i][j][0] → max profit on day i, j transactions, NOT holding
dp[i][j][1] → max profit on day i, j transactions, HOLDING
```

---

### Transition Logic

```
Sell / Rest:
dp[i][j][0] = max(
    dp[i-1][j][0],
    dp[i-1][j][1] + price[i] - fee
)

Buy / Hold:
dp[i][j][1] = max(
    dp[i-1][j][1],
    dp[i-1][j-1][0] - price[i]
)
```

---

### Graph Interpretation

Each DP state is a node in a DAG:

* REST → same state progression
* BUY → transaction consumed
* SELL → profit realized

👉 Final solution = **max path in DAG**

---

### Complexity

* Time: **O(n × k)**
* Space: **O(n × k)**

---

## 📊 Example

### Input

```json
{
  "prices": [100, 115, 95, 130, 120, 145],
  "maxTransactions": 2,
  "fee": 1.5
}
```

### Output

```json
{
  "maxProfit": 47.5,
  "trades": [
    { "day": 0, "action": "BUY" },
    { "day": 3, "action": "SELL" },
    { "day": 4, "action": "BUY" },
    { "day": 5, "action": "SELL" }
  ]
}
```

---

## 📁 Project Structure

```
stock-trading-optimizer/
├── backend/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   └── server.js
│
├── frontend/
│   ├── components/
│   ├── App.jsx
│   └── styles/
│
└── package.json
```

---

## 🚀 Running Locally

```bash
git clone <repo-url>
cd stock-trading-optimizer

npm install
cd backend && npm install
cd ../frontend && npm install

npm start
```

---

## 🔌 API Design

| Method | Endpoint                 | Purpose                  |
| ------ | ------------------------ | ------------------------ |
| POST   | /api/optimizer/calculate | Compute optimal strategy |
| POST   | /api/optimizer/save      | Persist scenario         |
| GET    | /api/optimizer/scenarios | Retrieve history         |

---

## 💡 Engineering Decisions

* Chose **DP over greedy** to support transaction constraints
* Modeled states as **graph nodes** for explainability
* Added **path reconstruction** → not just profit, but decisions
* Implemented **client fallback** → improves resilience

---

## 🎯 What This Project Demonstrates

* Strong grasp of **Dynamic Programming**
* Ability to convert theory → **production system**
* Understanding of **state modeling & optimization**
* Full-stack capability with **clean architecture**
* Focus on **UX + data visualization**

---

## 📌 Future Improvements

* Real-time stock API integration
* Multi-asset portfolio optimization
* Reinforcement learning strategy layer
* WebSocket live trading simulation

---

## 📄 License

MIT License

---

## 👨‍💻 Author

Ayush Shukla
B.Tech CSE | Aspiring Software Engineer | DSA Enthusiast
