# E-Commerce Platform - Complete Documentation

## 📋 Project Overview

**MyStore** is a full-featured enterprise-level e-commerce platform built with Java Servlets, JSP, and MySQL. It provides a comprehensive shopping experience with role-based access for Admins, Sellers, and Buyers.

---

## 👥 Team Members

- **MAYANK SOLANKI**
- **MONU KUMAR**
- **BHUPESH DUBEY**

---

## 🚀 Key Features

### 🔐 User Authentication & Authorization
- Secure registration and login system
- Password hashing using SHA-256
- Role-based access control (Admin, Seller, Buyer)
- Session management with automatic redirection
- Admin registration requires secret key (`SuperSecret123`)

### 👔 Admin Module
- **Dashboard**: View platform statistics (users, products, orders)
- **User Management**: View and delete users
- **Product Management**: Monitor and remove products
- **Order Management**: Update order status and process tracking
- Real-time analytics and metrics

### 🏪 Seller Module
- **Dashboard**: Overview of products and sales
- **Product Management**: CRUD operations on inventory
  - Add new products
  - Edit product details (AJAX-powered)
  - Soft delete products
  - Real-time stock updates
- **Inventory Overview**: Visual stock level monitoring with charts
- **Order History**: Track items sold with detailed breakdowns
- **Sales Performance**: 
  - Monthly sales trends
  - Product-wise analytics
  - Top-selling products

### 🛒 Buyer Module
- **Dashboard**: Personalized shopping experience
- **Product Browsing**: Browse all available products with filters
- **Shopping Cart**: 
  - Add/remove products
  - Update quantities
  - Real-time total calculation
- **Wishlist**: Save favorite products
- **Checkout System**:
  - Shipping address management
  - Multiple payment options (COD, Card, UPI)
  - Order confirmation
- **Order History**: Track past purchases with invoices
- **Profile Management**: Update personal information

---

## 🛠️ Technology Stack

### Backend
- **Java Servlets** (javax.servlet)
- **JDBC** for database operations
- **HikariCP** for connection pooling
- **SHA-256** for password hashing

### Frontend
- **JSP** (JavaServer Pages)
- **JSTL** (JSP Standard Tag Library)
- **Bootstrap 5** for responsive UI
- **jQuery** for AJAX operations
- **Chart.js** for data visualization

### Database
- **MySQL 8.0**

### Build & Server
- **Apache Maven** (optional)
- **Apache Tomcat 9+**

---

## 📦 Installation & Setup

### Prerequisites
- Java JDK 11 or higher
- MySQL 8.0
- Apache Tomcat 9+
- Maven (optional)
- IDE (IntelliJ IDEA / Eclipse recommended)

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd ecommerce-enterprise
```

### Step 2: Database Setup
1. Open MySQL and create the database:
```sql
CREATE DATABASE ecommerce_db;
```

2. Run the schema script:
```bash
mysql -u root -p ecommerce_db < sql/schema.sql
```

### Step 3: Configure Database Connection
Edit `src/main/resources/application.properties`:
```properties
db.url=jdbc:mysql://localhost:3306/ecommerce_db?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
db.user=your_mysql_username
db.pass=your_mysql_password
```

### Step 4: Import Project to IDE

#### For IntelliJ IDEA:
1. File → Open → Select project folder
2. Right-click on `pom.xml` → Maven → Reload Project
3. File → Project Structure → Set JDK to 11+

#### For Eclipse:
1. File → Import → Existing Maven Project
2. Select project folder
3. Right-click project → Maven → Update Project

### Step 5: Configure Tomcat Server

#### IntelliJ IDEA:
1. Run → Edit Configurations → Add New → Tomcat Server → Local
2. Configure Tomcat home directory
3. Deployment → Add → Artifact → Select WAR exploded
4. Set Application context to `/`

#### Eclipse:
1. Window → Preferences → Server → Runtime Environments
2. Add Tomcat 9
3. Right-click project → Run As → Run on Server

### Step 6: Run the Application
1. Start Tomcat server
2. Open browser and navigate to:
```
http://localhost:8080/ecommerce-enterprise/
```

---

## 🎯 User Roles & Access

### Admin Access
- **URL**: `/admin/dashboard`
- **Registration**: Requires secret key `SuperSecret123`
- **Default Credentials**: Register manually with admin role

### Seller Access
- **URL**: `/seller/dashboard`
- **Registration**: Select "Seller" role during signup
- **Features**: Product and inventory management

### Buyer Access
- **URL**: `/buyer/dashboard`
- **Registration**: Select "Buyer" role during signup
- **Features**: Shopping, cart, orders, wishlist

---

## 📁 Project Structure
```
ecommerce-enterprise/
├── sql/
│   ├── schema.sql              # Database schema
│   └── seed.sql                # Sample data (optional)
├── src/main/
│   ├── java/com/ecomm/
│   │   ├── dao/                # Data Access Objects
│   │   │   ├── CartDAO.java
│   │   │   ├── DBPool.java
│   │   │   ├── OrderDAO.java
│   │   │   ├── ProductDAO.java
│   │   │   ├── UserDAO.java
│   │   │   └── WishlistDAO.java
│   │   ├── filter/             # Servlet Filters
│   │   │   └── AuthFilter.java
│   │   ├── model/              # Domain Models
│   │   │   ├── CartItem.java
│   │   │   ├── Order.java
│   │   │   ├── Product.java
│   │   │   └── User.java
│   │   ├── servlet/            # Servlets
│   │   │   ├── AdminServlet.java
│   │   │   ├── AuthServlet.java
│   │   │   ├── BuyerServlet.java
│   │   │   ├── CartServlet.java
│   │   │   ├── CheckoutServlet.java
│   │   │   ├── OrderServlet.java
│   │   │   ├── PaymentServlet.java
│   │   │   ├── ProductServlet.java
│   │   │   ├── RegisterServlet.java
│   │   │   └── SellerServlet.java
│   │   └── util/
│   │       └── PasswordUtil.java
│   ├── resources/
│   │   └── application.properties
│   └── webapp/
│       ├── WEB-INF/
│       │   ├── jsp/            # JSP Pages
│       │   │   ├── admin/
│       │   │   ├── buyer/
│       │   │   ├── order/
│       │   │   ├── product/
│       │   │   └── seller/
│       │   └── web.xml
│       ├── index.jsp
│       ├── login.jsp
│       └── register.jsp
├── pom.xml
└── README.md
```

---

## 🔑 Key Functionalities

### Product Management
- CRUD operations with soft delete
- Stock management with low-stock alerts
- Real-time updates using AJAX
- Image support (default placeholder)

### Order Processing
- Multi-step checkout flow
- Address management
- Payment integration (COD, Card, UPI)
- Order status tracking
- Invoice generation

### Shopping Cart
- Session-based cart storage
- Quantity updates
- Real-time price calculation
- Cart persistence across sessions

### Analytics & Reports
- Sales performance metrics
- Monthly sales trends (Chart.js)
- Product-wise analytics
- Inventory statistics

---

## 🔒 Security Features

- **Password Hashing**: SHA-256 encryption
- **Role-Based Access Control**: Filter-based authorization
- **Session Management**: Secure session handling
- **SQL Injection Prevention**: Prepared statements
- **Admin Protection**: Secret key requirement

---

## 🎨 UI/UX Features

- Fully responsive design (Bootstrap 5)
- Modern gradient hero sections
- Interactive charts and graphs
- Modal-based product editing
- Toast notifications for actions
- Smooth animations and transitions

---

## 🐛 Troubleshooting

### Common Issues

**1. Database Connection Failed**
- Verify MySQL is running
- Check credentials in `application.properties`
- Ensure database exists

**2. Port Already in Use**
- Change Tomcat port in `server.xml`
- Or stop conflicting service

**3. ClassNotFoundException**
- Run `mvn clean install`
- Reload Maven dependencies

**4. 404 Error on Pages**
- Check servlet mappings in annotations
- Verify context path configuration

---

## 📄 API Endpoints

### Authentication
- `POST /login` - User login
- `POST /register` - User registration
- `GET /logout` - User logout

### Admin
- `GET /admin/dashboard` - Admin dashboard
- `GET /admin/users` - Manage users
- `GET /admin/products` - Manage products
- `GET /admin/orders` - Manage orders
- `POST /admin/*/action` - CRUD operations

### Seller
- `GET /seller/dashboard` - Seller dashboard
- `GET /seller/products` - Product inventory
- `POST /product/action` - Add/Edit/Delete products
- `GET /seller/orders` - Sales history
- `GET /seller/salesPerformance` - Analytics

### Buyer
- `GET /buyer/dashboard` - Buyer dashboard
- `GET /product/list` - Browse products
- `POST /cart/add` - Add to cart
- `POST /cart/remove` - Remove from cart
- `GET /order/Checkout` - Checkout page
- `POST /order/payment` - Process payment
- `GET /order/history` - Order history
- `GET /order/invoice?id={orderId}` - View invoice

---

## 🚀 Future Enhancements

- [ ] Email notifications
- [ ] Product reviews and ratings
- [ ] Advanced search and filters
- [ ] Payment gateway integration (Razorpay, Stripe)
- [ ] Multi-language support
- [ ] Product image upload
- [ ] Coupon and discount system
- [ ] Real-time chat support

---

## 📞 Support

For issues or questions:
- Create an issue in the repository
- Contact: support@mystore.com

---

## 📝 License

This project is licensed under the MIT License.

---

## 🙏 Acknowledgments

- Bootstrap team for UI framework
- Apache Tomcat community
- MySQL development team
- All contributors and testers

---

**Built with ❤️ by Team MyStore**
