# Bank-Loan-Credit-Risk-Analysis
In depth Bank Loan/Credit Risk Analysis by creating Dashboards in Excel, and cross verifying results with SQL Querires

# Bank Loan/Credit Report

## Introduction

Welcome to my Bank Loan Report project! In this project, I have developed a comprehensive set of Excel Dashboards to monitor and analyze a bank's lending activities and performance. These dashboards aim to provide valuable insights into key loan-related metrics and trends, facilitating data-driven decision-making and strategic planning within lending operations.

## Dashboard 1: Summary

### Overview
In Dashboard 1, titled "Summary," I have created a comprehensive Bank Loan Report to monitor and assess our bank's lending activities and performance. This report provides insights into key loan-related metrics and their changes over time.



![image](https://github.com/rahulmaurya255/California_house_prcing/assets/155320538/66e284b7-85d4-4959-a30d-c76a3fbdbd42)





### Key Performance Indicators (KPIs) Requirements
1. **Total Loan Applications:** Calculated the total number of loan applications received during a specified period, along with Month-to-Date (MTD) and Month-over-Month (MoM) changes.
2. **Total Funded Amount:** Analyzed the total amount of funds disbursed as loans, monitoring MTD Total Funded Amount and MoM changes.
3. **Total Amount Received:** Tracked the total amount received from borrowers to assess cash flow and loan repayment, analyzing MTD and MoM changes.
4. **Average Interest Rate:** Calculated the average interest rate across all loans, monitoring variations MTD and MoM.
5. **Average Debt-to-Income Ratio (DTI):** Evaluated the average DTI for borrowers, analyzing MTD and MoM fluctuations.




![image](https://github.com/rahulmaurya255/California_house_prcing/assets/155320538/aed184d7-751c-48a9-a445-537cf7d735be)




### Good Loan vs. Bad Loan KPIs
I have distinguished between 'Good Loans' and 'Bad Loans' based on specific loan status criteria and created KPIs for each category.





![image](https://github.com/rahulmaurya255/Bank-Loan-Credit-Risk-Analysis/assets/155320538/03b64515-fa81-48b4-a367-4d7c3f869b15)






### Loan Status Grid View
Created a grid view report categorized by 'Loan Status' to gain a comprehensive overview of our lending operations and monitor loan performance.





![image](https://github.com/rahulmaurya255/Bank-Loan-Credit-Risk-Analysis/assets/155320538/75e8bb16-e884-4a9d-960c-da4d8911575e)







## Dashboard 2: Overview

### Objective
In Dashboard 2, titled "Overview," I have visually represented critical loan-related metrics and trends using a variety of chart types.







![image](https://github.com/rahulmaurya255/Bank-Loan-Credit-Risk-Analysis/assets/155320538/fc42a707-1000-4e9a-ad5c-e735302411e5)








### Chart Requirements
1. **Monthly Trends by Issue Date (Line Chart):** Showcased variations in 'Total Loan Applications,' 'Total Funded Amount,' and 'Total Amount Received' over time.
2. **Regional Analysis by State (Filled Map):** Visually represented lending metrics categorized by state to identify regions with significant lending activity.
3. **Loan Term Analysis (Donut Chart):** Depicted loan statistics based on different loan terms to understand the distribution of loans across various term lengths.
4. **Employee Length Analysis (Bar Chart):** Illustrated how lending metrics are distributed among borrowers with different employment lengths.
5. **Loan Purpose Breakdown (Bar Chart):** Provided a visual breakdown of loan metrics based on stated loan purposes.
6. **Home Ownership Analysis (Tree Map):** Displayed loan metrics categorized by different home ownership statuses to understand their impact on loan applications and disbursements.

These diverse chart types enhance our ability to visualize and communicate loan-related insights effectively.

## Dashboard 3: Details

### Objective
In Dashboard 3, titled "Details," I have developed a comprehensive 'Details Dashboard' to provide a consolidated view of all essential loan-related information.

### Dataset
Used SQL queries to cross-verify results and Excel to create the dashboard components, ensuring accuracy and reliability of the data presented.


## Total Summary Using SQL: -
select
	loan_status,
	COUNT(id) AS Total_Loan_Applications,
	SUM(total_payment) as Total_amt_received,
	SUM(loan_amount) as Total_funded_amt,
	AVG(int_rate * 100) as Interest_rate,
	AVG(dti * 100) as Debt_to_Income
	From bank_loan_data GROUP BY loan_status




 ![image](https://github.com/rahulmaurya255/Bank-Loan-Credit-Risk-Analysis/assets/155320538/e7f09378-71cb-4571-875a-742ada6d2061)



 




## Month to Date Total Summary: -
select
	loan_status,
	COUNT(id) AS Total_Loan_Applications,
	SUM(total_payment) as Total_amt_received,
	SUM(loan_amount) as Total_funded_amt,
	AVG(int_rate * 100) as Interest_rate,
	AVG(dti * 100) as Debt_to_Income
From 
	bank_loan_data 
WHERE 
	YEAR(issue_date) = (Select MAX(YEAR(issue_date)) from bank_loan_data) AND
	MONTH(issue_date)=(Select MAX(Month(issue_date)) from bank_loan_data)
GROUP BY 
	loan_status







![image](https://github.com/rahulmaurya255/Bank-Loan-Credit-Risk-Analysis/assets/155320538/7e60e258-6b48-4fd5-97c5-2a0d605995bc)







 


## Month To date Total funded Amount
Select SUM(loan_amount) as MTD_Total_funded_amt from bank_loan_data
WHERE YEAR(issue_date) = (SELECT MAX(YEAR(issue_date)) FROM bank_loan_data)
AND MONTH(issue_date) = (SELECT MAX(MONTH(issue_date)) FROM bank_loan_data)




![image](https://github.com/rahulmaurya255/Bank-Loan-Credit-Risk-Analysis/assets/155320538/0bafeb6c-9f56-45de-a297-ffe4a15670c5)







## Monthly Trends: - 
SELECT
	MONTH(issue_date) as "Month_No.",
	DATENAME(MONTH, issue_date) AS Month_name,
	COUNT(id) AS Total_loan_applications,
	SUM(loan_amount) as Total_funded_amt,
	SUM(total_payment) as Total_received_amt
FROM 
	bank_loan_data
GROUP BY 
	DATENAME(MONTH, issue_date),MONTH(issue_date)
ORDER BY 
	MONTH(issue_date)






 ![image](https://github.com/rahulmaurya255/Bank-Loan-Credit-Risk-Analysis/assets/155320538/eac556a2-53a4-4ec7-a4af-00501a584d98)


















The primary objective of this Details Dashboard is to offer a comprehensive and user-friendly interface for accessing vital loan data, facilitating efficient analysis and decision-making.

## Conclusion

Through these Excel Dashboards, Aim to empower team with valuable insights into bank's lending operations, enabling to make informed decisions, track loan performance, and optimize our lending strategies for continued success.
