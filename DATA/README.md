## How to obtain raw data

1) **PLTR prices (Macrotrends)**
   - Download daily OHLCV CSV for ticker **PLTR** from Macrotrends.
   - Save as `MacroTrends_Data_Download_PLTR.csv`.

2) **GDELT GKG daily counts/tone**
   - Use BigQuery (GDELT **2.0** GKG) to export daily counts of AI–theme rows (`cnt_ai`),
     war–theme rows (`cnt_war`), and daily average V2Tone (`avg_tone`).
   - Export to CSV `gdelt_gkg_daily_ai_war_tone.csv`. See **Appendix.pdf** for the query and field definitions.

## Reproducibility

- Run **SCRIPTS/Project2.ipynb** section **01_merge_pltr_gkg** to produce the final merged file.
- Expected output: `pltr_with_gkg_daily-2.csv` with **~1,259** rows  
  (**2020-09-30 → 2025-10-03**), columns listed in the Appendix Data Dictionary.

## Licensing

- Software is MIT-licensed (see repository `LICENSE.md`).
- Data sources: Macrotrends (site terms) and GDELT (open with attribution).  
  We provide instructions and/or derived data; re-download raw data as needed.

## Metadata

For **Data Summary**, **Provenance**, **Ethical Statements**, **Data Dictionary**, and **Exploratory Plots**, see **DATA/Appendix.pdf** (kept up-to-date with the final dataset).
