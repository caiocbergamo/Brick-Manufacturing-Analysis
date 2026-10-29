# Brick Manufacturing Analysis

A Power BI portfolio project by **Caio Bergamo**, comparing production performance and recorded downtime before and after Lean Six Sigma (LSS) implementation.

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

- **[Read the analysis report](REPORT.md)** — findings, recommendations, methodology, and limitations.
- **[View the dashboard PDF](reports/Brick_Manufacturing_Dashboard.pdf)** — the supplied Power BI presentation.
- **[Download the Power BI file](powerbi/Brick_Manufacturing_Analysis.pbix)** — interactive report for Power BI Desktop.
- **[Download the Word report](reports/Brick_Manufacturing_Report.docx)**.
- **[Original source data and documentation](data/)** — four CSV files and the publisher's README, preserved unchanged.

## Version note

The supplied dashboard PDF retains earlier methodology wording, including a note that final checks are pending and the shorter label “Time-Weighted OEE.” The current [written report](REPORT.md) documents completed validation and explains why the metric is described as **time-weighted reported OEE**. The original PDF, PBIX, Word report, and source files are preserved as supplied.

## Tools and approach

- **Power Query:** remove empty rows and columns, check types, standardize field names, label periods, and append matching source files.
- **Power BI and DAX:** compare performance rates, output per observed production day, stop hours, and stop-time distributions.
- **Validation:** check summary calculations against the original files and document inconsistencies in the supplied metrics.

Period-level availability, performance, and quality use ratios of summed time or quantities. Reported OEE is weighted by planned production time. Stop group/type shares use total recorded stop duration within each period; unplanned downtime share uses planned production time. These denominators answer different questions.

## Scope and interpretation

| Source | Before LSS | After LSS |
| --- | --- | --- |
| OEE summaries | Sep 22–Dec 18, 2025; 62 records | Jan 30–Apr 3, 2026; 43 records |
| Stop-event logs | 635 events | 540 events |

Eleven baseline OEE values differ from Availability × Performance × Quality and approximately match Availability × Performance. Original values are retained and labeled **reported OEE**. Separately, eleven supplied Performance values exceed 100%. Event-log and OEE-summary unplanned stop totals also differ slightly. The report explains these issues and the different date coverage.

Recorded stop labels identify areas for investigation; they do not establish root causes or individual responsibility.

## Open the Power BI file

1. Download the repository files and open `powerbi/Brick_Manufacturing_Analysis.pbix` in Power BI Desktop on Windows.
2. Explore the saved report using its slicers. The dashboard PDF is available for viewing without Power BI.
3. To refresh the data, update the four CSV source paths in Power Query or Data source settings to point to the files in your local `data/` folder, then refresh.

## Data source and attribution

**Panos Ntoas — OEE and Downtime Dataset from Heavy Clay Manufacturing Line (Version 1.0).** University of Cyprus / Kakoyiannis Bricks Ltd. Published on Zenodo: https://doi.org/10.5281/zenodo.17855209.

The dataset is licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**, as stated in the [original README](data/README.md). Source files are reproduced unchanged. Cleaning and analytical transformations were performed in Power BI; the analysis and report are by Caio Bergamo. This is an independent portfolio project.
