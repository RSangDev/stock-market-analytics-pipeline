# 📈 Stock Market Analytics Pipeline

**Production-grade financial data engineering pipeline with real-time trading signals**

![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![Real Data](https://img.shields.io/badge/Real%20Data-Yahoo%20Finance-blue)
![Python](https://img.shields.io/badge/Python-3.11+-green)
![Finance](https://img.shields.io/badge/Finance-Technical%20Analysis-orange)

---

## 🎯 Project Overview

A **complete, production-ready** data pipeline for stock market analysis that:

✅ **Ingests REAL stock data** from Yahoo Finance API (5 years history)
✅ **Calculates 20+ technical indicators** (MA, RSI, MACD, Bollinger Bands, etc)
✅ **Generates trading signals** (Buy/Sell/Hold recommendations)
✅ **Tracks 10 major stocks** (AAPL, MSFT, GOOGL, AMZN, TSLA, etc)
✅ **Provides market sentiment analysis** (Bullish/Bearish/Neutral)
✅ **Monitors SLAs** (Data freshness, quality, completeness)
✅ **Production dashboards** with real-time metrics

---

## 📊 Architecture

### Complete Data Flow

```
Yahoo Finance API (Real-time)
        ↓
BRONZE: Raw price data (OHLCV)
        ├─ Open, High, Low, Close, Volume
        ├─ 5 years history
        └─ 10 major stocks
        ↓
SILVER: Technical Indicators
        ├─ Moving Averages (20d, 50d, 200d)
        ├─ Exponential MA (12, 26)
        ├─ MACD & Bollinger Bands
        ├─ RSI & Volatility
        └─ Trend signals
        ↓
GOLD: Analytics & Trading Signals
        ├─ Trading signals (STRONG_BUY, BUY, HOLD, SELL, STRONG_SELL)
        ├─ Performance rankings
        ├─ Volatility analysis
        ├─ Momentum indicators
        └─ Daily returns
        ↓
MONITORING: Dashboard & Alerts
        ├─ Market sentiment
        ├─ SLA compliance
        ├─ Technical alerts
        └─ Performance metrics
```

---

## 🏗️ Technical Stack

| Component | Technology |
|-----------|-----------|
| **Data Source** | Yahoo Finance API |
| **Processing** | Apache Spark + SQL |
| **Storage** | Delta Lake (ACID guarantees) |
| **Platform** | Databricks |
| **Catalog** | Unity Catalog |
| **Language** | Python + Spark SQL |

---

## 📁 Project Structure

```
stock-market-analytics-pipeline/
├── notebooks/
│   ├── 01_stock_data_ingestion.py       # Fetch real Yahoo Finance data
│   ├── 02_technical_indicators.py       # Calculate 20+ indicators
│   ├── 03_analytics_signals.py          # Generate trading signals
│   ├── 04_data_quality.py               # 20+ validation checks
│   └── 05_monitoring_dashboard.py       # Real-time metrics & SLAs
├── docs/
│   ├── README.md (this file)
│   ├── GETTING_STARTED.md
│   └── TECHNICAL_INDICATORS.md
└── LICENSE (MIT)
```

---

## 🚀 Quick Start

### Prerequisites
- Databricks Account (Community Edition FREE)
- Python 3.9+
- `yfinance` library (pip install yfinance)

### Setup (5 minutes)

**Step 1: Create Notebooks**
```
In Databricks workspace:
1. Create: 01_stock_data_ingestion
2. Create: 02_technical_indicators
3. Create: 03_analytics_signals
4. Create: 04_data_quality
5. Create: 05_monitoring_dashboard
```

**Step 2: Copy & Run Code**
```
For each notebook:
1. Copy from /notebooks/ folder
2. Paste into Databricks
3. Execute cells sequentially
```

**Step 3: Verify Success**
```sql
-- Check tables created
SELECT COUNT(*) FROM workspace.stock_analytics.gold_trading_signals;

-- View latest trading signals
SELECT Ticker, Trading_Signal, Confidence
FROM workspace.stock_analytics.gold_trading_signals
ORDER BY Confidence DESC;
```

---

## 📊 Data Captured

### Stocks Tracked

```
Technology:           Finance:
✅ AAPL (Apple)       ✅ JPM (JP Morgan)
✅ MSFT (Microsoft)   
✅ GOOGL (Google)     Healthcare:
✅ NVDA (Nvidia)      ✅ JNJ (J&J)
✅ META (Meta)        
                      Consumer:
Retail/Cloud:         ✅ PG (Procter & Gamble)
✅ AMZN (Amazon)      
                      Auto/Energy:
✅ TSLA (Tesla)
```

### Data Per Stock

```
OHLCV Data:
├─ Open (daily opening price)
├─ High (daily high price)
├─ Low (daily low price)
├─ Close (daily closing price)
└─ Volume (shares traded)

Time Period:
├─ 5 years of historical data
├─ Daily granularity
└─ ~1,250 trading days per stock
```

---

## 📈 Technical Indicators

### 20+ Indicators Calculated

**Moving Averages:**
- MA_20, MA_50, MA_200 (Simple Moving Averages)
- EMA_12, EMA_26 (Exponential Moving Averages)

**Momentum Indicators:**
- RSI_14 (Relative Strength Index)
- MACD Line, Signal, Histogram
- Daily Return %

**Volatility:**
- Bollinger Bands (Upper, Lower, Position)
- 30-day & 90-day Volatility
- Band Width

**Trend Signals:**
- Price Trend (Bullish/Bearish vs MA_20)
- Trend Direction (Uptrend/Downtrend vs MA_200)
- Golden Cross (50MA > 200MA = BUY)
- Death Cross (50MA < 200MA = SELL)

---

## 🎯 Trading Signals

### Signal Types

```
STRONG_BUY  → Multiple bullish indicators aligned
BUY         → Price oversold (RSI < 30) + bullish trend
ACCUMULATE  → MACD positive + price bullish
HOLD        → Mixed signals or consolidation
DISTRIBUTE  → MACD negative + price bearish
SELL        → Price overbought (RSI > 70) + bearish trend
STRONG_SELL → Multiple bearish indicators aligned
```

### Example Dashboard Output

```
Ticker | Signal      | Confidence | RSI   | MACD Status
-------|-------------|------------|-------|---------------
AAPL   | STRONG_BUY  | 92%        | 28    | Bullish
TSLA   | BUY         | 85%        | 32    | Bullish
MSFT   | HOLD        | 62%        | 55    | Neutral
GOOGL  | SELL        | 78%        | 68    | Bearish
AMZN   | STRONG_SELL | 89%        | 75    | Bearish
```

---

## 💡 Key Features

### 1. Real Data Integration
- **Yahoo Finance API** provides authentic market data
- 5 years of historical prices
- Daily updates (market close)
- No synthetic/fake data

### 2. Comprehensive Analysis
- **20+ technical indicators** for thorough analysis
- **Multiple timeframes** (20d, 50d, 200d)
- **Momentum + volatility** indicators combined
- **Trend confirmation** signals

### 3. Production Quality
- **20+ quality checks** (NULL, negatives, logic)
- **SLA monitoring** (freshness, completeness)
- **Error handling** (API failures, edge cases)
- **Data validation** across layers

### 4. Business Insights
- **Trading signals** for investment decisions
- **Performance rankings** (best/worst performers)
- **Market sentiment** analysis
- **Volatility assessment**

---

## 📊 Notebooks Explained

### Notebook 1: Stock Data Ingestion

**Purpose:** Fetch real stock prices from Yahoo Finance

```python
# Fetches:
- 10 major stocks (AAPL, MSFT, GOOGL, etc)
- 5 years of daily OHLCV data
- ~1,250 trading days × 10 stocks = 12,500 records

# Quality checks:
- No NULL values in critical fields
- Prices must be positive
- High ≥ Low ≥ Close logic
- No volume = 0 days
- No duplicate ticker-date combos

# Output:
✅ bronze_stock_prices table
   Raw data, ready for transformation
```

---

### Notebook 2: Technical Indicators

**Purpose:** Calculate 20+ indicators for trading analysis

```python
# Creates indicators:
- 5 moving averages (different periods)
- MACD (momentum)
- Bollinger Bands (volatility)
- RSI (strength)
- Volatility metrics
- Trend signals

# Output:
✅ silver_stock_indicators table
   Enriched data, all indicators calculated
```

---

### Notebook 3: Analytics & Signals

**Purpose:** Generate trading signals and insights

```python
# Creates 5 gold tables:
1. Trading Signals (buy/sell/hold)
2. Performance Rankings (best/worst)
3. Volatility Analysis (overbought/oversold)
4. Momentum Analysis (RSI, MACD status)
5. Historical Returns (daily % change)

# Output:
✅ 5 production-ready gold tables
   Ready for dashboards & analysis
```

---

### Notebook 4: Data Quality

**Purpose:** Validate data at every layer

```python
# 20+ checks:
- NULL validation
- Range validation (prices, RSI, etc)
- Logic validation (High > Low)
- Indicator quality (all calculated)
- Consistency checks

# Output:
✅ quality_metrics table
   Audit trail of all validations
```

---

### Notebook 5: Monitoring Dashboard

**Purpose:** Real-time metrics and SLA tracking

```python
# Dashboard shows:
- Trading signal distribution
- Market sentiment (bullish/bearish %)
- Top/bottom performers
- Technical alerts
- SLA compliance

# Output:
✅ pipeline_metrics table
   Historical tracking of performance
```

---

## 📊 Dashboard Example

```
╔════════════════════════════════════════════════╗
║     STOCK MARKET ANALYTICS DASHBOARD           ║
║              2026-06-16 14:30:00               ║
╚════════════════════════════════════════════════╝

📊 TRADING SIGNALS:
   Strong BUY:     2 stocks
   Strong SELL:    1 stock
   HOLD:           7 stocks

💪 MARKET CONDITIONS:
   Overbought:     3 stocks (RSI > 70)
   Oversold:       2 stocks (RSI < 30)
   High volatility: 4 stocks

🏆 PERFORMANCE (1M):
   Top 3: TSLA (+18.5%), NVDA (+12.3%), AAPL (+5.2%)
   Bottom: AMZN (-8.1%), GOOGL (-4.2%), META (-1.5%)

✅ SLA STATUS:
   Data Freshness:    ✅ PASS (0 days old)
   Data Completeness: ✅ PASS (10/10 stocks)
   Quality Metrics:   ✅ PASS (98% pass rate)

📈 MARKET SENTIMENT:
   Bullish:  60%
   Bearish:  30%
   Neutral:  10%
   Overall:  📈 BULLISH
```

---

## 🎯 Use Cases

### For Traders
```
"Check trading signals before market open"
SELECT Ticker, Trading_Signal, Confidence
FROM gold_trading_signals
WHERE Confidence > 80
ORDER BY Trading_Signal;
```

### For Investors
```
"Identify overbought/oversold opportunities"
SELECT Ticker, RSI_Status, Return_1M_Percent
FROM gold_momentum_analysis
WHERE RSI_Status IN ('Overbought', 'Oversold');
```

### For Analysts
```
"Analyze market sentiment"
SELECT Trading_Signal, COUNT(*) as count
FROM gold_trading_signals
GROUP BY Trading_Signal;
```

---

## 🎓 Skills Demonstrated

### Data Engineering
✅ Real API integration (Yahoo Finance)
✅ Time-series data handling
✅ Technical indicator calculation
✅ Signal generation logic
✅ Complex aggregations

### Production Engineering
✅ Data quality framework (20+ checks)
✅ SLA monitoring
✅ Error handling
✅ Performance tracking
✅ Alert mechanisms

### Finance Knowledge
✅ Technical analysis
✅ Indicator interpretation
✅ Trading signals
✅ Market sentiment
✅ Risk metrics

### Software Engineering
✅ Clean code organization
✅ Modular notebooks
✅ Professional documentation
✅ Production best practices

---

## 📈 Performance

| Metric | Value |
|--------|-------|
| **Stocks tracked** | 10 |
| **Data points** | 12,500+ |
| **Indicators per stock** | 20+ |
| **Trading signals** | 7 levels |
| **Quality checks** | 20+ |
| **Execution time** | ~3-5 minutes |
| **Data freshness** | Daily |

---

## 🔐 Important Notes

### API Rate Limiting
- Yahoo Finance: No official rate limit for `yfinance`
- Pipeline: Respectful 0.5s delay between requests
- Data volume: Minimal (10 stocks, 5 years = ~small)

### Data Quality
- Historic data is audited by Yahoo Finance
- Real OHLCV data, not simulated
- Quality checks catch anomalies
- Validation at every layer

### Financial Disclaimer
⚠️ **This pipeline is for educational purposes only!**

Not financial advice. Signals are technical indicators, not recommendations.
Always do your own research. Past performance ≠ future results.

---

## 🚀 Next Steps

### Immediate
1. ✅ Run all 5 notebooks
2. ✅ Verify data in gold tables
3. ✅ Review dashboard summary
4. ✅ Push to GitHub portfolio

### Enhancement Ideas
- Add more indicators (ATR, Stochastic, etc)
- Include sector analysis
- Add correlation analysis
- Implement prediction model (ML)
- Create interactive Streamlit dashboard
- Schedule daily automated runs

---

## 📚 Reference

- [Yahoo Finance API](https://pypi.org/project/yfinance/)
- [Databricks Docs](https://docs.databricks.com)
- [Technical Indicators Guide](https://www.investopedia.com/)
- [Spark SQL Reference](https://spark.apache.org/docs/latest/sql-ref.html)

---

## 👨‍💼 Interview Talking Points

**"I built a production stock market analytics pipeline that..."**

> "The pipeline fetches real stock data from Yahoo Finance for 10 major stocks with 5 years of historical prices. It calculates 20+ technical indicators (moving averages, RSI, MACD, Bollinger Bands, etc) using Spark for distributed processing.
>
> The system generates trading signals (Strong Buy/Buy/Hold/Sell/Strong Sell) based on multiple indicators, tracks market sentiment, and provides performance rankings.
>
> Key features:
> - **Real data**: Yahoo Finance API (not synthetic)
> - **Production quality**: 20+ quality checks, SLA monitoring
> - **Complete pipeline**: Bronze/Silver/Gold architecture
> - **Trading signals**: 7-level signal system with confidence scoring
> - **Monitoring**: Real-time dashboards, alerts, metrics
>
> This demonstrates data engineering expertise in financial domain, technical analysis knowledge, and production-grade system design."

---

## 📄 License

MIT License - Free to use for learning and portfolios

---

**Version**: 1.0  
**Status**: ✅ Production Ready  
**Last Updated**: June 2026

Built with ❤️ using Databricks Community Edition & Yahoo Finance