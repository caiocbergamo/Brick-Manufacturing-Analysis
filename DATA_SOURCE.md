# Data Source and Methodology

## Source and attribution

Panos Ntoas, **OEE and Downtime Dataset from Heavy Clay Manufacturing Line (Version 1.0)**, University of Cyprus / Kakoyiannis Bricks Ltd. Published on [Zenodo](https://doi.org/10.5281/zenodo.17855209).

The [original publisher README](data/README.md) states **Creative Commons Attribution 4.0 International (CC BY 4.0)**. The four CSV files and original README are reproduced unchanged. Power Query transformations and the analysis/report are by Caio Bergamo.

## Files and scope

| File | Observation period | Retained records |
| --- | --- | ---: |
| [OEEdataset.csv](data/OEEdataset.csv) | Sep 22–Dec 18, 2025 | 62 |
| [DowntimeDataset.csv](data/DowntimeDataset.csv) | Sep 22–Dec 18, 2025 | 635 |
| [OEEdataset_afterLSS.csv](data/OEEdataset_afterLSS.csv) | Jan 30–Apr 3, 2026 | 43 |
| [DowntimeDataset_afterLSS.csv](data/DowntimeDataset_afterLSS.csv) | Jan 30–Apr 3, 2026 | 540 |

The OEE files contain 62/43 production dates; event logs contain 62/45 dates. March 25 and April 1, 2026 have only no-production-schedule events and no corresponding OEE rows.

## Preparation

Power Query removed empty rows/columns, checked types, standardized names, added period labels, and appended matching files. Greek operator comments were excluded from analysis. Original CSVs remain unchanged, including their source comments and unused empty columns. OEE summaries and event logs remain separate tables.

## Metric definitions

| Metric | Definition |
| --- | --- |
| Time-weighted reported OEE | Sum of supplied daily OEE × planned production seconds ÷ total planned production seconds |
| Availability | Full-speed plus slow-production seconds ÷ planned production seconds |
| Performance | Output units ÷ ideal production quantity |
| Quality | Good units ÷ output units |
| Output per observed production day | Output units ÷ distinct observed production dates |
| Unplanned downtime share | Unplanned stop seconds ÷ planned production seconds |
| Stop group/type time share | Category duration ÷ recorded stop duration across groups/types in the period, retaining other filters |
| Stop hours | Event minutes ÷ 60; OEE time fields in seconds ÷ 3,600 |
| Average stop duration | Mean recorded event duration, across all included stop types |

The overview's Average Daily OEE and Average Daily Quality are simple daily means. The period comparison uses the weighted/summed measures above.

## Validation and limitations

Period rates, event counts/hours, stop-time shares, and leading unplanned reasons were independently reconciled to the CSVs. The ten actual DAX measures were checked against the written definitions.

Eleven baseline reported OEE values differ from Availability × Performance × Quality and approximately match Availability × Performance. Two baseline and nine after-LSS Performance values exceed 100%. Original values are retained. Ideal production quantity is interpreted as units because output ÷ ideal quantity reproduces supplied Performance, despite the original README's seconds label.

Timestamp-derived and recorded event durations differ by up to one minute. Unplanned hours differ between OEE summaries and event logs: 103.00 vs 103.09 before, and 68.31 vs 68.68 after. Unequal observation lengths and operating conditions limit comparisons and prevent causal attribution to LSS.

The current PBIX and written report contain updated validation notes. The dashboard PDF was corrected during the repository review for consistent labels, date coverage, and validation wording; chart figures are unchanged. Native Power BI rendering and interactive refresh were not rerun during the repository review.

[Back to project overview](README.md) · [Read the analysis report](REPORT.md)
