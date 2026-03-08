# 🤝 دليل المساهمة

شكراً لاهتمامك بالمساهمة في مشروع Flutter ERP!

## 📝 كيفية المساهمة

### 1. إنشاء Fork

قم بإنشاء fork للمشروع إلى حسابك على GitHub.

### 2. استنساخ المشروع

```bash
git clone https://github.com/your-username/flutter-erp.git
cd flutter-erp
```

### 3. إنشاء فرع جديد

```bash
git checkout -b feature/your-feature-name
```

### 4. إجراء التغييرات

قم بإجراء التغييرات المطلوبة واتبع معايير الكود.

### 5. اختبار التغييرات

```bash
flutter test
```

### 6. إرسال التغييرات

```bash
git add .
git commit -m "feat: description of your changes"
git push origin feature/your-feature-name
```

### 7. إنشاء Pull Request

اذهب إلى GitHub وقم بإنشاء Pull Request جديد.

## 📋 معايير الكود

### Flutter/Dart

- اتبع Effective Dart Style Guide
- استخدم `flutter_lints`
- اكتب اختبارات للمنطق المعقد
- استخدم Riverpod للـ State Management

### هيكل الملفات

```
lib/
├── core/           # الأساسيات (ثيمات، ثوابت، أدوات)
├── data/           # البيانات (نماذج، مستودعات)
├── services/       # الخدمات
├── providers/      # Riverpod Providers
├── screens/        # الشاشات
└── widgets/        # المكونات المشتركة
```

## 🏷️ أنواع Commit

| النوع | الوصف |
|-------|-------|
| `feat` | ميزة جديدة |
| `fix` | إصلاح خطأ |
| `docs` | تغييرات في التوثيق |
| `style` | تغييرات في التنسيق |
| `refactor` | إعادة هيكلة الكود |
| `test` | إضافة/تعديل اختبارات |
| `chore` | مهام صيانة |

## 📞 التواصل

- GitHub Issues: للتبليغ عن الأخطاء
- Discussions: للأسئلة والمناقشات

شكراً لمساهمتك! 🎉
