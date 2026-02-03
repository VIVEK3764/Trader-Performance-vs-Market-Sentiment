# Trader Performance vs Market Sentiment

## 📌 Overview  
This repository contains a complete data science analysis for the **Primetrade.ai Data Science Intern Round-0 Assignment**, investigating the relationship between **Bitcoin market sentiment (Fear/Greed Index)** and **trader behavior and performance on Hyperliquid**.

The project aligns high-frequency trade data to a daily level, engineers key trading metrics, analyzes behavioral changes across sentiment regimes, segments traders into meaningful groups, and derives actionable trading rules backed by data.

---

## 🎯 Objectives  
The analysis aims to:

- Align trade-level Hyperliquid data with daily Fear/Greed sentiment.
- Measure how trader performance (PnL, win rate, risk) varies across Fear, Greed, and Neutral days.
- Identify systematic behavioral changes in:
  - Trade frequency  
  - Position size  
  - Long/Short bias  
- Segment traders into meaningful groups such as:
  - Frequent vs Infrequent traders  
  - High vs Low risk traders (position size proxy)  
  - Consistent vs Inconsistent winners  
- Provide data-backed, actionable trading rules.
- (Bonus) Build a simple predictive model and cluster traders into behavioral archetypes.

---

## 🗂️ Data Used  

### 1️⃣ Fear & Greed Index (Daily)
**Columns:**
- `timestamp`
- `value`
- `classification` (Fear / Greed / Neutral)
- `date` (DD-MM-YYYY)

### 2️⃣ Hyperliquid Historical Trades (Trade-level)
**Key columns used:**
- `Account`
- `Execution Price`
- `Size USD`
- `Side` (Buy/Sell)
- `Timestamp IST` (DD-MM-YYYY HH:MM)
- `Closed PnL`

---

## 🛠️ Methodology  

### **1. Data Preparation**
- Converted `Timestamp IST` to a daily `date` field.
- Aggregated trade-level data to **per-account, per-day** metrics:
  - Total PnL  
  - Win rate  
  - Number of trades  
  - Average position size  
  - Long/Short ratio  

### **2. Sentiment Alignment**
- Merged daily aggregated trading data with Fear/Greed sentiment using `date` as the key.

### **3. Analysis**
- Compared trader performance across Fear, Greed, and Neutral days.
- Examined changes in:
  - Trade frequency  
  - Position size  
  - Long/Short bias  
- Visualized results using:
  - Boxplots  
  - Bar charts  
  - Time series plots  

### **4. Trader Segmentation**
Traders were segmented based on:
- **Frequency**: Frequent vs Infrequent (top 25% by trades/day)
- **Risk Proxy**: High vs Low position size
- **Performance**: Consistent vs Inconsistent winners

### **5. Actionable Strategies**
Derived two key data-backed trading rules based on findings.

### **6. Bonus Work**
- Built a simple Random Forest model to predict next-day profitability bucket.
- Clustered traders into behavioral archetypes using K-Means.

---

## 📊 Key Insights  

1. **Fear days show the highest average PnL but also the greatest downside risk**, indicating higher volatility.
2. **Traders trade more and take larger positions on Fear days**, suggesting reactive behavior.
3. **Frequent traders consistently outperform infrequent traders** across all sentiment regimes.

---

## 📈 Actionable Strategy Recommendations  

### **Strategy 1 — Risk Control (Fear Days)**
> Reduce position size and effective leverage for infrequent traders during Fear days.

### **Strategy 2 — Selective Aggression (Greed Days)**
> Allow higher trade frequency only for frequent traders on Greed days, while keeping position sizes controlled.

---

## 🧠 Bonus: Predictive & Clustering Work  
- **Predictive Model:** Random Forest classifier to forecast next-day PnL bucket (up/neutral/down).  
- **Clustering:** K-Means used to group traders into behavioral archetypes based on trade frequency and win rate.

---

## 🚀 How to Run  

### **1. Install dependencies**
```bash
pip install -r requirements.txt
