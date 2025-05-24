# دليل التنفيذ التفصيلي - تطبيق وسّط (Wassit)
**مخصص للتنفيذ بواسطة Claude Sonnet 4**  
**التاريخ: 24/05/2025**  
**نوع الوثيقة: Implementation Guide for AI Assistant**

---

## مقدمة مهمة
هذه الوثيقة مصممة خصيصاً ليتم تنفيذها بواسطة Claude Sonnet 4. كل خطوة مكتوبة بشكل واضح ومحدد مع الأوامر والأكواد المطلوبة. التصميم سيتم مباشرة في الكود بدون استخدام أدوات تصميم خارجية.

---

## المرحلة 1: إعداد البيئة والمشروع (يوم 1-2)

### اليوم 1: إعداد المشروع الأساسي

#### 1.1 إنشاء مشروع Flutter
```bash
# إنشاء المشروع
flutter create wassit_app --org com.wassit --project-name wassit_app

# الانتقال للمجلد
cd wassit_app

# إضافة الحزم المطلوبة
flutter pub add firebase_core
flutter pub add firebase_auth
flutter pub add cloud_firestore
flutter pub add firebase_storage
flutter pub add firebase_messaging
flutter pub add firebase_analytics
flutter pub add firebase_crashlytics
flutter pub add dio
flutter pub add riverpod
flutter pub add flutter_riverpod
flutter pub add go_router
flutter pub add cached_network_image
flutter pub add image_picker
flutter pub add hive
flutter pub add hive_flutter
flutter pub add intl
flutter pub add shimmer
flutter pub add flutter_svg
flutter pub add google_fonts
flutter pub add flutter_native_splash
flutter pub add permission_handler
flutter pub add share_plus
flutter pub add url_launcher
```

#### 1.2 هيكل المجلدات
```
lib/
├── main.dart
├── app.dart
├── core/
│   ├── constants/
│   │   ├── app_colors.dart
│   │   ├── app_strings.dart
│   │   ├── app_assets.dart
│   │   └── app_dimensions.dart
│   ├── errors/
│   │   ├── exceptions.dart
│   │   └── failures.dart
│   ├── utils/
│   │   ├── validators.dart
│   │   ├── formatters.dart
│   │   └── helpers.dart
│   └── widgets/
│       ├── app_button.dart
│       ├── app_text_field.dart
│       └── loading_indicator.dart
├── features/
│   ├── auth/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   ├── requests/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   ├── offers/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   └── messages/
│       ├── data/
│       ├── domain/
│       └── presentation/
└── config/
    ├── router/
    │   └── app_router.dart
    ├── theme/
    │   └── app_theme.dart
    └── firebase/
        └── firebase_config.dart
```

#### 1.3 ملفات الأساس

**lib/core/constants/app_colors.dart:**
```dart
import 'package:flutter/material.dart';

class AppColors {
  // الألوان الأساسية
  static const Color primary = Color(0xFF1A73E8); // أزرق احترافي
  static const Color primaryDark = Color(0xFF0D47A1);
  static const Color primaryLight = Color(0xFF64B5F6);
  
  // الألوان الثانوية
  static const Color secondary = Color(0xFFFF6B6B); // أحمر دافئ
  static const Color accent = Color(0xFF4ECDC4); // تركوازي
  
  // ألوان النصوص
  static const Color textPrimary = Color(0xFF212121);
  static const Color textSecondary = Color(0xFF757575);
  static const Color textHint = Color(0xFFBDBDBD);
  
  // ألوان الخلفيات
  static const Color background = Color(0xFFF5F5F5);
  static const Color surface = Color(0xFFFFFFFF);
  static const Color divider = Color(0xFFE0E0E0);
  
  // ألوان الحالات
  static const Color success = Color(0xFF4CAF50);
  static const Color warning = Color(0xFFFFC107);
  static const Color error = Color(0xFFF44336);
  static const Color info = Color(0xFF2196F3);
  
  // ألوان التدرجات
  static const LinearGradient primaryGradient = LinearGradient(
    begin: Alignment.topLeft,
    end: Alignment.bottomRight,
    colors: [primary, primaryDark],
  );
}
```

**lib/core/constants/app_strings.dart:**
```dart
class AppStrings {
  // عناوين التطبيق
  static const String appName = 'وسّط';
  static const String appTagline = 'منصة الخدمات الموثوقة';
  
  // الأزرار العامة
  static const String next = 'التالي';
  static const String back = 'رجوع';
  static const String submit = 'إرسال';
  static const String cancel = 'إلغاء';
  static const String confirm = 'تأكيد';
  static const String save = 'حفظ';
  static const String edit = 'تعديل';
  static const String delete = 'حذف';
  
  // صفحة تسجيل الدخول
  static const String welcomeMessage = 'أهلاً بك في وسّط';
  static const String enterPhone = 'أدخل رقم هاتفك';
  static const String phoneHint = '07XX XXX XXXX';
  static const String sendOtp = 'إرسال رمز التحقق';
  static const String enterOtp = 'أدخل رمز التحقق';
  static const String otpSentTo = 'تم إرسال رمز التحقق إلى';
  static const String resendOtp = 'إعادة إرسال الرمز';
  static const String verifyOtp = 'تحقق';
  
  // أنواع المستخدمين
  static const String selectUserType = 'اختر نوع الحساب';
  static const String clientAccount = 'صاحب مشروع';
  static const String providerAccount = 'مقدم خدمة';
  static const String clientDescription = 'أبحث عن خدمات تسويقية وإعلامية';
  static const String providerDescription = 'أقدم خدمات تسويقية وإعلامية';
  
  // الصفحة الرئيسية
  static const String createRequest = 'طلب خدمة جديدة';
  static const String myRequests = 'طلباتي';
  static const String availableRequests = 'الفرص المتاحة';
  static const String myOffers = 'عروضي';
  static const String activeOrders = 'الطلبات النشطة';
  
  // أنواع الخدمات
  static const String photography = 'تصوير';
  static const String design = 'تصميم';
  static const String contentWriting = 'كتابة محتوى';
  static const String socialMedia = 'سوشيال ميديا';
  
  // حالات الطلبات
  static const String pending = 'قيد المراجعة';
  static const String published = 'منشور';
  static const String inProgress = 'قيد التنفيذ';
  static const String completed = 'مكتمل';
  static const String cancelled = 'ملغي';
  
  // رسائل النجاح
  static const String requestCreatedSuccess = 'تم إنشاء طلبك بنجاح';
  static const String offerSubmittedSuccess = 'تم إرسال عرضك بنجاح';
  static const String loginSuccess = 'تم تسجيل الدخول بنجاح';
  
  // رسائل الخطأ
  static const String networkError = 'خطأ في الاتصال بالإنترنت';
  static const String invalidPhone = 'رقم الهاتف غير صحيح';
  static const String invalidOtp = 'رمز التحقق غير صحيح';
  static const String somethingWentWrong = 'حدث خطأ ما، يرجى المحاولة لاحقاً';
}
```

**lib/core/theme/app_theme.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';
import '../constants/app_colors.dart';

class AppTheme {
  static ThemeData get lightTheme {
    return ThemeData(
      primaryColor: AppColors.primary,
      scaffoldBackgroundColor: AppColors.background,
      colorScheme: const ColorScheme.light(
        primary: AppColors.primary,
        secondary: AppColors.secondary,
        surface: AppColors.surface,
        background: AppColors.background,
        error: AppColors.error,
      ),
      
      // Typography
      textTheme: GoogleFonts.cairoTextTheme(
        const TextTheme(
          displayLarge: TextStyle(
            fontSize: 32,
            fontWeight: FontWeight.bold,
            color: AppColors.textPrimary,
          ),
          displayMedium: TextStyle(
            fontSize: 28,
            fontWeight: FontWeight.bold,
            color: AppColors.textPrimary,
          ),
          displaySmall: TextStyle(
            fontSize: 24,
            fontWeight: FontWeight.bold,
            color: AppColors.textPrimary,
          ),
          headlineMedium: TextStyle(
            fontSize: 20,
            fontWeight: FontWeight.w600,
            color: AppColors.textPrimary,
          ),
          headlineSmall: TextStyle(
            fontSize: 18,
            fontWeight: FontWeight.w600,
            color: AppColors.textPrimary,
          ),
          titleLarge: TextStyle(
            fontSize: 16,
            fontWeight: FontWeight.w600,
            color: AppColors.textPrimary,
          ),
          bodyLarge: TextStyle(
            fontSize: 16,
            fontWeight: FontWeight.normal,
            color: AppColors.textPrimary,
          ),
          bodyMedium: TextStyle(
            fontSize: 14,
            fontWeight: FontWeight.normal,
            color: AppColors.textSecondary,
          ),
          labelLarge: TextStyle(
            fontSize: 14,
            fontWeight: FontWeight.w500,
            color: AppColors.textPrimary,
          ),
        ),
      ),
      
      // AppBar Theme
      appBarTheme: const AppBarTheme(
        backgroundColor: AppColors.surface,
        elevation: 0,
        centerTitle: true,
        iconTheme: IconThemeData(color: AppColors.textPrimary),
        titleTextStyle: TextStyle(
          color: AppColors.textPrimary,
          fontSize: 20,
          fontWeight: FontWeight.w600,
        ),
      ),
      
      // Card Theme
      cardTheme: CardTheme(
        color: AppColors.surface,
        elevation: 2,
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(12),
        ),
      ),
      
      // Button Themes
      elevatedButtonTheme: ElevatedButtonThemeData(
        style: ElevatedButton.styleFrom(
          backgroundColor: AppColors.primary,
          foregroundColor: Colors.white,
          elevation: 0,
          padding: const EdgeInsets.symmetric(horizontal: 24, vertical: 12),
          shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(8),
          ),
          textStyle: const TextStyle(
            fontSize: 16,
            fontWeight: FontWeight.w600,
          ),
        ),
      ),
      
      // Input Decoration Theme
      inputDecorationTheme: InputDecorationTheme(
        filled: true,
        fillColor: AppColors.surface,
        contentPadding: const EdgeInsets.symmetric(horizontal: 16, vertical: 12),
        border: OutlineInputBorder(
          borderRadius: BorderRadius.circular(8),
          borderSide: const BorderSide(color: AppColors.divider),
        ),
        enabledBorder: OutlineInputBorder(
          borderRadius: BorderRadius.circular(8),
          borderSide: const BorderSide(color: AppColors.divider),
        ),
        focusedBorder: OutlineInputBorder(
          borderRadius: BorderRadius.circular(8),
          borderSide: const BorderSide(color: AppColors.primary, width: 2),
        ),
        errorBorder: OutlineInputBorder(
          borderRadius: BorderRadius.circular(8),
          borderSide: const BorderSide(color: AppColors.error),
        ),
        hintStyle: const TextStyle(color: AppColors.textHint),
      ),
    );
  }
}
```

### اليوم 2: إعداد Firebase والمصادقة

#### 2.1 إعداد Firebase
```bash
# تثبيت Firebase CLI
npm install -g firebase-tools

# تسجيل الدخول
firebase login

# إنشاء مشروع Firebase
firebase init

# اختر:
# - Firestore
# - Functions
# - Storage
# - Hosting
```

#### 2.2 ملف firebase_options.dart
```dart
// يتم توليده تلقائياً بواسطة FlutterFire CLI
// flutter pub global activate flutterfire_cli
// flutterfire configure
```

#### 2.3 إعداد قواعد Firestore
**firestore.rules:**
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // قواعد المستخدمين
    match /users/{userId} {
      allow read: if request.auth != null;
      allow write: if request.auth != null && request.auth.uid == userId;
    }
    
    // قواعد الطلبات
    match /requests/{requestId} {
      allow read: if request.auth != null;
      allow create: if request.auth != null && 
        get(/databases/$(database)/documents/users/$(request.auth.uid)).data.type == 'CLIENT';
      allow update: if request.auth != null && 
        (request.auth.uid == resource.data.clientId || isAdmin());
    }
    
    // قواعد العروض
    match /offers/{offerId} {
      allow read: if request.auth != null && 
        (request.auth.uid == resource.data.providerId || 
         request.auth.uid == getRequest(resource.data.requestId).data.clientId ||
         isAdmin());
      allow create: if request.auth != null && 
        get(/databases/$(database)/documents/users/$(request.auth.uid)).data.type == 'PROVIDER';
      allow update: if request.auth != null && isAdmin();
    }
    
    // قواعد الرسائل
    match /messages/{messageId} {
      allow read: if request.auth != null && 
        (request.auth.uid == resource.data.senderId || 
         request.auth.uid == resource.data.recipientId ||
         isAdmin());
      allow create: if request.auth != null && 
        (request.auth.uid == request.resource.data.senderId);
    }
    
    // وظيفة مساعدة للتحقق من المشرف
    function isAdmin() {
      return get(/databases/$(database)/documents/users/$(request.auth.uid)).data.type == 'ADMIN';
    }
    
    // وظيفة للحصول على الطلب
    function getRequest(requestId) {
      return get(/databases/$(database)/documents/requests/$(requestId));
    }
  }
}
```

---

## المرحلة 2: تطوير واجهات المستخدم (يوم 3-7)

### اليوم 3: شاشات التسجيل والمصادقة

#### 3.1 شاشة Splash
**lib/features/auth/presentation/screens/splash_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import '../../../../core/constants/app_colors.dart';
import '../../../../core/constants/app_strings.dart';

class SplashScreen extends ConsumerStatefulWidget {
  const SplashScreen({Key? key}) : super(key: key);

  @override
  ConsumerState<SplashScreen> createState() => _SplashScreenState();
}

class _SplashScreenState extends ConsumerState<SplashScreen> 
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _fadeAnimation;
  late Animation<double> _scaleAnimation;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      duration: const Duration(seconds: 2),
      vsync: this,
    );
    
    _fadeAnimation = Tween<double>(
      begin: 0.0,
      end: 1.0,
    ).animate(CurvedAnimation(
      parent: _controller,
      curve: const Interval(0.0, 0.5, curve: Curves.easeIn),
    ));
    
    _scaleAnimation = Tween<double>(
      begin: 0.5,
      end: 1.0,
    ).animate(CurvedAnimation(
      parent: _controller,
      curve: const Interval(0.0, 0.5, curve: Curves.elasticOut),
    ));
    
    _controller.forward();
    _checkAuthStatus();
  }

  Future<void> _checkAuthStatus() async {
    await Future.delayed(const Duration(seconds: 3));
    // TODO: Check if user is logged in
    // Navigate to appropriate screen
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Container(
        decoration: const BoxDecoration(
          gradient: AppColors.primaryGradient,
        ),
        child: Center(
          child: AnimatedBuilder(
            animation: _controller,
            builder: (context, child) {
              return FadeTransition(
                opacity: _fadeAnimation,
                child: ScaleTransition(
                  scale: _scaleAnimation,
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      Container(
                        width: 120,
                        height: 120,
                        decoration: BoxDecoration(
                          color: Colors.white,
                          borderRadius: BorderRadius.circular(30),
                          boxShadow: [
                            BoxShadow(
                              color: Colors.black.withOpacity(0.2),
                              blurRadius: 20,
                              offset: const Offset(0, 10),
                            ),
                          ],
                        ),
                        child: const Icon(
                          Icons.handshake,
                          size: 60,
                          color: AppColors.primary,
                        ),
                      ),
                      const SizedBox(height: 24),
                      const Text(
                        AppStrings.appName,
                        style: TextStyle(
                          fontSize: 40,
                          fontWeight: FontWeight.bold,
                          color: Colors.white,
                        ),
                      ),
                      const SizedBox(height: 8),
                      const Text(
                        AppStrings.appTagline,
                        style: TextStyle(
                          fontSize: 18,
                          color: Colors.white70,
                        ),
                      ),
                    ],
                  ),
                ),
              );
            },
          ),
        ),
      ),
    );
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }
}
```

#### 3.2 شاشة إدخال رقم الهاتف
**lib/features/auth/presentation/screens/phone_input_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import '../../../../core/constants/app_colors.dart';
import '../../../../core/constants/app_strings.dart';
import '../../../../core/widgets/app_button.dart';

class PhoneInputScreen extends ConsumerStatefulWidget {
  const PhoneInputScreen({Key? key}) : super(key: key);

  @override
  ConsumerState<PhoneInputScreen> createState() => _PhoneInputScreenState();
}

class _PhoneInputScreenState extends ConsumerState<PhoneInputScreen> {
  final _phoneController = TextEditingController();
  final _formKey = GlobalKey<FormState>();
  bool _isLoading = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(24.0),
          child: Form(
            key: _formKey,
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                const SizedBox(height: 40),
                // رسم توضيحي
                Center(
                  child: Container(
                    width: 200,
                    height: 200,
                    decoration: BoxDecoration(
                      color: AppColors.primaryLight.withOpacity(0.1),
                      shape: BoxShape.circle,
                    ),
                    child: const Icon(
                      Icons.phone_android,
                      size: 80,
                      color: AppColors.primary,
                    ),
                  ),
                ),
                const SizedBox(height: 40),
                Text(
                  AppStrings.welcomeMessage,
                  style: Theme.of(context).textTheme.displaySmall,
                ),
                const SizedBox(height: 8),
                Text(
                  AppStrings.enterPhone,
                  style: Theme.of(context).textTheme.bodyLarge,
                ),
                const SizedBox(height: 24),
                // حقل إدخال رقم الهاتف
                TextFormField(
                  controller: _phoneController,
                  keyboardType: TextInputType.phone,
                  textDirection: TextDirection.ltr,
                  inputFormatters: [
                    FilteringTextInputFormatter.digitsOnly,
                    LengthLimitingTextInputFormatter(11),
                    _PhoneNumberFormatter(),
                  ],
                  decoration: InputDecoration(
                    hintText: AppStrings.phoneHint,
                    prefixIcon: Container(
                      padding: const EdgeInsets.all(12),
                      child: const Text(
                        '🇮🇶 +964',
                        style: TextStyle(fontSize: 16),
                      ),
                    ),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return 'يرجى إدخال رقم الهاتف';
                    }
                    if (value.length < 11) {
                      return 'رقم الهاتف غير كامل';
                    }
                    if (!value.startsWith('07')) {
                      return 'رقم الهاتف يجب أن يبدأ بـ 07';
                    }
                    return null;
                  },
                ),
                const Spacer(),
                // زر الإرسال
                AppButton(
                  text: AppStrings.sendOtp,
                  onPressed: _isLoading ? null : _sendOtp,
                  isLoading: _isLoading,
                ),
                const SizedBox(height: 16),
              ],
            ),
          ),
        ),
      ),
    );
  }

  Future<void> _sendOtp() async {
    if (!_formKey.currentState!.validate()) return;

    setState(() => _isLoading = true);
    
    try {
      // TODO: Implement OTP sending logic
      await Future.delayed(const Duration(seconds: 2));
      
      // Navigate to OTP screen
      // context.push('/otp', extra: _phoneController.text);
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text(e.toString())),
      );
    } finally {
      setState(() => _isLoading = false);
    }
  }

  @override
  void dispose() {
    _phoneController.dispose();
    super.dispose();
  }
}

// منسق رقم الهاتف
class _PhoneNumberFormatter extends TextInputFormatter {
  @override
  TextEditingValue formatEditUpdate(
    TextEditingValue oldValue,
    TextEditingValue newValue,
  ) {
    final text = newValue.text;
    if (text.length <= 4) return newValue;
    
    final buffer = StringBuffer();
    for (int i = 0; i < text.length; i++) {
      if (i == 4 || i == 7) buffer.write(' ');
      buffer.write(text[i]);
    }
    
    return TextEditingValue(
      text: buffer.toString(),
      selection: TextSelection.collapsed(offset: buffer.length),
    );
  }
}
```

#### 3.3 شاشة إدخال OTP
**lib/features/auth/presentation/screens/otp_verification_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import 'dart:async';

class OtpVerificationScreen extends ConsumerStatefulWidget {
  final String phoneNumber;
  
  const OtpVerificationScreen({
    Key? key,
    required this.phoneNumber,
  }) : super(key: key);

  @override
  ConsumerState<OtpVerificationScreen> createState() => _OtpVerificationScreenState();
}

class _OtpVerificationScreenState extends ConsumerState<OtpVerificationScreen> {
  final List<TextEditingController> _controllers = List.generate(
    6,
    (index) => TextEditingController(),
  );
  final List<FocusNode> _focusNodes = List.generate(
    6,
    (index) => FocusNode(),
  );
  
  bool _isLoading = false;
  int _resendTimer = 60;
  Timer? _timer;

  @override
  void initState() {
    super.initState();
    _startResendTimer();
  }

  void _startResendTimer() {
    _timer = Timer.periodic(const Duration(seconds: 1), (timer) {
      if (_resendTimer > 0) {
        setState(() => _resendTimer--);
      } else {
        timer.cancel();
      }
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.transparent,
        elevation: 0,
      ),
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(24.0),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.center,
            children: [
              const SizedBox(height: 40),
              // أيقونة
              Container(
                width: 80,
                height: 80,
                decoration: BoxDecoration(
                  color: AppColors.primaryLight.withOpacity(0.2),
                  shape: BoxShape.circle,
                ),
                child: const Icon(
                  Icons.lock_outline,
                  size: 40,
                  color: AppColors.primary,
                ),
              ),
              const SizedBox(height: 24),
              Text(
                AppStrings.enterOtp,
                style: Theme.of(context).textTheme.headlineMedium,
              ),
              const SizedBox(height: 8),
              Text(
                '${AppStrings.otpSentTo} ${widget.phoneNumber}',
                style: Theme.of(context).textTheme.bodyMedium,
              ),
              const SizedBox(height: 40),
              // حقول OTP
              Row(
                mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                children: List.generate(6, (index) {
                  return SizedBox(
                    width: 50,
                    height: 60,
                    child: TextFormField(
                      controller: _controllers[index],
                      focusNode: _focusNodes[index],
                      keyboardType: TextInputType.number,
                      textAlign: TextAlign.center,
                      maxLength: 1,
                      style: const TextStyle(
                        fontSize: 24,
                        fontWeight: FontWeight.bold,
                      ),
                      decoration: InputDecoration(
                        counterText: '',
                        border: OutlineInputBorder(
                          borderRadius: BorderRadius.circular(12),
                        ),
                      ),
                      inputFormatters: [
                        FilteringTextInputFormatter.digitsOnly,
                      ],
                      onChanged: (value) {
                        if (value.isNotEmpty && index < 5) {
                          _focusNodes[index + 1].requestFocus();
                        }
                        if (value.isEmpty && index > 0) {
                          _focusNodes[index - 1].requestFocus();
                        }
                        _checkOtpComplete();
                      },
                    ),
                  );
                }),
              ),
              const SizedBox(height: 24),
              // زر إعادة الإرسال
              TextButton(
                onPressed: _resendTimer == 0 ? _resendOtp : null,
                child: Text(
                  _resendTimer > 0
                      ? 'إعادة الإرسال بعد $_resendTimer ثانية'
                      : AppStrings.resendOtp,
                  style: TextStyle(
                    color: _resendTimer > 0 ? Colors.grey : AppColors.primary,
                  ),
                ),
              ),
              const Spacer(),
              // زر التحقق
              AppButton(
                text: AppStrings.verifyOtp,
                onPressed: _isLoading ? null : _verifyOtp,
                isLoading: _isLoading,
              ),
            ],
          ),
        ),
      ),
    );
  }

  void _checkOtpComplete() {
    final otp = _controllers.map((c) => c.text).join();
    if (otp.length == 6) {
      _verifyOtp();
    }
  }

  Future<void> _verifyOtp() async {
    final otp = _controllers.map((c) => c.text).join();
    if (otp.length != 6) return;

    setState(() => _isLoading = true);
    
    try {
      // TODO: Verify OTP
      await Future.delayed(const Duration(seconds: 2));
      
      // Navigate to next screen
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text(e.toString())),
      );
    } finally {
      setState(() => _isLoading = false);
    }
  }

  Future<void> _resendOtp() async {
    setState(() {
      _resendTimer = 60;
    });
    _startResendTimer();
    
    // TODO: Resend OTP logic
  }

  @override
  void dispose() {
    _timer?.cancel();
    for (var controller in _controllers) {
      controller.dispose();
    }
    for (var node in _focusNodes) {
      node.dispose();
    }
    super.dispose();
  }
}
```

#### 3.4 شاشة اختيار نوع المستخدم
**lib/features/auth/presentation/screens/user_type_selection_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';

class UserTypeSelectionScreen extends ConsumerWidget {
  const UserTypeSelectionScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    return Scaffold(
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(24.0),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              const SizedBox(height: 40),
              Text(
                AppStrings.selectUserType,
                style: Theme.of(context).textTheme.displaySmall,
              ),
              const SizedBox(height: 8),
              Text(
                'يمكنك تغيير نوع الحساب لاحقاً من الإعدادات',
                style: Theme.of(context).textTheme.bodyMedium,
              ),
              const SizedBox(height: 40),
              // بطاقة العميل
              _UserTypeCard(
                icon: Icons.business_center,
                title: AppStrings.clientAccount,
                description: AppStrings.clientDescription,
                color: AppColors.primary,
                onTap: () => _selectUserType(context, 'CLIENT'),
              ),
              const SizedBox(height: 16),
              // بطاقة مقدم الخدمة
              _UserTypeCard(
                icon: Icons.work,
                title: AppStrings.providerAccount,
                description: AppStrings.providerDescription,
                color: AppColors.secondary,
                onTap: () => _selectUserType(context, 'PROVIDER'),
              ),
            ],
          ),
        ),
      ),
    );
  }

  void _selectUserType(BuildContext context, String type) {
    // TODO: Save user type and navigate
  }
}

class _UserTypeCard extends StatelessWidget {
  final IconData icon;
  final String title;
  final String description;
  final Color color;
  final VoidCallback onTap;

  const _UserTypeCard({
    Key? key,
    required this.icon,
    required this.title,
    required this.description,
    required this.color,
    required this.onTap,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return InkWell(
      onTap: onTap,
      borderRadius: BorderRadius.circular(16),
      child: Container(
        padding: const EdgeInsets.all(24),
        decoration: BoxDecoration(
          color: color.withOpacity(0.1),
          borderRadius: BorderRadius.circular(16),
          border: Border.all(
            color: color.withOpacity(0.3),
            width: 2,
          ),
        ),
        child: Row(
          children: [
            Container(
              width: 60,
              height: 60,
              decoration: BoxDecoration(
                color: color.withOpacity(0.2),
                shape: BoxShape.circle,
              ),
              child: Icon(
                icon,
                size: 32,
                color: color,
              ),
            ),
            const SizedBox(width: 16),
            Expanded(
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Text(
                    title,
                    style: Theme.of(context).textTheme.headlineSmall,
                  ),
                  const SizedBox(height: 4),
                  Text(
                    description,
                    style: Theme.of(context).textTheme.bodyMedium,
                  ),
                ],
              ),
            ),
            Icon(
              Icons.arrow_forward_ios,
              color: color,
            ),
          ],
        ),
      ),
    );
  }
}
```

### اليوم 4: الصفحات الرئيسية للعميل ومقدم الخدمة

#### 4.1 الصفحة الرئيسية للعميل
**lib/features/home/presentation/screens/client_home_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';

class ClientHomeScreen extends ConsumerStatefulWidget {
  const ClientHomeScreen({Key? key}) : super(key: key);

  @override
  ConsumerState<ClientHomeScreen> createState() => _ClientHomeScreenState();
}

class _ClientHomeScreenState extends ConsumerState<ClientHomeScreen> {
  int _currentIndex = 0;

  final List<Widget> _pages = [
    const _HomePage(),
    const _RequestsPage(),
    const _ProfilePage(),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: IndexedStack(
        index: _currentIndex,
        children: _pages,
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _currentIndex,
        onTap: (index) => setState(() => _currentIndex = index),
        items: const [
          BottomNavigationBarItem(
            icon: Icon(Icons.home),
            label: 'الرئيسية',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.list_alt),
            label: 'طلباتي',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.person),
            label: 'حسابي',
          ),
        ],
      ),
    );
  }
}

class _HomePage extends StatelessWidget {
  const _HomePage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: CustomScrollView(
        slivers: [
          // AppBar مخصص
          SliverAppBar(
            expandedHeight: 200,
            floating: true,
            pinned: true,
            flexibleSpace: FlexibleSpaceBar(
              background: Container(
                decoration: const BoxDecoration(
                  gradient: AppColors.primaryGradient,
                ),
                child: SafeArea(
                  child: Padding(
                    padding: const EdgeInsets.all(24.0),
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      mainAxisAlignment: MainAxisAlignment.end,
                      children: [
                        Text(
                          'مرحباً محمد 👋',
                          style: Theme.of(context).textTheme.displaySmall?.copyWith(
                            color: Colors.white,
                          ),
                        ),
                        const SizedBox(height: 8),
                        Text(
                          'ماذا تحتاج اليوم؟',
                          style: Theme.of(context).textTheme.bodyLarge?.copyWith(
                            color: Colors.white70,
                          ),
                        ),
                      ],
                    ),
                  ),
                ),
              ),
            ),
          ),
          // الخدمات
          SliverPadding(
            padding: const EdgeInsets.all(16),
            sliver: SliverGrid(
              gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
                crossAxisCount: 2,
                mainAxisSpacing: 16,
                crossAxisSpacing: 16,
                childAspectRatio: 1.2,
              ),
              delegate: SliverChildListDelegate([
                _ServiceCard(
                  icon: Icons.camera_alt,
                  title: AppStrings.photography,
                  color: Colors.blue,
                  onTap: () => _navigateToServiceRequest(context, 'PHOTOGRAPHY'),
                ),
                _ServiceCard(
                  icon: Icons.palette,
                  title: AppStrings.design,
                  color: Colors.purple,
                  onTap: () => _navigateToServiceRequest(context, 'DESIGN'),
                ),
                _ServiceCard(
                  icon: Icons.edit,
                  title: AppStrings.contentWriting,
                  color: Colors.orange,
                  onTap: () => _navigateToServiceRequest(context, 'CONTENT_WRITING'),
                ),
                _ServiceCard(
                  icon: Icons.share,
                  title: AppStrings.socialMedia,
                  color: Colors.green,
                  onTap: () => _navigateToServiceRequest(context, 'SOCIAL_MEDIA'),
                ),
              ]),
            ),
          ),
          // الطلبات النشطة
          SliverToBoxAdapter(
            child: Padding(
              padding: const EdgeInsets.all(16),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Row(
                    mainAxisAlignment: MainAxisAlignment.spaceBetween,
                    children: [
                      Text(
                        'الطلبات النشطة',
                        style: Theme.of(context).textTheme.headlineSmall,
                      ),
                      TextButton(
                        onPressed: () {
                          // Navigate to all requests
                        },
                        child: const Text('عرض الكل'),
                      ),
                    ],
                  ),
                  const SizedBox(height: 8),
                  // TODO: Add active requests list
                  Container(
                    height: 120,
                    alignment: Alignment.center,
                    decoration: BoxDecoration(
                      color: AppColors.surface,
                      borderRadius: BorderRadius.circular(12),
                      border: Border.all(color: AppColors.divider),
                    ),
                    child: Text(
                      'لا توجد طلبات نشطة',
                      style: TextStyle(color: AppColors.textSecondary),
                    ),
                  ),
                ],
              ),
            ),
          ),
        ],
      ),
    );
  }

  void _navigateToServiceRequest(BuildContext context, String serviceType) {
    // TODO: Navigate to create request screen
  }
}

class _ServiceCard extends StatelessWidget {
  final IconData icon;
  final String title;
  final Color color;
  final VoidCallback onTap;

  const _ServiceCard({
    Key? key,
    required this.icon,
    required this.title,
    required this.color,
    required this.onTap,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return InkWell(
      onTap: onTap,
      borderRadius: BorderRadius.circular(16),
      child: Container(
        decoration: BoxDecoration(
          color: color.withOpacity(0.1),
          borderRadius: BorderRadius.circular(16),
          border: Border.all(
            color: color.withOpacity(0.3),
            width: 2,
          ),
        ),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(
              icon,
              size: 48,
              color: color,
            ),
            const SizedBox(height: 12),
            Text(
              title,
              style: Theme.of(context).textTheme.titleLarge,
            ),
          ],
        ),
      ),
    );
  }
}

class _RequestsPage extends StatelessWidget {
  const _RequestsPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return DefaultTabController(
      length: 3,
      child: Scaffold(
        appBar: AppBar(
          title: const Text('طلباتي'),
          bottom: const TabBar(
            tabs: [
              Tab(text: 'النشطة'),
              Tab(text: 'المكتملة'),
              Tab(text: 'الملغية'),
            ],
          ),
        ),
        body: const TabBarView(
          children: [
            _RequestsList(status: 'ACTIVE'),
            _RequestsList(status: 'COMPLETED'),
            _RequestsList(status: 'CANCELLED'),
          ],
        ),
      ),
    );
  }
}

class _RequestsList extends StatelessWidget {
  final String status;
  
  const _RequestsList({
    Key? key,
    required this.status,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    // TODO: Implement requests list
    return Center(
      child: Text('قائمة الطلبات - $status'),
    );
  }
}

class _ProfilePage extends StatelessWidget {
  const _ProfilePage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('حسابي'),
      ),
      body: ListView(
        padding: const EdgeInsets.all(16),
        children: [
          // معلومات المستخدم
          Container(
            padding: const EdgeInsets.all(16),
            decoration: BoxDecoration(
              color: AppColors.surface,
              borderRadius: BorderRadius.circular(12),
              boxShadow: [
                BoxShadow(
                  color: Colors.black.withOpacity(0.05),
                  blurRadius: 10,
                  offset: const Offset(0, 5),
                ),
              ],
            ),
            child: Row(
              children: [
                CircleAvatar(
                  radius: 40,
                  backgroundColor: AppColors.primary,
                  child: const Text(
                    'م',
                    style: TextStyle(
                      fontSize: 32,
                      color: Colors.white,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                ),
                const SizedBox(width: 16),
                Expanded(
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      Text(
                        'محمد أحمد',
                        style: Theme.of(context).textTheme.headlineSmall,
                      ),
                      const SizedBox(height: 4),
                      Text(
                        '0770 123 4567',
                        style: Theme.of(context).textTheme.bodyMedium,
                      ),
                      const SizedBox(height: 4),
                      Row(
                        children: [
                          const Icon(
                            Icons.star,
                            size: 16,
                            color: Colors.amber,
                          ),
                          const SizedBox(width: 4),
                          Text(
                            '4.8',
                            style: Theme.of(context).textTheme.bodyMedium,
                          ),
                          const SizedBox(width: 4),
                          Text(
                            '(23 تقييم)',
                            style: Theme.of(context).textTheme.bodySmall,
                          ),
                        ],
                      ),
                    ],
                  ),
                ),
              ],
            ),
          ),
          const SizedBox(height: 24),
          // قائمة الخيارات
          _ProfileMenuItem(
            icon: Icons.edit,
            title: 'تعديل الملف الشخصي',
            onTap: () {},
          ),
          _ProfileMenuItem(
            icon: Icons.location_city,
            title: 'المدينة: بغداد',
            onTap: () {},
          ),
          _ProfileMenuItem(
            icon: Icons.notifications,
            title: 'الإشعارات',
            onTap: () {},
          ),
          _ProfileMenuItem(
            icon: Icons.help,
            title: 'المساعدة والدعم',
            onTap: () {},
          ),
          _ProfileMenuItem(
            icon: Icons.info,
            title: 'عن التطبيق',
            onTap: () {},
          ),
          const SizedBox(height: 24),
          // زر تسجيل الخروج
          ElevatedButton(
            onPressed: () {
              // TODO: Logout
            },
            style: ElevatedButton.styleFrom(
              backgroundColor: AppColors.error,
              padding: const EdgeInsets.symmetric(vertical: 16),
            ),
            child: const Text('تسجيل الخروج'),
          ),
        ],
      ),
    );
  }
}

class _ProfileMenuItem extends StatelessWidget {
  final IconData icon;
  final String title;
  final VoidCallback onTap;

  const _ProfileMenuItem({
    Key? key,
    required this.icon,
    required this.title,
    required this.onTap,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return ListTile(
      leading: Icon(icon, color: AppColors.primary),
      title: Text(title),
      trailing: const Icon(Icons.arrow_forward_ios, size: 16),
      onTap: onTap,
    );
  }
}
```

#### 4.2 الصفحة الرئيسية لمقدم الخدمة
**lib/features/home/presentation/screens/provider_home_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';

class ProviderHomeScreen extends ConsumerStatefulWidget {
  const ProviderHomeScreen({Key? key}) : super(key: key);

  @override
  ConsumerState<ProviderHomeScreen> createState() => _ProviderHomeScreenState();
}

class _ProviderHomeScreenState extends ConsumerState<ProviderHomeScreen> {
  int _currentIndex = 0;

  final List<Widget> _pages = [
    const _OpportunitiesPage(),
    const _MyOffersPage(),
    const _ActiveOrdersPage(),
    const _ProfilePage(),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: IndexedStack(
        index: _currentIndex,
        children: _pages,
      ),
      bottomNavigationBar: BottomNavigationBar(
        type: BottomNavigationBarType.fixed,
        currentIndex: _currentIndex,
        onTap: (index) => setState(() => _currentIndex = index),
        items: const [
          BottomNavigationBarItem(
            icon: Icon(Icons.search),
            label: 'الفرص',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.send),
            label: 'عروضي',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.work),
            label: 'أعمالي',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.person),
            label: 'حسابي',
          ),
        ],
      ),
    );
  }
}

class _OpportunitiesPage extends StatelessWidget {
  const _OpportunitiesPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('الفرص المتاحة'),
        actions: [
          IconButton(
            icon: const Icon(Icons.filter_list),
            onPressed: () {
              // Show filter bottom sheet
            },
          ),
        ],
      ),
      body: RefreshIndicator(
        onRefresh: () async {
          // TODO: Refresh opportunities
        },
        child: ListView.builder(
          padding: const EdgeInsets.all(16),
          itemCount: 10,
          itemBuilder: (context, index) {
            return _OpportunityCard(
              title: 'تصوير منتجات للمتجر الإلكتروني',
              serviceType: 'تصوير',
              location: 'بغداد - المنصور',
              urgency: 'عادي',
              postedTime: 'قبل ساعتين',
              onTap: () {
                // Navigate to opportunity details
              },
            );
          },
        ),
      ),
    );
  }
}

class _OpportunityCard extends StatelessWidget {
  final String title;
  final String serviceType;
  final String location;
  final String urgency;
  final String postedTime;
  final VoidCallback onTap;

  const _OpportunityCard({
    Key? key,
    required this.title,
    required this.serviceType,
    required this.location,
    required this.urgency,
    required this.postedTime,
    required this.onTap,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Card(
      margin: const EdgeInsets.only(bottom: 12),
      child: InkWell(
        onTap: onTap,
        borderRadius: BorderRadius.circular(12),
        child: Padding(
          padding: const EdgeInsets.all(16),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Row(
                children: [
                  Container(
                    padding: const EdgeInsets.symmetric(
                      horizontal: 12,
                      vertical: 4,
                    ),
                    decoration: BoxDecoration(
                      color: AppColors.primary.withOpacity(0.1),
                      borderRadius: BorderRadius.circular(20),
                    ),
                    child: Text(
                      serviceType,
                      style: TextStyle(
                        color: AppColors.primary,
                        fontSize: 12,
                        fontWeight: FontWeight.w600,
                      ),
                    ),
                  ),
                  const SizedBox(width: 8),
                  if (urgency == 'عاجل')
                    Container(
                      padding: const EdgeInsets.symmetric(
                        horizontal: 12,
                        vertical: 4,
                      ),
                      decoration: BoxDecoration(
                        color: AppColors.error.withOpacity(0.1),
                        borderRadius: BorderRadius.circular(20),
                      ),
                      child: Text(
                        urgency,
                        style: TextStyle(
                          color: AppColors.error,
                          fontSize: 12,
                          fontWeight: FontWeight.w600,
                        ),
                      ),
                    ),
                  const Spacer(),
                  Text(
                    postedTime,
                    style: Theme.of(context).textTheme.bodySmall,
                  ),
                ],
              ),
              const SizedBox(height: 12),
              Text(
                title,
                style: Theme.of(context).textTheme.titleMedium,
                maxLines: 2,
                overflow: TextOverflow.ellipsis,
              ),
              const SizedBox(height: 8),
              Row(
                children: [
                  Icon(
                    Icons.location_on,
                    size: 16,
                    color: AppColors.textSecondary,
                  ),
                  const SizedBox(width: 4),
                  Text(
                    location,
                    style: Theme.of(context).textTheme.bodySmall,
                  ),
                ],
              ),
            ],
          ),
        ),
      ),
    );
  }
}

class _MyOffersPage extends StatelessWidget {
  const _MyOffersPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return DefaultTabController(
      length: 4,
      child: Scaffold(
        appBar: AppBar(
          title: const Text('عروضي'),
          bottom: const TabBar(
            isScrollable: true,
            tabs: [
              Tab(text: 'معلقة'),
              Tab(text: 'مقبولة'),
              Tab(text: 'مرفوضة'),
              Tab(text: 'منتهية'),
            ],
          ),
        ),
        body: const TabBarView(
          children: [
            _OffersList(status: 'PENDING'),
            _OffersList(status: 'ACCEPTED'),
            _OffersList(status: 'REJECTED'),
            _OffersList(status: 'EXPIRED'),
          ],
        ),
      ),
    );
  }
}

class _OffersList extends StatelessWidget {
  final String status;
  
  const _OffersList({
    Key? key,
    required this.status,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    // TODO: Implement offers list
    return Center(
      child: Text('قائمة العروض - $status'),
    );
  }
}

class _ActiveOrdersPage extends StatelessWidget {
  const _ActiveOrdersPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('أعمالي النشطة'),
      ),
      body: ListView.builder(
        padding: const EdgeInsets.all(16),
        itemCount: 3,
        itemBuilder: (context, index) {
          return _ActiveOrderCard(
            title: 'تصوير منتجات - متجر الأزياء',
            client: 'متجر روز',
            deadline: 'الموعد النهائي: بعد 3 أيام',
            progress: 0.6,
            onTap: () {
              // Navigate to order details
            },
          );
        },
      ),
    );
  }
}

class _ActiveOrderCard extends StatelessWidget {
  final String title;
  final String client;
  final String deadline;
  final double progress;
  final VoidCallback onTap;

  const _ActiveOrderCard({
    Key? key,
    required this.title,
    required this.client,
    required this.deadline,
    required this.progress,
    required this.onTap,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Card(
      margin: const EdgeInsets.only(bottom: 12),
      child: InkWell(
        onTap: onTap,
        borderRadius: BorderRadius.circular(12),
        child: Padding(
          padding: const EdgeInsets.all(16),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Row(
                mainAxisAlignment: MainAxisAlignment.spaceBetween,
                children: [
                  Expanded(
                    child: Text(
                      title,
                      style: Theme.of(context).textTheme.titleMedium,
                      maxLines: 1,
                      overflow: TextOverflow.ellipsis,
                    ),
                  ),
                  Container(
                    padding: const EdgeInsets.symmetric(
                      horizontal: 12,
                      vertical: 4,
                    ),
                    decoration: BoxDecoration(
                      color: AppColors.warning.withOpacity(0.1),
                      borderRadius: BorderRadius.circular(20),
                    ),
                    child: Text(
                      'قيد التنفيذ',
                      style: TextStyle(
                        color: AppColors.warning,
                        fontSize: 12,
                        fontWeight: FontWeight.w600,
                      ),
                    ),
                  ),
                ],
              ),
              const SizedBox(height: 8),
              Text(
                'العميل: $client',
                style: Theme.of(context).textTheme.bodyMedium,
              ),
              const SizedBox(height: 4),
              Text(
                deadline,
                style: Theme.of(context).textTheme.bodySmall?.copyWith(
                  color: AppColors.error,
                ),
              ),
              const SizedBox(height: 12),
              // Progress bar
              Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Row(
                    mainAxisAlignment: MainAxisAlignment.spaceBetween,
                    children: [
                      Text(
                        'التقدم',
                        style: Theme.of(context).textTheme.bodySmall,
                      ),
                      Text(
                        '${(progress * 100).toInt()}%',
                        style: Theme.of(context).textTheme.bodySmall,
                      ),
                    ],
                  ),
                  const SizedBox(height: 4),
                  LinearProgressIndicator(
                    value: progress,
                    backgroundColor: AppColors.divider,
                    valueColor: AlwaysStoppedAnimation<Color>(AppColors.success),
                  ),
                ],
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

### اليوم 5: شاشات إنشاء الطلبات وتقديم العروض

#### 5.1 شاشة إنشاء طلب جديد
**lib/features/requests/presentation/screens/create_request_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import 'package:image_picker/image_picker.dart';
import 'dart:io';

class CreateRequestScreen extends ConsumerStatefulWidget {
  final String serviceType;
  
  const CreateRequestScreen({
    Key? key,
    required this.serviceType,
  }) : super(key: key);

  @override
  ConsumerState<CreateRequestScreen> createState() => _CreateRequestScreenState();
}

class _CreateRequestScreenState extends ConsumerState<CreateRequestScreen> {
  final _formKey = GlobalKey<FormState>();
  final _titleController = TextEditingController();
  final _descriptionController = TextEditingController();
  final List<File> _attachments = [];
  String _selectedCity = 'بغداد';
  String _urgency = 'NORMAL';
  DateTime? _deadline;
  bool _isLoading = false;

  final List<String> _cities = [
    'بغداد',
    'البصرة',
    'الموصل',
    'أربيل',
    'النجف',
    'كربلاء',
    'كركوك',
    'السليمانية',
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('طلب خدمة ${_getServiceName()}'),
      ),
      body: Form(
        key: _formKey,
        child: ListView(
          padding: const EdgeInsets.all(16),
          children: [
            // عنوان الطلب
            TextFormField(
              controller: _titleController,
              decoration: const InputDecoration(
                labelText: 'عنوان الطلب',
                hintText: 'مثال: تصوير منتجات للمتجر الإلكتروني',
              ),
              validator: (value) {
                if (value == null || value.isEmpty) {
                  return 'يرجى إدخال عنوان الطلب';
                }
                if (value.length < 10) {
                  return 'العنوان قصير جداً';
                }
                return null;
              },
            ),
            const SizedBox(height: 16),
            
            // وصف الطلب
            TextFormField(
              controller: _descriptionController,
              maxLines: 5,
              decoration: const InputDecoration(
                labelText: 'وصف الطلب',
                hintText: 'اشرح بالتفصيل ما تحتاجه...',
                alignLabelWithHint: true,
              ),
              validator: (value) {
                if (value == null || value.isEmpty) {
                  return 'يرجى إدخال وصف الطلب';
                }
                if (value.length < 30) {
                  return 'الوصف قصير جداً، يرجى إضافة المزيد من التفاصيل';
                }
                return null;
              },
            ),
            const SizedBox(height: 16),
            
            // المدينة
            DropdownButtonFormField<String>(
              value: _selectedCity,
              decoration: const InputDecoration(
                labelText: 'المدينة',
                prefixIcon: Icon(Icons.location_city),
              ),
              items: _cities.map((city) {
                return DropdownMenuItem(
                  value: city,
                  child: Text(city),
                );
              }).toList(),
              onChanged: (value) {
                setState(() {
                  _selectedCity = value!;
                });
              },
            ),
            const SizedBox(height: 16),
            
            // الأولوية
            Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                Text(
                  'الأولوية',
                  style: Theme.of(context).textTheme.titleMedium,
                ),
                const SizedBox(height: 8),
                Row(
                  children: [
                    Expanded(
                      child: RadioListTile<String>(
                        title: const Text('عادي'),
                        value: 'NORMAL',
                        groupValue: _urgency,
                        onChanged: (value) {
                          setState(() {
                            _urgency = value!;
                          });
                        },
                      ),
                    ),
                    Expanded(
                      child: RadioListTile<String>(
                        title: const Text('عاجل'),
                        value: 'URGENT',
                        groupValue: _urgency,
                        onChanged: (value) {
                          setState(() {
                            _urgency = value!;
                          });
                        },
                      ),
                    ),
                  ],
                ),
              ],
            ),
            const SizedBox(height: 16),
            
            // الموعد النهائي
            ListTile(
              leading: const Icon(Icons.calendar_today),
              title: Text(
                _deadline == null
                    ? 'حدد الموعد النهائي (اختياري)'
                    : 'الموعد النهائي: ${_formatDate(_deadline!)}',
              ),
              trailing: _deadline == null
                  ? null
                  : IconButton(
                      icon: const Icon(Icons.clear),
                      onPressed: () {
                        setState(() {
                          _deadline = null;
                        });
                      },
                    ),
              onTap: _selectDeadline,
            ),
            const SizedBox(height: 16),
            
            // المرفقات
            Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                Row(
                  mainAxisAlignment: MainAxisAlignment.spaceBetween,
                  children: [
                    Text(
                      'المرفقات',
                      style: Theme.of(context).textTheme.titleMedium,
                    ),
                    TextButton.icon(
                      icon: const Icon(Icons.add_photo_alternate),
                      label: const Text('إضافة'),
                      onPressed: _addAttachment,
                    ),
                  ],
                ),
                const SizedBox(height: 8),
                if (_attachments.isEmpty)
                  Container(
                    height: 100,
                    decoration: BoxDecoration(
                      border: Border.all(color: AppColors.divider),
                      borderRadius: BorderRadius.circular(8),
                    ),
                    child: const Center(
                      child: Text(
                        'لا توجد مرفقات',
                        style: TextStyle(color: AppColors.textHint),
                      ),
                    ),
                  )
                else
                  SizedBox(
                    height: 100,
                    child: ListView.builder(
                      scrollDirection: Axis.horizontal,
                      itemCount: _attachments.length,
                      itemBuilder: (context, index) {
                        return Container(
                          width: 100,
                          margin: const EdgeInsets.only(left: 8),
                          decoration: BoxDecoration(
                            borderRadius: BorderRadius.circular(8),
                            image: DecorationImage(
                              image: FileImage(_attachments[index]),
                              fit: BoxFit.cover,
                            ),
                          ),
                          child: Stack(
                            children: [
                              Positioned(
                                top: 4,
                                left: 4,
                                child: CircleAvatar(
                                  backgroundColor: Colors.black54,
                                  radius: 16,
                                  child: IconButton(
                                    icon: const Icon(
                                      Icons.close,
                                      size: 16,
                                      color: Colors.white,
                                    ),
                                    onPressed: () {
                                      setState(() {
                                        _attachments.removeAt(index);
                                      });
                                    },
                                  ),
                                ),
                              ),
                            ],
                          ),
                        );
                      },
                    ),
                  ),
              ],
            ),
            const SizedBox(height: 24),
            
            // زر الإرسال
            ElevatedButton(
              onPressed: _isLoading ? null : _submitRequest,
              child: _isLoading
                  ? const CircularProgressIndicator()
                  : const Text('إرسال الطلب'),
            ),
          ],
        ),
      ),
    );
  }

  String _getServiceName() {
    switch (widget.serviceType) {
      case 'PHOTOGRAPHY':
        return 'تصوير';
      case 'DESIGN':
        return 'تصميم';
      case 'CONTENT_WRITING':
        return 'كتابة محتوى';
      case 'SOCIAL_MEDIA':
        return 'سوشيال ميديا';
      default:
        return '';
    }
  }

  String _formatDate(DateTime date) {
    return '${date.day}/${date.month}/${date.year}';
  }

  Future<void> _selectDeadline() async {
    final picked = await showDatePicker(
      context: context,
      initialDate: DateTime.now().add(const Duration(days: 7)),
      firstDate: DateTime.now().add(const Duration(days: 1)),
      lastDate: DateTime.now().add(const Duration(days: 90)),
    );
    
    if (picked != null) {
      setState(() {
        _deadline = picked;
      });
    }
  }

  Future<void> _addAttachment() async {
    final ImagePicker picker = ImagePicker();
    
    final source = await showModalBottomSheet<ImageSource>(
      context: context,
      builder: (context) => Column(
        mainAxisSize: MainAxisSize.min,
        children: [
          ListTile(
            leading: const Icon(Icons.camera_alt),
            title: const Text('الكاميرا'),
            onTap: () => Navigator.pop(context, ImageSource.camera),
          ),
          ListTile(
            leading: const Icon(Icons.photo_library),
            title: const Text('المعرض'),
            onTap: () => Navigator.pop(context, ImageSource.gallery),
          ),
        ],
      ),
    );
    
    if (source != null) {
      final XFile? image = await picker.pickImage(source: source);
      if (image != null) {
        setState(() {
          _attachments.add(File(image.path));
        });
      }
    }
  }

  Future<void> _submitRequest() async {
    if (!_formKey.currentState!.validate()) return;
    
    setState(() => _isLoading = true);
    
    try {
      // TODO: Submit request to Firebase
      await Future.delayed(const Duration(seconds: 2));
      
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(
          content: Text(AppStrings.requestCreatedSuccess),
          backgroundColor: AppColors.success,
        ),
      );
      
      Navigator.pop(context);
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(
          content: Text(e.toString()),
          backgroundColor: AppColors.error,
        ),
      );
    } finally {
      setState(() => _isLoading = false);
    }
  }

  @override
  void dispose() {
    _titleController.dispose();
    _descriptionController.dispose();
    super.dispose();
  }
}
```

### اليوم 6-7: تطوير لوحة التحكم الإدارية (Web)

سأقوم بإنشاء لوحة تحكم ويب بسيطة باستخدام Flutter Web:

#### 6.1 الصفحة الرئيسية للوحة التحكم
**lib/features/admin/presentation/screens/admin_dashboard_screen.dart:**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';

class AdminDashboardScreen extends ConsumerStatefulWidget {
  const AdminDashboardScreen({Key? key}) : super(key: key);

  @override
  ConsumerState<AdminDashboardScreen> createState() => _AdminDashboardScreenState();
}

class _AdminDashboardScreenState extends ConsumerState<AdminDashboardScreen> {
  int _selectedIndex = 0;

  final List<_MenuItem> _menuItems = [
    _MenuItem(icon: Icons.dashboard, title: 'لوحة القيادة', page: const _DashboardPage()),
    _MenuItem(icon: Icons.list_alt, title: 'الطلبات', page: const _RequestsManagementPage()),
    _MenuItem(icon: Icons.local_offer, title: 'العروض', page: const _OffersManagementPage()),
    _MenuItem(icon: Icons.people, title: 'المستخدمون', page: const _UsersManagementPage()),
    _MenuItem(icon: Icons.attach_money, title: 'المالية', page: const _FinancePage()),
    _MenuItem(icon: Icons.settings, title: 'الإعدادات', page: const _SettingsPage()),
  ];

  @override
  Widget build(BuildContext context) {
    final isDesktop = MediaQuery.of(context).size.width > 800;

    return Scaffold(
      body: Row(
        children: [
          // Sidebar
          if (isDesktop)
            Container(
              width: 250,
              color: AppColors.primary,
              child: Column(
                children: [
                  Container(
                    padding: const EdgeInsets.all(24),
                    child: const Text(
                      'وسّط - لوحة التحكم',
                      style: TextStyle(
                        color: Colors.white,
                        fontSize: 24,
                        fontWeight: FontWeight.bold,
                      ),
                    ),
                  ),
                  Expanded(
                    child: ListView.builder(
                      itemCount: _menuItems.length,
                      itemBuilder: (context, index) {
                        final item = _menuItems[index];
                        final isSelected = _selectedIndex == index;
                        
                        return ListTile(
                          leading: Icon(
                            item.icon,
                            color: isSelected ? Colors.white : Colors.white70,
                          ),
                          title: Text(
                            item.title,
                            style: TextStyle(
                              color: isSelected ? Colors.white : Colors.white70,
                              fontWeight: isSelected ? FontWeight.bold : FontWeight.normal,
                            ),
                          ),
                          selected: isSelected,
                          selectedTileColor: Colors.white.withOpacity(0.1),
                          onTap: () {
                            setState(() {
                              _selectedIndex = index;
                            });
                          },
                        );
                      },
                    ),
                  ),
                ],
              ),
            ),
          // Main Content
          Expanded(
            child: Column(
              children: [
                // Top Bar
                Container(
                  height: 60,
                  decoration: BoxDecoration(
                    color: Colors.white,
                    boxShadow: [
                      BoxShadow(
                        color: Colors.black.withOpacity(0.1),
                        blurRadius: 4,
                        offset: const Offset(0, 2),
                      ),
                    ],
                  ),
                  child: Row(
                    children: [
                      if (!isDesktop)
                        IconButton(
                          icon: const Icon(Icons.menu),
                          onPressed: () {
                            // Show drawer
                          },
                        ),
                      const Spacer(),
                      IconButton(
                        icon: const Icon(Icons.notifications),
                        onPressed: () {},
                      ),
                      const SizedBox(width: 16),
                      const CircleAvatar(
                        child: Text('أ'),
                      ),
                      const SizedBox(width: 16),
                    ],
                  ),
                ),
                // Page Content
                Expanded(
                  child: _menuItems[_selectedIndex].page,
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }
}

class _MenuItem {
  final IconData icon;
  final String title;
  final Widget page;

  _MenuItem({
    required this.icon,
    required this.title,
    required this.page,
  });
}

// Dashboard Page
class _DashboardPage extends StatelessWidget {
  const _DashboardPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(24),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Text(
            'لوحة القيادة',
            style: Theme.of(context).textTheme.displaySmall,
          ),
          const SizedBox(height: 24),
          // Statistics Cards
          GridView.count(
            shrinkWrap: true,
            crossAxisCount: 4,
            crossAxisSpacing: 16,
            mainAxisSpacing: 16,
            childAspectRatio: 1.5,
            children: [
              _StatCard(
                title: 'إجمالي الطلبات',
                value: '1,234',
                icon: Icons.shopping_cart,
                color: Colors.blue,
              ),
              _StatCard(
                title: 'الطلبات النشطة',
                value: '56',
                icon: Icons.pending,
                color: Colors.orange,
              ),
              _StatCard(
                title: 'إجمالي المستخدمين',
                value: '892',
                icon: Icons.people,
                color: Colors.green,
              ),
              _StatCard(
                title: 'الإيرادات الشهرية',
                value: '2.5M IQD',
                icon: Icons.attach_money,
                color: Colors.purple,
              ),
            ],
          ),
          const SizedBox(height: 24),
          // Recent Activity
          Expanded(
            child: Card(
              child: Padding(
                padding: const EdgeInsets.all(16),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Text(
                      'النشاط الأخير',
                      style: Theme.of(context).textTheme.headlineSmall,
                    ),
                    const SizedBox(height: 16),
                    Expanded(
                      child: ListView.builder(
                        itemCount: 10,
                        itemBuilder: (context, index) {
                          return ListTile(
                            leading: const CircleAvatar(
                              child: Icon(Icons.person),
                            ),
                            title: Text('طلب جديد #${1234 + index}'),
                            subtitle: const Text('تصوير منتجات - بغداد'),
                            trailing: const Text('قبل 5 دقائق'),
                          );
                        },
                      ),
                    ),
                  ],
                ),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

class _StatCard extends StatelessWidget {
  final String title;
  final String value;
  final IconData icon;
  final Color color;

  const _StatCard({
    Key? key,
    required this.title,
    required this.value,
    required this.icon,
    required this.color,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Card(
      child: Padding(
        padding: const EdgeInsets.all(16),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          children: [
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: [
                Icon(
                  icon,
                  color: color,
                  size: 32,
                ),
                Text(
                  value,
                  style: Theme.of(context).textTheme.headlineMedium?.copyWith(
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ],
            ),
            Text(
              title,
              style: Theme.of(context).textTheme.bodyMedium,
            ),
          ],
        ),
      ),
    );
  }
}

// Requests Management Page
class _RequestsManagementPage extends StatelessWidget {
  const _RequestsManagementPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(24),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceBetween,
            children: [
              Text(
                'إدارة الطلبات',
                style: Theme.of(context).textTheme.displaySmall,
              ),
              Row(
                children: [
                  OutlinedButton.icon(
                    icon: const Icon(Icons.filter_list),
                    label: const Text('فلتر'),
                    onPressed: () {},
                  ),
                  const SizedBox(width: 8),
                  OutlinedButton.icon(
                    icon: const Icon(Icons.download),
                    label: const Text('تصدير'),
                    onPressed: () {},
                  ),
                ],
              ),
            ],
          ),
          const SizedBox(height: 24),
          // Data Table
          Expanded(
            child: Card(
              child: SingleChildScrollView(
                scrollDirection: Axis.horizontal,
                child: DataTable(
                  columns: const [
                    DataColumn(label: Text('رقم الطلب')),
                    DataColumn(label: Text('العميل')),
                    DataColumn(label: Text('نوع الخدمة')),
                    DataColumn(label: Text('المدينة')),
                    DataColumn(label: Text('الحالة')),
                    DataColumn(label: Text('التاريخ')),
                    DataColumn(label: Text('الإجراءات')),
                  ],
                  rows: List.generate(20, (index) {
                    return DataRow(
                      cells: [
                        DataCell(Text('#${1000 + index}')),
                        DataCell(Text('عميل ${index + 1}')),
                        DataCell(Text('تصوير')),
                        DataCell(Text('بغداد')),
                        DataCell(
                          Container(
                            padding: const EdgeInsets.symmetric(
                              horizontal: 8,
                              vertical: 4,
                            ),
                            decoration: BoxDecoration(
                              color: AppColors.warning.withOpacity(0.2),
                              borderRadius: BorderRadius.circular(12),
                            ),
                            child: const Text(
                              'قيد المراجعة',
                              style: TextStyle(
                                color: AppColors.warning,
                                fontSize: 12,
                              ),
                            ),
                          ),
                        ),
                        DataCell(Text('2025/05/24')),
                        DataCell(
                          Row(
                            children: [
                              IconButton(
                                icon: const Icon(Icons.visibility),
                                onPressed: () {},
                              ),
                              IconButton(
                                icon: const Icon(Icons.edit),
                                onPressed: () {},
                              ),
                            ],
                          ),
                        ),
                      ],
                    );
                  }),
                ),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

// Other pages (simplified)
class _OffersManagementPage extends StatelessWidget {
  const _OffersManagementPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return const Center(child: Text('إدارة العروض'));
  }
}

class _UsersManagementPage extends StatelessWidget {
  const _UsersManagementPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return const Center(child: Text('إدارة المستخدمين'));
  }
}

class _FinancePage extends StatelessWidget {
  const _FinancePage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return const Center(child: Text('المالية'));
  }
}

class _SettingsPage extends StatelessWidget {
  const _SettingsPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return const Center(child: Text('الإعدادات'));
  }
}
```

---

## المرحلة 3: تطوير Backend و APIs (يوم 8-10)

### اليوم 8: إعداد Cloud Functions

#### 8.1 هيكل المشروع
```
functions/
├── src/
│   ├── index.ts
│   ├── auth/
│   │   ├── sendOtp.ts
│   │   ├── verifyOtp.ts
│   │   └── userRegistration.ts
│   ├── requests/
│   │   ├── createRequest.ts
│   │   ├── updateRequest.ts
│   │   └── getRequests.ts
│   ├── offers/
│   │   ├── submitOffer.ts
│   │   ├── processOffer.ts
│   │   └── getOffers.ts
│   ├── messaging/
│   │   ├── sendMessage.ts
│   │   └── filterMessage.ts
│   ├── notifications/
│   │   └── sendNotification.ts
│   └── utils/
│       ├── validators.ts
│       ├── auth.ts
│       └── pricing.ts
├── package.json
└── tsconfig.json
```

#### 8.2 الوظائف الأساسية

**functions/src/index.ts:**
```typescript
import * as functions from 'firebase-functions';
import * as admin from 'firebase-admin';
import { sendOtp } from './auth/sendOtp';
import { verifyOtp } from './auth/verifyOtp';
import { createRequest } from './requests/createRequest';
import { submitOffer } from './offers/submitOffer';
import { sendMessage } from './messaging/sendMessage';

admin.initializeApp();

// Auth Functions
export const sendOtpFunction = functions.https.onCall(sendOtp);
export const verifyOtpFunction = functions.https.onCall(verifyOtp);

// Request Functions
export const createRequestFunction = functions.https.onCall(createRequest);

// Offer Functions
export const submitOfferFunction = functions.https.onCall(submitOffer);

// Messaging Functions
export const sendMessageFunction = functions.https.onCall(sendMessage);

// Triggers
export const onRequestCreated = functions.firestore
  .document('requests/{requestId}')
  .onCreate(async (snap, context) => {
    const request = snap.data();
    // Notify admin and relevant providers
  });

export const onOfferSubmitted = functions.firestore
  .document('offers/{offerId}')
  .onCreate(async (snap, context) => {
    const offer = snap.data();
    // Process offer and notify admin
  });
```

**functions/src/utils/pricing.ts:**
```typescript
interface PricingConfig {
  serviceType: string;
  baseMargin: number;
  urgencyMultipliers: {
    NORMAL: number;
    URGENT: number;
    VERY_URGENT: number;
  };
}

export function calculateFinalPrice(
  originalPrice: number,
  serviceType: string,
  urgency: string,
  clientHistory: any
): number {
  const config = getPricingConfig(serviceType);
  
  let margin = config.baseMargin;
  margin *= config.urgencyMultipliers[urgency] || 1;
  
  // Apply volume discount
  if (clientHistory.totalOrders > 10) {
    margin -= 0.05;
  }
  
  // Ensure margin is within bounds
  margin = Math.max(0.15, Math.min(0.5, margin));
  
  return Math.round(originalPrice * (1 + margin));
}

function getPricingConfig(serviceType: string): PricingConfig {
  const configs = {
    PHOTOGRAPHY: {
      baseMargin: 0.3,
      urgencyMultipliers: {
        NORMAL: 1,
        URGENT: 1.2,
        VERY_URGENT: 1.5,
      },



