# Saudi Arabia – Foreign Direct Investment Dashboard

A Power BI report and summarising foreign direct investment (FDI) in Saudi Arabia from 2015 to 2024, by economic activity and by source country.


## Data source

Ministry of Investment, *Annual Foreign Direct Investment 2024* (Arabic/English Excel workbook). Five sheets are used:

| Sheet | Content | Years |
|---|---|---|
| 1.1 | FDI stock by main economic activity | 2015–2024 |
| 1.3 | FDI inflow by main economic activity | 2016–2024 |
| 1.4 | FDI outflow by main economic activity | 2016–2024 |
| 2.1 | FDI stock by source country | 2015–2024 |
| 2.2 | Net FDI inflow by source country | 2016–2024 |

Figures are calculated by the Ministry using the assets/liabilities methodology.

## Units

- The source workbook is in **SAR million**, and the tables in the model keep that unit (column `Value (SAR mn)`).
- The report shows **SAR billion** (SAR million ÷ 1,000) so the numbers stay readable. For example, Manufacturing stock in 2024 is 277,154 SAR million in the workbook and 277.2 SAR billion in the report.

## Report pages

1. **Dashboard:** headline cards for the latest year (FDI stock, growth versus the previous year, inflow and outflow), the stock trend since 2015, inflow and outflow since 2016, and the top 10 activities and source countries by stock.
2. **By Activity:** FDI stock by activity, plus a table of stock, growth, inflow and outflow for every activity. Includes a year selector.
3. **By Country:** FDI stock by source country, plus a table of stock, growth and net inflow for all 165 countries. Includes a year selector.

When no year is selected, every figure shows the **latest year (2024)**.

## Key figures for 2024

| Measure | SAR billion |
|---|---|
| FDI stock (year end) | 977.4 (+8.9% on 2023) |
| FDI inflow | 119.2 |
| FDI outflow | 39.2 |
| Net FDI inflow (by country, sheet 2.2) | 80.0 |

The largest activity by stock is Manufacturing (277.2), and the largest source country is the United Arab Emirates (161.3).

## Data model

- **Fact tables** (one row per activity or country per year): `FDI Stock by Activity`, `FDI Inflow by Activity`, `FDI Outflow by Activity`, `FDI Stock by Country`, `FDI Net Inflow by Country`.
- **Lookup tables:** `Activity` (19 activities with section codes A–S and Arabic names), `Country` (165 countries with Arabic names) and `Year`.
- **Relationships:** each fact table links to `Year`, and to `Activity` or `Country`, so one year selection filters every visual.
- **Measures** return SAR billion for the selected year, or the latest year when none is selected. Growth % compares each year with the year before.

## Notes

- **Stock and flows are different things.** Stock is the accumulated position at year end, while inflow and outflow are the movements during the year. Stock values are never added up across years.
- **Inflow by activity and net inflow by country are not the same figure.** Sheet 2.2 reports net inflows, so its totals (80.0 bn in 2024) differ from the inflow by activity totals in sheet 1.3 (119.2 bn).
- Negative values are real: they mean disinvestment, or repayments larger than new investment, in that year.
- "Not classified" is the Ministry's "(N/A)" country row: investment it could not attribute to a country.

## Updating the data

1. Download the new edition of the Ministry workbook.
2. In Power BI Desktop, go to **Transform data → Manage parameters → SourceFile** and paste the workbook's full path.
3. Click **Refresh**.

New years are picked up only if the Ministry keeps the same sheet layout. If a new year column is added, the year steps in each query must be extended.

The published report holds a snapshot of the data. Because the source is a local Excel file, the online copy does not refresh by itself. To update it, refresh in Desktop and publish again.
