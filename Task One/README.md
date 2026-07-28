# Task 1: Telemetry Data Analysis in Tableau

Part of the [Deloitte Forage Virtual Internship](../).

## Background

Daikibo, an industrial manufacturing company, collected telemetry data from four factories
worldwide:

- Daikibo Factory Meiyo (Tokyo, Japan)
- Daikibo Factory Seiko (Osaka, Japan)
- Daikibo Berlin (Berlin, Germany)
- Daikibo Shenzhen (Shenzhen, China)

Each factory had 9 types of machines, generating a telemetry message every 10 minutes over a
one-month period (May 2021). The goal was to analyze machine failures to answer two key
questions:

1. Which factory had the most machine breakdowns?
2. Which machines broke down most frequently in that location?

## Approach

1. Imported the JSON telemetry data into Tableau, checking all schema levels so every nested
   field (status, temperature, location, factory, section, etc.) was available.
2. Created a calculated field called `Unhealthy`, assigning a value of 10 to unhealthy machine
   statuses (representing 10 minutes of potential downtime per message):
   ```
   IF [Status] = "unhealthy" THEN 10 ELSE 0 END
   ```
3. Built visualizations:
   - Bar chart: "Down Time per Factory" to compare machine downtime across factories.
   - Bar chart: "Down Time per Device Type" to show breakdowns by machine type.
4. Designed an interactive dashboard:
   - Linked both charts to allow filtering by factory.
   - Enabled dynamic insights by selecting a factory to view its machine downtime details.
5. Identified the factory with the highest downtime and captured a screenshot for submission.

## Findings

| Factory | Downtime (minutes) |
|---|---|
| Daikibo Factory Seiko | 480 |
| Daikibo Shenzhen | 420 |
| Daikibo Factory Meiyo | 110 |
| Daikibo Berlin | 20 |

- **Most downtime**: Daikibo Factory Seiko, with 480 minutes (8 hours) over the month.
- **Worst-performing machine there**: the LaserWelder, which accounted for all of Seiko's
  downtime.
- Across factories, LaserCutter and LaserWelder units were consistently the biggest
  contributors to downtime.

## Tableau Dashboard

![Down Time dashboard](Task One/Dashboard.png)

## Notes on the data file

The raw `daikibo-telemetry-data.json` source file (~58 MB, 160,704 records) is not included in
this repository to keep it lightweight. It can be requested from Forage's Task 1 resources, or
regenerated from Daikibo's telemetry export.