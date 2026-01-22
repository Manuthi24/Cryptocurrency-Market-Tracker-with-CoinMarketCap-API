## 📌 Project Overview
This project automates the process of pulling **real-time cryptocurrency market data** from the **CoinMarketCap API**.  
It goes beyond basic API requests by implementing an **automated data collection loop**, a **robust transformation pipeline**, and **custom visualisations** to track market trends over time.

The tool is designed for cryptocurrency enthusiasts, analysts, or traders who want **continuous monitoring** of top coins and insightful visual analysis of price movements.

---

## 📊 Key Features

### 1. Automated Data Extraction
- Custom function `api_runner` triggers API calls at **set intervals** using the `time` and `sleep` modules.  
- Ensures **continuous, real-time tracking** of market data.

### 2. Dual-Method Storage
- Supports **data persistence**:
  - Append to a **Pandas DataFrame** in memory for quick analysis.
  - Write directly to a **local CSV file** to prevent data loss during interruptions.

### 3. Custom Timestamping
- Adds a **system-generated timestamp** for every data pull.  
- Ensures accurate tracking of automated runs independent of the API's internal update time.

### 4. Data Transformation Pipeline
- Converts **scientific notation** to readable floats.  
- Aggregates data by coin name to calculate **average percentage changes**.  
- Reshapes data from **wide to long format** for compatibility with advanced visualisation.

### 5. Advanced Visualisations
- **Categorical Plots (catplot):** Compare price fluctuations across multiple timeframes (1h, 24h, 7d, 30d, 90d).  
- **Line Charts:** Track individual coin price trajectories over time.  
- Uses **Seaborn** with a darkgrid theme for a professional look.

---

## 🔄 Project Workflow

1. **Extraction:** Call the API and normalize JSON responses into a flat table.  
2. **Automation:** The loop runs up to **333 times/day** to stay within free tier limits; typically pauses **60 seconds** between runs.  
3. **Cleaning:** Focus on the **top 15 cryptocurrencies** for efficiency.  
4. **Reshaping:** Transform data from Series to DataFrame and index for clarity.  
5. **Visualisation:** Generate clear, actionable plots using Seaborn and Matplotlib.

---

## 🛠️ Technologies Used
- **Python:** Core scripting and automation.  
- **Pandas:** Data manipulation, aggregation, and JSON normalization.  
- **Seaborn & Matplotlib:** Categorical and time-series visualisations.  
- **OS & Time Modules:** File path management and automation timing.  
- **CoinMarketCap API:** Primary source of cryptocurrency market data.

---

## 💡 Lessons Learned & Best Practices
- **Error Handling:** Resolve local variable issues by declaring variables as global inside functions.  
- **Storage Strategy:** Appending to CSV ensures data persistence if memory storage fails.  
- **Data Formatting:** Lambda functions for float formatting improve readability of financial data.

---

## 📝 How to Use
1. Obtain a **CoinMarketCap API key** from [their developer portal](https://coinmarketcap.com/api/).  
2. Update the script with:
   - Your **API key**
   - Your preferred **local CSV file path**  
3. Execute the `api_runner` loop to begin automated data collection.  
4. Visualisations are generated automatically during runtime.

---

## 📁 Project Files
```text
├── crypto_tracker.py         # Main Python script with API automation and visualisation
├── data/                     # Folder for storing CSV data
│   └── crypto_data.csv
├── assets/                   # Optional folder for saved plots/screenshots
└── README.md
