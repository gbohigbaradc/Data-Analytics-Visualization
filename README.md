# DeepTech Mentorship Programme: Data Analyst Assessment

**Author:** Gboh-Igbara D. Charles
**Dataset:** `DeepTech_Data_Analyst_Assessment_100_Records.xlsx` (100 fictional mentee records, October 2026)
**Tool used:** Microsoft Excel (.xlsx, formula-driven)

## Submission links

| Item | Link |
|---|---|
| Dashboard / analysis workbook (Google Sheets) | `[paste shared link here]` |
| One-page executive report | `[paste shared link here]` |

Both links must be set to "Anyone with the link can view" before submitting.

## What is in this submission

| File | Purpose |
|---|---|
| `DeepTech_Mentorship_Analysis.xlsx` | Cleaned data, analysis tables, dashboard, priority list and cleaning log |
| Executive report (Doc / Word / PDF) | One-page summary of findings and recommendations |
| `README.md` | This guide |

## Workbook guide

| Tab | What it contains |
|---|---|
| **Dashboard** | Headline figures, four charts, high-risk-by-track table, key findings |
| **Analysis** | Editable assumptions (top), then eight tables: track, mentor status, region, support requests, mentor load, correlations, risk tier by track, risk flag prevalence |
| **Clean_Data** | 100 cleaned records plus derived columns (attendance rate, assignment rate, days inactive, six risk flags, risk score, risk tier, risk drivers, data quality note) |
| **Priority_List** | The 16 high-risk mentees with the reasons they were flagged, sorted by risk score then lowest capstone progress |
| **Cleaning_Log** | Every change made, every check that passed, and what could not be verified |

## Approach

1. **Clean:** profiled every column for duplicates, missing values, inconsistent labels, impossible values and status/progress conflicts. Nothing was deleted (100 records in, 100 out) and nothing was imputed.
2. **Analyse:** compared tracks, regions, mentor status and support requests, and tested which measures move with capstone progress.
3. **Visualise:** a single-page dashboard built from formula-driven tables.
4. **Recommend:** five prioritised actions in the executive report.

## Metric definitions

| Metric | Definition |
|---|---|
| Attendance rate | Sessions Attended / Sessions Scheduled (blank where attended exceeds scheduled) |
| Assignment completion | Assignments Submitted / Assignments Expected (expected is 6 for every mentee) |
| Days inactive | 25 Oct 2026 minus Last Active Date |
| Mentor status | Assigned, Unassigned, or Not recorded (blank in source) |
| Risk score | Count of six flags: attendance below 50%, no mentor, Foundation Check below 50, capstone not started, inactive 10+ days, assignment completion below 50% |
| Risk tier | High = 4+ flags, Medium = 2-3, Low = 0-1 |

Thresholds are analyst judgement because the brief gives no targets. They are the blue input cells at the top of the **Analysis** tab; changing them updates every flag, table and chart. If you change them, refresh the ID column on **Priority_List**, which is sorted from the default thresholds.

## Data cleaning summary

| Issue | Treatment |
|---|---|
| Duplicate ID `DTR-027` (two rows with different data; `DTR-028` missing) | Kept both, renamed second to `DTR-027-B`. Cause cannot be confirmed |
| Track label `gen AI` | Standardised to `Generative AI` |
| Status `In progress` | Standardised to `In Progress` |
| Support request `foundation concepts` | Standardised to `Foundational concepts` |
| Blank Mentor ID (`DTR-069`) | Labelled `Not recorded`, kept separate from `Unassigned` |
| Missing Foundation, Capstone and Satisfaction values (one each) | Left blank, excluded from averages |
| Attended exceeds scheduled (`DTR-058`) | Kept as supplied, excluded from attendance averages |
| Blank Support Request (49 rows) | Interpreted as "None" (assumption) |
| Dates stored as text | Converted to real dates |

Full detail, including checks that passed, is in the **Cleaning_Log** tab.

## Headline findings

- Only 7 of 100 mentees have completed the capstone; 26 have not started it.
- Unassigned mentees attend 33% of sessions versus 73% for assigned mentees, with no weaker foundation scores.
- Computer Vision has the lowest average Foundation Check (47 versus 60 overall) and 65% of its mentees have not started the capstone.
- Assignment completion (r = 0.71) and Foundation Check (r = 0.62) track capstone progress most closely; attendance is weaker (r = 0.30).
- 40 mentees have been inactive for 10+ days; 16 are high risk.

## Limitations

- A single snapshot with no defined reporting window, so no trends over time can be claimed.
- About 20 mentees per track and 12-22 per region; mentor-level groups are as small as 3-4. Findings are descriptive, not causal.
- Blank support requests, the `DTR-027` duplicate and the `DTR-069` mentor gap rest on assumptions that cannot be verified from the data.

## How to reproduce

Open `DeepTech_Mentorship_Analysis.xlsx` in Excel or Google Sheets. All analysis cells are formulas referencing **Clean_Data**, so no macros or add-ins are required.
