# SQL-Project---Creating-database-and-generating-Insights

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/5117464b-48db-4dcc-86b5-61ccd99bac7d)

In this project, I created company_ltd database. The database created was used to identify trends, give insights and solutions to the company. MySQL workbench was used for this project.

Company_ltd database consists of salestable, customertable and stafftable.
 
I created company_ltd database using CREATE DATABASE company_ltd. I proceeded to create each table and its content. 

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/633c96e9-2d01-409c-ac70-3cbb39f43457)

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/3961baed-2fdb-4710-b4ac-52e3da11ece5)

![image](https://github.com/UduakN/SQL-Project---Creating-database-and-generating-Insights/assets/128192166/fdf096dd-dd89-4e3e-84de-fae658a1eba4)

 
 Below company questions were asked for more insights to the database

USE company_ltd;

/* How many staff do we have in the company? */

SELECT count(distinct MatriculeNo) AS Number_of_Staff
from stafftable ;

/* How many staff are younger than 30 years?*/

SELECT count(distinct MatriculeNo) AS Staff_Below_30
from stafftable
where Age < 30;

# 3.) How many staff are between 30 and 25 years?
select count(distinct MatriculeNo) AS Staff_Between_25_and_30 
from stafftable
where Age between 25 and 30;

# 4.) Select all the female staff and sort their age in descending order (from the oldest to the youngest)

select *  
from stafftable
where StaffSex = 'Female'
order by Age desc;

# 5.) What is the Average age of Peter and Nina?

SELECT avg(Age) AS Average_Age
FROM stafftable
WHERE StaffName IN ('Peter', 'Nina')
;

# 6.) How many customers do we have?

SELECT COUNT(DISTINCT CustomerCode) AS Number_of_Customers
FROM customertable ;

# 7.) How many customers are from Cameroon?
SELECT COUNT(DISTINCT CustomerCode) AS Number_of_Cameroon_Customers
FROM customertable
WHERE CustomerCountry = 'Cameroon';

# 8.) How many customers are from Cameroon and are Males?

SELECT COUNT(DISTINCT CustomerCode) AS Male_Cameroon_Customers
FROM customertable
WHERE CustomerCountry = 'Cameroon' AND CustomerSex = 'Male';

# 9.) What are the First names and Last names of customers who come from Togo and USA?

SELECT CustomerFirstName, CustomerLastName
FROM customertable
WHERE CustomerCountry IN ('Togo','USA') ;

# 10. Show the first 5 oldest customers and arrange the list in decreasing order of Age (Oldest to youngest)

SELECT *
FROM customertable
ORDER BY Age DESC
LIMIT 5;

# 11.) What is the average age of customers per country
SELECT CustomerCountry, AVG(Age) AS AverageAge
FROM customertable
GROUP BY CustomerCountry;

# 12.) What is the total profit made?

SELECT SUM(Profit) AS TotalProfit
FROM salestable;

# 13.) What is the total cost incurred for these 03 countries "Cameroon","USA","Togo"?

SELECT CustomerCountry, SUM(Cost) AS TotalCost
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
GROUP BY CustomerCountry;

# 14.) What is the total profit made per country?
SELECT CustomerCountry, SUM(Profit) AS TotalProfit
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
GROUP BY CustomerCountry;

# 15.) What is the average profit made per country?
SELECT CustomerCountry, AVG(Profit) AS AverageProfit
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
GROUP BY CustomerCountry;

# 16.) What is the total revenue per Staff?
SELECT StaffName, SUM(Revenue) AS TotalRevenue
FROM stafftable
JOIN salestable
ON stafftable.MatriculeNo = salestable.StaffCode
GROUP BY StaffName;

# 17.) Which countries made more than 100 sales transactions? Sort them in decreasing order (from biggest to smallest)

SELECT CustomerCountry, UnitsSold
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
WHERE UnitsSold > 100
ORDER BY UnitsSold DESC;

# 18.) What is the total profit made per country by the following staff "Emelda","Anita","Cynthia"?

SELECT CustomerCountry, SUM(Profit) AS TotalProfit
FROM customertable
JOIN salestable
ON customertable.CustomerCode = salestable.CustomerCode
JOIN stafftable
ON stafftable.MatriculeNo = salestable.StaffCode
WHERE StaffName IN ('Emelda','Anita','Cynthia')
GROUP BY CustomerCountry;


 
