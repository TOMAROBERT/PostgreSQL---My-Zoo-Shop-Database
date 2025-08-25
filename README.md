# PostgreSQL---My-Zoo-Shop-Database


Relational database design for a retail store specializing in pet supplies, live animals, and related services.  
This project was developed as part of an EPAM learning exercise.

---

## 📌 Overview
The **Zoo Shop database** is designed to manage daily operations of a shop that sells products (food, toys, accessories, animals) and provides services (e.g. grooming, consultations).  
It integrates **customers, employees, suppliers, products, orders and order items** to ensure:

- Smooth **inventory management**
- Seamless **order processing** (online & in-store)
- Effective **customer engagement**
- Support for **reporting & analytics**

---

## 🗂️ Entities

### 🐶 Product
- **Product_ID** (PK)  
- Name, Category, Price, Quantity_in_Stock, Description  
- **Supplier_ID** (FK → Supplier)

### 🛒 Order
- **Order_ID** (PK)  
- Date_and_Time, Total_Amount, Order_Status, Discount_Applied  
- **Customer_ID** (FK → Customer)  
- **Employee_ID** (FK → Employee)

### 📦 Order Item
- **Order_Item_ID** (PK)  
- **Order_ID** (FK → Order)  
- **Product_ID** (FK → Product)  
- Quantity, Subtotal  

### 👤 Customer
- **Customer_ID** (PK)  
- Full_Name, Phone_Number, Email, Address, Membership_Status  

### 🧑‍💼 Employee
- **Employee_ID** (PK)  
- Name, Position, Phone_Number, Email  

### 🚚 Supplier
- **Supplier_ID** (PK)  
- Name, Contact_Information, Address  

---

## 🔗 Relationships

- **Supplier (1) → (N) Product**  
- **Customer (1) → (N) Order**  
- **Employee (1) → (N) Order** (nullable, `ON DELETE SET NULL`)  
- **Order (1) → (N) Order_Item**  
- **Product (1) → (N) Order_Item**  

Many-to-Many between **Products** and **Orders** is resolved through **Order_Item**.

---

## ✅ Normalization
- Database normalized to **3rd Normal Form (3NF)**:
  - Atomic attributes only
  - No partial dependencies
  - No transitive dependencies

---

## 📊 Operations Supported

### For Customers:
- Place, view, cancel orders  
- Browse products by category, price, availability  
- Manage membership levels (Basic, Premium)  

### For Employees:
- Update order status, process returns  
- Update inventory stock  
- Generate performance & sales reports  

### For Administrators:
- Employee performance reports  
- Revenue analysis by product category, time period, employee  
- Customer insights for promotions  

---

## 📐 Diagrams
- ERD designed in **dbdiagram.io**  
- Export available in PDF and DBML  

<img width="1391" height="696" alt="2025-08-25_15h44_47" src="https://github.com/user-attachments/assets/799cb4c4-89cd-4900-86a1-904b5cf30c94" />


<img width="1397" height="714" alt="2025-08-25_15h44_52" src="https://github.com/user-attachments/assets/9aa890b4-fc08-4047-8e7d-6e75554c689f" />


---

## ⚙️ Tech Notes
- Designed for **PostgreSQL 13+**  
- Monetary values use `NUMERIC(12,2)`  
- Constraints ensure data integrity (positive values, unique emails)  

---

