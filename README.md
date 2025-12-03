# HR-Analysis-Dashboard

**I. Project Title** <br>
HR Analytics Dashboard - A comprehensive HR analytics dashboard designed to deliver actionable insights that strengthen employee retention and support data-driven hiring decisions.


**II. Purpose**<br>
To build a data-driven HR analytics dashboard that clearly identifies the underlying drivers of employee attrition. By uncovering patterns in separations, the dashboard supports more informed talent acquisition strategies and helps improve retention of high-value employees.


**III. Tech Stack**<br>
The dashboard was built using the **Power BI Desktop** tool.<br>
 1. **Power Query:** Data ingestion, schema exploration, and transformation using Power BI Query Editor.
 2. **Data Cleaning & Feature Engineering:** Data type corrections, handling inconsistencies, and creating derived fields (e.g., Region, Age Groups).
 3. **Data Modeling:** Star schema design, relationship building with BUCode, GenderID, and Date keys, and ensuring referential integrity.
 4. **DAX Calculations:** Development of KPI measures for Active Employees, New Hires, Separations, Tenure, Gender metrics, and workforce segmentation.
 5. **Report & Dashboard Design:** Interactive visuals, slicers, and UX-focused layout development in Power BI.
 6. **Security & Deployment:** Row-Level Security (RLS), .pbix packaging, exporting to PDF/PPT, and publishing to Power BI Service.


**IV. Data Source**<br>
 1. **Source –** Edureka Project Dataset
 2. **Time Period –** 2011 to 2014
 3. **Size –** 5,46,363 employees data 


**V. Features/ Highlights**<br>
***Business problem***<br>
Organizations often face challenges in understanding the drivers behind employee attrition, which can hinder effective retention and recruitment strategies. This project aims to design a comprehensive HR analytics dashboard that enables HR professionals to analyse separation trends, uncover underlying factors influencing employee exits, and derive actionable insights to enhance retention and improve future hiring decisions.


***Key Visuals***
 1. Stacked Bar Graph – To show active employees by Age Group and Pay Type
 2. Cards – Total and gender-wise Separations, Active Employees and New Hires
 3. Slicers – Region-wise and year-wise
 4. Clustered Column Chart – Region-wise and gender-wise trends for employees’ Average Tenure Months
 5. Line Chart – Region-wise trend for new hires in the categories of Full-time and part-time
 6. Pie Chart – New Hires trend based on age groups
 7. Stacked Bar Chart – Region-wise trend in separations in various age groups


***DAX Measures & KPI Logic***<br>
Create a dedicated measure table with DAX formulas for various metrics as mentioned below: - 
 1.	AgeGroupID = IF(Employee[Age] <30, 1, IF(Employee[Age]<50, 2, 3))
2.	isNewHire = IF(YEAR([date]) = YEAR([HireDate]) && MONTH([date])=MONTH([HireDate]), 1) 
3.	TenureDays = IF([date]-[HireDate]<0,[HireDate]-[date],[date]-[HireDate])
4.	EmpCount = CALCULATE(COUNT(Employee[EmplID]), FILTER(ALL('Date'[PeriodNumber]), 'Date'[PeriodNumber] = MAX('Date'[PeriodNumber]))) 
5.	Actives = CALCULATE([EmpCount], FILTER(Employee, ISBLANK(Employee[TermDate]))) 
6.	New Hires = COUNTX(FILTER(Employee, Employee[isNewHire] = 1), Employee[EmplID])
7.	Separations = COUNTX(FILTER(Employee, NOT (ISBLANK(Employee[TermDate]))),Employee[EmplID])
8.	AVG Tenure Days = AVERAGE(Employee[TenureDays])
9.	AVG Tenure Months = ROUND([AVG Tenure Days]/30,1)-1
10.	Female Emp Actives = CALCULATE([Actives], Gender[Gender]="Female")
11.	Female New Hires = CALCULATE([New Hires], Gender[Gender]="Female")
12.	Female Separations = CALCULATE([Separations],Gender[Gender]="Female")
13.	Male Emp Actives = CALCULATE([Actives],Gender[Gender] = "Male")
14.	Male New Hires = COUNTX(FILTER(Employee, Employee[Gender] = "D" && NOT ISBLANK(Employee[isNewHire])), Employee[EmplID])
15.	Male Separations = CALCULATE([Separations],Gender[Gender]="Male")


***Insights***
1.	In North Region, employees under 30 accounted for 15.14% of separations. Overall, employees under 30 recorded the highest average separations (1,374.83), significantly exceeding the 30–49 and 50+ groups.
2.	Hourly employees dominated the <30 age group with 5,504 employees (40.83%), while salaried employees peaked in the 30–49 age group at 583. The largest gap between Hourly employees and the salaried employees was observed in the <30 age group.
3.	Female active employee counts declined steadily with age (2,872 in <30 vs. 1,120 in 50+), while overall active employees increased from 2011–2014—up 48.06% for females and 37.74% for males.
4.	The West region recorded the highest share of new hires (21.07%) and, also showed the strongest preference for part-time hiring—19.78% of all part-time new hires came from this region.
5.	Average new hires were significantly higher for part-time roles (2,707.33) compared to full-time (155.17), with the largest gap observed in the West region, where part-time hires exceeded full-time hires by 3,170.
6.	A majority of new hires (72.68%) were in the <30 age group. Between 2011–2014, hiring averaged 11.87% for females and 13.12% for males, with 408 more female hires than males in the <30 group.
7.	Average Tenure Months was higher for Male (111.83) than Female (91). 


***Future Recommendations***<br>
1.	Strengthen Retention for <30 Hourly Employees: Implement structured onboarding, early-career mentorship, and clear pathways from part-time to full-time roles. These interventions can reduce high separation rates in the <30 group and boost long-term engagement.
2.	Optimize Hiring Strategy in the West Region: Given the heavy reliance on part-time hiring, introduce a balanced hiring plan that increases full-time recruitment where needed and establishes performance-based conversion programs to improve workforce stability and reduce turnover.
3.	Improve Female Tenure and Career Progression: Address the gender tenure gap by expanding flexible work options, leadership development opportunities, and return-to-work programs that support women through key career transitions.


**VI. Screenshots**

![Dashboard Preview](https://github.com/QuietPredictions/HR-Analysis-Dashboard/blob/main/HRAnalysisDashboard.png)
