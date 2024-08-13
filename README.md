# Patients-Emergency Room-Power BI Dashboard:
Objective:

Utilized Power BI to analyze healthcare data, focusing on key metrics to enhance patient care and operational efficiency. Evaluated average waiting times to optimize scheduling and patient flow. Analyzed monthly patient visits to identify trends and peak periods for resource allocation. Investigated total visits by department referral to streamline inter-departmental workflows. Segmented patient visits by age group to target demographic-specific healthcare needs. Determined average satisfaction levels by age group and patient race to enhance patient experience and service delivery. Calculated average wait times by demographic factors to improve operational efficiency and patient satisfaction metrics
## Problem Statement
Objective:
1).Evaluate the average waiting time of the patient.
2).Analyze patient visits on a monthly basis.
3).Determine the total visits by department referral.
4).Break down patient visits by age group.
5).Determine the average satisfaction by age group and patient race.
6).Determine the average wait time by age group and patient race.

## Problem Statement Snap:
![Power-BI-Healthcare-Analytic-Dashboard-Hospital-Cl(2) - frame at 0m37s](https://github.com/user-attachments/assets/307307a5-f4e3-4d21-9965-0029545ef89e)

## Power BI Dashboard Snap:
![hospital power BI](https://github.com/user-attachments/assets/38cc045c-f97d-41f9-86cf-75ec8411e506)

## DAX Funtions Used:


For each objective listed, here are potential DAX (Data Analysis Expressions) functions that could be used in Power BI to achieve the analysis:

1. Objective: Evaluate the average waiting time of the patient.
   - DAX Function: AVERAGEX
     - Example: AVERAGEX('Patients', 'Patients'[WaitingTime])

2. Objective: Analyze patient visits on a monthly basis.
   - DAX Function: CALENDAR
     - Example: CALENDAR(DATE(2024, 1, 1), DATE(2024, 12, 31))

3. Objective: Determine the total visits by department referral.
   - DAX Function: COUNTROWS
     - Example: SUMMARIZE('Patients', 'Patients'[Department], "Total Visits", COUNTROWS('Patients'))

4. Objective: Break down patient visits by age group.
   - DAX Function: SWITCH or IF
     - Example: 
       DAX
       SWITCH(
           TRUE(),
           'Patients'[Age] < 18, "Under 18",
           'Patients'[Age] >= 18 && 'Patients'[Age] < 30, "18-29",
           'Patients'[Age] >= 30 && 'Patients'[Age] < 50, "30-49",
           'Patients'[Age] >= 50, "50 and above"
       )
       

5. Objective: Determine the average satisfaction by age-group and Patient race.
   - DAX Function: AVERAGEX with FILTER
     - Example: 
       DAX
       AVERAGEX(
           FILTER('Patients', 'Patients'[Race] = "Caucasian"),
           'Patients'[Satisfaction]
       )
       

6. Objective: Determine the average wait time by age-group and patient race.
   - DAX Function: CALCULATE with AVERAGEX and FILTER
     - Example: 
       DAX
       CALCULATE(
           AVERAGEX('Patients', 'Patients'[WaitingTime]),
           FILTER('Patients', 'Patients'[Age] >= 18 && 'Patients'[Age] < 30 && 'Patients'[Race] = "African American")
       )
       
