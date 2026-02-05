# guvi-hackathon
PROJECT DESCRIPTION
Hospital Resource Utilization & Patient Outcomes Dashboard

Summary:
An end-to-end Healthcare Analytics Dashboard that provides real-time insights into hospital operations, resource utilization, financial performance, and patient outcomes. Built to help hospital administrators make data-driven decisions that improve efficiency, reduce costs, and enhance patient care.

Problem Statement:
Design and build an interactive analytics dashboard for hospital operations teams to monitor, analyze, and optimize resource utilization across departments in a mid-sized multi-specialty hospital network in India. The solution must provide decision-makers with visibility into patient admissions, bed occupancy, doctor workloads, procedure volumes, emergency cases, discharge turnaround times, and patient outcomes. The dashboard should allow drill-down by department (Cardiology, Oncology, Orthopedics, Pediatrics, Emergency, General Medicine), time period, and patient demographics. The system should highlight operational bottlenecks (e.g., surplus patients during peak hours, delayed discharges), predict upcoming resource needs (e.g., ICU beds, ventilators), and generate monthly performance summaries. Insights must support both short-term staffing decisions and long-term capacity planning. Additionally, the platform must support comparisons across hospital branches and show KPIs such as cost per discharge, readmission rates, and average length of stay. All analytics must be interpretable by non-technical administrative staff using simple visualizations and standardized metrics.

Project Overview:
Modern hospitals struggle with bed shortages, inefficient resource allocation, high readmission rates, and lack of operational visibility.
This project solves these challenges by integrating Flask APIs, MySQL, and Power BI into a single interactive analytics platform.
Key Features:
•	Real-time KPI Dashboard (Admissions, ALOS, Bed Occupancy, Readmission Rate)
•	Department-wise Resource Utilization
•	Financial Analysis (Revenue, Cost per Patient, Insurance Distribution)
•	Doctor Utilization & Workload Insights
•	Patient Outcome & Quality Metrics
•	CSV Export for Reporting & Compliance
•	Interactive Power BI Visuals with Slicers & Drill-through

Technology Stack:
Layer	Technology	Purpose
Backend Framework	Flask 3.0.0	RESTful API development
Database	MySQL 8.0	Relational data storage
BI Tool	Power BI Desktop	Interactive visualizations
Data Processing	Pandas 2.1.4	Data transformation & export
API Security	Flask-CORS	Cross-origin resource sharing
Database Connector	mysql-connector-python	Database operations
Configuration	python-dotenv	Environment management
Deployment	PythonAnywhere	Cloud hosting (free tier)
Version Control	GitHub	Code repository

How the System Is Organized:
1.Backend (Flask API)
The backend exposes REST APIs that calculate hospital KPIs directly from a MySQL database.
Purpose:
•	Centralize business logic
•	Enable live data refresh in Power BI
•	Allow easy integration with other tools in the future
Key APIs include:
•	Average Length of Stay (ALOS)
•	Bed Occupancy Rate
•	Readmission Rate (30-day)
•	Procedure volume & revenue
•	Cost per patient
•	CSV export for reporting
2.Database (MySQL)
The database models a realistic hospital environment using 8 core tables:
•	Patients
•	Admissions
•	Departments
•	Doctors
•	Beds
•	Procedures
•	Billing
•	Outcomes
3.Analytics Layer (Power BI)
Power BI connects to the Flask APIs and visualizes the KPIs through interactive dashboards.
Key design focus:
•	Clear KPI storytelling
•	Minimal visual clutter
•	Reviewer-friendly navigation
•	Slicers for department, date, insurance, and branch

How This Dashboard Solves the Problem:
1️⃣ Unpredictable Bed Shortages
Solution:
•	Real-time bed occupancy tracking
•	Peak-period trend analysis
•	Department-wise capacity view
•	Alerts when occupancy exceeds safe limits
Impact: Fewer bed shortage issues and better capacity planning
2️⃣ Inefficient Resource Allocation
Solution:
•	Compare resource usage across departments
•	Identify underutilized beds and services
•	Support data-driven resource reallocation
Impact: Improved overall resource utilization
3️⃣ Long Patient Waiting Time
Solution:
•	Track admissions vs discharges
•	Identify bottlenecks using length-of-stay metrics
•	Balance emergency and scheduled cases
Impact: Reduced patient waiting time
4️⃣ High Readmission Rates
Solution:
•	Monitor 30-day readmissions
•	Analyze patient outcomes by department
•	Identify areas needing quality improvement
Impact: Better quality of care and fewer readmissions
5️⃣ Budget and Cost Overruns
Solution:
•	Track cost per patient
•	Analyze revenue by procedures and departments
•	Monitor insurance vs self-pay trends
Impact: Better cost control and financial planning
6️⃣ Unbalanced Doctor Workload
Solution:
•	Track doctor utilization
•	Monitor patient-to-doctor ratios
•	Support fair workload distribution
Impact: Improved staff efficiency and reduced burnout
7️⃣ Manual Reporting Effort
Solution:
•	Automated data export (CSV)
•	Ready-to-use Power BI dashboards
•	One-click reporting for reviews and compliance
Impact: Significant reduction in manual reporting time

Conclusion:
The Hospital Resource Utilization & Patient Outcomes Dashboard represents a comprehensive, production-ready solution to the critical challenges faced by modern hospitals. By providing real-time visibility, predictive insights, and automated reporting, this platform empowers healthcare administrators to make data-driven decisions that improve patient care, optimize resources, and reduce costs.

