<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="client/public/logo.png">
    <source media="(prefers-color-scheme: light)" srcset="client/public/logo.png">
    <img alt="Al-Marah Logo" src="client/public/logo.png" width="180" height="auto" style="border-radius: 20px;">
  </picture>
</p>

<h1 align="center">🥩 ملحمة النعيمي الفاخر</h1>
<h2 align="center">Al-Marah Luxury Butchery — Asset Manager</h2>

<p align="center">
  <strong>Full-stack Arabic E-commerce + Operations Management Platform for Premium Butchery</strong>
</p>

<p align="center">
  <a href="#-system-architecture">🏗️ Architecture</a> ·
  <a href="#-features">✨ Features</a> ·
  <a href="#-roles--permissions">👥 Roles</a> ·
  <a href="#-database-schema">🗄️ Schema</a> ·
  <a href="#-tech-stack">🛠️ Stack</a> ·
  <a href="#-setup">🚀 Setup</a>
</p>

<p align="center">
  <a href="https://almarah.vercel.app" target="_blank">
    <img alt="Live Demo" src="https://img.shields.io/badge/demo-LIVE-8B0000?style=for-the-badge&logo=vercel">
  </a>
  <a href="https://github.com/HSG116/almarah">
    <img alt="GitHub" src="https://img.shields.io/badge/source-GitHub-1a1a2e?style=for-the-badge&logo=github">
  </a>
  <a href="#">
    <img alt="License" src="https://img.shields.io/badge/license-MIT-22c55e?style=for-the-badge">
  </a>
  <br>
  <a href="https://discord.com/users/1416151331965767810">
    <img alt="Discord" src="https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white">
  </a>
  <a href="https://x.com/Moh_HSG">
    <img alt="X (Twitter)" src="https://img.shields.io/badge/X-000000?style=for-the-badge&logo=x&logoColor=white">
  </a>
</p>

<br>

---

## 📋 Table of Contents

- [📋 Table of Contents](#-table-of-contents)
- [🏗️ System Architecture](#️-system-architecture)
- [✨ Features Overview](#-features-overview)
- [👥 Roles & Permissions](#-roles--permissions)
  - [👤 Customer (العميل)](#-customer-العميل)
  - [🛡️ Admin (الإدارة)](#️-admin-الإدارة)
  - [🥩 Butcher (الجزار)](#-butcher-الجزار)
  - [🚚 Delivery Driver (السائق)](#-delivery-driver-السائق)
  - [💰 Accountant (المحاسب)](#-accountant-المحاسب)
  - [🎨 Designer (المصمم)](#-designer-المصمم)
  - [📞 Support (الدعم)](#-support-الدعم)
  - [📊 Manager (المدير)](#-manager-المدير)
  - [🏢 General Manager (المدير العام)](#-general-manager-المدير العام)
- [🗄️ Database Schema](#️-database-schema)
- [🛠️ Tech Stack](#️-tech-stack)
- [📦 Order Workflow](#-order-workflow)
- [🚀 Setup & Installation](#-setup--installation)
- [🌐 Deployment](#-deployment)
- [📜 Legal Pages](#-legal-pages)
- [🤝 Contributing](#-contributing)

<br>

---

## 🏗️ System Architecture

```mermaid
graph TB
    subgraph "👤 Frontend (React SPA)"
        A[Home Page] --> B[Products]
        A --> C[Cart]
        C --> D[Checkout 3-Step]
        A --> E[Auth / Profile]
        F[Admin Dashboard] --> G[CRM]
        F --> H[Analytics]
        F --> I[Staff Mgmt]
        J[Staff Dashboard] --> K[Butcher Terminal]
        J --> L[Delivery Terminal]
        J --> M[Accountant Panel]
        J --> N[Support Tickets]
        J --> O[Designer Tasks]
        J --> P[Manager Oversight]
    end

    subgraph "⚙️ Backend (Express.js)"
        Q[API Routes] --> R[Auth Passport.js]
        Q --> S[CRUD Operations]
        Q --> T[File Upload]
        U[Telegram Bot] --> V[Phone Verification]
    end

    subgraph "🗄️ Database & Services"
        W[(Supabase PostgreSQL)] --> X[Users]
        W --> Y[Orders]
        W --> Z[Products]
        W --> AA[Delivery Zones]
        W --> AB[Notifications]
        W --> AC[Financial Records]
        AD[Supabase Realtime] --> AE[Live Updates]
        AF[Supabase Auth] --> AG[Google OAuth]
        AF --> AH[Email/Password]
    end

    subgraph "📦 External"
        AI[Google OAuth] --> AF
        AJ[Telegram API] --> U
        AK[Vercel CDN] --> A
    end

    F --> Q
    J --> Q
    A --> Q
    Q --> W
    Q --> U
    AD --> F
    AD --> J
```

<br>

---

## ✨ Features Overview

| # | Feature | Description |
|---|---------|-------------|
| 🛍️ | **Online Store** | Browse meat cuts, chicken, vegetables with detailed pricing, cutting options, packaging choices |
| 🧑‍🍳 | **Butcher Terminal** | Digital workstation for butchers — receive orders, process meat, update inventory in real-time |
| 🚚 | **Smart Delivery** | Auto-assign drivers, GPS zone detection, trip management, proof of delivery |
| 💰 | **Accounting Suite** | P&L reports, sales charts (Recharts), payout requests, wallet management |
| 🧾 | **ZATCA Invoices** | Saudi tax-compliant invoices — A4 premium + 80mm thermal receipt formats |
| 🔔 | **Real-time Alerts** | Supabase Realtime WebSocket — instant notifications on order status changes |
| 🤖 | **Telegram Bot** | Phone number verification via Telegram (`@sms_otp_new_bot`) |
| 🗺️ | **Delivery Zones** | Interactive map polygon editor — auto-fee calculation via ray-casting algorithm |
| 🎫 | **Coupons & Offers** | Discount codes, flash sales, BOGO, tier-based pricing |
| 📱 | **Responsive RTL** | Full Arabic right-to-left support, mobile-first design |
| 👥 | **8 Staff Roles** | Granular role-based dashboards with custom permissions |
| 🔒 | **RLS Security** | Row-Level Security on all tables, role-gated API routes |

<br>

---

## 👥 Roles & Permissions

### 👤 Customer (العميل)

The customer-facing experience is a fully-featured e-commerce store:

**🖥️ Pages:**
- **Home** (`/`) — Hero banner with featured products, category grid, service highlights, footer
- **Products** (`/products`) — Grid layout with category filter, search bar, mobile filter sheet
- **Cart** (`/cart`) — Quantity controls, cutting/packaging options summary, price breakdown
- **Checkout** (`/checkout`) — 3-step flow:
  1. Review order with item options
  2. Address selection with interactive GPS map (MapLibre GL) — auto-detects delivery zone & fee
  3. Payment (COD active, cards coming soon) & coupon code — VAT 15% breakdown

**📦 Order Management:**
- Profile (`/profile`) — Order history with expandable details, re-order
- Address book with GPS location, saved addresses
- Real-time order status notifications (pending → preparing → ready → shipping → completed)
- Auth via email/password, Google OAuth, or Telegram phone verification

**🎨 UI/UX:**
- Framer Motion page transitions & micro-animations
- Bottom navigation bar (mobile) with scroll-aware hide/show
- Responsive from 320px to 4K
- Arabic-first with Cairo/Tajawal fonts

<br>

---

### 🛡️ Admin (الإدارة)

The **Admin Dashboard** (`/admin/dashboard`, 3300+ lines) is a complete CRM with **12+ tabs**:

| Tab | Features |
|-----|----------|
| **📊 Overview** | KPIs: total orders, revenue, active users, top products; sales charts (7-day, monthly, yearly) |
| **📦 Orders** | Full order table with filters (status, date, driver), assign driver/butcher, print A4/thermal invoice, cancel |
| **🥩 Products** | CRUD for products — name, price, unit, category, image upload with object-position, badge, stock toggle |
| **📂 Categories** | Manage product categories with icons, images, parent/child hierarchy |
| **👥 Customers** | User list with roles, ban/unban, toggle admin status, view order history |
| **👨‍💼 Staff** | Create/promote staff accounts, assign roles & permissions, manage wallets, view payouts |
| **🎟️ Coupons** | Create discount codes (percentage/fixed), min purchase, expiry, usage limits, tier targeting |
| **🎁 Offers** | Marketing banners, BOGO deals, flash sales with start/end dates |
| **🗺️ Delivery Zones** | Interactive map (Leaflet) — draw polygons, set fee & min order, driver commission % |
| **📄 Invoices** | View and re-print any invoice (A4 premium or thermal receipt) |
| **📢 Broadcast** | Send push notifications to all users or by role |
| **⚙️ Settings** | Site-wide configuration, legal content editor, SEO meta |

**Security:** Admin-only routes are gated via `isAdmin` check + RLS policies. Image upload restricted to staff.

<br>

---

### 🥩 Butcher (الجزار)

The **Butcher Terminal** (`/butcher`) is a digital workstation replacing paper orders:

**🧑‍🍳 Workflow:**
1. **Active Tasks** — Real-time list of orders assigned to this butcher
2. **Take Task** — Butcher clicks "استلام المهمة" to claim an order → status changes to `preparing`
3. **Process Order** — View order details: items, cutting specs (e.g., "مكعبات", "شرائح"), packaging type, special instructions
4. **Mark Complete** — Butcher finishes → status changes to `ready`, auto-notifies available drivers
5. **Print Label** — Print barcode/product labels for packaged meat

**📦 Inventory Management:**
- `butcher_inventory` — Track stock per product (whole cuts, processed portions)
- `butcher_inventory_logs` — Audit trail of all inventory changes (who, what, when)
- Real-time stock level alerts when items run low

**📜 History:**
- Completed jobs log with timestamps
- Performance metrics (orders/day, avg processing time)

<br>

---

### 🚚 Delivery Driver (السائق)

The **Delivery Terminal** (`/delivery`) manages the entire delivery lifecycle:

**🚗 Driver Workflow:**
1. **Trip Dashboard** — See assigned deliveries with customer address, GPS coordinates, phone
2. **Navigation** — One-tap open in Google Maps / Waze
3. **Status Updates** — Pickup → On Route → Delivered
4. **Proof of Delivery** — Optional photo capture, customer signature
5. **Trip History** — Completed deliveries with timestamps, route tracking

**📊 Driver Details:**
- `drivers` table — External driver registry (name, phone, active status)
- `delivery_trips` — Trip records with timestamps, distance, status
- Commission tracking per delivery, payout requests

**🗺️ Zone Integration:**
- GPS-based zone auto-detection during checkout
- Driver commission varies by zone (set in delivery zone config)
- Coverage map shows active delivery areas

<br>

---

### 💰 Accountant (المحاسب)

The **Accountant Panel** (`/accountant`) provides full financial oversight:

**📈 Reports & Analytics:**
- **Revenue Charts** — Daily, weekly, monthly, yearly sales (Recharts)
- **Profit & Loss** — Revenue vs expenses breakdown
- **Top Products** — Best-selling items by quantity & revenue
- **Category Performance** — Sales distribution across lamb, chicken, veggies

**💳 Financial Operations:**
- `financial_records` — All financial entries with type, amount, description, timestamp
- `payout_requests` — Staff/driver payout management, approval workflow
- **Wallet Management** — Staff wallets with balance, auto-crediting, withdrawal requests

**🧾 Invoice Reconciliation:**
- Match orders to payments
- ZATCA-compliant tax reporting
- VAT (15%) breakdown on all transactions

<br>

---

### 🎨 Designer (المصمم)

The **Designer Panel** (`/designer`) for marketing content creators:

**🎯 Marketing Tasks:**
- `marketing_tasks` — Task assignments: create banner, edit photo, design promo
- Asset management — Upload/approve store images, banners, promotional materials
- Offer visual preview before publishing

**📸 Content Management:**
- Product image upload with cropping & positioning
- Category icons & hero banners
- Social media content calendar (upcoming)

<br>

---

### 📞 Support (الدعم)

The **Support Panel** (`/support`) handles customer inquiries:

**🎫 Ticket System:**
- `support_tickets` — Customer issues with priority levels
- Status workflow: Open → In Progress → Resolved → Closed
- Internal notes & customer replies

**🔍 Customer Lookup:**
- Search orders by customer name/phone/order ID
- View full order history, modify order status (with admin approval)
- Issue refunds or replacements

<br>

---

### 📊 Manager (المدير)

The **Manager Dashboard** (`/manager`) for operational oversight:

**📋 KPIs & Oversight:**
- Staff performance metrics (orders processed/delivered per staff member)
- Sales trends & forecasts
- Butcher throughput (orders completed / hour)
- Driver on-time delivery rate

**👁️ Live View:**
- All active orders across the system
- Staff online/offline status
- Real-time sales ticker

<br>

---

### 🏢 General Manager (المدير العام)

Full admin-level access with additional strategic tools:

- Cross-department analytics
- Staff cost analysis
- Business intelligence reports
- All permissions from all roles combined

<br>

---

## 🗄️ Database Schema

The system uses **PostgreSQL via Supabase** with **Drizzle ORM**. Here's the complete schema:

```mermaid
erDiagram
    USERS ||--o{ ORDERS : places
    USERS ||--o{ NOTIFICATIONS : receives
    USERS ||--o{ STAFF : is
    STAFF ||--o{ BUTCHER_LOGS : logs
    STAFF ||--o{ DELIVERY_TRIPS : completes
    STAFF ||--o{ FINANCIAL_RECORDS : creates
    STAFF ||--o{ SUPPORT_TICKETS : handles
    STAFF ||--o{ MARKETING_TASKS : assigned
    STAFF ||--o{ PAYOUT_REQUESTS : requests
    CATEGORIES ||--o{ PRODUCTS : contains
    PRODUCTS ||--o{ ORDER_ITEMS : includes
    PRODUCTS ||--o{ BUTCHER_INVENTORY : tracks
    PRODUCTS ||--o{ PRODUCT_ATTRIBUTES : has
    ORDERS ||--o{ ORDER_ITEMS : composed_of
    ORDERS ||--o{ NOTIFICATIONS : triggers
    ORDERS ||--o{ DELIVERY_TRIPS : assigned
    DELIVERY_ZONES ||--o{ ORDERS : defines_area
    COUPONS ||--o{ ORDERS : applied_to
    OFFERS ||--o{ PRODUCTS : promotes
    ORDERS ||--o{ FINANCIAL_RECORDS : generates

    USERS {
        uuid id PK
        string username
        string password
        string email
        string phone
        string city
        string district
        string street
        string building
        string landmark
        float gps_lat
        float gps_lng
        boolean isAdmin
        boolean isBanned
        enum role "customer|admin|butcher|delivery|manager|accountant|support|designer"
        text[] permissions
        timestamp createdAt
        string avatar_url
    }

    ORDERS {
        int id PK
        uuid userId FK
        float total
        enum status "pending|preparing|ready|shipping|completed|cancelled"
        string address
        string customerName
        string customerPhone
        string notes
        string paymentMethod
        int driverId
        uuid butcherStaffId
        uuid driverStaffId
        int zoneId
        float gpsLat
        float gpsLng
        timestamp createdAt
        timestamp updatedAt
    }

    PRODUCTS {
        int id PK
        string name
        string categoryId FK
        float price
        string unit
        string image
        string description
        string badge
        string size
        float weight
        boolean isFeatured
        boolean isActive
        string imageObjectPosition
        int stockQuantity
        boolean isOutOfStock
        boolean hasCutting
        boolean hasPackaging
        boolean hasExtras
        boolean allowSpecialInstructions
    }

    CATEGORIES {
        string id PK
        string name
        string icon
        string image
        string parentId FK
    }

    DELIVERY_ZONES {
        int id PK
        string name
        float fee
        float driverCommission
        float minOrder
        boolean isActive
        json coordinates "Polygon array of [lat, lng]"
    }
```

### 📊 Core Tables

| Table | Rows | Description |
|-------|------|-------------|
| `users` | ~ | User accounts with role, address, GPS, permissions |
| `categories` | 3 | Product categories: lamb, chicken, veggies |
| `products` | 42 | Product catalog with pricing, options, inventory |
| `orders` | ~ | Customer orders with status workflow |
| `order_items` | ~ | Line items: product, quantity, cutting, packaging, notes |

### ⚙️ Feature Tables

| Table | Description |
|-------|-------------|
| `delivery_zones` | Geographic polygons with fees & commissions |
| `product_attributes` | Cutting/packaging/extra options per product |
| `coupons` | Discount codes with conditions, tiers, expiry |
| `offers` | Banners, BOGO, flash sales promotions |
| `notifications` | Push notification queue with read status |

### 👔 Staff Tables

| Table | Description |
|-------|-------------|
| `staff` | Staff records linked to users, roles, permissions, wallet |
| `butcher_logs` | Activity log for butchers |
| `butcher_inventory` | Per-product stock tracking |
| `butcher_inventory_logs` | Audit trail for inventory changes |
| `delivery_trips` | Trip records with timestamps |
| `financial_records` | All financial transactions |
| `payout_requests` | Staff payout/withdrawal management |
| `support_tickets` | Customer support tickets |
| `marketing_tasks` | Marketing task assignments |

### 🔐 Security
- **Row-Level Security (RLS)** policies on all tables
- Password hashing via Node.js `scrypt`
- Session-based auth with `express-session` + `memorystore`
- Role-gated API routes with middleware checks

<br>

---

## 🛠️ Tech Stack

| Layer | Technology | Version |
|-------|-----------|---------|
| **Frontend Framework** | [React](https://react.dev) | 19.2.0 |
| **Build Tool** | [Vite](https://vitejs.dev) | 7.1.9 |
| **Styling** | [Tailwind CSS](https://tailwindcss.com) | 4.1.14 |
| **Component Library** | [shadcn/ui](https://ui.shadcn.com) (Radix primitives) | Latest |
| **Animation** | [Framer Motion](https://www.framer.com/motion) | 12.23.24 |
| **Routing** | [wouter](https://github.com/molefrog/wouter) | 3.3.5 |
| **Data Fetching** | [TanStack Query](https://tanstack.com/query) | 5.60.5 |
| **Forms** | [react-hook-form](https://react-hook-form.com) + Zod | Latest |
| **Charts** | [Recharts](https://recharts.org) | 2.15.4 |
| **Maps** | [Leaflet](https://leafletjs.com) + [MapLibre GL](https://maplibre.org) | Latest |
| **Icons** | [Lucide React](https://lucide.dev) | 0.545.0 |
| **Backend** | [Express.js](https://expressjs.com) | 5.0.1 |
| **Auth** | [Passport.js](http://www.passportjs.org) (local strategy) | 0.7.0 |
| **Database** | [Supabase](https://supabase.com) PostgreSQL | Latest |
| **ORM** | [Drizzle ORM](https://orm.drizzle.team) | 0.39.3 |
| **Real-time** | [Supabase Realtime](https://supabase.com/realtime) | Built-in |
| **Image Processing** | [Sharp](https://sharp.pixelplumbing.com) | 0.34.5 |
| **Telegram Bot** | [node-telegram-bot-api](https://github.com/yagop/node-telegram-bot-api) | 0.67.0 |
| **File Upload** | [Multer](https://github.com/expressjs/multer) | 2.0.2 |
| **Session Store** | memorystore | 1.6.7 |
| **Deployment** | [Vercel](https://vercel.com) + [GitHub Actions](https://github.com/features/actions) | — |
| **Language** | [TypeScript](https://www.typescriptlang.org) | 5.6.3 |

<br>

---

## 📦 Order Workflow

```mermaid
sequenceDiagram
    actor C as Customer
    participant S as Store
    participant B as Butcher
    participant D as Driver
    participant N as Notifications

    C->>S: Places Order
    S->>S: Status: "pending"
    S->>N: Notify all butchers
    N-->>B: 🔔 New order alert

    B->>S: استلام المهمة (Take Task)
    S->>S: Status: "preparing"
    S->>B: Butcher assigned
    B->>B: Process meat order
    B->>S: Mark as ready
    S->>S: Status: "ready"
    S->>N: Notify all drivers
    N-->>D: 🔔 Ready for delivery

    D->>S: Accept delivery
    S->>S: Status: "shipping"
    D->>C: Deliver order
    D->>S: Mark as delivered
    S->>S: Status: "completed"
    N-->>C: ✅ Order completed
```

### Status Flow

```
pending → preparing → ready → shipping → completed
                                     ↘ cancelled
```

Each status transition triggers:
1. **Database update** via Supabase REST API
2. **Notification insert** with user/staff targeting
3. **Real-time push** via WebSocket to all connected clients
4. **Toast notification** + sound in the dashboard

<br>

---

## 🚀 Setup & Installation

### Prerequisites
- **Node.js** 20+ ([Download](https://nodejs.org))
- **npm** 10+
- **Supabase** account ([Free tier](https://supabase.com))
- **Telegram Bot Token** (optional, for phone verification)

### 1️⃣ Clone & Install

```bash
git clone https://github.com/HSG116/almarah.git
cd almarah
npm install
```

### 2️⃣ Configure Environment

Create a `.env` file in the project root:

```env
# Supabase (Required)
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_KEY=your-service-role-key

# Session (Required)
SESSION_SECRET=your-secret-key

# Database (Optional - for Drizzle push)
DATABASE_URL=postgresql://postgres:password@host:5432/postgres

# Telegram Bot (Optional)
TELEGRAM_BOT_TOKEN=your-bot-token

# Port (Optional, defaults to 3000)
PORT=3000
```

### 3️⃣ Database Setup

Run the SQL scripts in order from the project root:
1. `SUPABASE_FINAL_SETUP.sql` — Tables & schemas
2. `POPULATE_DB.sql` — Seed categories + 42 products
3. `FIX_ORDER_WORKFLOW.sql` — Real-time triggers
4. `BUTCHER_INVENTORY_TABLES.sql` — Inventory tracking
5. `DELIVERY_SYSTEM_SETUP.sql` — Delivery zones

Or push with Drizzle:

```bash
npm run db:push
```

### 4️⃣ Run Development Server

```bash
npm run dev
```

This starts:
- 🖥️ **Vite dev server** on port 3000 (with HMR)
- ⚙️ **Express API server** on the same port
- 🤖 **Telegram bot** (if configured)

Open **http://localhost:3000** in your browser.

### 5️⃣ Build for Production

```bash
npm run build
npm start
```

<br>

---

## 🌐 Deployment

### Vercel (Frontend)

The frontend is deployed to **Vercel**:

```bash
vercel --prod
```

`vercel.json` rewrites all routes to `index.html` for SPA support.

### GitHub Actions (CI/CD)

The workflow `.github/workflows/pages.yml` auto-deploys on push to `main`.

### Environment Variables on Vercel

| Variable | Description |
|----------|-------------|
| `VITE_SUPABASE_URL` | Your Supabase project URL |
| `VITE_SUPABASE_ANON_KEY` | Your Supabase anonymous key |
| `SESSION_SECRET` | Session encryption secret |

<br>

---

## 📜 Legal Pages

The application includes full legal documentation built-in as editable pages via `site_settings`:

- **🔒 Privacy Policy** (`/legal/privacy`) — Data collection, storage, usage, and user rights
- **📋 Terms of Service** (`/legal/terms`) — Usage rules, liabilities, dispute resolution
- **🔄 Return Policy** (`/legal/copyright`) — Product return & refund terms

All legal content is configurable through the Admin Settings panel.

<br>

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

<br>

---

<p align="center">
  <strong>Built with ❤️ by HSG for the community</strong>
  <br><br>
  <a href="https://discord.com/users/1416151331965767810">💬 Join Discord</a> ·
  <a href="https://x.com/Moh_HSG">🐦 Follow on X</a>
  <br><br>
  <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/HSG116/almarah">
  <img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/HSG116/almarah">
  <img alt="GitHub stars" src="https://img.shields.io/github/stars/HSG116/almarah?style=social">
</p>
