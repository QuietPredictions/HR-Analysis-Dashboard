# HR-Analysis-Dashboard

**1. Project Title**
HR Analytics Dashboard - A comprehensive HR analytics dashboard designed to deliver actionable insights that strengthen employee retention and support data-driven hiring decisions.

**2. Purpose**
To build a data-driven HR analytics dashboard that clearly identifies the underlying drivers of employee attrition. By uncovering patterns in separations, the dashboard supports more informed talent acquisition strategies and helps improve retention of high-value employees.

**3. Tech Stack**
The dashboard was built using the **Power BI Desktop** tool.
- **Power Query:** Data ingestion, schema exploration, and transformation using Power BI Query Editor.
- **Data Cleaning & Feature Engineering:** Data type corrections, handling inconsistencies, and creating derived fields (e.g., Region, Age Groups).
- **Data Modeling:** Star schema design, relationship building with BUCode, GenderID, and Date keys, and ensuring referential integrity.
- **DAX Calculations:** Development of KPI measures for Active Employees, New Hires, Separations, Tenure, Gender metrics, and workforce segmentation.
- **Report & Dashboard Design:** Interactive visuals, slicers, and UX-focused layout development in Power BI.
- **Security & Deployment:** Row-Level Security (RLS), .pbix packaging, exporting to PDF/PPT, and publishing to Power BI Service.

**4. Data Source**
•	**Source –** Edureka Project Dataset
•	**Time Period –** 2011 to 2014
•	**Size –** 5,46,363 employees data 

**5. Features/ Highlights**
***Business problem***
Organizations often face challenges in understanding the drivers behind employee attrition, which can hinder effective retention and recruitment strategies. This project aims to design a comprehensive HR analytics dashboard that enables HR professionals to analyse separation trends, uncover underlying factors influencing employee exits, and derive actionable insights to enhance retention and improve future hiring decisions.

***Key Visuals***
•	Stacked Bar Graph – To show active employees by Age Group and Pay Type
•	Cards – Total and gender-wise Separations, Active Employees and New Hires 
•	Slicers – Region-wise and year-wise
•	Clustered Column Chart – Region-wise and gender-wise trends for employees’ Average Tenure Months
•	Line Chart – Region-wise trend for new hires in the categories of Full-time and part-time
•	Pie Chart – New Hires trend based on age groups
•	Stacked Bar Chart – Region-wise trend in separations in various age groups

***DAX Measures & KPI Logic***
Create a dedicated measure table with DAX formulas for various metrics as mentioned below: - 
•	AgeGroupID = IF(Employee[Age] <30, 1, IF(Employee[Age]<50, 2, 3))
•	isNewHire = IF(YEAR([date]) = YEAR([HireDate]) && MONTH([date])=MONTH([HireDate]), 1) 
•	TenureDays = IF([date]-[HireDate]<0,[HireDate]-[date],[date]-[HireDate])
•	EmpCount = CALCULATE(COUNT(Employee[EmplID]), FILTER(ALL('Date'[PeriodNumber]), 'Date'[PeriodNumber] = MAX('Date'[PeriodNumber]))) 
•	Actives = CALCULATE([EmpCount], FILTER(Employee, ISBLANK(Employee[TermDate]))) 
•	New Hires = COUNTX(FILTER(Employee, Employee[isNewHire] = 1), Employee[EmplID])
•	Separations = COUNTX(FILTER(Employee, NOT (ISBLANK(Employee[TermDate]))),Employee[EmplID])
•	AVG Tenure Days = AVERAGE(Employee[TenureDays])
•	AVG Tenure Months = ROUND([AVG Tenure Days]/30,1)-1
•	Female Emp Actives = CALCULATE([Actives], Gender[Gender]="Female")
•	Female New Hires = CALCULATE([New Hires], Gender[Gender]="Female")
•	Female Separations = CALCULATE([Separations],Gender[Gender]="Female")
•	Male Emp Actives = CALCULATE([Actives],Gender[Gender] = "Male")
•	Male New Hires = COUNTX(FILTER(Employee, Employee[Gender] = "D" && NOT ISBLANK(Employee[isNewHire])), Employee[EmplID])
•	Male Separations = CALCULATE([Separations],Gender[Gender]="Male")

***Insights***
•	In North Region, employees under 30 accounted for 15.14% of separations. Overall, employees under 30 recorded the highest average separations (1,374.83), significantly exceeding the 30–49 and 50+ groups.
•	Hourly employees dominated the <30 age group with 5,504 employees (40.83%), while salaried employees peaked in the 30–49 age group at 583. The largest gap between Hourly employees and the salaried employees was observed in the <30 age group.
•	Female active employee counts declined steadily with age (2,872 in <30 vs. 1,120 in 50+), while overall active employees increased from 2011–2014—up 48.06% for females and 37.74% for males.
•	The West region recorded the highest share of new hires (21.07%) and, also showed the strongest preference for part-time hiring—19.78% of all part-time new hires came from this region. 
•	Average new hires were significantly higher for part-time roles (2,707.33) compared to full-time (155.17), with the largest gap observed in the West region, where part-time hires exceeded full-time hires by 3,170.
•	A majority of new hires (72.68%) were in the <30 age group. Between 2011–2014, hiring averaged 11.87% for females and 13.12% for males, with 408 more female hires than males in the <30 group.
•	Average Tenure Months was higher for Male (111.83) than Female (91). 

***Future Recommendations***
**- Target Retention Efforts on Employees Under 30:** This age group shows the highest separation rates and turnover risk, especially in the North region. Tailored engagement programs, growth opportunities, and early-career development can help reduce attrition.
**- Strengthen Hiring Strategies for High-Demand Segments:** Most new hires (72.68%) are under 30, and part-time roles—particularly in the West region—show significantly higher hiring volumes. HR should prioritize talent pipelines for younger and hourly/part-time candidates to meet workforce demand.
**- Address Workforce Composition and Diversity Trends:** Female representation declines sharply with age and tenure is lower for female employees compared to males. Improving career progression, support programs, and retention strategies for women can enhance long-term workforce stability and diversity.

**6. Screenshots**
https://github.com/QuietPredictions/HR-Analysis-Dashboard/blob/main/HRAnalysisDashboard.png

