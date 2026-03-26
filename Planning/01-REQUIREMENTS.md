# System Requirements

## User Types
1. **Administrator**  
   - Manage users
   - Manage product listings
   - View reports

2. **Customer**  
   - View products
   - Add products to cart
   - Place orders
   - Manage orders

3. **Vendor**  
   - Manage own product listings
   - View orders related to own products

## Functional Requirements
### User Management  
- Administrators can create, read, update, and delete user accounts.  
- Users can register, log in, and reset passwords.  

### Product Management  
- Administrators can add, update, or remove products.  
- Vendors can manage their own products without administrative intervention.  

### Shopping Cart  
- Customers can add products to a shopping cart and modify quantities.  
- Customers can checkout and make payments using various methods (Credit Card, PayPal, etc.).  

### Order Management  
- Customers can view their order history.  
- Administrators can view all orders and their statuses.  
- Vendors can view orders related to their products.  

### Reporting  
- Administrators can generate sales reports based on date ranges, user types, and more.  

## Database Schema  
**Users Table**  
| Column Name | Type       | Description                        |  
|-------------|------------|------------------------------------|  
| id          | INT        | Primary Key                        |  
| username    | VARCHAR    | Unique username                    |  
| email       | VARCHAR    | Unique email address               |  
| password     | VARCHAR    | Hashed password                    |  
| user_type   | ENUM       | Type (Admin, Customer, Vendor)    |  

**Products Table**  
| Column Name   | Type        | Description                                   |  
|---------------|-------------|-----------------------------------------------|  
| id            | INT         | Primary Key                                   |  
| name          | VARCHAR     | Product name                                 |  
| description   | TEXT        | Product description                          |  
| price         | DECIMAL     | Product price                                |  
| vendor_id     | INT         | Foreign key referencing Users(id)            |  

**Orders Table**  
| Column Name   | Type        | Description                                   |  
|---------------|-------------|-----------------------------------------------|  
| id            | INT         | Primary Key                                   |  
| user_id       | INT         | Foreign key referencing Users(id)            |  
| total_amount  | DECIMAL     | Total order amount                           |  
| status        | ENUM        | Status (Pending, Completed, Cancelled)      |  
| created_at    | DATETIME    | Timestamp of order placement                 |  
