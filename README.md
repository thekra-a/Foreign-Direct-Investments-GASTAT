# Foreign Direct Investments: 

A Power BI report and interactive dashboard summarising foreign direct investment (FDI) in Saudi Arabia from 2015 to 2024 and categorized by economic activity and by source country.


## Data source

[Annual FDI data published by the General Authority for Statistics (GASTAT) as CSV files](https://www.stats.gov.sa/en/statistics-tabs?tab=436312&category=123583)

* Tables used are as follows:
Table 1.1 FDI stock by main economic activity 
Table 1.3 FDI inflow by main economic activity 
Table 1.4 FDI outflow by main economic activity
Table 2.1 FDI stock by source country | 2015–2024 
Table 2.2 Net FDI inflow by source country 

* A full data dictionary is available in the `data` folder of this repository.

## Methodology 
* Data Selection: of +10 tables, the 6 tables above were selected to provide the best comprehensive, high-level reporting that sumarizes the status of FDI over time across different econimic activities. 
* Report Concept: the report was designed to encompass 3 main pages: a Dashboard to provide overall statistics, Activity page to showcase the investments across 15 industries referred to as Economic Activities, and a Country page to summarize investments by country.
* A Star schema was used to build the report. See **Data Model** for further details.
* Key data transformations in Power Query while building the report: 
* a. <Unpivot Tables>
* b. <Standard> function was used to convert figures from SAR mn in the original report to SAR Bn so the numbers can easily be reported and compared. For example, Manufacturing stock in 2024 is 277,154 SAR million in the workbook but was converted to 277.2 SAR billion in the report.



## Data model
A star schema was used to build the report, with the below Fact and Dimentsions tables:
- **Fact tables** (one row per activity or country per year): `FDI Stock by Activity`, `FDI Inflow by Activity`, `FDI Outflow by Activity`, `FDI Stock by Country`, `FDI Net Inflow by Country`.
- **Dimensions tables** Because I needed to filter all fact tables with the same variables: `Year` , `country`, `activity`, I created those tables separately and linked them to be *Dimensions*.
- **Relationships:** each fact table links to `Year`, and to `Activity` or `Country`, so one year selection filters every visual.
- **Measures** return SAR billion for the selected year.


## Results



## Notes
* When no year is selected, every figure shows the **latest year (2024)**.
* Growth % compares each year with the year before.