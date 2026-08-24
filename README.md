# E-commerce Mini Store

A simple full-stack e-commerce project built with **HTML, CSS, Python, and Django** — good for a fresher portfolio/resume "full-stack" project.

## Features
- Product listing with search + category filter
- Product detail page
- Session-based shopping cart (add / update quantity / remove)
- User sign up / login / logout
- Checkout with shipping details form (dummy payment - Cash on Delivery, no real gateway)
- Order confirmation page + "My Orders" history
- Django Admin panel to add/edit Products, Categories, and view Orders

## Tech Stack
- Backend: Python, Django
- Frontend: HTML, CSS (templates in `shop/templates/`)
- Database: SQLite (default, no setup needed)
- Image uploads: Pillow (for product images)

## Setup Instructions

1. **Open the folder in VS Code**, open a terminal.

2. Make sure you're in the folder that directly contains `manage.py` (use `dir` to check — extract the zip fully first, avoid nested duplicate folders).

3. **Install dependencies:**
   ```
   pip install -r requirements.txt
   ```

4. **Run migrations:**
   ```
   python manage.py makemigrations
   python manage.py migrate
   ```

5. **Create an admin account:**
   ```
   python manage.py createsuperuser
   ```

6. **Run the server:**
   ```
   python manage.py runserver
   ```

7. **Open in browser:**
   - Main store: http://127.0.0.1:8000/
   - Admin panel: http://127.0.0.1:8000/admin/

## How to Use
1. Log in to `/admin/` with your superuser account.
2. Add a few **Categories** and **Products** (with price, stock, and optionally an image).
3. Go back to the main site (http://127.0.0.1:8000/) — browse, search, and add products to cart.
4. Sign up a normal account (or use the superuser), go to **Cart → Checkout**, fill shipping details, place the order.
5. Check **My Orders** to see order history.

## Folder Structure
```
ecommerce_store/
├── manage.py
├── requirements.txt
├── ecommerce_project/    # Project settings, main urls.py
└── shop/                 # App: models, views, forms, cart logic, admin, templates, static CSS
    ├── models.py          # Category, Product, Order, OrderItem
    ├── cart.py            # Session-based cart class
    ├── views.py
    ├── forms.py
    ├── urls.py
    ├── admin.py
    ├── templates/
    └── static/shop/css/style.css
```

## Notes for your Resume/Interview
- Explain the cart: it's stored in the Django **session** (not the database) until checkout, so guests can add items before logging in.
- At checkout, the cart's `Order` and `OrderItem` rows are created and stock is reduced.
- `OrderItem` stores a snapshot of `product_name` and `price` at order time, so historical orders stay correct even if a product's price changes later.
- Possible extensions: real payment gateway integration (Razorpay/Stripe test mode), product reviews/ratings, wishlist, order status tracking with email notifications.
