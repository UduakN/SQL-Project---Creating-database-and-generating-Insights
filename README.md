# SQL-Project---Creating-database-and-generating-Insights

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/5117464b-48db-4dcc-86b5-61ccd99bac7d)


In this project, I created company_ltd database. The database created was used to identify trends, give insights and solutions to the company. MySQL workbench was used for this project.


Company_ltd database consists of salestable, customertable and stafftable.
 
I created company_ltd database using CREATE DATABASE company_ltd. I proceeded to create each table and its content.[company_ltd database.txt](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/files/11682669/company_ltd.database.txt)


![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/633c96e9-2d01-409c-ac70-3cbb39f43457)

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/3961baed-2fdb-4710-b4ac-52e3da11ece5)

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/fdf096dd-dd89-4e3e-84de-fae658a1eba4)

 
 # Below company questions were asked for more insights to the database

USE company_ltd;

# 1.) How many staff do we have in the company?

SELECT COUNT(DISTINCT MatriculeNo) AS Number_of_Staff
from stafftable ;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/4175be3b-8fd0-4a2c-bce4-112d6d114801)


# 2.) How many staff are younger than 30 years?

SELECT COUNT(DISTINCT MatriculeNo) AS Staff_Below_30
from stafftable
where Age < 30;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/7bd17f57-d3f4-4c7a-81c9-b33e48d1e3ee)

# 3.) How many staff are between 30 and 25 years?

SELECT COUNT(DISTINCT MatriculeNo) AS Staff_Between_25_and_30 
from stafftable
where Age between 25 and 30;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/9d9d9bb0-c4bf-47d8-864f-9c76eb22688f)


# 4.) Select all the female staff and sort their age in descending order (from the oldest to the youngest)

SELECT *  
FROM stafftable
WHERE StaffSex = 'Female'
ORDER BY Age desc;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/31829998-f6a5-4b1c-98bb-5fb6e4d6b3a7)


# 5.) What is the Average age of Peter and Nina?

SELECT avg(Age) AS Average_Age
FROM stafftable
WHERE StaffName IN ('Peter', 'Nina')
;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/eca047c9-43d8-4633-a6fa-6e1ac30a2065)


# 6.) How many customers do we have?

SELECT COUNT(DISTINCT CustomerCode) AS Number_of_Customers
FROM customertable ;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/a2b20b53-0f0b-4326-8311-3ee84abafd5f)


# 7.) How many customers are from Cameroon?
SELECT COUNT(DISTINCT CustomerCode) AS Number_of_Cameroon_Customers
FROM customertable
WHERE CustomerCountry = 'Cameroon';

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/1e9a4467-3d25-4df7-ac74-49a2a15b1738)


# 8.) How many customers are from Cameroon and are Males?

SELECT COUNT(DISTINCT CustomerCode) AS Male_Cameroon_Customers
FROM customertable
WHERE CustomerCountry = 'Cameroon' AND CustomerSex = 'Male';

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/4b6073c7-3906-4cbf-889e-caee2b3034cf)


# 9.) What are the First names and Last names of customers who come from Togo and USA?

SELECT CustomerFirstName, CustomerLastName
FROM customertable
WHERE CustomerCountry IN ('Togo','USA') ;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/71315dec-2844-48d5-9960-0b923500b666)


# 10. Show the first 5 oldest customers and arrange the list in decreasing order of Age (Oldest to youngest)

SELECT *
FROM customertable
ORDER BY Age DESC
LIMIT 5;


![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/2fd5c0c4-e83b-4b33-b9bd-d25c47a538d1)


# 11.) What is the average age of customers per country
SELECT CustomerCountry, AVG(Age) AS AverageAge
FROM customertable
GROUP BY CustomerCountry;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/3800638f-e777-463d-a9c1-9b90b04b6e0a)

# 12.) What is the total profit made?

SELECT SUM(Profit) AS TotalProfit
FROM salestable;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/fdc691ae-1a7c-43bd-8161-cca595686140)


# 13.) What is the total cost incurred for these 03 countries "Cameroon","USA","Togo"?

SELECT CustomerCountry, SUM(Cost) AS TotalCost
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
GROUP BY CustomerCountry;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/26a9719e-2f55-4c05-8837-ff495ae72ed2)


# 14.) What is the total profit made per country?
SELECT CustomerCountry, SUM(Profit) AS TotalProfit
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
GROUP BY CustomerCountry;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/b1f02111-f0f1-481b-9ad6-d3329531a09e)


# 15.) What is the average profit made per country?
SELECT CustomerCountry, AVG(Profit) AS AverageProfit
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
GROUP BY CustomerCountry;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/bc31f22e-15a5-473b-aa5c-a3d627e6bd6a)


# 16.) What is the total revenue per Staff?
SELECT StaffName, SUM(Revenue) AS TotalRevenue
FROM stafftable
JOIN salestable
ON stafftable.MatriculeNo = salestable.StaffCode
GROUP BY StaffName;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/546ceb1a-23e1-47d1-a85a-2edeac4cb3ad)


# 17.) Which countries made more than 100 sales transactions? Sort them in decreasing order (from biggest to smallest)

SELECT CustomerCountry, UnitsSold
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
WHERE UnitsSold > 100
ORDER BY UnitsSold DESC;

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/ebca6f74-8f9d-4fc5-a4c5-6a1488cd7c5e)


# 18.) What is the total profit made per country by the following staff "Emelda","Anita","Cynthia"?

SELECT CustomerCountry, SUM(Profit) AS TotalProfit
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
JOIN stafftable
ON stafftable.MatriculeNo = salestable.StaffCode
WHERE StaffName IN ('Emelda','Anita','Cynthia')
GROUP BY CustomerCountry;


 ![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/a0486486-28d9-4569-8345-27b205fe641c)

