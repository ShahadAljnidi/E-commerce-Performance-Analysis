# TechSphere E-Commerce Performance Analysis (2019-2022)

An end-to-end Power BI analysis of TechSphere, a US-based consumer electronics retailer founded in 2018, covering sales, products, regions, refunds, the loyalty program, and customer retention. The report was built for the Head of Operations to help cross-functional teams streamline processes and improve commercial performance.

## Business Context

TechSphere sells popular consumer electronics and accessories to a global customer base. It has grown quickly, but faces rising competition and the shifts in demand brought on by COVID-19. The dataset covers roughly **88K customers**, **108K orders**, and **$28.1M in revenue** between 2019 and 2022.

## Business Questions

1. How did revenue and order volume evolve over time, and by region?
2. Which products and regions drive the most revenue?
3. Where do refunds concentrate, and how do they differ between loyalty and non-loyalty customers?
4. Is the loyalty program delivering value?
5. How well does TechSphere retain customers, and which channels retain best?

## Dataset

One row per order line, with these fields:

`USER_ID`, `ORDER_ID`, `PURCHASE_TS`, `PURCHASE_TS_(Cleaned)`, `PURCHASE_MONTH`, `PURCHASE_YEAR`, `PURCHASE_MONTH-ONLY-NUM`, `Quarter`, `Season`, `Week_start_`, `Month_end`, `Days_to_deliver_`, `SHIP_TS`, `DELIVERY_TS`, `REFUND_TS`, `REFUND_TS_Cleaned_`, `Refunded_`, `PRODUCT_NAME`, `PRODUCT_NAME_(Cleaned)`, `PRODUCT_ID`, `USD_PRICE`, `LOCAL_PRICE`, `CURRENCY`, `PURCHASE_PLATFORM`, `MARKETING_CHANNEL`, `ACCOUNT_CREATION_METHOD`, `COUNTRY_CODE`, `Country_Name`, `REGION`, `LOYALTY_PROGRAM`, `CREATED_ON`

All other metrics in the report (revenue, AOV, repeat buyer %, cohort retention, drop-off rates, days to second purchase, refund amounts) are calculations I built on top of these fields.

## Data Preparation

- Cleaned raw timestamps into `PURCHASE_TS_(Cleaned)` and `REFUND_TS_Cleaned_`
- Standardized product names into `PRODUCT_NAME_(Cleaned)`
- Added a `Refunded_` flag (0/1) from refund timestamps
- Derived time fields: quarter, season, week start, month end, and delivery time
- Mapped country codes to country names and regions

## Dashboard Pages

Every page shares slicers for Region, Purchase Year, Loyalty Program, Marketing Channel, Purchase Platform, and Country.

| Page | Focus |
|---|---|
| 1. Executive Overview | Headline KPIs, quarterly revenue, share of orders by region |
| 2. Regional Performance | Users by region split by refund status, monthly sales by region |
| 3. Orders and Loyalty | Revenue vs. order count over time, sales by loyalty status |
| 4. Product Performance | Product sales over time, by year, and by region |
| 5. Refunds | Revenue vs. refunds per product, refund amounts, refunds by loyalty status |
| 6. Retention and Cohorts | Repeat vs. one-time buyers, cohort table, AOV, revenue per user |
| 7. Retention Drivers | Retention by channel and quarter, drop-off rates, days to second purchase |
| 8. Platform and Loyalty | Revenue by platform and loyalty status, retention by loyalty status |

Screenshots are in the [`images/`](images) folder.

![Executive Overview](images/01_overview.png)

## Key Metrics

| Metric | Value |
|---|---|
| Total revenue | $28.11M |
| Total orders | 108K |
| Customers in cohorts | 87,628 |
| Average order value | $260.00 |
| Revenue per user | $320.82 |
| Repeat buyers | 19.84% |
| One-time buyers | 80.16% |
| Top region | North America |
| Top product | 27 Inch 4K Gaming Monitor |

## Key Findings

**Revenue and growth**
- Revenue peaked in 2020 (about $10.5M) during the pandemic demand surge, then declined to roughly $8.7M in 2021 and $4.5M in 2022. Q4 2022 is the lowest quarter and may reflect incomplete data.
- North America generates 51.6% of orders, followed by EMEA (29.4%), APAC (12.1%), and LATAM (6.7%). All regions follow the same seasonal and yearly pattern.

**Products**
- Four products drive nearly all revenue: the 27 Inch 4K Gaming Monitor, Apple AirPods, Macbook Air, and Thinkpad Laptop. Accessories and the iPhone contribute very little.
- Product mix is consistent across regions, with the monitor leading in NA, EMEA, and APAC.

**Refunds**
- Refunds are highest in dollar terms for the Macbook Air (about $750K) and the 4K Gaming Monitor (about $645K), followed by AirPods and Thinkpad.
- By refund count, AirPods lead, and loyalty members account for roughly twice as many AirPods refunds as non-loyalty customers.

**Loyalty program**
- Non-loyalty customers generated more revenue until early 2021. Loyalty members then overtook them through 2021 and into mid 2022, so the program is growing in importance as the base shrinks.
- The website drives almost all revenue, with the mobile app contributing a small share.

**Retention**
- Only 19.84% of customers buy more than once, and cohort retention is low: 1.07% at month 1, 0.42% at month 3, 0.19% at month 6, and 0.18% at month 12.
- Affiliate and direct channels retain best. Social media and email retain weakest.
- Average days to a second purchase fall each year, from about 330 days in 2019 to about 68 in 2022. Later cohorts have had less time to return, so this trend should be read with caution.

## Recommendations

1. Reduce refunds on the high-value products (Macbook Air, 4K Monitor, AirPods) by reviewing product descriptions, quality control, and delivery experience.
2. Shift acquisition spend toward affiliate and direct channels, which produce better retention.
3. Build a post-purchase program aimed at the second order, since 80% of customers never buy again.
4. Review loyalty benefits, especially on products with high loyalty refund counts such as AirPods.
5. Grow the mobile app, which is currently underused compared with the website.

## Limitations

- The final months of 2022 look incomplete, which affects yearly comparisons and retention windows.
- Some records have an unknown region (`UNK`) or a blank marketing channel.
- Retention and days-to-second-purchase figures are affected by how much follow-up time each cohort has had.

## Repository Structure

```
.
├── README.md
├── data
├── dashboard 
└── images/              
         
```
