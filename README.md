# Alkamal Library — Medical Bookstore App

A full-stack, cross-platform e-commerce and e-learning app for a medical bookstore, built with **Flutter** and **Firebase**. It ships a customer-facing storefront and a separate admin dashboard from a single codebase, targeting **Android, iOS, Web, Windows, macOS, and Linux**.

<p align="center">
  <img src="assets/store/feature_1024x500.png" alt="Alkamal Library" width="640">
</p>

![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-3.11-0175C2?logo=dart&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%7C%20Auth%20%7C%20Functions-FFCA28?logo=firebase&logoColor=black)
![Platforms](https://img.shields.io/badge/Platforms-Android%20%7C%20iOS%20%7C%20Web%20%7C%20Windows%20%7C%20macOS%20%7C%20Linux-4CAF50)

> ~29,000 lines of Dart across 60+ screens/services, plus a Node.js Cloud Functions backend with 16 callable/trigger functions.

---

## Features

### Customer app
- **Storefront** — browse medical books and supplies, product details, full-text search, cart, and checkout.
- **Ordering** — place orders, track status in real time, cancel a pending order within 1 hour, promo-code validation.
- **Delivery** — interactive map (OpenStreetMap via `flutter_map` + geolocation), saved addresses, and zone-based delivery fees.
- **E-learning** — browse lectures by academic year/subject, and order **printed lectures** (upload a PDF, preview the print job, see per-page pricing).
- **Auth** — phone-number OTP sign-in with App Check protection.
- **Engagement** — push notifications (new products, restocks, order status), an in-app **RAG chatbot** for support, onboarding, and force-update gating.

### Admin dashboard
- Manage products and supplies (create/edit with image upload to Firebase Storage).
- Manage lectures: single and **batch upload**, drag-to-reorder, auto lecture numbering, subject management.
- Web/desktop admin shell with a dedicated login, deployed as a hosted web app.
- Send targeted push notifications to customer segments.

---

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | Flutter 3.x · Dart 3.11 · Material 3 |
| State / storage | `shared_preferences`, `cached_network_image` |
| Backend | Firebase Cloud Functions (Node.js) — 16 functions |
| Database | Cloud Firestore (with security rules & composite indexes) |
| Files | Firebase Storage |
| Auth | Firebase Auth (phone OTP) + App Check + custom claims |
| Messaging | Firebase Cloud Messaging (push) |
| Maps | `flutter_map` + `geolocator` |
| Media | `video_player`, `pdfx` / PDF.js, `audioplayers` |
| Ops | Crashlytics, Analytics, connectivity handling |

**Cloud Functions** include: `placeOrder`, `validatePromo`, `ragChat` (RAG support bot), `grantAdminClaim`, `deleteMyAccount`, phone verification, and a suite of FCM notification triggers (`notifyOnNewProduct`, `notifyOnProductRestock`, `notifyStudentOnStatusChange`, `notifyDeliveryOnNewOrder`, `sendTargetedNotification`), plus scheduled cleanup of old print files.

---

## Architecture

```
lib/
├── main.dart              # Customer app entry point
├── main_admin.dart        # Admin dashboard entry point
├── app_theme.dart         # Theme & design tokens
├── screens/               # 25+ customer screens
│   └── admin/             # Admin dashboard screens
├── services/              # Firestore / backend access layer
├── widgets/               # Shared UI components
└── models/

functions/                 # Firebase Cloud Functions (Node.js backend)
firestore.rules            # Firestore security rules
storage.rules              # Storage security rules
firestore.indexes.json     # Composite indexes
```

The same Flutter codebase produces **two apps** via separate entry points: the student storefront (`main.dart`) and the admin dashboard (`main_admin.dart`), so business logic and UI components are shared while entry-specific concerns (e.g. admin session bootstrap) stay isolated.

---

## Source code

This is a portfolio overview. The full source code is kept in a private repository and is **available on request** — feel free to reach out for a walkthrough or a code sample.

---

## Author

**Muhannad Daboul** — Software Engineer / Automation Specialist.
Designed and built the full stack: Flutter clients for six platforms, Firestore data model and security rules, and the Node.js Cloud Functions backend.

---

<div dir="rtl">

## نبذة بالعربية

**مكتبة الكمال الطبية** — تطبيق متكامل لمكتبة طبية مبني بـ Flutter وFirebase، يعمل على ست منصّات (أندرويد، iOS، ويب، ويندوز، ماك، لينكس). يضمّ تطبيقاً للطلاب (تصفّح المنتجات والمستلزمات، سلة وشراء، تتبّع الطلبات، خرائط توصيل مع رسوم حسب المنطقة، محاضرات وطلبات طباعة PDF، مساعد دردشة RAG، وإشعارات)، ولوحة تحكم للمشرفين (إدارة المنتجات والمحاضرات مع رفع دفعات وإعادة ترتيب، وإرسال إشعارات موجّهة). الخلفية عبارة عن 16 دالة على Firebase Cloud Functions.

ملفات الإعدادات الحساسة (مفاتيح Firebase، توقيع التطبيق، سر الأدمن) **غير مرفوعة** لأسباب أمنية — تُضاف يدوياً عند الاستنساخ.

</div>
