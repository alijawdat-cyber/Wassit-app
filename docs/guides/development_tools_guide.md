# 🛠️ دليل أدوات التطوير - تطبيق وسّط

> **دليل شامل لاستخدام كل أدوات التطوير المطلوبة للمشروع**

---

## 📋 فهرس الأدوات

### **✅ مثبت ومهيأ:**
- [📱 Xcode (للآيفون)](#-xcode-للآيفون)
- [🤖 Android Studio (للأندرويد)](#-android-studio-للأندرويد)
- [🌐 VS Code (التطوير الرئيسي)](#-vs-code-التطوير-الرئيسي)
- [🔥 Firebase CLI](#-firebase-cli)
- [⚡ FlutterFire CLI](#-flutterfire-cli)
- [🍎 CocoaPods (للآيفون)](#-cocoapods-للآيفون)

---

## 📱 **Xcode (للآيفون)**

### الاستخدام الأساسي:
```bash
# فتح محاكي الآيفون
open -a Simulator

# تشغيل التطبيق على الآيفون
flutter run -d ios

# بناء للإنتاج
flutter build ios --release
```

### المهام الرئيسية:
- **محاكي الآيفون للاختبار**
- **بناء وتصدير التطبيق للـ App Store**
- **إعداد certificates و profiles**
- **تصحيح أخطاء iOS المخصصة**

### أوامر مفيدة:
```bash
# فتح مشروع iOS في Xcode
open ios/Runner.xcworkspace

# تنظيف البناء
flutter clean && cd ios && pod install && cd ..

# عرض الأجهزة المتاحة
flutter devices
```

---

## 🤖 **Android Studio (للأندرويد)**

### الاستخدام الأساسي:
```bash
# تشغيل محاكي الأندرويد
flutter emulators --launch android

# تشغيل التطبيق على الأندرويد  
flutter run -d android

# بناء APK للإنتاج
flutter build apk --release
```

### المهام الرئيسية:
- **محاكي الأندرويد للاختبار**
- **إدارة SDK و AVD**
- **بناء وتصدير APK/Bundle**
- **إعداد توقيع التطبيق**

### أوامر مفيدة:
```bash
# إدارة المحاكيات
flutter emulators

# بناء App Bundle
flutter build appbundle --release

# تثبيت على جهاز متصل
flutter install
```

---

## 🌐 **VS Code (التطوير الرئيسي)**

### الإضافات المطلوبة:
- **Flutter & Dart extensions**
- **Firebase extensions**
- **Arabic language support**
- **GitLens للتحكم بالإصدارات**

### المهام الرئيسية:
- **كتابة وتحرير الكود**
- **تشغيل وتصحيح التطبيق**
- **إدارة Git وإصدارات الكود**
- **إدارة ملفات Firebase**

### اختصارات مفيدة:
```bash
# فتح أوامر Flutter
Cmd+Shift+P → Flutter

# تشغيل التطبيق
F5 أو Cmd+F5

# إعادة تحميل سريع
R في terminal

# إعادة تشغيل كامل
Shift+R في terminal
```

---

## 🔥 **Firebase CLI**

### أوامر التسجيل والإعداد:
```bash
# تسجيل دخول Firebase
firebase login

# عرض المشاريع المتاحة
firebase projects:list

# ربط المشروع الحالي
firebase use wassit-app-dca48

# عرض حالة المشروع
firebase use
```

### أوامر النشر:
```bash
# نشر Cloud Functions
firebase deploy --only functions

# نشر قواعد Firestore
firebase deploy --only firestore:rules

# نشر لوحة الإدارة (Hosting)
firebase deploy --only hosting

# نشر كل شيء
firebase deploy
```

### أوامر مفيدة أخرى:
```bash
# عرض لوجات المشروع
firebase functions:log

# محاكي محلي للتطوير
firebase emulators:start

# إعداد Firebase في مجلد
firebase init
```

---

## ⚡ **FlutterFire CLI**

### الإعداد الأولي:
```bash
# ربط Firebase مع Flutter (المرة الأولى)
flutterfire configure

# ربط مشروع محدد
flutterfire configure --project=wassit-app-dca48

# تحديث الإعدادات
flutterfire reconfigure
```

### أوامر الخدمات:
```bash
# إضافة Authentication
flutter pub add firebase_auth

# إضافة Firestore
flutter pub add cloud_firestore

# إضافة Cloud Messaging
flutter pub add firebase_messaging

# إضافة Analytics
flutter pub add firebase_analytics
```

### حل المشاكل:
```bash
# إعادة إنشاء ملف الإعدادات
rm lib/firebase_options.dart
flutterfire configure

# تحديث FlutterFire CLI
dart pub global activate flutterfire_cli
```

---

## 🍎 **CocoaPods (للآيفون)**

### أوامر التثبيت والتحديث:
```bash
# الانتقال لمجلد iOS
cd ios

# تثبيت/تحديث pods
pod install

# تحديث repositories
pod repo update

# تنظيف cache
pod cache clean --all
```

### حل مشاكل Dependencies:
```bash
# حذف Podfile.lock وإعادة التثبيت
rm Podfile.lock
pod install

# تحديث CocoaPods نفسه
sudo gem install cocoapods

# عرض pods المثبتة
pod list
```

### المهام الرئيسية:
- **إدارة مكتبات الآيفون**
- **حل مشاكل dependencies**
- **تحديث Firebase iOS SDK**
- **ربط المكتبات النشطة**

---

## 🚀 التدفق المطلوب للبدء

### 1. إعداد أول مشروع:
```bash
# إنشاء مشروع Flutter
flutter create wassit_app
cd wassit_app

# ربط Firebase
flutterfire configure --project=wassit-app-dca48

# تثبيت dependencies الأساسية
flutter pub get
cd ios && pod install && cd ..
```

### 2. اختبار التشغيل:
```bash
# تشغيل على الويب
flutter run -d web

# تشغيل على macOS
flutter run -d macos

# تشغيل على iOS (بعد فتح المحاكي)
flutter run -d ios
```

### 3. تسجيل دخول Firebase:
```bash
# تسجيل دخول Firebase
firebase login

# تأكيد ربط المشروع
firebase use wassit-app-dca48
```

---

## 🎯 حالة الأدوات الحالية

### **✅ جاهز للاستخدام:**
- **Flutter SDK:** 3.32.0 ✅
- **Dart SDK:** 3.8.0 ✅  
- **Firebase CLI:** 14.4.0 ✅
- **FlutterFire CLI:** 1.2.0 ✅
- **CocoaPods:** مثبت ✅
- **Xcode:** 16.3 ✅
- **VS Code:** متوفر ✅

### **🔄 قيد الإعداد:**
- **Android Studio:** 2024.3.2.14 (90% مكتمل)

### **📱 للتطوير المتاح الآن:**
- ✅ **iOS Development** - جاهز بالكامل
- ✅ **Web Development** - جاهز بالكامل  
- ✅ **macOS Desktop** - جاهز بالكامل
- 🔄 **Android Development** - جاهز بعد انتهاء تحميل Android Studio

---

## ⚠️ مشاكل شائعة وحلولها

### **مشاكل Flutter:**
```bash
# مشكلة packages
flutter clean
flutter pub get

# مشكلة build
flutter clean
flutter pub get
cd ios && pod install && cd ..
```

### **مشاكل Firebase:**
```bash
# مشكلة ربط
flutterfire configure

# مشكلة authentication
firebase login --reauth
```

### **مشاكل iOS:**
```bash
# مشكلة pods
cd ios
rm Podfile.lock
pod install
```

---

**📅 آخر تحديث:** 24 مايو 2025  
**🎯 الحالة:** جاهز للبدء بالتطوير  
**📱 المنصات الجاهزة:** iOS, Web, macOS 