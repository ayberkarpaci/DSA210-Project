# AI Investment News and Big Tech Stock Prices

[![notebooks](https://github.com/ayberkarpaci/DSA210-Project/actions/workflows/notebooks.yml/badge.svg)](https://github.com/ayberkarpaci/DSA210-Project/actions/workflows/notebooks.yml)

DSA 210 term project. It asks whether news
about AI investments moves the stock prices of **Tesla, Amazon, Google,
Microsoft and Nvidia**, using daily prices and Google News headlines from
January to April 2025.

## Research questions

1. Does the tone of AI-related news predict next-day stock returns?
2. Do positive-news days see better returns than negative-news days?
3. Does volatility rise after AI news?
4. Do the five companies react differently?
5. Can technical indicators plus news sentiment predict whether a stock closes
   higher the next day?

## Key findings

- **Tone matters, weakly.** Headline sentiment has a small but significant
  positive correlation with the next day's return relative to the other four
  stocks (Spearman rho = 0.15, Holm-adjusted p = 0.02). After negative-news
  days the stock trailed its peers by 0.92% the next day; after positive-news
  days it led by 0.27%.
- **No volatility effect.** Absolute returns are not significantly higher in
  the five days after news than in the five days before.
- **Companies differ.** Microsoft outperformed its peers after news days and
  Tesla fell behind (ANOVA and Kruskal-Wallis both significant).
- **Next-day direction is hard to predict.** On the final test period no model
  beats "always predict down" on accuracy (67.7%). Ranking quality is modest
  (walk-forward ROC AUC 0.60 to 0.67), driven mostly by technical features
  rather than sentiment.
- News appears on 74 of 75 trading days for every company, so the data
  cannot compare "announcement" with "no announcement"; the analysis compares
  the tone of the news instead.

## Data

| Folder | Contents | Source |
|---|---|---|
| `DATA/2025 stock data` | Daily OHLCV, 2 Jan to 22 Apr 2025 | Yahoo Finance via `yfinance` |
| `DATA/2025 enriched data` | Adds simple return, 10-day volatility, 14-day Wilder RSI and traded value | Computed |
| `DATA/2025 ai investment news` | 783 headlines for "<company> AI investment" | Google News via `GoogleNews` |
| `DATA/2025 ai investment news sentimented data` | Adds a VADER compound score and a positive / neutral / negative label | Computed |

## Repository structure

```
Codes/                                   data collection pipeline (needs internet)
  Raw data extraction code.ipynb         1. download prices
  Raw data to enriched data code.ipynb   2. add return, volatility, RSI, value
  Raw news extraction code.ipynb         3. collect headlines
  Raw news to sentimented news code.ipynb  4. score sentiment
DATA/                                    the collected and processed data
Exploratory Data Analysis and Hypothesis Testing.ipynb
Applying Machine Learning Methods.ipynb
Final Report.pdf                         report as submitted for the course
```

## Methods

- **Event table.** Each headline is mapped to the first trading session on or
  after its date; headlines about the same company on the same day are averaged
  into one event (315 events).
- **Peer-adjusted returns.** A stock's return minus the mean return of the five
  stocks that day, which removes sector-wide moves such as the April tariff
  sell-off.
- **Tests.** Spearman correlation, OLS with robust (HC3) errors, Welch t-tests,
  paired t and Wilcoxon tests, ANOVA and Kruskal-Wallis, with a Holm correction
  across all tests.
- **Machine learning.** Logistic regression, random forest, XGBoost, SVM and a
  tuned KNN predict whether tomorrow's close is above today's from features
  known at today's close. The data is split by date (first 80% of days for
  training) and every model is compared against a majority-class baseline and
  in a four-fold walk-forward evaluation.

## Running it

```bash
pip install -r requirements.txt
jupyter notebook
```

Run the notebooks from the repository root. The two analysis notebooks only
read `DATA/` and are re-executed by CI on every push. The notebooks in
`Codes/` rebuild `DATA/` from the internet; run them from inside `Codes/`, in
the order listed above. Google News results change over time, so a fresh
download will not match the committed headlines exactly.

## Revisions after submission

The notebooks were revised after the course ended; `Final Report.pdf` is the
original submission and still shows the earlier results. The changes:

- **Volatility test.** The original test compared the level of volatility with
  zero, which is always true for a standard deviation. It now compares the five
  days after each event with the five days before. The earlier "volatility
  rises significantly after AI news" finding does not hold.
- **Target leakage in the ML models.** The models predicted `Close > Open` for
  the same day while using that day's `Open` and `Close` as inputs, with a
  random train/test split. They now predict the next day from information
  available today, with a chronological split. The notebook reproduces the old
  setup to show where its 70-87% accuracy came from.
- **Invented trading days.** Market holidays were filled in by forward-filling
  the previous day, which duplicated returns. Holidays are now left out.
- **Mislabelled tests.** Tests described as 5-day cumulative abnormal returns
  used a 1-day raw return. Returns are now peer-adjusted, and the test names
  say what is measured.
- **Pipeline code.** The code in `Codes/` did not produce the committed data
  (log vs simple returns, 14-day vs 10-day volatility, simple vs Wilder RSI,
  TextBlob vs VADER sentiment, an invalid `2025-04-31` end date, and file names
  that did not match). It now reproduces `DATA/`.
- **Dependencies.** `requirements.txt` was a `pip list` dump that `pip`
  could not install; it now lists the packages the project uses.
