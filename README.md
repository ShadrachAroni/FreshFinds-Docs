<p align="center">
  <img src="./assets/logo.png" alt="FreshFinds Logo" width="120" />
</p>

<h1 align="center">🍽️ FreshFinds</h1>

<p align="center">
  <strong>A modern, full-stack food delivery platform built with React, Node.js, and Supabase</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Frontend-React_18-61dafb?logo=react" />
  <img src="https://img.shields.io/badge/Backend-Node.js_20-339933?logo=node.js" />
  <img src="https://img.shields.io/badge/Database-Supabase-3FCF8E?logo=supabase" />
  <img src="https://img.shields.io/badge/Payments-Pesapal-blue" />
  <img src="https://img.shields.io/badge/License-MIT-yellow" />
</p>

---

## 📖 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Screenshots](#screenshots)
- [Demo Video](#demo-video)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [API Reference](#api-reference)
- [Security](#security)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

**FreshFinds** is a full-featured food ordering and delivery platform designed for the Kenyan market. It provides:

- A **customer-facing storefront** where users can browse, search, filter, and order food
- An **admin dashboard** for managing products, orders, users, and delivery status
- **Secure payment processing** via Pesapal (M-Pesa, cards) with server-side verification
- **Real-time order tracking** with status updates from placement through delivery

The platform emphasizes security (JWT auth, rate limiting, CORS, Helmet), a premium dark-themed UI, and a smooth mobile-responsive experience.

---

## Features

### 🛒 Customer App
| Feature | Description |
|---------|-------------|
| **Product Catalog** | Browse food items by category with search and filter |
| **Shopping Cart** | Add/remove items, adjust quantities, persistent across sessions |
| **Secure Checkout** | Pay via Pesapal (M-Pesa/Card) or Cash on Delivery |
| **Order Tracking** | Real-time order status: Pending → Out for Delivery → Delivered |
| **User Accounts** | Register with OTP email verification, profile management |
| **Responsive Design** | Mobile-first, works on all screen sizes |

### 🔧 Admin Dashboard
| Feature | Description |
|---------|-------------|
| **Product CRUD** | Add, edit, remove food items with image upload |
| **Order Management** | View all orders, update delivery status, mark as paid, cancel |
| **User Management** | View all users, search, change roles, delete accounts |
| **Secure Login** | Admin-only authentication with JWT tokens |

### 🔐 Security
| Feature | Description |
|---------|-------------|
| **JWT Authentication** | Access + refresh tokens with 7-day expiry |
| **OTP Verification** | Email-based OTP for customer registration/login |
| **Rate Limiting** | Protection against brute force on auth endpoints |
| **Helmet + CORS** | Security headers and origin whitelisting |
| **Server-side Payment Verification** | IPN callbacks + status verification to prevent fraud |

---

## Architecture

```
┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│   Customer App   │     │  Admin Dashboard  │     │  Pesapal Gateway │
│   (React + Vite) │     │  (React + Vite)   │     │   (M-Pesa/Card)  │
└────────┬─────────┘     └────────┬──────────┘     └────────┬─────────┘
         │                        │                          │
         │  HTTPS (JWT)           │  HTTPS (JWT)             │  IPN Callback
         │                        │                          │
         ▼                        ▼                          ▼
┌────────────────────────────────────────────────────────────────────┐
│                     Express.js Backend (Node 20)                   │
│  ┌─────────┐  ┌──────────┐  ┌──────────┐  ┌─────────────────┐    │
│  │  Auth   │  │  Food    │  │  Order   │  │  Cart           │    │
│  │ Routes  │  │  Routes  │  │  Routes  │  │  Routes         │    │
│  └─────────┘  └──────────┘  └──────────┘  └─────────────────┘    │
│  ┌─────────────────────────────────────────────────────────────┐  │
│  │  Middleware: JWT Auth | Admin Auth | Rate Limiter | Helmet  │  │
│  └─────────────────────────────────────────────────────────────┘  │
└─────────────────────────────┬──────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │     Supabase     │
                    │   (PostgreSQL)   │
                    │  ┌────────────┐  │
                    │  │   users    │  │
                    │  │   foods    │  │
                    │  │   orders   │  │
                    │  │   carts    │  │
                    │  │  user_otps │  │
                    │  └────────────┘  │
                    └──────────────────┘
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18, Vite, React Router, Axios, React Toastify |
| **Admin** | React 18, Vite, React Router, Axios, React Toastify |
| **Backend** | Node.js 20, Express.js, bcryptjs, jsonwebtoken |
| **Database** | Supabase (PostgreSQL) with Row Level Security |
| **Payments** | Pesapal API (M-Pesa, Visa/Mastercard) |
| **Email** | Nodemailer (Gmail SMTP) for OTP delivery |
| **Security** | Helmet, CORS, express-rate-limit |
| **Hosting** | Render (Backend + Frontend + Admin) |

---

## Screenshots

> 📸 **Add your screenshots below.** Replace the placeholder paths with actual screenshot images.

### Customer App

#### Homepage & Hero Section
<!-- 📸 TODO: Add screenshot of the homepage with hero banner -->
`[Screenshot: Homepage hero section with search and category filters]`

#### Product Catalog
<!-- 📸 TODO: Add screenshot of food listing grid -->
`[Screenshot: Food items displayed in a responsive grid with prices]`

#### Product Categories / Filter
<!-- 📸 TODO: Add screenshot showing category filters in action -->
`[Screenshot: Category filter bar with selected category highlighted]`

#### Shopping Cart
<!-- 📸 TODO: Add screenshot of cart with items -->
`[Screenshot: Cart page showing items, quantities, subtotal, and checkout button]`

#### Checkout / Place Order
<!-- 📸 TODO: Add screenshot of checkout form -->
`[Screenshot: Checkout form with delivery address and payment method selection]`

#### Payment Verification
<!-- 📸 TODO: Add screenshot of the payment verification page -->
`[Screenshot: Glassmorphic verification card with status animation]`

#### Order Tracking
<!-- 📸 TODO: Add screenshot of My Orders page -->
`[Screenshot: My Orders page showing order cards with status badges]`

#### User Registration / OTP
<!-- 📸 TODO: Add screenshot of registration with OTP flow -->
`[Screenshot: Registration form and OTP email verification step]`

#### Mobile Responsive View
<!-- 📸 TODO: Add mobile screenshot -->
`[Screenshot: Mobile view of the homepage and cart]`

---

### Admin Dashboard

#### Admin Login
<!-- 📸 TODO: Add screenshot of admin login page -->
`[Screenshot: Dark-themed admin login page with glassmorphic card]`

#### Food Items List
<!-- 📸 TODO: Add screenshot of list page -->
`[Screenshot: Admin food list with inline editing for price/category]`

#### Add New Food Item
<!-- 📸 TODO: Add screenshot of add page -->
`[Screenshot: Add food form with image upload, name, description, category, price]`

#### Order Management
<!-- 📸 TODO: Add screenshot of orders page -->
`[Screenshot: Admin orders page with status dropdowns and payment actions]`

#### User Management
<!-- 📸 TODO: Add screenshot of users page -->
`[Screenshot: Users table with search bar, role dropdowns, and delete actions]`

---

## Demo Video

> 🎬 **Add a demo video walkthrough below.**

<!-- 🎬 TODO: Record and embed a demo video showing the full flow:
   1. Customer browsing products
   2. Adding items to cart
   3. Checkout and payment
   4. Order verification
   5. Admin login
   6. Admin updating order status
   7. Admin managing products and users
-->

`[Video: Full platform walkthrough — customer ordering flow → admin management]`

You can upload the video to YouTube and embed it like this:
```markdown
[![FreshFinds Demo](https://img.youtube.com/vi/YOUR_VIDEO_ID/maxresdefault.jpg)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)
```

---

## Getting Started

### Prerequisites

- **Node.js** 18+ (recommended: 20 LTS)
- **npm** 9+
- A **Supabase** project ([supabase.com](https://supabase.com))
- A **Pesapal** merchant account ([pesapal.com](https://www.pesapal.com))
- A **Gmail** account for SMTP (or any SMTP provider)

### Installation

```bash
# Clone the repository
git clone https://github.com/ShadrachAroni/FreshFinds.git
cd FreshFinds

# Install dependencies for all three apps
cd backend && npm install && cd ..
cd frontend && npm install && cd ..
cd admin && npm install && cd ..
```

### Environment Setup

Create `.env` files in each directory:

#### `backend/.env`
```env
JWT_SECRET=your_jwt_secret_here

SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_KEY=your_service_role_key
SUPABASE_ANON_KEY=your_anon_key

PESAPAL_CONSUMER_KEY=your_pesapal_key
PESAPAL_CONSUMER_SECRET=your_pesapal_secret

EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password

FRONTEND_URL=http://localhost:5173
BACKEND_URL=http://localhost:4000
ADMIN_URL=http://localhost:5174
ALLOWED_ORIGINS=http://localhost:5173,http://localhost:5174

NODE_ENV=development
LOG_LEVEL=info
```

#### `frontend/.env`
```env
VITE_BACKEND_URL=http://localhost:4000
```

#### `admin/.env`
```env
VITE_BACKEND_URL=http://localhost:4000
```

### Running Locally

```bash
# Terminal 1 — Backend
cd backend
npm run dev          # Starts on port 4000

# Terminal 2 — Customer Frontend
cd frontend
npm run dev          # Starts on port 5173

# Terminal 3 — Admin Dashboard
cd admin
npm run dev          # Starts on port 5174
```

---

## Project Structure

```
FreshFinds/
├── backend/
│   ├── controllers/         # Route handlers (food, user, order, cart)
│   ├── middleware/           # Auth, admin auth, rate limiter, validation
│   ├── routes/               # Express route definitions
│   ├── services/             # Email service, logger, Pesapal integration
│   ├── server.js             # Express app entry point
│   └── .env                  # Environment variables
│
├── frontend/
│   ├── src/
│   │   ├── assets/           # Images, icons, static assets
│   │   ├── components/       # Reusable UI components
│   │   ├── context/          # React Context (StoreContext)
│   │   └── pages/            # Page components (Home, Cart, Orders, etc.)
│   └── .env
│
├── admin/
│   ├── src/
│   │   ├── assets/           # Admin-specific assets
│   │   ├── components/       # Navbar, Sidebar
│   │   └── pages/            # Admin pages (Add, List, Orders, Users, Login)
│   └── .env
│
├── .gitignore
└── README.md
```

---

## API Reference

### Authentication
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/user/register` | ❌ | Register a new user |
| `POST` | `/api/user/send-otp` | ❌ | Send email OTP |
| `POST` | `/api/user/login` | ❌ | Login with email + password + OTP |
| `POST` | `/api/user/admin-login` | ❌ | Admin login (email + password) |
| `POST` | `/api/user/refresh-token` | 🔑 | Refresh access token |

### Food Items
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/api/food/list` | ❌ | Get all food items |
| `GET` | `/api/food/total` | ❌ | Get total item count |
| `POST` | `/api/food/add` | 🔒 Admin | Add a new food item |
| `POST` | `/api/food/remove` | 🔒 Admin | Remove a food item |
| `POST` | `/api/food/update` | 🔒 Admin | Update a food item |

### Cart
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/cart/add` | 🔑 | Add item to cart |
| `POST` | `/api/cart/remove` | 🔑 | Remove item from cart |
| `POST` | `/api/cart/get` | 🔑 | Get cart contents |

### Orders
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/order/place` | 🔑 | Place a new order (online payment) |
| `POST` | `/api/order/place-on-delivery` | 🔑 | Place order (cash on delivery) |
| `POST` | `/api/order/verify` | ❌ | Verify payment status |
| `POST` | `/api/order/userorders` | 🔑 | Get user's orders |
| `GET` | `/api/order/list` | 🔒 Admin | List all orders |
| `POST` | `/api/order/status` | 🔒 Admin | Update order status |

**Auth Legend:** ❌ Public | 🔑 User JWT | 🔒 Admin JWT

---

## Security

FreshFinds implements multiple layers of security:

- **JWT Authentication** — Short-lived access tokens (7d) with refresh token rotation
- **bcrypt Password Hashing** — 12 rounds of salted hashing
- **OTP Email Verification** — Required for customer registration and login
- **Admin Role Enforcement** — Server-side role check on all admin endpoints
- **Rate Limiting** — Auth endpoints throttled to prevent brute force
- **Helmet Security Headers** — XSS protection, CSP, and more
- **CORS Whitelisting** — Only registered origins can access the API
- **Server-side Payment Verification** — IPN + status polling to prevent payment fraud
- **Input Validation** — Express-validator on all user inputs
- **Automatic 401 Logout** — Expired tokens trigger immediate session cleanup

---

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  Built with ❤️ by <a href="https://github.com/ShadrachAroni">Shadrach Aroni</a>
</p>
