# ShopCraft 🛍️

> A modern e-commerce platform for seamless online shopping experiences

![ShopCraft Banner](./public/banner.png)

## 👨‍💻 Author

**KAKTHIK V**

## 📋 About The Project

ShopCraft is a full-featured e-commerce web application that provides users with an intuitive shopping experience. The platform enables customers to browse products, manage their cart, and complete purchases with ease.

### Built With

* **Frontend**: React.js
* **Styling**: CSS3 / Tailwind CSS
* **State Management**: React Context API / Redux
* **Backend**: Node.js & Express.js
* **Database**: MongoDB
* **Authentication**: JWT (JSON Web Tokens)

## ✨ Features

- 🛒 **Shopping Cart**: Add, remove, and update product quantities
- 🔍 **Product Search & Filter**: Find products quickly with advanced filtering
- 👤 **User Authentication**: Secure login and registration system
- 💳 **Checkout System**: Streamlined checkout process
- 📱 **Responsive Design**: Optimized for all device sizes
- ⭐ **Product Reviews**: View and add product ratings
- 📦 **Order History**: Track past and current orders
- 🎨 **Modern UI/UX**: Clean and intuitive interface

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:
```bash
node -v  # Node.js version 16 or higher
npm -v   # npm version 8 or higher
```

### Installation

1. Clone the repository
```bash
git clone https://github.com/karthi2216/Shop-E-commerce-website.git
```

2. Navigate to the project directory
```bash
cd shopcraft
```

3. Install frontend dependencies
```bash
npm install
```

4. Install backend dependencies
```bash
cd backend
npm install
```

5. Set up environment variables

Create a `.env` file in the backend directory:
```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
```

6. Start the backend server
```bash
cd backend
npm start
```

7. Start the frontend development server
```bash
cd ..
npm start
```

8. Open your browser and visit
```
http://localhost:3000
```

## 📱 Live Demo

Check out the live version: [ShopCraft Live](https://kyn3g6md3hbow.mocha.app/)

## 🗂️ Project Structure

```
shopcraft/
├── public/           # Static files
├── src/
│   ├── components/   # Reusable React components
│   ├── pages/        # Page components
│   ├── context/      # Context API for state management
│   ├── utils/        # Utility functions
│   └── App.js        # Main app component
├── backend/
│   ├── models/       # Database models
│   ├── routes/       # API routes
│   ├── controllers/  # Route controllers
│   └── server.js     # Express server
└── package.json
```

## 🎯 Usage

1. **Browse Products**: Navigate through different product categories
2. **Add to Cart**: Click "Add to Cart" on any product
3. **Manage Cart**: Update quantities or remove items from your cart
4. **Checkout**: Proceed to checkout and complete your order
5. **Track Orders**: View your order history in your profile

## 🛠️ API Endpoints

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get single product

### Users
- `POST /api/users/register` - Register new user
- `POST /api/users/login` - User login

### Orders
- `POST /api/orders` - Create new order
- `GET /api/orders/:userId` - Get user orders

## 🤝 Contributing

Contributions are welcome! Feel free to:

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request


## 📧 Contact
**KAKTHIK V**

Project Link: [https://github.com/karthi2216/Shop-E-commerce-website](https://github.com/karthi2216/Shop-E-commerce-website)

---

⭐ If you found this project helpful, please give it a star!
