# AI Investment News Impact on Companies Financial Data

## Project Overview
Artificial Intelligence (AI) has become a significant driver of innovation and business transformation. This project aims to investigate how AI investments influence company valuation over time. By analyzing financial and market data, I will assess the effects of AI-related expenditures on business growth and market perception.

---

## Objectives
1. **Evaluate Financial Impact**  
   Examine how AI investments correlate with stock prices, profit margins, and some other financial data such as volatility, RSI etc. .  

3. **Analyze Market Perception**  
    Assess how AI-related announcements affect investor confidence and market sentiment.  

5. **Identify Company Trends**  
    Track patterns to determine which companies benefit the most from AI investments.  

7. **Predict Future Performance**  
    Use data-driven methods to form a relation on how AI investments might shape companies' financial data.

---

## Motivation
The growing adoption of AI has led to significant financial commitments from businesses. Understanding whether these investments result in tangible financial gains can help companies make more strategic decisions. This project will provide a data-driven perspective on the real impact of AI funding.

### Why This Matters?
#### 🔹 Strategic Decision-Making  
  Quantify ROI of AI investments to guide budgeting and R&D prioritization.  
#### 🔹 Investor Confidence  
  Understand how AI initiatives influence market sentiment and stock performance.  
#### 🔹 Competitive Advantage  
  Identify optimal AI investment strategies for best market values.  

---

## Dataset
In this study, I utilize data collected from multiple sources, specifically focusing on five major technology companies: Tesla, Amazon, Google, Microsoft, and Nvidia. The dataset components are categorized as follows:

### Stock Market Data 📈
To assess the financial market response to AI developments, I employ both raw and enriched daily stock price data for the year 2025:
#### ➖ Raw stock data:
Includes Date, Open, High, Low, Close, Volume
#### ➖ Enriched stock data:
Includes all raw data fields, along with Return Price, Volatility, and RSI (Relative Strength Index) Value

### AI-Related News Coverage 📰
To capture external signals and information flow relevant to AI:
#### ➖ News dataset:
Contains AI-related articles from Google Search with fields such as Company, Month, Date, Title, and Link

### Sentiment Analysis of News 💬
To measure market sentiment and emotional tone in response to AI news:
#### ➖ Sentiment-enriched news dataset:
Builds upon the news dataset by including Sentiment Score and a categorical Sentiment Label (Positive, Negative, or Neutral)

---

## Tools and Technologies
To process, analyze, and visualize the data, I will use:  
📌 Python (Pandas, NumPy) – Data cleaning and preprocessing  
📌 Matplotlib & Seaborn – Trend visualization  
📌 NLP (NLTK, spaCy, TextBlob) – Sentiment analysis of market news  
📌 Machine Learning (Scikit-learn) – Predictive modeling  
📌 SQL & APIs – Financial data extraction  
📌 Jupyter Notebook – Analysis documentation
📌 yfinance – Stock price data collection
📌 GoogleNews Python Library – AI-related news scraping
📌 openpyxl – Excel file handling



---

## Analysis Plan
### 1️⃣ Data Collection & Preprocessing  
Gather financial reports, stock data, and sentiment indicators.  
Standardize data formats and handle missing values.  

### 2️⃣ Exploratory Data Analysis (EDA)  
Visualize AI investment trends vs. valuation changes.  
Calculate correlation matrices for key financial metrics.  

### 3️⃣ Statistical Testing & Hypothesis Validation  
Test significance of AI spending on market values (ANOVA/t-test/regression).  
Analyze stock price reactions to AI announcements (event study methodology).  

### 4️⃣ Predictive Modeling & Industry Benchmarking  
Build regression models to forecast valuation impacts.  
Compare AI ROI across sectors using clustering techniques.  

### 5️⃣ Strategic Recommendations  
Develop frameworks for optimizing trader transactions according to AI investment news.  
Create company-specific guidelines for maximizing valuation growth considering AI investments.  

---

## Project Objective 🎯
This study aims to empirically investigate how AI-related news and announcements influence market behavior, particularly focusing on short-term financial indicators. Rather than assuming AI investment increases firm value, this analysis takes a data-driven approach to test the real market effects of AI developments. Specifically, the study seeks to answer the following questions: 
### 🔍 Key Research Questions
#### ✔ Does market sentiment around AI announcements influence short-term stock returns or volatility?  
→ Explores whether positive or negative news articles lead to measurable return differences and how they affect market stability.
#### ✔ Do AI announcements increase abnormal stock price movements (CAR)?
→ Tests whether AI-related company announcements are associated with significant abnormal returns in the days following the news.  
#### ✔ Does market volatility increase after AI-related news events?
→ Evaluates whether investor uncertainty or trading activity rises in response to AI developments.
#### ✔ Are there differences in how companies benefit from AI announcements?
→ Compares company-level responses to AI news to detect any firm-specific market advantages.  

### 🧠 Broader Goal
#### By combining sentiment analysis, event study methodology, and financial modeling, this project aims to uncover the true market response to AI narratives—separating substance from hype. The goal is to help investors identify realistic AI-driven opportunities and guide businesses toward strategic, impact-driven AI communication.
