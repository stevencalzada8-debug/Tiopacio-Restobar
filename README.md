# Tiopacio Restobar: Mobile Inventory & Stock Tracker

Complete Android Studio Java/XML inventory and operations tracker for a restobar running from 7:00 PM to 3:00 AM.

## What is included

- Android Java client with `LoginActivity`, `RegisterActivity`, `MainActivity`, profile/settings, fragments, RecyclerView adapters, Volley API calls, SharedPreferences session handling, role-based navigation, and light/dark theme switching.
- PHP/MySQL backend API using MySQLi prepared statements and JSON responses.
- SQL schema for `tiopacio_db`.

## Android setup

1. Open this folder in Android Studio.
2. Sync Gradle.
3. In `app/src/main/java/com/tiopacio/inventory/network/ApiConfig.java`, keep `http://10.0.2.2/tiopacio_api/` for the Android emulator. Use your machine IP for a physical Android device.
4. Run the app. `LoginActivity` is the launcher activity and will auto-open `MainActivity` when a saved session exists.

## Backend setup

1. Start XAMPP Apache and MySQL.
2. Create/import the database using `backend/sql/tiopacio_db.sql` in phpMyAdmin.
3. Copy all files in `backend/api` to `xampp/htdocs/tiopacio_api`.
4. Update database credentials in `backend/api/config.php` if your MySQL user/password differs.
5. Create an Admin account manually in the database. In-app registration intentionally allows only Manager, Staff, and Cashier.

## Revision migration

If you already imported the first version of the database, run `backend/sql/revision_2026_05_16.sql` in phpMyAdmin before using the revised app. It adds profile images, product images, item prices, daily earnings/losses, remaining-stock log fields, user/system logs, and updates supplier addresses to `Daet, Camarines Norte`.

After copying the revised PHP files, make sure `xampp/htdocs/tiopacio_api/uploads` is writable by Apache. Profile and product image uploads are saved there.

## Default role behavior

- Admin: full inventory, suppliers, reports, and operational access.
- Manager: inventory, suppliers, reports, deliveries, and stock auditing.
- Staff: inventory view plus usage/wastage logging.
- Cashier: limited inventory visibility.
