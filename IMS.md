
# DBMS – PROJECT

## INVENTORY MANAGEMENT SYSTEM

## 1- 
Create Database

### Query
```sql
CREATE DATABASE INVENTORY_MANAGEMENT;
```

## 2- 
Create table Product:

### Query
```sql
CREATE TABLE Product (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    category_id INT,
    supplier_id INT,
    price DECIMAL(10,2),
    quantity INT
);
```

## 3- 
Create table category:

### Query
```sql
CREATE TABLE Category (
    category_id INT PRIMARY KEY,
    category_name VARCHAR(100) NOT NULL
);
```

## 4- 
Create table Supplier:

### Query
```sql
CREATE TABLE Supplier (
    supplier_id INT PRIMARY KEY,
    supplier_name VARCHAR(100) NOT NULL,
    contact VARCHAR(15),
    address VARCHAR(200)
);
```

## 5- 
Create table Customer:

### Query
```sql
CREATE TABLE Customer (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100) NOT NULL,
    phone VARCHAR(15),
    email VARCHAR(100)
);
```

# 6- 
Create table orders:

### Query
```sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10,2)
);
```

# 7- 
Create Table order_details:

### Query
```sql
CREATE TABLE Order_Details (
    order_detail_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    price DECIMAL(10,2)
);
```

# 8- 
Insert into Customer:

### Query
```sql
INSERT INTO Customer VALUES
(1, 'Rahul Sharma', '9999999999', 'rahul@gmail.com'),
(2, 'Priya Singh', '8888888888', 'priya@gmail.com');
```

# 9- 
Insert into Product:

### Query
```sql
INSERT INTO Product VALUES
(1, 'Laptop', 1, 101, 50000, 10),
(2, 'Smartphone', 1, 101, 30000, 15),
(3, 'Rice Bag', 2, 102, 1200, 50),
(4, 'T-Shirt', 3, 103, 800, 40);
```


# 10- 
Insert into Order:

### Query
```sql
INSERT INTO Orders VALUES
(1001, 1, '2026-02-20', 50800),
(1002, 2, '2026-02-21', 30000);
```

# 11- 
Insert into Order_details:

### Query
```sql
INSERT INTO Order_Details VALUES
(1, 1001, 1, 1, 50000),
(2, 1001, 4, 1, 800),
(3, 1002, 2, 1, 30000);
```

# 12- 
Insert into Supplier:

### Query
```sql
INSERT INTO Supplier VALUES
(101, 'TechSupplier', '9876543210', 'Delhi'),
(102, 'FreshFoods Ltd', '9123456780', 'Mumbai'),
(103, 'FashionHub', '9988776655', 'Kolkata');
```

# 13- 
Insert into Category:

### Query
```sql
INSERT INTO Category VALUES
(1, 'Electronics'),
(2, 'Groceries'),
(3, 'Clothing');
```

# 14- 
Display information in all tables:

### Query
```sql
SELECT * FROM Product;
SELECT * FROM Customer;
SELECT * FROM Orders;
SELECT * FROM Supplier;
SELECT * FROM Category;
SELECT * FROM Orders_Details;
```

# 15- 
Adding Cities column in table Customer:

### Query
```sql
ALTER TABLE Customer
ADD Cities VARCHAR(100);
```

# 16- 
Insert into Cities from Customer:

### Query
```sql
UPDATE Customer
SET Cities = CASE
    WHEN customer_id = 1 THEN 'Delhi'
    WHEN customer_id = 2 THEN 'Mumbai'
END;
```

# 17- 
Find names and prices of products costing more than 500.

### Query
```sql
SELECT Name, Price FROM Product WHERE Price > 500;
```

# 18- 
Find products whose stock is between 5 and 20.

### Query
```sql
SELECT * FROM Product WHERE Stock BETWEEN 5 AND 20;
```

# 19- 
Find names of customers from Delhi.

### Query
```sql
SELECT Customer_Name FROM Customer WHERE City = 'Delhi';
```

# 20- 
Find orders placed after 1 Jan 2025.

### Query
```sql
SELECT * FROM Orders WHERE Order_Date >= '2025-01-01';
```

# 21- 
List product names in descending order of price.

### Query
```sql
SELECT Name FROM Product ORDER BY Price DESC;
```

# 22- 
Find all unique cities of customers.

### Query
```sql
SELECT DISTINCT City FROM Customer;
```

# 23- 
Find products whose name starts with ‘S’.

### Query
```sql
SELECT * FROM Product WHERE Name LIKE 'S%';
```

# 24- 
Find products that are out of stock.

### Query
```sql
SELECT * FROM Product WHERE Stock = 0;
```

# 25- 
Find customers whose names contain ‘a’.

### Query
```sql
SELECT * FROM Customer WHERE Customer_Name LIKE '%a%';
```

# 26- 
Display products sorted by stock in ascending order.

### Query
```sql
SELECT * FROM Product ORDER BY Stock ASC;
```

# 27- 
Find total number of products.

### Query
```sql
SELECT COUNT(*) FROM Product;
```

# 28- 
Find total stock available.

### Query
```sql
SELECT SUM(Stock) FROM Product;
```

# 29- 
Find average price of products.

### Query
```sql
SELECT AVG(Price) FROM Product;
```

# 30- 
Find highest priced product.

### Query
```sql
SELECT MAX(Price) FROM Product;
```

# 31- 
Find lowest priced product.

### Query
```sql
SELECT MIN(Price) FROM Product;
```

# 32- 
Count number of products in each category.

### Query
```sql
SELECT Category_ID, COUNT(*) 
FROM Product 
GROUP BY Category_ID;
```

# 33- 
Find number of orders per customer.

### Query
```sql
SELECT Customer_ID, COUNT(Order_ID)
FROM Orders
GROUP BY Customer_ID;
```

# 34- 
Find total quantity sold for each product.

### Query
```sql
SELECT Product_ID, SUM(Quantity)
FROM Order_Details
GROUP BY Product_ID;
```

# 35- 
Find products with total sales quantity greater than 10.

### Query
```sql
SELECT Product_ID, SUM(Quantity)
FROM Order_Details
GROUP BY Product_ID
HAVING SUM(Quantity) > 10;
```

# 36- 
Find average price of products in each category.

### Query
```sql
SELECT Category_ID, AVG(Price)
FROM Product
GROUP BY Category_ID;
```

# 37- 
Display product name with its category name.

### Query
```sql
SELECT p.Name, c.Category_Name
FROM Product p
JOIN Category c ON p.Category_ID = c.Category_ID;
```

# 38- 
Display order ID with customer name.

### Query
```sql
SELECT o.Order_ID, cu.Customer_Name
FROM Orders o
JOIN Customer cu ON o.Customer_ID = cu.Customer_ID;
```

# 39- 
Display order details with product name and quantity.

### Query
```sql
SELECT od.Order_ID, p.Name, od.Quantity
FROM Order_Details od
JOIN Product p ON od.Product_ID = p.Product_ID;
```

# 40- 
Display all customers and their orders (if any).

### Query
```sql
SELECT cu.Customer_Name, o.Order_ID
FROM Customer cu
LEFT JOIN Orders o ON cu.Customer_ID = o.Customer_ID;
```

# 41- 
Display all products and their ordered quantities (if any).

### Query
```sql
SELECT p.Name, od.Quantity
FROM Product p
LEFT JOIN Order_Details od ON p.Product_ID = od.Product_ID;
```

# 42- 
Display order ID, product name, and quantity.

### Query
```sql
SELECT o.Order_ID, p.Name, od.Quantity
FROM Orders o
JOIN Order_Details od ON o.Order_ID = od.Order_ID
JOIN Product p ON od.Product_ID = p.Product_ID;
```

# 43- 
Display customer name and products purchased.

### Query
```sql
SELECT cu.Customer_Name, p.Name
FROM Customer cu
JOIN Orders o ON cu.Customer_ID = o.Customer_ID
JOIN Order_Details od ON o.Order_ID = od.Order_ID
JOIN Product p ON od.Product_ID = p.Product_ID;
```

# 44- 
Display category name with number of products.

### Query
```sql
SELECT c.Category_Name, COUNT(p.Product_ID)
FROM Category c
LEFT JOIN Product p ON c.Category_ID = p.Category_ID
GROUP BY c.Category_ID;
```

# 45- 
Find products priced above average price.

### Query
```sql
SELECT Name 
FROM Product 
WHERE Price > (SELECT AVG(Price) FROM Product);
```

# 46- 
Find the most expensive product.

### Query
```sql
SELECT Name 
FROM Product 
WHERE Price = (SELECT MAX(Price) FROM Product);
```

# 47- 
Find the cheapest product.

### Query
```sql
SELECT Name 
FROM Product 
WHERE Price = (SELECT MIN(Price) FROM Product);
```

# 48- 
Find customers who have placed orders.

### Query
```sql
SELECT Customer_Name 
FROM Customer 
WHERE Customer_ID IN (SELECT Customer_ID FROM Orders);
```

# 49- 
Find orders placed by customer ‘Rahul’.

### Query
```sql
SELECT * 
FROM Orders 
WHERE Customer_ID = (
    SELECT Customer_ID 
    FROM Customer 
    WHERE Customer_Name = 'Rahul'
);
```

# 50- 
Display product name with total quantity sold.

### Query
```sql
SELECT p.Name, SUM(od.Quantity)
FROM Product p
JOIN Order_Details od ON p.Product_ID = od.Product_ID
GROUP BY p.Product_ID;
```









