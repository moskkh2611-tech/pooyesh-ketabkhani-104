# پویش کتابخوانی ۱.۰.۴ - راهنمای ساخت APK اندروید

## اصلاحات نسخه
- چیدمان خودکار بر اساس جهت صفحه: portrait (عمودی) و landscape (افقی).
- گزینه تنظیمات مدیر برای خاموش‌کردن صفحه ورود/رمز. در حالت بدون رمز، برنامه با حساب مدیر فعال باز می‌شود؛ این گزینه فقط برای دستگاه شخصی/محیط کنترل‌شده توصیه می‌شود.
- فایل وب در `www/index.html` برای بسته‌بندی Capacitor قرار دارد.

## پیش‌نیاز ساخت APK
- Node.js (نسخه LTS)
- Android Studio و Android SDK
- JDK موردنیاز Android Studio

## ساخت
1. در پوشه پروژه، Terminal باز کنید.
2. اجرا:
   ```bash
   npm install
   npx cap add android
   npx cap sync android
   npx cap open android
   ```
3. پس از ایجاد Android project، در فایل `android/app/src/main/AndroidManifest.xml` روی Activity اصلی (معمولاً `.MainActivity`) این ویژگی را اضافه کنید تا چرخش خودکار پشتیبانی شود:
   ```xml
   android:screenOrientation="fullSensor"
   ```
   اگر `screenOrientation` از قبل دارد، مقدار آن را به `fullSensor` تغییر دهید.
4. Android Studio: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. APK خروجی را از مسیر `android/app/build/outputs/apk/debug/app-debug.apk` بردارید.

## نکات مهم
- کتابخانه همچنان پایگاه داده محلی IndexedDB دارد؛ داده‌ها خودکار بین گوشی‌ها همگام نمی‌شوند.
- حالت بدون رمز امنیت ورود را حذف می‌کند؛ هر شخص دارای دسترسی به گوشی می‌تواند داده‌ها را ببیند یا تغییر دهد.
- بعضی خروجی‌های Excel/PDF به کتابخانه‌های آنلاین وابسته‌اند و برای آن قابلیت‌ها اینترنت لازم است.
- این بسته پروژه آماده‌سازی‌شده برای ساخت APK است، نه APK کامپایل‌شده. ساخت APK در محیط فعلی به دلیل نبود Android SDK/Gradle انجام نشده است.


## ساخت خودکار با GitHub Actions

فایل workflow در `.github/workflows/build-apk.yml` قرار دارد. بعد از Commit کردن پروژه، تب Actions را باز کنید و artifact خروجی را دانلود کنید.


## نسخه ۱.۰.۴
- رده سنی اکنون امکان انتخاب هم‌زمان چند گزینه را دارد.
- با انتخاب «سایر»، فیلد اختیاری برای واردکردن سن عددی نمایش داده می‌شود.
