# Task 2: Gender Pay Equality Classification in Excel

Part of the [Deloitte Forage Virtual Internship](../).

## Background

Daikibo received internal complaints about gender pay inequality across different job roles
and locations. The Forensic Tech Team developed an algorithm to compute an Equality Score for
each job role, where:

- 0 indicates perfect equality.
- Negative values indicate gender pay disparity against women.
- Positive values indicate gender pay disparity against men.
- Scores range from -100 to +100.

## Approach

1. Imported the "Task 5 Equality Table.xlsx" dataset, which contained:
   - `Factory`
   - `Job Role`
   - `Equality Score`
2. Created a new column, "Equality Class", to categorize the scores using an Excel formula:

   ```
   =IF(ABS(C2)<=10,"Fair",IF(ABS(C2)<=20,"Unfair","Highly Discriminative"))
   ```

3. Classification logic:
   - **Fair**: scores between -10 and +10
   - **Unfair**: scores between -20 and -11, or +11 and +20
   - **Highly Discriminative**: scores below -20 or above +20
4. Saved and submitted the updated file with the classification applied to all job roles.

## Deliverable

[`Task 5 Equality Table.xlsx`](Task 5 Equality Table.xlsx) — the original Factory / Job Role / Equality Score
table with the new Equality Class column added.

## Findings

- Every factory skews negative overall — no location shows a bias in favor of men.
- The most extreme scores are concentrated in senior roles: Daikibo Factory Meiyo's VP (-26)
  and C-Level (-25) roles are the two worst scores in the dataset.
- Engineering roles (Sr. Engineer, Engineer, Jr. Engineer) trend close to "Fair" at every
  factory, while Manager-tier and above roles are disproportionately "Unfair" or "Highly
  Discriminative."