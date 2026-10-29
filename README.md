# Brick Manufacturing Analysis

An independent portfolio project by **Caio Bergamo**, using Power BI to compare production performance and recorded downtime before and after Lean Six Sigma (LSS) implementation.

## Business objective

Compare production performance and recorded stop events, identify where time is being lost, and recommend priorities for further investigation.

## Main findings

Reported OEE and availability were higher after LSS, while quality declined and output per observed production day remained similar. Unplanned stops also accounted for a larger share of planned production time.

| Metric | Before LSS | After LSS |
| --- | ---: | ---: |
| Observed production dates | 62 | 43 |
| Total output units | 1,955,731 | 1,342,331 |
| Output per observed production day | 31,544.05 | 31,217.00 |
| Time-weighted reported OEE | 54.36% | 63.99% |
| Availability rate | 59.17% | 69.66% |
| Performance rate | 93.20% | 93.74% |
| Quality rate | 98.50% | 96.82% |
| Unplanned share of planned production time | 18.69% | 21.31% |

My recommendation is to investigate the quality decline, manual brick handling and equipment failures, and monitor unplanned losses against comparable production time. The periods differ in length, and the before-and-after comparison does not establish that LSS caused the changes.

## Explore the project

| File | Contents |
| --- | --- |
| [Analysis report](REPORT.md) | Findings, recommendations, methodology, and limitations |
| [Power BI file](powerbi/Brick_Manufacturing_Analysis.pbix) | Current four-page interactive report |
| [Word report](reports/Brick_Manufacturing_Report.docx) | Current written project analysis |
| [Dashboard PDF](reports/Brick_Manufacturing_Dashboard.pdf) | Dashboard export with corrected metric labels and validation notes |
| [Original source files](data/) | Four CSV files and the publisher's README |
| [Source documentation](DATA_SOURCE.md) | Dataset origin, preparation, and attribution |

## Tools and approach

- **Power Query:** remove empty rows and columns, check types, standardize field names, label periods, and append matching source files.
- **Power BI and DAX:** compare performance rates, output per observed production day, stop hours, and stop-time distributions.
- **Validation:** check summary calculations against the original files and document inconsistencies in the supplied metrics.

Period-level availability, performance, and quality use ratios of summed time or quantities. Reported OEE is weighted by planned production time. Stop group/type shares use total recorded stop duration within each period; unplanned downtime share uses planned production time. These denominators answer different questions.

## Scope and methodology

| Source | Before LSS | After LSS |
| --- | --- | --- |
| OEE summaries | Sep 22–Dec 18, 2025; 62 records | Jan 30–Apr 3, 2026; 43 records |
| Stop-event logs | 635 events | 540 events |

## Limitations and interpretation

Eleven baseline OEE values differ from Availability × Performance × Quality and approximately match Availability × Performance. Original values are retained and labeled **reported OEE**. Separately, two baseline and nine after-LSS Performance values exceed 100%. Event-log and OEE-summary unplanned stop totals also differ slightly. The report explains these issues and the different date coverage.

Recorded stop labels identify areas for investigation; they do not establish root causes or individual responsibility. Unequal observation lengths and operating conditions limit before-and-after comparisons.

**Export version note:** the dashboard PDF was updated during the repository review to correct the reported-OEE label, date-coverage note, and validation text. Chart figures are unchanged. The PBIX and original Word report are retained as supplied.

## Open and refresh

1. Download the repository using **Code → Download ZIP**, extract it, and open `powerbi/Brick_Manufacturing_Analysis.pbix` in Power BI Desktop on Windows.
2. Explore the saved report using its slicers. The dashboard PDF is available for viewing without Power BI.
3. To refresh the data, update the four CSV source paths in Power Query or Data source settings to point to the files in your local `data/` folder, then refresh.

## Data source and attribution

**Panos Ntoas — OEE and Downtime Dataset from Heavy Clay Manufacturing Line (Version 1.0).** University of Cyprus / Kakoyiannis Bricks Ltd. Published on Zenodo: https://doi.org/10.5281/zenodo.17855209.

The dataset is licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**, as stated in the [original README](data/README.md). Source files are reproduced unchanged. Cleaning and analytical transformations were performed in Power BI; the analysis and report are by Caio Bergamo. See [source details](DATA_SOURCE.md).

## Other portfolio projects

- [Olist Delivery Analysis](https://github.com/caiocbergamo/Olist_Delivery_Analysis)
- [Maven Manufacturing Analysis](https://github.com/caiocbergamo/Maven_Manufacturing_Analysis)
