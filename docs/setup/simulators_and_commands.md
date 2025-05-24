# 📱 دليل المحاكيات وأوامر التشغيل - Wassit App

> **دليل شامل لكل أوامر تشغيل المحاكيات والمنصات مع المسارات الواضحة**

---

## 🎯 الحالة الحالية للمحاكيات

### **✅ المحاكيات الجاهزة والعاملة:**

#### **🍎 iOS Simulator (iPhone 16 Pro)**
```
الحالة: ✅ جاهز ويعمل
المعرف: D89DBDEB-9307-4745-9EAC-2A92995F2A4C
iOS Version: 18.4 (22E238)
الجهاز: iPhone 16 Pro
```

#### **🤖 Android Emulator**
```
الحالة: ✅ جاهز ويعمل  
المعرف: sdk gphone64 arm64
الجهاز: Android SDK built for arm64
```

#### **🌐 Web Browser (Chrome)**
```
الحالة: ✅ جاهز ويعمل
المتصفح: Chrome
```

#### **💻 macOS Desktop**
```
الحالة: ✅ جاهز ويعمل (Native)
النظام: macOS 24.5.0
```

---

## 🚀 أوامر تشغيل المحاكيات

### **📋 قائمة كل الأجهزة المتاحة:**
```bash
# عرض كل الأجهزة المتاحة
flutter devices

# عرض المحاكيات المتاحة فقط
xcrun simctl list devices available

# التحقق من حالة الأجهزة
flutter doctor
```

### **🍎 أوامر iOS Simulator:**

#### **تشغيل محاكي iPhone:**
```bash
# تشغيل iPhone 16 Pro (الافتراضي)
flutter run -d "iPhone 16 Pro"

# أو باستخدام المعرف
flutter run -d D89DBDEB-9307-4745-9EAC-2A92995F2A4C

# تشغيل محاكي iPhone يدوياً
xcrun simctl boot "iPhone 16 Pro"

# فتح تطبيق Simulator
open -a Simulator

# إيقاف المحاكي
xcrun simctl shutdown "iPhone 16 Pro"
```

#### **محاكيات iPhone المتاحة:**
```bash
# iPhone 16 Pro ✅
xcrun simctl boot "iPhone 16 Pro"

# iPhone 15 Pro
xcrun simctl boot "iPhone 15 Pro"

# iPhone 14 Pro  
xcrun simctl boot "iPhone 14 Pro"

# iPhone SE (3rd generation)
xcrun simctl boot "iPhone SE (3rd generation)"
```

#### **محاكيات iPad المتاحة:**
```bash
# iPad Pro (13-inch) (M4)
xcrun simctl boot "iPad Pro (13-inch) (M4)"

# iPad Pro (11-inch) (M4)
xcrun simctl boot "iPad Pro (11-inch) (M4)"

# iPad Air (13-inch) (M2)
xcrun simctl boot "iPad Air (13-inch) (M2)"
```

### **🤖 أوامر Android Emulator:**

#### **تشغيل محاكي Android:**
```bash
# تشغيل على محاكي Android الافتراضي
flutter run -d android

# أو بالاسم المحدد
flutter run -d "sdk gphone64 arm64"

# قائمة محاكيات Android المتاحة
emulator -list-avds

# تشغيل محاكي معين
emulator -avd [اسم_المحاكي]
```

### **🌐 أوامر Web Browser:**

#### **تشغيل على المتصفح:**
```bash
# تشغيل على Chrome (الافتراضي)
flutter run -d chrome

# تشغيل على Firefox
flutter run -d firefox

# تشغيل على Safari (macOS فقط)
flutter run -d safari

# تشغيل مع port محدد
flutter run -d chrome --web-port=8080
```

### **💻 أوامر macOS Desktop:**

#### **تشغيل على سطح المكتب:**
```bash
# تشغيل على macOS
flutter run -d macos

# بناء التطبيق للـ macOS
flutter build macos
```

---

## 🎮 أوامر التطوير المتقدمة

### **🔥 Hot Reload والتطوير:**
```bash
# تشغيل مع Hot Reload
flutter run -d [اسم_الجهاز]

# أثناء التشغيل:
# r - Hot reload
# R - Hot restart  
# q - إنهاء التشغيل
# h - عرض المساعدة
```

### **🛠️ أوامر Build للمنصات:**
```bash
# بناء للـ iOS
flutter build ios

# بناء للـ Android
flutter build apk
flutter build appbundle

# بناء للـ Web
flutter build web

# بناء للـ macOS
flutter build macos
```

### **📊 أوامر التشخيص:**
```bash
# فحص حالة Flutter
flutter doctor -v

# فحص الأجهزة المتصلة
flutter devices -v

# تنظيف المشروع
flutter clean

# تحديث الحزم
flutter pub get
flutter pub upgrade
```

---

## 📁 مسارات مهمة

### **🔧 مسارات Flutter:**
```bash
# مسار Flutter SDK
which flutter
# النتيجة: /opt/homebrew/bin/flutter

# مسار Dart SDK  
which dart
# النتيجة: /opt/homebrew/bin/dart

# مجلد المشروع
cd "/Users/alijawdat/Downloads/wassit app/wassit_app"
```

### **🍎 مسارات iOS:**
```bash
# مسار Xcode
xcode-select -p
# النتيجة: /Applications/Xcode.app/Contents/Developer

# مسار iOS Simulators
~/Library/Developer/CoreSimulator/Devices/

# مسار CocoaPods
which pod
# النتيجة: /opt/homebrew/bin/pod
```

### **🤖 مسارات Android:**
```bash
# مسار Android SDK (عادة)
$HOME/Library/Android/sdk

# مسار Android Studio
/Applications/Android Studio.app

# مسار AVD Manager
~/Library/Android/avd/
```

---

## 🎯 أوامر تشغيل سريعة

### **🚀 الأوامر الأكثر استخداماً:**

```bash
# 1. التحقق من الأجهزة المتاحة
flutter devices

# 2. تشغيل على iPhone
flutter run -d "iPhone 16 Pro"

# 3. تشغيل على Android  
flutter run -d android

# 4. تشغيل على الويب
flutter run -d chrome

# 5. تشغيل على macOS
flutter run -d macos

# 6. فحص حالة النظام
flutter doctor

# 7. تنظيف وإعادة تشغيل
flutter clean && flutter pub get && flutter run
```

---

## 🔄 سيناريوهات التشغيل

### **🎯 السيناريو 1: تطوير للـ iOS**
```bash
# 1. التأكد من تشغيل Simulator
open -a Simulator

# 2. تشغيل iPhone 16 Pro
xcrun simctl boot "iPhone 16 Pro"

# 3. تشغيل التطبيق
cd "/Users/alijawdat/Downloads/wassit app/wassit_app"
flutter run -d "iPhone 16 Pro"
```

### **🎯 السيناريو 2: تطوير للـ Android**
```bash
# 1. تشغيل Android Emulator (إذا لم يكن يعمل)
emulator -list-avds
emulator -avd [اسم_المحاكي]

# 2. تشغيل التطبيق
cd "/Users/alijawdat/Downloads/wassit app/wassit_app"
flutter run -d android
```

### **🎯 السيناريو 3: تطوير للويب**
```bash
# 1. تشغيل مباشر
cd "/Users/alijawdat/Downloads/wassit app/wassit_app"
flutter run -d chrome --web-port=3000

# 2. فتح في المتصفح:
# http://localhost:3000
```

### **🎯 السيناريو 4: اختبار على كل المنصات**
```bash
cd "/Users/alijawdat/Downloads/wassit app/wassit_app"

# تشغيل متتالي على كل المنصات
echo "🍎 اختبار iOS..."
flutter run -d "iPhone 16 Pro" &

echo "🤖 اختبار Android..." 
flutter run -d android &

echo "🌐 اختبار Web..."
flutter run -d chrome &

echo "💻 اختبار macOS..."
flutter run -d macos &
```

---

## ⚠️ حل المشاكل الشائعة

### **🔴 مشكلة: iOS Simulator لا يعمل**
```bash
# 1. إعادة تشغيل Simulator
sudo xcrun simctl shutdown all
sudo xcrun simctl erase all

# 2. إعادة تشغيل نظيف
xcrun simctl boot "iPhone 16 Pro"
open -a Simulator
```

### **🔴 مشكلة: Android Emulator بطيء**
```bash
# 1. تسريع الأداء
emulator -avd [اسم_المحاكي] -gpu host

# 2. زيادة الذاكرة
emulator -avd [اسم_المحاكي] -memory 4096
```

### **🔴 مشكلة: Flutter لا يكتشف الجهاز**
```bash
# 1. إعادة تشغيل Flutter daemon
flutter daemon --stop
flutter daemon

# 2. تنظيف وإعادة التشغيل
flutter clean
flutter pub get
flutter devices
```

### **🔴 مشكلة: Hot Reload لا يعمل**
```bash
# 1. إعادة تشغيل التطبيق
# اضغط 'R' في terminal

# 2. إعادة تشغيل كامل
flutter clean
flutter pub get
flutter run
```

---

## 📊 معلومات المنصات

### **🍎 iOS Platform:**
```
✅ Xcode: 16.3
✅ iOS Simulator: 18.4 (22E238)
✅ CocoaPods: مثبت
✅ iPhone Models: 16 Pro, 15 Pro, 14 Pro, SE
✅ iPad Models: Pro 13", Pro 11", Air 13"
```

### **🤖 Android Platform:**
```
✅ Android Studio: مثبت
✅ Android SDK: محدث
✅ Emulator: sdk gphone64 arm64
✅ Build Tools: آخر إصدار
```

### **🌐 Web Platform:**
```
✅ Chrome: محدث
✅ Firefox: متاح
✅ Safari: متاح (macOS)
✅ Hot Reload: مفعل
```

### **💻 macOS Platform:**
```
✅ macOS: 24.5.0 (Native)
✅ Flutter Desktop: مفعل
✅ Build Tools: جاهز
```

---

## 🎉 تقرير نجاح الإعداد

### **📊 نسبة الإنجاز: 100%**

#### **✅ تم بنجاح:**
- **4 منصات جاهزة للتطوير**
- **كل المحاكيات تعمل**
- **Firebase مربوط بالكامل**
- **بيئة التطوير مكتملة**

#### **🎯 الإنجازات:**
1. **iOS Simulator:** iPhone 16 Pro يعمل ✅
2. **Android Emulator:** sdk gphone64 arm64 يعمل ✅
3. **Web Browser:** Chrome يعمل ✅
4. **macOS Desktop:** Native يعمل ✅
5. **Flutter Project:** مُنشأ ومُعد ✅
6. **Firebase Integration:** مكتمل ✅

---

## 🚀 الخطوات التالية

### **💻 جاهز للتطوير:**
```bash
# البدء بتطوير تطبيق Wassit
cd "/Users/alijawdat/Downloads/wassit app/wassit_app"

# اختيار منصة التطوير المفضلة
flutter run -d "iPhone 16 Pro"    # للـ iOS
flutter run -d android             # للـ Android  
flutter run -d chrome              # للـ Web
flutter run -d macos               # للـ macOS
```

### **📋 المهام القادمة:**
1. **تطوير شاشة Splash**
2. **تطوير شاشة تسجيل الدخول**
3. **ربط Firebase Authentication**
4. **اختبار على كل المنصات**

---

**📅 آخر تحديث:** 24 مايو 2025  
**🎯 الحالة:** كل المحاكيات جاهزة وتعمل 100%  
**⏭️ التالي:** بدء التطوير الفعلي للتطبيق  
**📊 نسبة الإنجاز:** 100% من إعداد المحاكيات 