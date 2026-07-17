# pharma-sales-eda
Exploratory data analysis of 6 years of pharmacy sales data using Excel — pharma/healthcare-focused data analytics portfolio project
Pharma Sales EDA — Exploratory Data Analysis in Excel
Project Overview
This project explores six years (2014–2019) of daily pharmaceutical sales data from a single pharmacy, covering 8 drug categories classified under the ATC (Anatomical Therapeutic Chemical) classification system. As a pharmacy student building toward a data analytics career, I chose this dataset to combine domain knowledge of drug classifications with hands-on exploratory data analysis in Excel.
Dataset: Pharma Sales Data by Milan Zdravković (Kaggle)
File used: salesdaily.csv — 2,107 rows, 13 columns
Tools: Microsoft Excel (PivotTables, PivotCharts, formulas, descriptive statistics)
Drug categories covered: M01AB, M01AE (anti-inflammatories), N02BA, N02BE (analgesics/antipyretics), N05B, N05C (psycholeptics — sedatives/anti-anxiety), R03, R06 (respiratory-related)
Data Cleaning
Removed a redundant hour column (leftover artifact from aggregation — same value in every row, not meaningful for daily data)
Verified datum (date) column was properly formatted as a real date, not text
Checked for and confirmed no blank cells or duplicate rows
Noted that ATC sales columns are normalized/scaled values, not raw unit counts — standard practice in datasets built for demand forecasting
Identified that 2019 data is incomplete, ending in October rather than December
Key Findings
1. One category dominates overall sales
N02BE (other analgesics/antipyretics — pain and fever relievers) accounts for the largest share of total sales by a wide margin, roughly 5–10x higher than any other category across the full period.
2. The 2019 dip is a data artifact, not a real decline
Every single ATC category appeared to decline in 2019 on an initial year-over-year chart. Investigating further showed this wasn't a genuine drop in sales — 2019 in the dataset only runs through October, so it was being compared unfairly against six full years of data. Once this was identified, 2019 was excluded from year-over-year trend comparisons (yearly totals, correlation calculations) to avoid drawing a false conclusion. This caveat is applied consistently across the analysis below.
3. Yearly trend — N02BE (2014–2018, complete years only)
N02BE sales rose steadily from 2014, peaked in 2016, then declined from 2016 to 2017, before rising again in 2018. The cause of the 2016–2017 decline is not yet explained — flagged as an open question for further investigation (possible directions: a change in pricing, a shift in prescribing guidelines, or a genuinely milder flu season that year).
4. Yearly trend — N05B (2014–2018, complete years only)
N05B follows a different shape entirely: it declined from 2014 to 2015, then remained relatively flat and stable for the rest of the period (2015–2018). Unlike N02BE, there's no sharp rise-and-fall cycle — just an early drop followed by a steady plateau. This distinction matters: it shows N05B's behavior isn't just a smaller-scale copy of N02BE's pattern, it's a genuinely different trend shape.
5. Seasonality — N02BE monthly pattern
Looking at N02BE sales by month (all years combined), a clear cycle emerges:
Declines steadily from January through June
Stays roughly flat from June through August
Rises from August through October
Dips again in November
Rises again in December
This winter-high, mid-year-low pattern lines up with cold and flu season driving demand for pain/fever relief — colder months (Oct–Dec, Jan) show higher sales, while the summer months (Jun–Aug) are consistently lower. The November dip breaks the pattern slightly and doesn't have a clear explanation yet — noted as a minor open question rather than forced into the seasonal story.
6. Seasonality — N05B
By contrast, N05B (psycholeptics — sedatives/anti-anxiety medications) stays relatively flat year-round, with no clear seasonal swing. This makes sense pharmacologically: anxiety and sleep-related conditions are typically chronic rather than tied to weather or seasonal illness, so demand doesn't rise and fall with the seasons the way pain/fever relief does.
7. Weekend spike — specific to N02BE
N02BE sales are noticeably higher on Saturdays and Sundays compared to weekdays. No other category shows this same weekend spike — in fact, N05B and N05C are at their lowest on Sunday, the opposite direction. This selectivity strengthens a hypothesis: N02BE's weekend spike may reflect walk-in/OTC purchases for minor pain or fever relief, versus prescription refills for other conditions that follow a weekday pattern (e.g., pharmacy hours, doctor visits) — while sedative/anti-anxiety categories (N05B, N05C) may dip on Sundays if they're more tied to weekday routines like clinic visits or work-related stress.
8. Top 3 highest single-day sales — N02BE
Identifying N02BE's three highest single-day sales values confirmed the seasonal and weekend patterns rather than surfacing a surprise outlier:
December 30, 2016 (Friday)
December 31, 2016 (Saturday)
January 27, 2019 (Sunday)
All three fall in winter months and on Friday/Saturday/Sunday — directly consistent with both the winter-seasonality finding and the weekend-spike finding. This is a good sign that those two patterns are real and not just an artifact of how the data was aggregated.
9. Cross-category correlation (with an important caveat)
Correlation between drug categories, calculated on 2014–2018 monthly totals, was high across all tested pairs (0.92–0.997). Rather than indicating a specific pharmacological relationship between categories, this most likely reflects a shared overall seasonal/monthly sales pattern across the whole pharmacy — when the pharmacy is busier or quieter overall, most categories move up or down together, regardless of whether they're medically related. This is a deliberate caveat: high correlation in aggregated time-series data does not imply a direct link between categories, and I chose not to over-claim one.
10. Descriptive statistics
Calculated sum, average, median, and standard deviation for all 8 categories, confirming N02BE's dominance in both total volume and variability — consistent with its weekend and seasonal spikes (a category with genuine peaks and dips will naturally show higher standard deviation than a flat one like N05B).
Skills Demonstrated
Data cleaning and validation in Excel
PivotTables and PivotCharts for time-series and categorical analysis
Identifying and correcting for incomplete/misleading data (partial-year adjustment)
Correlation analysis and correct interpretation of its limitations
Domain-informed interpretation of trends using pharmacology background
Clear, honest reporting of findings — including open questions rather than forcing conclusions to fit a tidy narrative
Next Steps
This is Project 1 of a three-part portfolio. Project 2 will apply SQL to query and analyze a related healthcare/pharma dataset, and Project 3 will use Python for web scraping — building toward a full pipeline narrative (scrape → clean/analyze → query).
