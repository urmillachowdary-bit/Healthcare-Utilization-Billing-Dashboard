# Healthcare Analytics Dashboards

An interactive, browser-based healthcare analytics portfolio combining **two dashboards** in a single page:

1. **Healthcare Revenue Cycle & Claims** — utilization and billing patterns across 55,500 synthetic healthcare admission records.
2. **Hospital Operations & Resource Utilization Analysis** — throughput, admissions, department referrals, and waiting-time performance across 9,216 synthetic emergency room visits.

**Live dashboard (after GitHub Pages is enabled):**  
https://urmillachowdary-bit.github.io/Healthcare-Utilization-Billing-Dashboard/

![Preview of both dashboard tabs](dashboard-preview.png)

## How to open

Open `index.html` in a modern browser, or visit the GitHub Pages URL above after publishing. Use the two top tabs to switch between dashboards. The HTML includes its CSS, JavaScript, D3 library, and compressed synthetic datasets, so it does not need a server or installation.

## Dashboard 1 — Revenue Cycle & Claims

- **55,500 admission records** in the source dataset (not necessarily 55,500 unique patients)
- Average billed amount per record: approximately **$25,539**
- Average length of stay: **15.5 days**
- Abnormal test result rate: **33.6%**
- Admissions by medical condition and admission type
- Billing comparison across insurance providers
- Monthly length-of-stay/billing trend toggle
- Billing heatmap by condition and test result
- Date range and chart-click filtering

**Interpretation note:** The dataset represents synthetic hospital visits and billed amounts. It does not contain insurance claim denial decisions or actual reimbursement payments; the title "Revenue Cycle & Claims" describes the broader business context, not a validated claims-denial model. The patient-level billing calculation groups by the `Name` field and therefore should not be treated as a reliable unique-patient identifier without additional validation.

## Dashboard 2 — Hospital Operations

- **9,216 synthetic ER visits** in the source dataset
- Admission rate: **50.0%**
- Mean waiting time: **35.3 minutes**
- Visits exceeding the default 30-minute target: **59.3%**
- Service-line table by *referral department* (seven named referral departments, plus "No referral")
- Wait-time histogram, day/time heatmap, and monthly trends
- Adjustable 15–60 minute waiting-time threshold, admissions filter, period filter, and chart-click cross-filtering

**Interpretation note:** This page analyzes ER arrivals and referral destinations; it is not evidence of six staffed clinical departments. The default 30-minute target is an analytical threshold rather than proof of an organizational contractual SLA.

## Implementation

- **Frontend:** HTML5, CSS3, JavaScript, inline D3.js v7.9.2 (SVG charts)
- **Data:** compressed public synthetic dataset extracts embedded directly into `index.html`
- **Deployment:** GitHub Pages — static site, no backend
- **Interaction:** responsive tabs, dynamic KPI calculations, filters, trend switches, tooltips, and heatmaps

The project is a **web recreation**. It does **not** include a native `.pbix` Power BI or Tableau workbook, nor executable SQL ETL pipelines. Example SQL/DAX formulas displayed as documentation in the dashboard are not proof that the web page was built with those tools.

## Reproducibility and data sources

- Healthcare admissions and billing: [Kaggle Healthcare Dataset (prasad22)](https://www.kaggle.com/datasets/prasad22/healthcare-dataset).
- Hospital ER source and reference: [Harsh Raj's Hospital ER dashboard repository](https://github.com/rjharshpatel/hospital-er-dashboard).

Both dashboards are reproductions of published examples. The billing/utilization visualization was inspired by [Ananyaa Shahi's Healthcare Utilization & Billing Dashboard](https://github.com/AnanyaaShahi/Healthcare-Utilization-Billing-Dashboard). Please check upstream dataset and code licensing terms before redistributing their underlying material. Do not interpret synthetic patient or encounter records as real clinical data.

## Deploy on GitHub Pages

1. Put `index.html`, `README.md` and `dashboard-preview.png` at the **root** of the repository.
2. In GitHub, open **Settings → Pages**.
3. Choose **Deploy from a branch**, `main`, `/(root)`, then save.
4. When deployment finishes, open the live dashboard URL above.

To update an existing deployment, commit a new `index.html` in the same root folder. Your repository URL and Pages URL remain the same.
