# Ad Traffic IVT (Invalid Traffic) Analysis

## Overview
This project analyzes ad request data from multiple mobile applications to identify behavioral patterns that distinguish **valid** from **invalid (IVT)** traffic.  
The analysis combines **Python (for data preprocessing, correlation, and statistics)** and **Power BI (for interactive visualization and reporting)** to uncover insights about fraudulent ad behavior.

---

## Objective
To determine **why certain apps are flagged for Invalid Traffic (IVT)** by analyzing:
- Traffic composition across valid and invalid apps.
- Ratios such as `idfa_ua_ratio` and `idfa_ip_ratio`.
- Behavioral indicators of spoofing or automation over time.

---

## Dataset Description
The dataset contains six sheets:
- **Valid1, Valid2, Valid3** → Apps without IVT flags.
- **Invalid1, Invalid2, Invalid3** → Apps marked with IVT at different times.

Each sheet includes:
| Column | Description |
|--------|--------------|
| Date | Time period of record (daily/hourly) |
| unique_idfas | Number of unique device identifiers |
| unique_ips | Unique IP addresses from requests |
| unique_uas | Unique User-Agent strings |
| total_requests | Total ad requests received |
| requests_per_idfa | Avg. requests per device |
| impressions | Total ads shown |
| idfa_ip_ratio | Ratio of devices per IP |
| idfa_ua_ratio | Ratio of devices per User-Agent |
| IVT | Invalid Traffic metric |

---

## ⚙️ Tools & Technologies
- **Python:** Pandas, NumPy, Matplotlib, Seaborn  
- **Power BI:** Interactive dashboard for visual trends and KPIs  
- **Git & GitHub:** Version control and documentation  

---

## Analysis Summary

### Key Observations
- **Valid apps** show stable `idfa_ua_ratio` and balanced correlations among metrics → indicates genuine device diversity.
- **Invalid apps** have inflated `unique_uas` and lower `idfa_ua_ratio` → suggests User-Agent spoofing or automated bot activity.
- **IVT scores** are higher and more volatile in invalid apps, confirming behavioral irregularities rather than volume-based fraud.

### Statistical Highlights
| Metric | Valid Apps (Mean) | Invalid Apps (Mean) | Insight |
|--------|------------------|--------------------|---------|
| `unique_idfas` | 189K | 152K | Similar device counts across both types |
| `unique_uas` | 298 | 506 | Invalid apps inflate UA counts |
| `idfa_ua_ratio` | 3975 | 495 | Lower ratio = higher UA rotation (spoofing) |
| `IVT` | 0.37 | 0.72 | Invalid apps show consistently higher IVT |

---

## Conclusion
- **IVT detection is pattern-driven, not volume-driven.**
- Fraudulent apps manipulate User-Agent diversity and device behavior rather than increasing total requests.
- Behavioral metrics (`idfa_ua_ratio`, `unique_uas`, `IVT`) are strong fraud indicators.
- Machine learning or anomaly detection based on **temporal and ratio-based features** can outperform static thresholds.

---

## Future Scope
- Develop a **predictive ML model** to classify IVT automatically.
- Incorporate **time-series anomaly detection** for real-time monitoring.
- Expand dashboard KPIs for continuous fraud tracking.

---

## 🧑‍💻 Author
**Kerissa Patel**  
