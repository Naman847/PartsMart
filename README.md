# PartsMart

[![PHP](https://img.shields.io/badge/PHP-7.4%2B-blue)](https://www.php.net/) [![MySQL](https://img.shields.io/badge/MySQL-MariaDB-yellow)](https://www.mysql.com/) [![JavaScript](https://img.shields.io/badge/Vanilla%20JS-ES6-green)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

PartsMart is a full-stack e-commerce platform built for selling hardware parts and tools. Developed as a final-year BCA project, it demonstrates core web development skills in backend scripting, database management, and user interface design. The application includes a customer storefront, admin dashboard, and delivery agent portal, with features like product cataloging, shopping cart, secure checkout, and automated PDF invoice generation.

This project showcases practical implementation of e-commerce workflows, including user authentication, inventory management, and basic security practices, while highlighting areas for scalable improvements in a production environment.

## 🚀 Features

- **Customer Storefront**: Browse products with filtering by category, material, and price range; detailed product views with variants (e.g., color, stock, images).
- **Shopping Cart & Checkout**: AJAX-powered cart operations (add/update/remove items); seamless checkout flow with order creation and simulated payment processing.
- **User Management**: Secure signup/login with password hashing; user profiles for order history.
- **Admin Dashboard**: CRUD operations for products, variants, categories, and users; basic reporting tools.
- **Delivery Agent Interface**: Order tracking and status updates for logistics management.
- **PDF Invoice Generation**: Automated invoice creation using the FPDF library.
- **Search & Filtering**: Real-time product search with dynamic filters for an intuitive shopping experience.

## 🛠 Tech Stack

- **Backend**: PHP (procedural with OOP elements), MySQL/MariaDB (via mysqli with prepared statements).
- **Frontend**: HTML5, CSS3, Vanilla JavaScript (ES6+ for interactive elements like cart updates).
- **Libraries**: FPDF (bundled for PDF generation).
- **Database**: Relational schema with tables for products, users, carts, orders, and reviews.
- **Other**: PHP sessions for state management; no external frameworks for lightweight, vanilla implementation.

## 📁 Project Structure

```
PartsMart/
├── config/
│   └── dbConnect.php          # Database connection (update credentials here)
├── admin/                      # Admin dashboard
│   ├── addProduct.php
│   ├── editProduct.php
│   ├── products.php
│   ├── productVariants.php
│   ├── users.php
│   └── dbConnect.php          # Admin-specific DB config
├── client/                     # Customer storefront
│   ├── index.php              # Homepage
│   ├── products.php           # Product listing with filters
│   ├── product-details.php    # Individual product view
│   ├── cart.php               # Shopping cart
│   ├── checkout.php           # Order placement
│   ├── login.php              # User authentication
│   ├── signup.php             # User registration
│   ├── profile.php            # User profile
│   └── generate_invoice.php   # PDF invoice endpoint
├── delivery/                   # Delivery agent portal
│   ├── index.php              # Dashboard
│   └── OrderStatus.php        # Order tracking
├── assets/                     # Static files
│   └── products/              # Product images
├── scripts/                    # Client-side JS
│   ├── addToCart.js
│   └── navbar.js
├── styles/                     # CSS stylesheets
│   ├── navbar.css
│   └── footer.css
└── fpdf/                       # Bundled FPDF library for invoices
```

## 🗄 Database Schema

The application uses a MySQL/MariaDB database with the following key tables (inferred from code queries):

- `product_tbl` & `product_details_tbl`: Product info and variants (price, stock, color, material, images).
- `category_tbl`: Product categories.
- `user_detail_tbl` & `security_questions_tbl`: User accounts and recovery.
- `cart_tbl` & `cart_detail_tbl`: Shopping cart items.
- `order_tbl`, `order_detail_tbl`, & `payment_tbl`: Orders and payments.
- `review_tbl`: Product reviews.

**Note**: No SQL dump is included. Create the database manually or export from your local setup. Example setup script available upon request.

## 🚀 Quick Start (Local Development)

### Prerequisites

- PHP 7.4+ with mysqli extension.
- MySQL/MariaDB 5.7+.
- Web server (Apache/Nginx) or PHP's built-in server.
- Composer (optional, not required for core functionality).

### Setup Steps

1. **Clone the Repository**:

   ```
   git clone https://github.com/yourusername/PartsMart.git
   cd PartsMart
   ```

2. **Database Configuration**:

   - Create a new MySQL database (e.g., `partsmart_db`).
   - Update credentials in `config/dbConnect.php` (host, username, password, database name).
   - (Optional) Mirror updates in `admin/dbConnect.php`.

3. **Initialize Database**:

   - Run the following SQL to create tables (or import a dump if available):
     ```sql
     -- Example: Create product_tbl
     CREATE TABLE product_tbl (
         id INT PRIMARY KEY AUTO_INCREMENT,
         name VARCHAR(255) NOT NULL,
         category_id INT,
         price DECIMAL(10,2),
         -- Add other fields based on code queries
     );
     -- Repeat for other tables: product_details_tbl, category_tbl, etc.
     ```
   - Full schema details can be derived from the codebase queries.

4. **Run the Application**:

   - Start the built-in PHP server:
     ```
     php -S localhost:8000
     ```
   - Access the storefront at `http://localhost:8000/client/index.php`.
   - Admin: `http://localhost:8000/admin/products.php`.
   - Delivery: `http://localhost:8000/delivery/index.php`.

5. **Test Features**:
   - Register a user via `/client/signup.php`.
   - Add products to cart and checkout.
   - Generate an invoice PDF after order placement.

For production, configure a proper web server (e.g., Apache with mod_rewrite) and secure the environment.

## 📄 PDF Invoices

Invoices are generated dynamically using the bundled FPDF library. Triggered post-checkout via `client/generate_invoice.php`, it pulls order details and outputs a downloadable PDF. No additional setup required.

## 🔒 Security Considerations

- **Strengths**: Password hashing (`password_hash`/`password_verify`), prepared statements in key queries, session-based auth.
- **Recommendations**:
  - Parameterize all SQL queries to prevent injection.
  - Validate/sanitize file uploads (images in `assets/products/`).
  - Implement CSRF tokens for forms and HTTPS in production.
  - Use environment variables for DB credentials (e.g., via `.env` file).

## 🔮 Future Enhancements

- Integrate a full SQL schema export for easy setup.
- Add environment-based config (e.g., `.env` support with Dotenv).
- Implement unit tests with PHPUnit for auth, cart, and checkout flows.
- Dockerize for containerized development (PHP + MySQL stack).
- Enhance with modern JS (e.g., Vue.js for dynamic UI) or migrate to a framework like Laravel.

## 📝 Contributing

This project is a showcase of foundational web development skills. Contributions for improvements (e.g., security audits, tests, or schema export) are welcome! Fork the repo, create a feature branch, and submit a pull request.

---

_Built with ❤️ during BCA Final Year Project. Questions? Open an issue or reach out via GitHub._
