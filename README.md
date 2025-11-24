# MERN E-Commerce Application

A full-stack e-commerce application built with MongoDB, Express, React, and Node.js. This application supports three user roles: Buyer, Seller, and Admin, with complete CRUD operations for products, orders, and user management.

## Features

### User Roles

1. **Buyer**
   - Browse products and categories
   - Search and filter products
   - Add products to cart (guest cart with localStorage sync)
   - Checkout with mock payment
   - View order history
   - Add product reviews and ratings

2. **Seller**
   - Add new products
   - Edit own products
   - Delete own products
   - View orders for their products
   - Seller dashboard

3. **Admin**
   - Full system access
   - Manage users (approve seller accounts)
   - Manage all products
   - Manage categories
   - View all orders
   - Admin dashboard

### Core Features

- User authentication (JWT + bcrypt)
- Product listing with pagination
- Search, filters, and sorting
- Product reviews and ratings
- Guest cart (localStorage) with sync after login
- Checkout with mock payment (card starting with "4" = success)
- Order management
- Role-based access control
- Responsive UI with Tailwind CSS

## Project Structure

```
Full_Stack/
├── server/
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── adminController.js
│   │   ├── authController.js
│   │   ├── cartController.js
│   │   ├── orderController.js
│   │   ├── productController.js
│   │   └── sellerController.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── errorHandler.js
│   ├── models/
│   │   ├── Cart.js
│   │   ├── Category.js
│   │   ├── Order.js
│   │   ├── Product.js
│   │   ├── Review.js
│   │   └── User.js
│   ├── routes/
│   │   ├── adminRoutes.js
│   │   ├── authRoutes.js
│   │   ├── cartRoutes.js
│   │   ├── categoryRoutes.js
│   │   ├── orderRoutes.js
│   │   ├── productRoutes.js
│   │   └── sellerRoutes.js
│   ├── .env.example
│   ├── package.json
│   └── server.js
├── client/
│   ├── src/
│   │   ├── api/
│   │   │   ├── admin.js
│   │   │   ├── auth.js
│   │   │   ├── axios.js
│   │   │   ├── cart.js
│   │   │   ├── categories.js
│   │   │   ├── orders.js
│   │   │   ├── products.js
│   │   │   └── seller.js
│   │   ├── components/
│   │   │   ├── Header.jsx
│   │   │   ├── Pagination.jsx
│   │   │   ├── ProductCard.jsx
│   │   │   └── ProtectedRoute.jsx
│   │   ├── context/
│   │   │   ├── AuthContext.jsx
│   │   │   └── CartContext.jsx
│   │   ├── pages/
│   │   │   ├── AdminDashboard.jsx
│   │   │   ├── Cart.jsx
│   │   │   ├── Categories.jsx
│   │   │   ├── Checkout.jsx
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Orders.jsx
│   │   │   ├── ProductDetail.jsx
│   │   │   ├── Register.jsx
│   │   │   └── SellerDashboard.jsx
│   │   ├── App.jsx
│   │   ├── index.css
│   │   └── main.jsx
│   ├── index.html
│   ├── package.json
│   ├── postcss.config.js
│   ├── tailwind.config.js
│   └── vite.config.js
├── docker-compose.yml
└── README.md
```

## Technology Stack

### Backend
- **Node.js** + **Express** - Server framework
- **MongoDB** (local) + **Mongoose** - Database
- **JWT** - Authentication
- **bcryptjs** - Password hashing

### Frontend
- **React** - UI library
- **Vite** - Build tool
- **Tailwind CSS** - Styling
- **React Router** - Routing
- **Axios** - HTTP client

## Installation & Setup

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local installation or Docker)
- npm or yarn

### Step 1: Clone and Setup

1. Navigate to the project directory:
cd Full_Stack


### Step 2: Setup MongoDB

**Option A: Using Docker (Recommended)**
docker-compose up -d

**Option B: Local MongoDB**
- Install MongoDB locally
- Start MongoDB service
- MongoDB will run on `mongodb://localhost:27017`

### Step 3: Setup Backend
cd server
npm install

Create a .env file in the server directory:
PORT=5000
MONGODB_URI=mongodb://localhost:27017/ecommerce
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRE=7d
NODE_ENV=development

### Step 4: Start Backend Server
npm start
# or for development
npm run dev
Backend will run on `http://localhost:5000`

### Step 5: Setup Frontend
Open a new terminal:
cd client
npm install

### Step 6: Start Frontend
npm run dev
Frontend will run on `http://localhost:3000`

## Getting Started

1. **Register a new account** - Go to /register and create an account
2. **Choose your role** - Select Buyer, Seller, or Admin during registration
3. **Start using the app** - Based on your role, you'll have access to different features

**Note:** The first user to register as Admin will have full system access. Sellers can add products, and Buyers can shop.

## API Endpoints

### Authentication
- POST /api/auth/register - Register new user
- POST /api/auth/login - Login user
- GET /api/auth/me - Get current user

### Products (Public)
- GET /api/products - Get all products (with filters, search, pagination)
- GET /api/products/:id - Get single product
- POST /api/products/:id/review - Add review (Buyer only)

### Cart (Buyer)
- GET /api/cart - Get user cart
- POST /api/cart - Add/Update cart item
- DELETE /api/cart/:productId - Remove item from cart

### Orders (Buyer)
- POST /api/checkout - Create order
- GET /api/orders - Get user orders

### Seller
- GET /api/seller/products - Get seller's products
- POST /api/seller/products - Create product
- PUT /api/seller/products/:id - Update product
- DELETE /api/seller/products/:id - Delete product
- GET /api/seller/orders - Get seller's orders

### Admin
- GET /api/admin/users - Get all users
- PATCH /api/admin/users/:id/role - Update user role
- GET /api/admin/categories - Get all categories
- POST /api/admin/categories - Create category
- GET /api/admin/products - Get all products
- POST /api/admin/products - Create product
- PUT /api/admin/products/:id - Update product
- DELETE /api/admin/products/:id - Delete product
- GET /api/admin/orders - Get all orders

### Categories (Public)
- GET /api/categories - Get all categories

##  Frontend Routes

- / - Home page (product listing)
- /categories - Browse categories
- /product/:id - Product detail page
- /login - Login page
- /register - Register page
- /cart - Shopping cart (Buyer only)
- /checkout - Checkout page (Buyer only)
- /orders - Order history (Buyer only)
- /seller/dashboard - Seller dashboard
- /admin/dashboard - Admin dashboard

## Mock Payment

The checkout process uses a mock payment system:
- **Card numbers starting with "4"** = Payment successful
- **Any other card number** = Payment failed

Example successful card: 4000 1234 5678 9010

## Authentication & Authorization

- JWT tokens are stored in localStorage
- Protected routes require authentication
- Role-based access control (Buyer, Seller, Admin)
- Guest cart syncs with user cart after login

## Cart Functionality

- **Guest users:** Cart stored in localStorage
- **Logged-in users:** Cart stored in database
- Cart automatically syncs when guest user logs in

## Notes

- This application is designed to run **locally only** (no deployment)
- Uses **MongoDB local** (not Atlas)
- Images use placeholder services (picsum.photos)
- All passwords are hashed using bcrypt
- JWT tokens expire after 7 days (configurable)
- **No seed data** - Users must register themselves with their chosen role (buyer, seller, or admin)

## Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running
- Check MONGODB_URI in .env file
- If using Docker, ensure container is running: docker-compose ps

### Port Already in Use
- Change PORT in server .env file
- Update Vite proxy in client/vite.config.js if needed

### CORS Issues
- Backend CORS is configured to allow all origins in development
- Update CORS settings in server/server.js for production

## License

This project is for educational purposes (college project).

## Development

### Backend Development
cd server
npm run dev  # Uses nodemon for auto-restart

### Frontend Development
cd client
npm run dev  # Vite dev server with hot reload

## Future Enhancements

- Image upload functionality
- Real payment integration
- Email notifications
- Product image gallery
- Advanced search with filters
- Wishlist functionality
- Order tracking
- Seller analytics dashboard

---

**Built with passion for college project**

