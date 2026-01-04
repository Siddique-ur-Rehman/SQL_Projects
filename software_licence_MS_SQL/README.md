# Software License Management System

A professional relational database project designed to manage an E-commerce platform for digital software licenses. This system handles everything from supplier inventory to customer payments and digital key delivery.

## 📌 Project Overview
The **Software License Management System** is built to solve the complexities of selling digital products. Unlike physical goods, software requires tracking license durations (monthly vs. yearly), expiry dates, and unique activation keys.

### Core Features:
* **Inventory Management:** Track software versions, stock levels, and pricing.
* **Licensing Logic:** Supports various types including Trial, Annual, and Lifetime access.
* **Order Workflow:** Full automation of orders, from "Pending" status to "Paid" and "Completed."
* **Secure Payments:** Logs transaction methods (Credit Card, Bank Transfer, JazzCash, etc.).
* **Digital Delivery:** Automates the storage and issuance of unique license keys.


## 📊 System Design

### 1. Data Flow (DFD)
The system acts as a bridge between **Suppliers** (who provide the software) and **Customers** (who purchase licenses). The flow ensures that once a payment is confirmed, a license key is automatically assigned to the customer's order.

### 2. Database Schema (ERD)
The database is highly organized to prevent data duplication (Normalization). Key tables include:
* **Customer & Supplier:** Stores contact details for buyers and vendors.
* **Product & ProductSKU:** Separates the general product (e.g., Windows 11) from the specific sale item (e.g., Windows 11 Pro - 1 Year).
* **Orders & Order_Item:** Manages the shopping cart and final sales.
* **LicenceDelivery:** The final step where keys are issued and expiry dates are calculated.



## 🛠️ Tech Stack & Tools
* **Database:** MySQL
* **Server Environment:** XAMPP (Apache + MySQL)
* **Management Tool:** phpMyAdmin
* **Diagrams:** ERD and DFD models for system architecture.


## 🚀 Getting Started with XAMPP

### 1. Database Setup
1. Open the **XAMPP Control Panel** and start **Apache** and **MySQL**.
2. Click the **Admin** button next to MySQL to open **phpMyAdmin** in your browser.
3. Click on the **New** tab in the left sidebar and create a database named:
   `Software_licences_EMS`

### 2. Creating Tables
1. Select the `Software_licences_EMS` database.
2. Click on the **SQL** tab.
3. Copy and paste the `CREATE TABLE` scripts provided in this repository and click **Go**.

### 3. Inserting Sample Data
1. Go back to the **SQL** tab.
2. Copy and paste the `INSERT INTO` scripts to populate the system with sample products (MS Office, Norton, Adobe, etc.) and click **Go**.

## 📝 Example Query
To see which customers have purchased which software and their assigned license keys, run this in the SQL tab:
```sql
SELECT c.CustomerID,c.Cst_Name,c.Cst_email,o.Order_ID,o.Order_Date,o.Ordr_Total_Amount,o.Ordr_Status
FROM customer c
INNER JOIN orders o
ON c.CustomerID=o.CustomerID;


SELECT i.Order_Item_ID,i.Order_ID,i.Product_sku_ID,
i.Order_Item_Quantity,i.Order_Item_Price,o.CustomerID,o.Order_Date,o.Ordr_Status
FROM order_item i
RIGHT JOIN orders o
ON i.Order_ID=o.Order_ID;
