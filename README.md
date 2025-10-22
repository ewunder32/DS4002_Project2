# DS4002 Project 2 - Predicting Palantir stock prices based on price history and keywords in the world news
This repository contains all code, documentation, and outputs for DS4002 Project 2. We merge Palantir (PLTR) daily prices (9/30/2020–present) with GDELT GKG counts/tone of **AI- and war-related** keywords to forecast **5-day returns**. Models include ARIMAX and a Hybrid (ARIMAX + LSTM residuals), compared to a drift baseline and evaluated with a debiased long/flat backtest.

## Contents of Repository 
- **DATA**
  - `Appendix.pdf`: Contains dataset descriptions, variable dictionaries, and descriptive statistics
- **SCRIPTS**
  - `Project2.ipynb`: Colab notebook with the full dataset creation and analysis pipeline.
- **OUTPUT**
  - `Project 2 Output.pdf`: Final report including figures, tables, and summary of findings.
- **LICENSE.md**: MIT License for code and documentation in this repository.
- **README.md**: (this file) Orientation, environment requirements, and reproduction instructions.

## Section 1: Software and Platform
**Software Used**
- Python 3.10+  
- Google Colab

**Required Packages**
- `pandas`  
- `numpy`
- 'pathlib'
- 'matplotlib.pyplot'
- 'sklearn.preprocessing'
- 'sklearn'
- 'statsmodels'
- 'tensorflow'
  
**Platform Used**
- Windows 11 25H2 (local), Colab for execution

## Section 2: Map of Documentation
```
Project2
├── DATA
│   ├── Appendix.pdf            # Data dictionary and descriptive statistics
├── OUTPUT
│   └── Project 2 Output.pdf     # Final report with results
├── SCRIPTS
│   └── project2.ipynb          # Full dataset creation + analysis pipeline
├── LICENSE.md                  # MIT License for repository code
└── README.md                   # Main orientation file (this document)
```

## Section 3: Instructions for reproducing your results
Follow these steps to reproduce the analysis 

### Step 1: Prepare Data
- Download PLTR OHLCV CSV from Macrotrends
- Export GDELT GKG daily data from BigQuery

### Step 2: Merge and Clean
- Clean and merge PLTR + GDLET data
- Forward-fill weekends/holidays
- Add daily and log returns 

### Step 3: Visualizations (optional)
- Validate columns and missing data
- Generate basic plots and summaries

### Step 4: Train Hybrid Model
- Feature engineering: lags, EWMA, surprises, rolling z-scores.
- Walk-forward **H=5** (5 folds), **seed=42**.
- Train **ARIMAX + LSTM residuals**; compute metrics and DM tests.
- Save predictions/metrics to `OUTPUT/`.

### Step 5: Drift + Signal Variant
- Train on **demeaned (drift-removed)** returns; add drift back to predictions.
- Compare against Train-Mean baseline and ARIMAX.

### Step 6: Risk Metrics (Backtest) 
- Debiased **H-tranche long/flat** backtest with **5 bps** per switch.
- Report **annualized return, volatility, Sharpe, Sortino, max drawdown, Calmar**; compare to Buy-and-Hold.
