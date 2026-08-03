# Employee Attrition Dashboard for HR Analysis

## Introduction
One of the major problem Business or any Organization from any industry face is the Employee Attrition. It cost them huge in terms of monitory values over a period of time. Through this 2 page automated HR Dashboard I tried to help the HR department of the organization to monitor and analyze the attrition issue the organization facing and ways to resolve it, over a dataset of around 1500 employees.

## Questions to Be Answered
- What is the overall attrition rate?
- Which departments are losing the most people?
- Is there a relationship between pay, age, and the decision to leave?

## Deliverables
A fully automatic, governed and secured dashboard.

## Dashboard Overview
<img width="1909" height="822" alt="image" src="https://github.com/user-attachments/assets/ef5d49ba-ff6a-4c18-83d6-db4706a4bec2" />
<img width="1910" height="819" alt="image" src="https://github.com/user-attachments/assets/f424ff89-e279-4d01-9248-84283069b5e0" />

## Live Dashboard
- Dashboard App Link : https://app.fabric.microsoft.com/Redirect?action=OpenReport&appId=dd5f001b-7f1f-48a4-a6c8-94630be5d62b&reportObjectId=922fd4f3-769e-4493-bc58-4b3d3ac6d0c3&ctid=68925209-7378-4959-87b9-88ea918ae4e0&reportPage=90745bee0a00a7831092&pbi_source=appShareLink&portalSessionId=3ad205d6-25f5-44ab-bdf3-32ec54bae17f
- Dashboard Link : https://app.fabric.microsoft.com/links/D9bW6U3op5?ctid=68925209-7378-4959-87b9-88ea918ae4e0&pbi_source=linkShare

⚠ To access the live dashboard you should have a Microsoft Account and need to get authorize. To view it you can view the dashboard from attached screenshot, uploaded .pdf version or the .pbix version. 

## Approach
As per the business requirement we have a set of questions need to answer through the dashboard. Along with the analysis needed to be done what parameter affecting the attrition. 

### Data Ignition: 
I have pulled the employee data from a HTTP Source and ignite it into a Dataflow Gen 2 to do further cleaning. 

### Dataflow Gen 2 and why?
The dashboard will be used by HR Team. I'm assuming that the team is efficient in Power Bi, SQL, Excel. But may not be efficient in technical tools like python, pyspark, handling pipeline. In Fabric Dataflow Gen 2 gives us a opportunity to explore the same tools like Microsoft Excel Power Query, though which team can clean the dataset, remove any unnecessary data, remove nulls, fix duplicates, set the data types of each columns and add any calculated columns efficiently for better dashboarding. Also for small dataset it will help to reduce cost by removing the use of un-necessary tools. 

Here we added two calculated columns based on existing data. 
- Age Group : To determine and idnetify the people from which Age Group is leaving the company most
- Salary Band : Rather than analyzing people from indivisual salary, I have put the people in seperate band and analyzed afterwards

Transformation: 
Changed the data type of the created Calculated Columns from number-text to text only for better sagrigration. 

Then we stored this data in lakehouse as a Delta Table.

Dataflow Gen 2 screenshot
<img width="1855" height="881" alt="image" src="https://github.com/user-attachments/assets/1f25da47-91a0-4bc1-9765-fdead9b237a3" />

### Lakehouse
After data transformation in Dataflow Gen 2 I had stored the data in Lakehouse, and after analyzing and verifying the data in SQL end points, created a Semantic Model to create dashboard. As we have small dataset I had skipped the Data Modelling phase. Created the dashboard in Power Bi on the Flat Table. 

In side Lakehouse I have managed the OneLake security to hide critical data like employee salary. 

<img width="1823" height="816" alt="image" src="https://github.com/user-attachments/assets/02b888fa-3ee5-400e-9433-ce95cd587554" />


### Semantic Model
Created the Semantic Model from Lakehouse and created a blank dashboard in Fabric on top of that Semantic Model. Then downloaded the dashboard and edited that dashboard to build the HR Attrition Dashboard in DirectLake mode, to auto refresh data and minimize query running time. 

Upon completion the dashboard Published the dashboard in my Work-Space in Fabric. Then created a App from Fabric and Published. 

### Outcomes
After Analyzing the dataset these are the Final Outcomes:
- The Organization's Attrition Rate is 16.1%, where average Industry Attrition rate in 10 to 15%
- Employees from Sales department has highest Attrition Rate of 20.6%
- Employees with 3K and Less Salary are most to leave the company 28.6%
- Employees from 18 to 25 Age has the most Attrition 35.8%
- People with Overtime has the Highest Attrition 30.5%
- People who are traveling frequently for Company are leaving company with a rate of 25.5%
- So yes there is a direct relation of these factors on the Attrition of the Organization

### Resolution
- It is found that people in Sales doing most of the Overtime and Single Handedly reaching the attrition to 37.5%. So need to revise the work schedule
- ALso most people in Sales are leaving as they have salary 3K and less. Need to restructure the salary composition.
- From Sales most people are Sales Representative and Sales Executive and falls under 3K to 10K range. Need restructure it as per industry compenstaion standerd.
- Need to arrange Hybrid or WFH work structure and need to reduce the travel requirement where it is required. 



 
