# 🛒 E-Commerce Website (Java, JSP, Servlets, MySQL)

This project is a **Java-based E-Commerce Website** developed using **JSP, Servlets, JDBC, and MySQL**.  
It provides user authentication, product browsing, cart management, and order placement.  
Admins can manage products and view orders via a dashboard.

---

## 🚀 Features
### User Side
- User Registration & Login
- Product Listing & Details
- Add to Cart & Checkout
- Place Orders
- View Order History

### Admin Side
- Admin Dashboard
- Add / Edit / Delete Products
- Manage Orders
- View Registered Users

---

## 🛠️ Tech Stack
- **Frontend:** JSP, HTML, CSS
- **Backend:** Java Servlets (JDK 8+)
- **Database:** MySQL
- **Server:** Apache Tomcat 9/10/11
- **Build Tool:** Eclipse Dynamic Web Project

---

## 📂 Project Structure
ECommerceWebsite/
│── .classpath / .project # Eclipse config files
│── src/main/java/com/ecommerce/ # Java source code
│ ├── dao/ # Data Access Objects
│ │ ├── CartDAO.java
│ │ ├── OrderDAO.java
│ │ ├── ProductDAO.java
│ │ └── UserDAO.java
│ ├── model/ # Entity classes
│ │ ├── Cart.java
│ │ ├── Order.java
│ │ ├── OrderItem.java
│ │ ├── Product.java
│ │ └── User.java
│ ├── servlet/ # Servlets
│ │ ├── CartServlet.java
│ │ ├── CheckoutServlet.java
│ │ ├── DashboardServlet.java
│ │ ├── LoginServlet.java
│ │ ├── LogoutServlet.java
│ │ ├── OrdersServlet.java
│ │ ├── ProductsServlet.java
│ │ └── RegisterServlet.java
│ └── util/ # Utility classes
│ ├── DatabaseConnection.java
│ └── ConnectionTest.java
│── WebContent/ # JSP, CSS, JS, Images
│ ├── index.jsp
│ ├── login.jsp
│ ├── register.jsp
│ ├── products.jsp
│ ├── cart.jsp
│ ├── checkout.jsp
│ ├── dashboard.jsp (admin)
│ └── orders.jsp
│── lib/ # JAR files (MySQL Connector, etc.)

sql
Copy code

---

## ⚙️ Setup Instructions

### 1. Prerequisites
- Install **JDK 8+**
- Install **Apache Tomcat 9/10/11**
- Install **MySQL Server**
- Download **MySQL JDBC Driver** and place in `/lib`

### 2. Database Setup
Run the following SQL:
```sql
CREATE DATABASE ecommerce;

USE ecommerce;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100) UNIQUE,
  password VARCHAR(100),
  role VARCHAR(20) DEFAULT 'user'
);

CREATE TABLE products (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  description TEXT,
  price DECIMAL(10,2),
  stock INT
);

CREATE TABLE orders (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT,
  order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE order_items (
  id INT AUTO_INCREMENT PRIMARY KEY,
  order_id INT,
  product_id INT,
  quantity INT,
  FOREIGN KEY (order_id) REFERENCES orders(id),
  FOREIGN KEY (product_id) REFERENCES products(id)
);
3. Configure Database Connection
Edit DatabaseConnection.java:

java
Copy code
private static final String URL = "jdbc:mysql://localhost:3306/ecommerce";
private static final String USER = "root";
private static final String PASSWORD = "yourpassword";
4. Deploy on Tomcat
Import project into Eclipse as Dynamic Web Project.

Add Tomcat server.

Right-click → Run on Server.

Open browser:

arduino
Copy code
http://localhost:8080/ECommerceWebsite/
👤 Default Login (Optional)
Admin: admin@shop.com / admin123

User: user@test.com / user123

📝 Future Enhancements
Payment Integration (PayPal / Razorpay)

Responsive Frontend (Bootstrap/Tailwind)

REST API endpoints

Advanced Search & Filters

📜 License
This project is for educational purposes only.# E-commerce
