# متطلبات المشروع والحسابات المطلوبة 📋

**مرجع شامل لكل الأدوات والحسابات اللي نحتاجها لتطبيق وسّط**

---

## 🎯 **أولوية الحسابات (حسب مراحل التطوير)**

### **المرحلة 1: الضروري جداً (للبدء) 🔴**
- [x] **حساب Google** (مجاني) - للوصول لكل خدمات Google  
  📧 **الحساب:** alijawdat4@gmail.com ✅  
  📅 **تاريخ الإنجاز:** متوفر مسبقاً
- [x] **Firebase Console** (مجاني + مدفوع) - قاعدة البيانات والخدمات  
  🔥 **المشروع:** wassit-app ✅  
  🆔 **Project ID:** wassit-app-dca48 ✅  
  🔢 **Project Number:** 7669276356 ✅  
  📅 **تاريخ الإنجاز:** ديسمبر 2024  
  🔧 **الخدمات المفعلة:**
    - [x] Authentication (Phone) ✅ مع رقم اختبار عراقي
    - [x] Cloud Firestore Database ✅ (Test mode)
    - [x] Google Analytics ✅
    - [x] Cloud Messaging ✅
    - [ ] Storage ⏸️ (مؤجل - مشكلة البطاقة الائتمانية)
    - [ ] Cloud Functions (غير ضروري للبداية)
- [x] **GitHub** (مجاني) - حفظ الكود  
  👤 **الحساب:** alijawdat-cyber ✅  
  📦 **Repository:** WASSIT موجود بالفعل ✅  
  📅 **تاريخ الإنجاز:** متوفر مسبقاً
- [ ] **Flutter SDK** (مجاني) - بيئة التطوير  
  📍 **الحالة:** جاهز للتثبيت  
  🎯 **الأولوية:** المهمة التالية المباشرة ⚡

### **المرحلة 2: مهم للتطوير (خلال أول شهر) 🟡**
- [ ] **Android Developer Account** ($25 مرة واحدة) - نشر على Play Store
- [ ] **Apple Developer Account** ($99 سنوياً) - نشر على App Store
- [ ] **SMS Gateway Provider** ($20-50 شهرياً) - إرسال رموز التحقق  
  ✅ **حالياً:** Firebase Phone Auth مع 10 رسائل/يوم (كافي للتطوير)
- [ ] **Firebase Billing Account** (حسب الاستخدام) - لـ Storage والخدمات المتقدمة  
  ⚠️ **مشكلة:** البطاقات العراقية غير مدعومة، يحتاج حل بديل

### **المرحلة 3: للتشغيل والتوسع (بعد الإطلاق) 🟢**
- [ ] **Firebase Paid Plan** ($25+ شهرياً) - عند زيادة الاستخدام
- [ ] **Domain Name** ($10-15 سنوياً) - للوحة الإدارة
- [ ] **SSL Certificate** (مجاني مع Firebase Hosting)
- [ ] **Analytics Tools** (اختياري)

---

## 📊 **حالة المشروع الحالية - ديسمبر 2024**

### **✅ تم إنجازه بنجاح (Phase 0 & 1):**
```
✅ Phase 0: التخطيط والوثائق (100%)
   - TODO.md (200+ مهمة منظمة عبر 15 مرحلة)
   - README.md (نظرة عامة شاملة للمشروع)
   - REQUIREMENTS.md (هذا الملف)
   - docs/ (الوثائق التقنية الأساسية)

✅ Phase 1: إعداد Firebase Services الأساسية (80%)
   - Firebase Project ✅ (wassit-app-dca48)
   - Authentication ✅ (Phone verification + رقم اختبار عراقي)
   - Cloud Firestore Database ✅ (Test mode)
   - Google Analytics ✅ (مفعل ويعمل)
   - Cloud Messaging ✅ (للإشعارات)
   - Storage ⏸️ (مؤجل - مشكلة billing)
```

### **🔄 الوضع الحالي:**
```
✅ Firebase Core Services جاهزة للتطوير:
- تسجيل المستخدمين ✅
- قاعدة البيانات ✅  
- الإشعارات ✅
- التحليلات ✅

⏸️ Storage مؤجل:
- سبب التأجيل: مشكلة في إضافة بطاقة ائتمان عراقية
- البديل المؤقت: استخدام Firestore لروابط الصور
- خطة الحل: استخدام بطاقة دولية أو Payoneer لاحقاً
```

### **⏭️ المرحلة التالية (Phase 2):**
```
🎯 إعداد بيئة التطوير:
1. تثبيت Flutter SDK (الأولوية الأولى)
2. تثبيت Android Studio
3. إعداد iOS development environment
4. إنشاء Flutter project الأساسي
5. ربط Firebase مع التطبيق
```

---

## 💰 **التكاليف المتوقعة**

### **التكلفة الابتدائية (أول 3 أشهر):**
```
Google Play Store       = $25 (مرة واحدة)
Apple App Store        = $99 (سنوياً)
SMS Provider           = $60 (3 أشهر × $20) - مؤجل
Domain Name            = $15 (سنوياً) - مؤجل
Firebase (Free Tier)   = $0 ✅ مستخدم حالياً
─────────────────────────────────────
المجموع                = $139 (مخفض من $199)
```

### **التكلفة الشهرية (بعد الإطلاق):**
```
SMS Provider           = $20-50 (مؤجل)
Firebase Paid Plan     = $25-100 (حسب الاستخدام)
─────────────────────────────────────
المجموع الشهري         = $25-100 (مخفض بسبب تأجيل SMS)
```

### **📈 التكلفة الحالية والوفورات:**
```
إجمالي المصروف حتى الآن: $0 ✅
الوفورات المحققة: $60 (تأجيل SMS و Storage)
Firebase: Free Tier (Spark Plan) - يكفي للشهور الأولى
GitHub: مجاني
Google Account: مجاني
SMS: 10 رسائل مجانية يومياً (كافية للاختبار)
```

---

## 🔧 **الأدوات والبرامج المطلوبة**

### **بيئة التطوير - مجاني (المرحلة التالية)**
- [ ] **Flutter SDK 3.19+** - https://flutter.dev/docs/get-started/install  
  📍 **الحالة:** جاهز للتثبيت (الأولوية الأولى)  
  ⏱️ **وقت التثبيت:** ~15 دقيقة
- [ ] **Android Studio** - https://developer.android.com/studio  
  📍 **الحالة:** جاهز للتثبيت (الثانية)  
  ⏱️ **وقت التثبيت:** ~30 دقيقة
- [ ] **VS Code** (اختياري) - https://code.visualstudio.com/  
  📍 **الحالة:** بديل خفيف لـ Android Studio
- [x] **Xcode** (لـ iOS على Mac) - مجاني من App Store  
  📍 **نظام التشغيل:** macOS 24.5.0 ✅ متوافق  
  📍 **الحالة:** يحتاج تثبيت من App Store
- [x] **Git** - https://git-scm.com/  
  📍 **الحالة:** متوفر من خلال terminal ✅

### **أدوات التصميم - مجاني/مدفوع (لاحقاً)**
- [ ] **Figma** (مجاني للاستخدام الشخصي) - للتصميم
- [ ] **Canva** (مجاني + مدفوع) - لتصميم الشعار والمواد التسويقية
- [ ] **Adobe XD** (مجاني) - بديل للتصميم

---

## 🔑 **دليل إنشاء الحسابات (خطوة بخطوة)**

### **1. حساب Google (مجاني) - الأولوية الأولى** ✅
```
✅ الحساب المستخدم: alijawdat4@gmail.com
✅ الوصول لكل خدمات Google متاح
✅ التحقق بخطوتين مفعل (مطلوب)
✅ هذا الحساب مستخدم لكل شي في المشروع
```

### **2. Firebase Console - الأولوية الأولى** ✅
```
📍 الرابط: https://console.firebase.google.com/
✅ المشروع: wassit-app (wassit-app-dca48)
✅ الخدمات المفعلة والجاهزة:
   - Authentication ✅ (Phone verification)
     * رقم اختبار عراقي: +964 771 995 6000
     * كود التحقق: 482785
     * حد يومي: 10 رسائل (كافي للتطوير)
   - Cloud Firestore ✅ (Test mode لمدة 30 يوم)
     * قواعد الأمان: مفتوحة للتطوير
     * المنطقة: nam5 (United States)
   - Google Analytics ✅ (تتبع المستخدمين)
   - Cloud Messaging ✅ (الإشعارات)
   
⏸️ الخدمات المؤجلة:
   - Storage (مشكلة billing account)
   - Cloud Functions (غير ضروري للبداية)
   
💰 الحالة: Spark Plan (مجاني)
📊 الاستخدام: ضمن الحدود المجانية
🕒 مدة Test Mode: 30 يوم (تنتهي يناير 2025)
```

### **3. GitHub - الأولوية الأولى** ✅
```
📍 الرابط: https://github.com/
✅ الحساب: alijawdat-cyber
✅ Repository: WASSIT موجود ومرتبط
✅ Git متصل بالمشروع المحلي
✅ الفروع: main branch جاهز
   
💰 التكلفة: مجاني للمشاريع العامة والخاصة
📁 مجلد العمل: `/Users/alijawdat/Downloads/wassit app`
```

### **4. Google Play Console - الأولوية الثانية** ⏸️
```
📍 الرابط: https://play.google.com/console/
📋 متطلبات:
   - حساب Google (جاهز ✅)
   - دفع $25 (مرة واحدة)
   - معلومات شخصية وبنكية
   - وثائق الهوية (قد تطلب)
   
💰 التكلفة: $25 مرة واحدة
⏰ وقت المراجعة: 1-3 أيام
🎯 موعد الإنشاء: بعد اكتمال التطبيق الأساسي (Phase 4-5)
```

### **5. Apple Developer Program - الأولوية الثانية** ⏸️
```
📍 الرابط: https://developer.apple.com/programs/
📋 متطلبات:
   - Apple ID (يحتاج إنشاء)
   - دفع $99 سنوياً
   - معلومات شخصية أو شركة
   - جهاز Mac للتطوير ✅ (متوفر)
   
💰 التكلفة: $99 سنوياً
⏰ وقت المراجعة: 1-7 أيام
🎯 موعد الإنشاء: مع Google Play Console
```

### **6. Firebase Billing Account - مشكلة حالية** ⚠️
```
🚨 المشكلة: البطاقات الائتمانية العراقية غير مدعومة
📍 الخطأ: OR_MIVEM_02 (مشكلة في تفاصيل البطاقة)

🔧 الحلول المقترحة:
   Option 1: بطاقة Payoneer (الأفضل)
   - إنشاء حساب Payoneer
   - طلب بطاقة ماستركارد
   - استخدامها مع Google Cloud
   
   Option 2: بطاقة دولية من بنك آخر
   - البحث عن بنوك تدعم المعاملات الدولية
   - فتح حساب جديد مع بطاقة مفعلة دولياً
   
   Option 3: مساعدة من صديق/قريب
   - استخدام بطاقة شخص موثوق
   - تسديد المبالغ له نقداً
   
   Option 4: تأجيل مؤقت
   - الاستمرار مع Free Tier
   - حل المشكلة عند الحاجة الفعلية

💰 التكلفة المتوقعة: $0-50 شهرياً (حسب الاستخدام)
🎯 الأولوية: متوسطة (يمكن تأجيله لشهور)
```

### **7. SMS Gateway Provider - مؤجل مؤقتاً** ⏸️
```
🌍 للعراق - خيارات مقترحة:
   
   ✅ الخيار الحالي: Firebase Phone Auth
   💰 التكلفة: مجاني ✅
   📊 الحد: 10 رسائل يومياً
   📱 رقم الاختبار: +964 771 995 6000
   🔐 كود التحقق: 482785
   👍 المميزات: كافي للتطوير والاختبار
   
   🔜 للمستقبل:
   Option 1: Twilio
   📍 الرابط: https://www.twilio.com/
   💰 التكلفة: ~$0.05 لكل رسالة SMS
   
   Option 2: مزود محلي عراقي
   📞 التواصل مع شركات الاتصالات
   💰 التكلفة: متغيرة
   
🎯 القرار: البقاء مع Firebase حتى الحاجة لأرقام حقيقية
```

### **8. Domain Name - الأولوية الثالثة** ⏸️
```
🌍 مزودين مقترحين:
   
   Option 1: Namecheap
   📍 الرابط: https://www.namecheap.com/
   💰 التكلفة: $10-15 سنوياً
   
   Option 2: Cloudflare
   📍 الرابط: https://www.cloudflare.com/
   💰 التكلفة: $8-12 سنوياً
   
💡 اقتراحات أسماء:
   - wassitapp.com
   - wassit.app  
   - wassit-iraq.com
   
🎯 موعد الشراء: Phase 6-7 (بعد اكتمال التطبيق)
```

---

## 📊 **خطة التنفيذ المحدثة (مرحلياً)**

### **الأسبوع الأول - إعداد Firebase** ✅ مكتمل
- [x] ✅ إنشاء حساب Google (alijawdat4@gmail.com)
- [x] ✅ إنشاء حساب GitHub (alijawdat-cyber)
- [x] ✅ إنشاء repository WASSIT مع الوثائق
- [x] ✅ إنشاء مشروع Firebase (wassit-app-dca48)
- [x] ✅ إعداد Firebase Authentication (Phone)  
- [x] ✅ إعداد Cloud Firestore Database (Test mode)
- [x] ✅ تفعيل Google Analytics و Cloud Messaging
- [x] ✅ إضافة رقم اختبار عراقي (+964 771 995 6000)
- [ ] ⏸️ إعداد Firebase Storage (مؤجل - مشكلة billing)

### **الأسبوع الثاني - بيئة التطوير** 🎯 الحالي
- [ ] 📱 تثبيت Flutter SDK (الأولوية الأولى) ⚡
- [ ] 🔧 تثبيت Android Studio
- [ ] 📱 إعداد Android Emulator  
- [ ] 🍎 تثبيت Xcode من App Store
- [ ] 🍎 إعداد iOS Simulator
- [ ] 🚀 إنشاء Flutter project الأساسي
- [ ] 🔗 ربط Flutter مع Firebase
- [ ] 🧪 اختبار أول تطبيق بسيط

### **الأسبوع الثالث - التطوير الأساسي** ⏭️ قادم
- [ ] 🎨 تصميم الشاشات الأساسية (تسجيل دخول، الرئيسية)
- [ ] 🔐 تطبيق نظام التسجيل مع Firebase Auth
- [ ] 📊 ربط قاعدة البيانات مع التطبيق
- [ ] 🧪 اختبار الوظائف الأساسية

### **الأسبوع الرابع - التطوير المتقدم** ⏭️ قادم
- [ ] 👥 تطوير واجهات المستخدمين (عملاء، مزودين)
- [ ] 📝 نظام الطلبات والعروض
- [ ] 💬 نظام المحادثات الأساسي
- [ ] 📱 تجربة المستخدم وتحسينات الأداء

### **الشهر الثاني - التحضير للنشر** ⏸️ مؤجل
- [ ] 📱 إنشاء Google Play Console ($25)
- [ ] 🍎 إنشاء Apple Developer Account ($99)
- [ ] 🔐 حل مشكلة Firebase Billing Account
- [ ] 📨 إعداد SMS Provider للأرقام الحقيقية

---

## 🎯 **الخطوة التالية المباشرة - Flutter SDK**

### **الآن (ديسمبر 2024) - أولوية قصوى:**
```
1. 📱 تثبيت Flutter SDK على macOS
   - تحميل Flutter stable channel
   - إعداد PATH environment variables
   - تشغيل flutter doctor للتحقق
   
2. 🔧 تثبيت Android Studio
   - تحميل وتثبيت Android Studio
   - إعداد Android SDK
   - إنشاء Android Virtual Device
   
3. 🚀 إنشاء أول Flutter project
   - flutter create wassit_app
   - اختبار التشغيل على المحاكي
   - إضافة Firebase dependencies الأساسية
```

### **هذا الأسبوع - خطة مفصلة:**
```
اليوم 1: تثبيت Flutter SDK
اليوم 2: تثبيت Android Studio وإعداد AVD
اليوم 3: تثبيت Xcode وإعداد iOS Simulator  
اليوم 4: إنشاء Flutter project الأساسي
اليوم 5: ربط Firebase مع Flutter
اليوم 6-7: اختبار وتحسين بيئة التطوير
```

---

## ⚠️ **ملاحظات مهمة ومشاكل محلولة**

### **للأمان:**
- ✅ نفس الإيميل مستخدم لكل الحسابات المرتبطة بالمشروع
- ✅ التحقق بخطوتين مفعل لحساب Google الرئيسي
- ✅ Firebase Security Rules في Test mode (30 يوم)
- ⚠️ احتفظ بنسخة من كل كلمات المرور في مكان آمن

### **للدفع:**
- ⚠️ مشكلة البطاقات العراقية مع Google Cloud
- 💡 حلول بديلة: Payoneer، بطاقة دولية، مساعدة صديق
- ✅ تأجيل المدفوعات حتى ضرورة فعلية
- ✅ الاستفادة القصوى من Free Tier

### **لتوفير المال:**
- ✅ بدأنا بالخدمات المجانية بالكامل ($0 تكلفة)
- ✅ نستخدم Firebase Free Tier لأقصى حد ممكن
- ✅ أجلنا كل الحسابات المدفوعة لحين الحاجة الفعلية
- 💡 وفرنا $60 في أول 3 أشهر بتأجيل SMS وStorage

### **للتطوير:**
- 🖥️ نظام التشغيل: macOS 24.5.0 ✅ مثالي لتطوير iOS وAndroid
- 🐚 Shell: /bin/zsh ✅ متوافق مع أدوات التطوير الحديثة
- 📁 مجلد العمل: `/Users/alijawdat/Downloads/wassit app`
- 🔗 Git repository متصل ومحدث

### **Firebase Test Mode:**
- ⏰ مدة Test Mode: 30 يوم (حتى يناير 2025)
- 📊 بعد انتهاء Test Mode: تحديث Security Rules
- 🔒 خطة الأمان: تطبيق قوانين صارمة قبل الإنتاج

---

## 🚨 **الحد الأدنى للبدء (حققنا $0 تكلفة!)**

تمكنا من البدء بدون أي تكلفة مالية:

```
✅ مجاني ومفعل بالكامل:
- Google Account ✅
- Firebase Project (Spark Plan) ✅
- GitHub Repository ✅  
- Cloud Firestore Database ✅
- Phone Authentication ✅ (مع رقم اختبار عراقي)
- Google Analytics ✅
- Cloud Messaging ✅
- 10 SMS يومياً للاختبار ✅

🔜 قادم مجاناً:
- Flutter SDK (15 دقيقة تثبيت)
- Android Studio (30 دقيقة تثبيت)
- Xcode من App Store (60 دقيقة تثبيت)
- VS Code (اختياري)

💰 أول تكلفة فعلية:
- Google Play Console: $25 (عند جاهزية للنشر)
- Apple Developer: $99 (عند جاهزية للنشر)

المجموع المصروف حتى الآن: $0 ✅
المجموع المطلوب للإطلاق: $124 (مخفض من $199)
```

---

## 📈 **إحصائيات التقدم المحدثة**

### **Phase Completion (ديسمبر 2024):**
```
Phase 0 (Planning):     ████████████ 100% ✅
Phase 1 (Firebase):     ████████░░░░  80% ✅ (Storage مؤجل)
Phase 2 (Flutter):      ░░░░░░░░░░░░   0% ⚡ (التالي)
Phase 3 (UI/UX):        ░░░░░░░░░░░░   0% ⏸️
Phase 4 (Backend):      ░░░░░░░░░░░░   0% ⏸️
Phase 5 (Testing):      ░░░░░░░░░░░░   0% ⏸️
```

### **Services Status:**
```
✅ Authentication:      100% (Phone ready + test number)
✅ Database:            100% (Firestore Test mode ready)  
✅ Analytics:           100% (Google Analytics active)
✅ Messaging:           100% (Cloud Messaging ready)
⏸️ Storage:              0% (مؤجل - billing issue)
⏸️ Functions:            0% (غير ضروري للبداية)
⏸️ Hosting:              0% (للمواقع فقط)
```

### **Development Environment:**
```
🖥️ System:              ✅ macOS 24.5.0 (perfect for iOS)
🐚 Shell:               ✅ /bin/zsh (modern tools compatible)
📁 Workspace:           ✅ /Users/alijawdat/Downloads/wassit app
🔗 Git:                 ✅ Connected to GitHub
📱 Flutter:             🔄 Ready to install
🤖 Android Studio:      🔄 Ready to install  
🍎 Xcode:               🔄 Ready to install from App Store
```

---

## 📞 **الدعم والمساعدة**

### **مشاكل محتملة وحلولها:**
```
🚨 مشكلة البطاقة الائتمانية:
   - الحل المؤقت: تأجيل Storage
   - الحل النهائي: Payoneer أو بطاقة دولية
   
🚨 مشاكل تثبيت Flutter:
   - الوثائق الرسمية: https://flutter.dev/docs/get-started/install/macos
   - فيديوهات عربية: YouTube "تثبيت Flutter على Mac"
   
🚨 مشاكل Android Studio:
   - متطلبات النظام: 8GB RAM (متوفر)
   - مساحة فارغة: 4GB على الأقل
```

### **مصادر المساعدة:**
1. **الوثائق الرسمية** - Flutter.dev, Firebase.google.com
2. **فيديوهات عربية** - YouTube بحث "Flutter شرح عربي"
3. **المجتمعات** - Flutter Community، Firebase Community
4. **Stack Overflow** - للمشاكل التقنية المحددة

---

## 🎯 **الخلاصة والخطوة التالية**

### **✅ ما تم إنجازه:**
- إعداد Firebase Project بنجاح مع الخدمات الأساسية
- تحضير بيئة العمل والوثائق
- حل مشكلة التكاليف (وصلنا لـ $0)
- وضع خطة واضحة للمراحل القادمة

### **🎯 الخطوة التالية المباشرة:**
**تثبيت Flutter SDK على النظام** - هذا هو التركيز الكامل الآن

### **📅 الجدول الزمني:**
```
الآن → أسبوع واحد: إعداد بيئة التطوير (Flutter + Android Studio + Xcode)
أسبوع 2-3: تطوير التطبيق الأساسي
أسبوع 4: اختبار وتحسين
الشهر 2: التحضير للنشر
```

---

**آخر تحديث:** 24/12/2024 ✅  
**حالة المشروع:** Phase 1 مكتمل (80%) - Firebase جاهز للتطوير  
**التالي:** Phase 2 - تثبيت Flutter SDK وبداية التطوير الفعلي  
**التكلفة الحالية:** $0 (نجحنا في البدء مجاناً تماماً!) 🎉

---

## ✅ **الخطوة التالية**

**🎯 المهمة الآن:** تثبيت Flutter SDK وإنشاء أول تطبيق  
**⏱️ الوقت المقدر:** 1-2 ساعة  
**🎉 النتيجة:** تطبيق Flutter يعمل على Android و iOS  

**جاهز نبدأ تثبيت Flutter؟** 🚀 