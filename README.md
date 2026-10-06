# Quick-Commerce Delivery SLA Diagnostic

Diagnosing why sub-10-minute delivery compliance drops in Mumbai and Bengaluru, by hour, dark-store cluster and product category.

## Business question
A quick-commerce operations head sees 10-minute delivery compliance falling in two metro cities. Where is it failing, what are the top three patterns behind the misses, and what should the regional ops team change first?

This is a case built on [public / simulated] data to practice an operations diagnosis. It is not company data.

## Metric definitions
- **SLA met:** an order delivered in 10 minutes or less from order placement.
- **Compliance rate:** orders with SLA met / total orders.
- **Peak hours:** [define after exploring, e.g. 12:00-14:00 and 18:00-22:00].
- **Store cluster:** [define, e.g. dark stores grouped by area or order volume].

## Data
- Source: [Kaggle dataset link] or "simulated in `notebooks/00_simulate_data.ipynb`, assumptions in `docs/assumptions.md`"
- Size and period: [rows, date range]
- Key columns: order time, delivery time, city, store ID, category, [others]
- Limitations: [e.g. no rider-level data, no weather, no real traffic]

## Approach
1. Clean the data, define the SLA flag and time features (hour, day of week, peak or off-peak).
2. Compare compliance by hour, cluster, category and city.
3. Check interactions, such as peak hours at high-volume stores.
4. Fit a simple decision tree or gradient boosting model on "SLA missed" as a supporting check on which factors matter most.
5. Quantify how much compliance would improve if each bottleneck were fixed.
6. Build a three-page Power BI dashboard: overview, drill-down, bottleneck summary.

## Key findings
Overall compliance: [x%] in Mumbai, [y%] in Bengaluru.

1. **Bottleneck 1:** [pattern, share of total misses]
2. **Bottleneck 2:** [pattern, share of total misses]
3. **Bottleneck 3:** [pattern, share of total misses]

## Recommendations
| Bottleneck | Action | Estimated compliance gain |
|---|---|---|
| 1 | [e.g. position riders before peak] | [+x points] |
| 2 | [action] | [+x points] |
| 3 | [action] | [+x points] |

## Limitations
- [Data is public or simulated, so findings show method, not real company performance.]
- [Correlation in this data does not prove cause.]
- [What you would check next with real operational data.]

## Dashboard
![Overview](outputs/dashboard_overview.png)
![Drill-down](outputs/dashboard_drilldown.png)

Power BI file: `outputs/sla_dashboard.pbix`

## How to run
1. `pip install -r requirements.txt`
2. Run the notebooks in `notebooks/` in order.

## Repository structure
- `data/` small sample files or links to the source
- `notebooks/` cleaning, analysis, model
- `outputs/` charts, dashboard screenshots, .pbix
- `docs/` assumptions and data dictionary
