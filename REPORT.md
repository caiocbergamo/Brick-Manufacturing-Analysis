# Brick Manufacturing Performance and Downtime Analysis

*Prepared by Caio Bergamo*

[Back to project overview](README.md) · [Data source and methodology](DATA_SOURCE.md)

## Executive summary

The after-LSS period recorded higher time-weighted reported OEE, increasing from 54.36% to 63.99%, and higher availability, from 59.17% to 69.66%. However, quality declined from 98.50% to 96.82%, while output per observed production day remained similar. Unplanned stops also accounted for a larger share of planned production time, increasing from 18.69% to 21.31%. These results show a mixed picture rather than improvement across every measure.

My suggestion is to investigate the quality decline and unplanned stop losses, with particular attention to manual brick handling and equipment failures. The two periods have different observation lengths, and some source OEE values are inconsistent with their components. The analysis identifies areas for investigation, but it does not establish that Lean Six Sigma caused the changes.

## Business objective

Compare production performance and recorded stop events before and after Lean Six Sigma (LSS) implementation, identify where time is being lost, and recommend priorities for further investigation. The intended audience includes production managers, operations analysts, and continuous improvement teams.

## Production performance

| Metric | Before LSS | After LSS |
| --- | --- | --- |
| Observed production dates | 62 | 43 |
| Total output units | 1,955,731 | 1,342,331 |
| Output per observed production day | 31,544.05 | 31,217.00 |
| Time-weighted reported OEE | 54.36% | 63.99% |
| Availability rate | 59.17% | 69.66% |
| Performance rate | 93.20% | 93.74% |
| Quality rate | 98.50% | 96.82% |
| Unplanned share of planned production time | 18.69% | 21.31% |

Availability increased by 10.49 percentage points, while performance increased by 0.54 points. Quality declined by 1.68 points. Output per observed production day was slightly lower after LSS. This daily comparison accounts for the number of observed production dates, but it does not control for differences in scheduled hours or operating conditions.

## Downtime findings

The stop-event logs recorded 173.13 hours before LSS and 145.17 hours after LSS, across 635 and 540 events. Average recorded stop duration was similar, at 16.36 and 16.13 minutes. Lower total hours alone do not establish better performance because the observation periods differ.

In the OEE summaries, unplanned stop time fell from 103.00 to 68.31 hours. However, planned production time also fell, from 550.96 to 320.50 hours. As a result, unplanned stops represented a larger share of planned production time after LSS. This is why the total hours and the downtime share need to be considered together.

### Distribution of recorded stop time

| Stop type | Before LSS | After LSS |
| --- | --- | --- |
| Planned - Included in OEE | 27.44% | 20.14% |
| Planned - Not included in OEE | 13.01% | 32.55% |
| Unplanned | 59.54% | 47.31% |

Unplanned events made up a smaller share of all recorded stop time after LSS. This does not contradict the higher unplanned share on the production comparison page: one divides by all recorded stop time, while the other divides by planned production time.

By stop group, failure-related events declined from 31.13% to 19.40% of recorded stop time, while operational events increased from 30.12% to 39.45%. Materials increased from 22.82% to 24.82%, and setups and changeovers remained similar at 15.92% and 16.33%. These percentages describe the distribution of stop time, not the frequency of events.

### Leading unplanned stop reasons

Across both periods combined, the five largest unplanned stop reasons were manual brick handling (42.05 hours), mechanical failure (37.82 hours), automation failure (36.60 hours), rack starvation (14.26 hours), and racks (8.12 hours). These are recorded reason labels, not confirmed root causes. The Power BI period slicer allows the ranking to be examined separately for each period.

## Recommended investigation priorities

### 1 - Investigate the quality decline

I suggest examining dates with higher reject rates and comparing product mix, process settings, material conditions, and inspection records. Quality fell even though reported OEE and availability increased. Additional records would help determine whether the change was concentrated in particular products or operating conditions.

### 2 - Investigate manual handling and equipment failures

Manual brick handling, mechanical failure, and automation failure recorded the most unplanned stop hours across both periods. Review the related events and maintenance history to understand what led to these stoppages. Compare each period separately before deciding where corrective action is needed.

### 3 - Monitor losses against comparable production time

Continue monitoring unplanned stop time as a share of planned production time, alongside quality and output. Compare similar products and scheduled hours where possible. This would help determine whether the observed differences persist and avoid treating lower total stop hours as proof of improvement.

## Data source and scope

The analysis uses four CSV files published by Panos Ntoas on Zenodo. They contain OEE summaries and stop-event records from a continuous brick manufacturing line. The dataset README states that the data is licensed under Creative Commons Attribution 4.0 International (CC BY 4.0).

| File | Observation period | Records |
| --- | --- | --- |
| OEEdataset.csv | Sep 22-Dec 18, 2025 | 62 |
| DowntimeDataset.csv | Sep 22-Dec 18, 2025 | 635 |
| OEEdataset_afterLSS.csv | Jan 30-Apr 3, 2026 | 43 |
| DowntimeDataset_afterLSS.csv | Jan 30-Apr 3, 2026 | 540 |

## Preparation and measurement

Preparation was completed in Power Query: empty rows and columns were removed, data types and names were checked, period labels were added, and matching files were appended. Greek comments were excluded; original CSVs were preserved. OEE summaries and event logs remained separate. Retained values and displayed summary calculations were checked against the source files.

Time-weighted reported OEE weights supplied daily OEE by planned production seconds. Availability is full-speed plus slow-production seconds divided by planned production seconds. Performance is output divided by ideal production quantity; quality is good units divided by output. These period rates use summed quantities or time, rather than simple daily averages.

Output per day divides output by distinct observed production dates. Unplanned downtime share divides unplanned stop seconds by planned production seconds. Group and type shares divide category duration by total recorded stop duration within each period, retaining other filters. Hours are OEE seconds divided by 3,600 or event minutes divided by 60. Average stop duration includes all stop types, not repairs alone. The overview cards Average Daily OEE and Average Daily Quality use simple daily averages.

## Limitations and interpretation

The periods do not overlap and have unequal observation lengths. The OEE tables cover 62 and 43 production dates. The event logs cover 62 and 45 dates; March 25 and April 1, 2026 contain only no-production-schedule events and have no corresponding OEE rows. These differences should be considered when comparing totals. The before-and-after design does not establish a causal effect of LSS.

Eleven baseline records contain supplied OEE values that differ from Availability × Performance × Quality and approximately match Availability × Performance. The original OEE values were retained and clearly labeled as reported OEE. Separately, Performance exceeded 100% in two baseline records and nine after-LSS records. These values were retained. Ideal production quantity was interpreted as units because output divided by this quantity reproduces the supplied Performance values, despite the README labeling it as seconds.

Recorded event durations differed from timestamp-derived durations by 0 to 1 minute before LSS and -1 to 1 minute after LSS. Calculated durations were positive. Original durations and unspecified stop-location labels were retained. Unplanned stop totals also differ slightly between sources: OEE summaries versus event logs were 103.00 versus 103.09 hours before LSS and 68.31 versus 68.68 hours after LSS. The causes of these differences remain unconfirmed.

The findings apply to this manufacturing line and the observed periods. The recorded stop labels do not establish underlying causes or individual responsibility. Maintenance history, product-level production information, operating conditions, and longer observation periods would support a more complete assessment.

## Source links

- Dataset: https://doi.org/10.5281/zenodo.17855209
- Original dataset documentation: [data/README.md](data/README.md)