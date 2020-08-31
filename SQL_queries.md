## Question 2
#### a)How many orders were shipped by Speedy Express in total?

Query: 

SELECT COUNT(DISTiNCT OrderID) FROM Orders o
JOIN Shippers s
ON o.ShipperID = s.ShipperID
WHERE s.ShipperName = 'Speedy Express';

Answer:

54

#### b) What is the last name of the employee with the most orders?

Query: 

SELECT LastName FROM Employees 
WHERE EmployeeID = 
  (SELECT EmployeeID from ORDERS
  GROUP BY EmployeeID
  ORDER BY COUNT(OrderID) DESC
  LIMIT 1);

Answer:

Peacock

#### c) What product was ordered the most by customers in Germany?

Query:

SELECT ProductName FROM Products
WHERE ProductID = 

  (SELECT ProductID FROM OrderDetails 
  WHERE OrderID IN

    (SELECT OrderID FROM Orders o
    JOIN Customers c
    ON o.CustomerID = c.CustomerID
    WHERE c.Country = 'Germany')

  GROUP BY ProductID
  ORDER BY COUNT(*) DESC
  LIMIT 1);


Answer:

Gorgonzola Telino


^^^^^^
This is the query for which product was included in the most number of orders by German customers- To get the product which was ordered in the greatest quantity by German customers, the query and answer would be:

SELECT ProductName FROM Products
WHERE ProductID = 

  (SELECT ProductID FROM OrderDetails 
  WHERE OrderID IN

    (SELECT OrderID FROM Orders o
    JOIN Customers c
    ON o.CustomerID = c.CustomerID
    WHERE c.Country = 'Germany')

 GROUP BY ProductID
 ORDER BY Quantity DESC
 LIMIT 1);

 Answer: 
 Steeleye Stout