# 🔖 Ekhsemli  — Coupon, Cashback & Rewards Platform

> A full-featured **coupon aggregation and cashback** platform built with **Laravel**,
> serving users through a **dynamic web frontend** and a **mobile REST API**.
> Integrated with the **Admitad affiliate network** for real cashback tracking and confirmation.

---

## ✨ Features

### 🌐 Web Frontend

- Browse stores, coupons, categories, and blog posts
- Universal search across stores and coupons
- OTP-based authentication (login / register)
- User profile management and favorites
- Coupon effectiveness voting (public + authenticated)
- Newsletter subscription
- Multi-language support (Arabic / English)
- Contact us, FAQ, Privacy, Terms pages

### 📱 Mobile API

- OTP-based auth — register, login, forget/reset password
- Cashback order confirmation and order history
- Rewards system — browse, redeem, and view brand rewards
- Coupon effectiveness voting
- Favourites toggle and listing
- Invitation system with referral tracking
- Push notification management (FCM)

### 🛠️ Admin Dashboard

- Full management: Users, Brands, Coupons, Categories, Blog, Rewards
- Role-based staff permissions
- Custom permission mapping (route → friendly name)
- Admitad cashback status management and reporting
- Multi-language support (Arabic / English)

---

## 👤 My Role

Joined the project mid-flight as the **backend developer** responsible for:

- **Frontend → Blade Migration**: Converted the entire static HTML/CSS/JS
website into a fully dynamic Laravel Blade application with server-side
routing, auth, and localization and dynamic content with componsents and layouts and partials.
- **Mobile API — Phase 2**: Designed and built the cashback confirmation,
rewards, brand rewards, coupon effectiveness, and invitation endpoints
consumed by the iOS and Android native apps.
- **Admitad Integration**: Built the full affiliate cashback integration
from scratch — custom HTTP client, postback handling, and status lifecycle.

---

## 🏗️ Tech Stack


| Layer       | Technology                                |
| ----------- | ----------------------------------------- |
| Backend     | Laravel 9 (PHP 8.1)                              |
| Auth        | Laravel Sanctum + OTP (SMS)               |
| Admin UI    | Blade + Yajra DataTables                  |
| Permissions | Role-based with route mapping with spatie |
| i18n        | Laravel Localization (AR / EN)            |
| Push        | Firebase Cloud Messaging (FCM)            |
| Affiliate   | Admitad Integration                       |


---

## 📐 Architecture

```
├── app/
│   ├── Http/Controllers/
│   │   ├── Front/          # Web frontend controllers
│   │   ├── Admin/          # Admin dashboard controllers
│   │   └── API/            # Mobile API (V2 + V3)
│   ├── Core/
│   │   ├── Services/       # Business logic layer
│   │   ├── Datatables/     # Yajra DataTable definitions
│   │   ├── Enums/          # Type-safe constants
│   │   └── Helpers/        # Firebase, media, Admitad
└── resources/views/        # Blade templates (web + admin)
```

---

## 🧩 Technical Challenges & Solutions

### 1. Route-Based Permissions → Human-Readable UI

**Challenge:** The permission system was built on raw route identifiers —
no friendly names. The admin UI needed to show readable,
controllable permission labels to staff managers.

**Solution:** Built a mapping layer that translates internal route keys
into human-readable permission names, allowing the admin panel
to display and manage permissions cleanly without refactoring
the underlying auth layer.

---

### 2. Admitad Cashback Integration

**Challenge:** Integrating with Admitad's affiliate network from scratch —  
with difficult documentation. The system needed to handle postback events  
and transition cashback records through states  
(`waiting → pending → confirmed`) based on the network's response.

**Solution:** Built a full custom integration **without any third-party package** —
including a direct HTTP client to Admitad's API endpoints and a postback handler
that validates incoming events, maps status codes to internal cashback states,
and updates records accordingly — with full logging for every transition.

---

### 3. Live Production DB Migrations & Data Backfilling

**Challenge:** Schema changes and data transformations had to run on a
live production database with real users — requiring safe, non-destructive
operations on existing records.

**Solution:** Used chunked processing, upserts, and targeted Artisan commands
to safely transform and backfill production data. For example, generating and
assigning unique referral codes to all existing users without downtime —
with collision-safe generation logic that retries until a truly unique code
is found across the full dataset.

---

## 📸 Screenshots

### 🖥️ Admin Dashboard

---

### 📱 Mobile App

---



## 📄 License

Private commercial project — source shared for **portfolio purposes only**.
Not for redistribution or reuse.
