# 💳 Credit Card Transaction Dashboard

A Power BI dashboard for analyzing credit card transaction performance, revenue drivers, and cardholder demographics — built to help a card-issuing business understand *where* revenue and interest income come from and *who* their most valuable customers are.

---

## 📝 Short Description & Purpose

This report turns raw credit card transaction and customer records into an interactive, two-page analytical dashboard. It answers questions like:

- How is revenue trending over time, and is transaction growth keeping pace with revenue growth?
- Which card products, spend categories, and channels (chip vs. non-chip) generate the most revenue?
- Which customer segments — by age, gender, education, marital status, job, income, or location — are most profitable?
- How satisfied are customers, and does satisfaction correlate with revenue or product tier?

The goal is to give business, marketing, and risk stakeholders a single, filterable source of truth for credit card portfolio performance, rather than relying on static spreadsheet reports.

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Data modeling & transformation | Power Query (M) within Power BI Desktop |
| Data model | Power BI (Import mode), star-schema relationship between fact and dimension tables |
| Visualization | Power BI Desktop (report canvas, DAX measures, custom theme) |
| File format | `.pbix` (Power BI Desktop file) |

---

## 🗄️ Data Source

The model is built on two related tables:

### `cc_detail` — Transaction (fact) table
| Field | Description |
|---|---|
| `Qtr` | Calendar quarter of the transaction |
| `Week_Start_Date` | Week-level date (expanded into a Year → Month → Day hierarchy) |
| `Revenue` | Revenue generated from the transaction |
| `Total_Trans_Amt` | Total transaction amount (spend) |
| `Total_Trans_Vol` | Total transaction volume (count) |
| `Interest_Earned` | Interest income earned |
| `Card_Category` | Card product tier (e.g. Blue, Silver, Gold, Platinum) |
| `Exp_Type` | Expenditure/spend category |
| `Use_Chip` | Chip vs. swipe/online usage flag |

### `cust_detail` — Customer (dimension) table
| Field | Description |
|---|---|
| `Gender` | Customer gender |
| `AgeGroup` | Customer age band |
| `Marital_Status` | Customer marital status |
| `Education_Level` | Customer education level |
| `Customer_Job` | Customer occupation |
| `Income` | Customer income |
| `IncomeGroup` | Binned income segment |
| `state_cd` | Customer state/location code |
| `Cust_Satisfaction_Score` | Customer satisfaction score (CSS) |

`cc_detail` and `cust_detail` are related on a shared customer key, so every transaction-level metric (Revenue, Interest Earned, etc.) can be sliced by any customer attribute.

> Update this section with your actual source system (e.g. data warehouse table, CSV export, API) and refresh cadence.

---

## ✨ Features / Highlights

### Business Problems
Card issuers generate large volumes of transaction and customer data, but it's often scattered across systems and hard to translate into decisions. Without a consolidated view, it's difficult to answer basic but critical questions: which products are actually profitable, which customer segments to target, and whether channel shifts (like chip adoption) are affecting revenue.

### Goal
Provide a single interactive dashboard that:
- Consolidates transaction and customer data into one model
- Surfaces revenue, spend, and interest trends at a glance
- Lets stakeholders slice performance by product, channel, and customer demographic without writing a query
- Highlights customer satisfaction alongside financial performance

### Walkthrough of Key Visuals

**Page 1 — CC Transaction** (product & channel performance)
- **KPI cards:** Total Revenue, Total Amount, Total Interest, Total Transactions
- **Revenue and Total Transactions by QTR** — combo chart showing whether transaction volume and revenue are moving together over time
- **Revenue by Expenditure Type / Education Type / Job Type / Card Category / Chip Usage** — bar charts ranking revenue across five different cuts of the business
- **Card Category summary table** — Revenue, Total Transaction Amount, and Interest Earned side-by-side by product tier
- **Slicers:** Week Start Date, Gender, Quarter, Card Category, Income Group

**Page 2 — CC Customer** (customer & demographic performance)
- **KPI cards:** Revenue, Income, # Interest, CSS (Customer Satisfaction Score)
- **Customer Job summary table** — Revenue, Income, and Interest Earned by occupation
- **Revenue by Week** — weekly revenue trend split by gender
- **Revenue by Age Group / Education Level / Top 5 States / Marital Status** — bar charts, each split by gender, to find the most valuable demographic segments
- **Slicers:** Quarter, Gender, Card Category, Week Start Date, Chip Usage

### Business Impact & Insights
- **Product strategy:** The Card Category views make it easy to see which product tiers punch above their weight on revenue and interest, informing upsell and product-mix decisions.
- **Channel/risk visibility:** The Chip Usage breakdown flags how much revenue still comes from non-chip transactions — relevant to fraud exposure and EMV migration planning.
- **Targeted marketing:** Cross-cutting revenue by age, education, job, marital status, income group, and state helps marketing and CRM teams prioritize the segments most worth targeting or retaining.
- **Customer experience linkage:** Placing the Customer Satisfaction Score (CSS) alongside revenue and income KPIs lets teams check whether high-revenue segments are also the most satisfied — or a retention risk.
- **Self-service exploration:** Because every visual responds to the shared slicers, stakeholders can answer their own follow-up questions (e.g. "What does Q3 look like for Platinum cardholders only?") without needing a new report built for them.

---

## 📸 Screenshots

> Add screenshots of each report page here so viewers can preview the dashboard without opening the `.pbix` file.

```
docs/screenshots/cc-transaction-page.png
docs/screenshots/cc-customer-page.png
```

```markdown
![CC Transaction page](docs/screenshots/cc-transaction-page.png)
![CC Customer page](docs/screenshots/cc-customer-page.png)
```

To capture them: open `Credit_Card_Transaction_Dashboard.pbix` in Power BI Desktop, go to each page, and use **File → Export → Export to image** (or a screen capture), then drop the images into a `docs/screenshots/` folder in this repo and update the paths above.

---

## 🚀 Getting Started

1. Clone this repository.
2. Open `Credit_Card_Transaction_Dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
3. Update/refresh the data source connection(s) if prompted.
4. Use the slicers at the top of each page to filter the report.
5. Switch between the **CC Transaction** and **CC Customer** pages using the tabs at the bottom.

## 📁 Repository Contents

| File | Description |
|---|---|
| `Credit_Card_Transaction_Dashboard.pbix` | The Power BI report file |
| `README.md` | This file |
| `docs/Dashboard_Documentation.docx` | Detailed component-by-component documentation |

## 📄 License

Add your license of choice here (e.g. MIT).
