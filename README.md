# Insider Trading Impact Study on US Politicians

This project investigates whether US politicians earn abnormal returns around their equity transactions — a signal of potential insider trading. The analysis is conducted via an **event study methodology** and regression-based testing using the **Fama-French 3-Factor Model**.

---

## Dataset Source
All transaction data is sourced from **[OpenSecrets](https://www.opensecrets.org/bulk-data/signup)** — a non-profit, nonpartisan research group that tracks money in U.S. politics. Simply sign up to access their data dump including:
- Stock trades
- Transaction dates
- Politician identity, party, and state
- Sector & industry classification

---

## Methodology
1. **Event Identification:** Each transaction date is treated as an event.
2. **Estimation Window:** 250 trading days before the event used to estimate CAPM/Fama-French parameters.
3. **Event Window:** We calculate abnormal returns over three windows:
   - **CAR5** = Cumulative Abnormal Return from Day -5 to +5
   - **CAR10** = Day -10 to +10
   - **CAR120** = Day -120 to +120
4. **Abnormal Returns (AR):** Calculated using the Market Model (CAPM) and Fama-French model.
5. **CAAR (Cumulative Average Abnormal Return):** Average of CARs across all trades.
6. **Statistical Testing:** We run t-tests and regressions to test significance and explanatory power.

---

## Key Results Summary

| **Metric**                        | **CAR5**        | **CAR10**       | **CAR120**      |
| --------------------------------- | --------------- | --------------- | --------------- |
| **Mean CAR**                      | -1.37%          | -1.30%          | -6.45%          |
| **T-Statistic**                   | -27.12          | -21.68          | -38.19          |
| **P-Value**                       | 7.52e-161       | 8.23e-104       | < 0.0001        |
| **Statistical Significance?**     | Yes             | Yes             | Yes             |
| **R²: Sector → CAR**              | 0.0024 (0.24%)  | 0.0022 (0.22%)  | 0.0020 (0.20%)  |
| **R²: Party → CAR**               | 0.0022 (0.22%)  | 0.0021 (0.21%)  | 0.0018 (0.18%)  |
| **R²: Fama-French Model**         | \~0.00          | \~0.00          | \~0.00          |
| **Model P-Value (FF Regression)** | 0.112           | 0.349           | 0.584           |
| **Conclusion (Fama-French)**      | Not explanatory | Not explanatory | Not explanatory |

---

## Interpretation
- **Consistent Negative Abnormal Returns:** CAARs across all windows are negative.
- **Statistically Significant:** Strong rejection of null hypothesis (CAAR = 0).
- **Poor Explanatory Power from Fama-French Model:** Traditional financial factors don’t explain these returns.
- **Weak Influence of Sector or Party:** Sector and party affiliation have negligible R² values.

---

## Visuals Included
- AAR & CAAR time series plots
- <img width="989" height="490" alt="AAR Over Time" src="https://github.com/user-attachments/assets/d437101f-c07e-40ff-beb9-6c45450f0194" />
- <img width="989" height="490" alt="CAAR Over TIme" src="https://github.com/user-attachments/assets/a4721159-f0f6-429e-b8bf-39ae41dd66e3" />

- CAAR by sector (boxplots)
- <img width="1385" height="590" alt="Untitled-1" src="https://github.com/user-attachments/assets/a5bcb432-faee-49f1-bcd4-294cd1146094" />

- Fama-French predicted vs actual CAAR scatterplots
- <img width="1787" height="490" alt="Untitled-1" src="https://github.com/user-attachments/assets/25182afd-ca0e-4347-bf10-048fdf71a163" />

- CAAR evolution over time
<img width="989" height="490" alt="Untitled" src="https://github.com/user-attachments/assets/83ac8a9c-6b68-45d8-badc-8a1b19a8b6b7" />

- CAAR Distribution
- <img width="1389" height="590" alt="Untitled-1" src="https://github.com/user-attachments/assets/849384ad-82e5-450d-8ad7-d2432446fff0" />

---

## Tech Stack
- Python: pandas, NumPy, matplotlib, seaborn
- Statsmodels & Scikit-learn
- Jupyter Notebook

---

## File Structure
```
├── data/
│   └── (OpenSecrets CSV files)
├── src/
│   └── event_study_analysis.ipynb
├── outputs/
│   ├── plots/
│   └── Event_Study_CARs.csv
└── README.md
```

---

## How to Reproduce
1. Sign up at [OpenSecrets Bulk Data Access](https://www.opensecrets.org/bulk-data/signup)
2. Download the data dump and place CSVs in `data/`
3. Run the notebook in `src/event_study_analysis.ipynb`

---

## License & Acknowledgements
- This project is for academic and illustrative purposes only.
- All data is publicly available via OpenSecrets.org.
- Inspired by work from academic literature and news investigations into political finance ethics.
