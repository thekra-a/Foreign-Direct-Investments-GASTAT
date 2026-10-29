## Foreign Direct Investments in Saudi Arabia (2015-2024)

### Data source

[Foreign Direct Investments, 2024, General Authority for Statistics (GASTAT)](https://www.stats.gov.sa/en/statistics-tabs?tab=436312&category=123583)

#### **Tables used are as follows:**

**Table 1.1** FDI stock by main economic activity
**Table 1.3** FDI inflow by main economic activity 
**Table 1.4** FDI outflow by main economic activity
**Table 2.1** FDI stock by source country | 2015–2024 
**Table 2.2** Net FDI inflow by source country 

*A full data dictionary is available in the `data` folder of this repository.*

### Methodology 
* Data Selection: of +10 tables, the 6 tables above were selected to provide the best comprehensive, high-level reporting that sumarizes the status of FDI over time across different econimic activities. 
* Report Concept: the report was designed to encompass 3 main pages: a Dashboard to provide overall statistics, Activity page to showcase the investments across 15 industries referred to as Economic Activities, and a Country page to summarize investments by country.
* A **Star schema** was used to build the report. See **Data Model** for further details.
> Key data transformations in Power Query while building the report: 
* a. `Unpivot Tables` function
* b. `Standard` function was used to convert figures from SAR mn in the original report to SAR Bn so the numbers can easily be reported and compared. For example, Manufacturing stock in 2024 is 277,154 SAR million in the workbook but was converted to 277.2 SAR billion in the report.


### Data model
A star schema was used to build the report, with the below Fact and Dimentsions tables:
- **Fact tables** (one row per activity or country per year): `FDI Stock by Activity`, `FDI Inflow by Activity`, `FDI Outflow by Activity`, `FDI Stock by Country`, `FDI Net Inflow by Country`.
- **Dimensions tables** Because I needed to filter all fact tables with the same variables: `Year` , `country`, `activity`, I created those tables separately and linked them to be *Dimensions*.
- **Relationships:** each fact table links to `Year`, and to `Activity` or `Country`, so one year selection filters every visual.
- **Measures** return SAR billion for the selected year.


### Results

<img width="603" height="369" alt="{1C9A91D6-1AC0-4037-9B24-3CD8F82B3456}" src="https://github.com/user-attachments/assets/0b71cff0-7f8a-4161-acfb-155bf56a930d" /> <img width="603" height="369" alt="{512F7975-FC6C-4FF2-8FBA-075EFE7C3C9F}" src="https://github.com/user-attachments/assets/8a515e28-ce68-4fc9-b906-7c9debdd0167" /> <img width="601" height="368" alt="{3DABB152-F0A9-4D5D-B836-534079A31BC2}" src="https://github.com/user-attachments/assets/949a241b-f131-4949-9241-70ac0e4c7399" />






### Notes
* When no year is selected, every figure shows the **latest year (2024)**.
* Growth % compares each year with the year before.
