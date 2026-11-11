# Singapore birth rate: what moves it?

five factors against the total fertility rate (TFR), SingStat Table Builder, 2010–2025.

## What is in this folder

| File / folder | What |
|---|---|
| `Fertility_Dashboard.py` | The whole Streamlit dashboard in one file. Run: `streamlit run Fertility_Dashboard.py` |
| `Fertility_Combined_Data.csv` | Everyone's data in one table: one row per year 2000–2025, 111 columns |
| `Fertility_Group_Analysis.ipynb` | All five parts in one notebook (Healthcare, Housing, Marriage, Income, Education) |
| `members/<n>_<factor>_<name>/` | Each member's own notebook and own CSV |
| `charts/` | Every chart: one folder per member (from their notebook) + `0_Dashboard/` (screenshots of each page) |
| `sections/` | Helper code and figures the combined notebook uses (Education), output folders for Healthcare / Housing |


## Run

```bash
pip install -r requirements.txt
streamlit run Fertility_Dashboard.py          # dashboard
jupyter lab                                   # notebooks: Restart Kernel and Run All
```

## Methods used everywhere

- Real income = nominal income (17872) ÷ CPI All Items (M213751, annual mean, expressed as 2010 = 100) × 100.
  This reproduces SingStat's published real change (17885) exactly in every year 2011–2024.
- Pearson r with two-sided p-value, n = years used. Levels: r of x[t] and TFR[t+L].
  Yearly change: r of x[t] − x[t−1] and TFR[t+L] − TFR[t+L−1]. Lag L = 0–3 years.
- Later-marriage shift index (Marriage) = female marriage rate 30–34 ÷ rate 25–29.
