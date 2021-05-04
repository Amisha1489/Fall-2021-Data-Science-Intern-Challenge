# Fall-2021-Data-Science-Intern-Challenge
Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

## Please check the following link for the code: 
https://github.com/Amisha1489/Fall-2021-Data-Science-Intern-Challenge/blob/main/Question1.ipynb

a.	Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
After looking into the data set, I found out that there possible outliers makes the value of AOV very high. These outliers are consist of two kinds of data.
1. For user_id – 607, there are 17 orders and each order consists of 2000 units. 
2. shop_id – 78 has priced its shoe at $25,725. For the same metric I would either remove these outliers data and recalculate AOV with the remaining data set and that value turns out be $302.52 or we can calculate the median for the same metric as it turns out that 75% of data falls below 390 as shown in the output from the code.

b.	What metric would you report for this dataset?
I would calculate the median on the column order_amount

c.	What is its value?
$284

Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

### a.	How many orders were shipped by Speedy Express in total?

Query - SELECT count(ShipperID) FROM orders WHERE ShipperID in (SELECT ShipperID FROM Shippers WHERE ShipperName = "Speedy Express")
### Answer – 54

### b.	What is the last name of the employee with the most orders?

Query - SELECT LastName FROM Employees where EmployeeID in (SELECT EmployeeID from Orders group By EmployeeID order by count(OrderID) desc limit 1)
### Answer – Peacock

### c.	What product was ordered the most by customers in Germany?

Query – SELECT ProductName FROM Products WHERE ProductID in (SELECT ProductID FROM OrderDetails WHERE OrderID in (SELECT OrderID FROM Orders WHERE CustomerID in (SELECT CustomerID FROM Customers WHERE Country = "Germany")) GROUP BY ProductID ORDER BY sum(Quantity) desc LIMIT 1)
### Answer - Boston Crab Meat


