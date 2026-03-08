# 🤝 دليل المساهمة

شكراً لاهتمامك بالمساهمة في مشروع ERP! نرحب بجميع المساهمات.

## 📝 كيفية المساهمة

### 1. إنشاء Fork

قم بإنشاء fork للمشروع إلى حسابك على GitHub.

### 2. استنساخ المشروع

```bash
git clone https://github.com/your-username/erp-system.git
cd erp-system
```

### 3. إنشاء فرع جديد

```bash
git checkout -b feature/your-feature-name
```

### 4. إجراء التغييرات

قم بإجراء التغييرات المطلوبة واتبع معايير الكود.

### 5. اختبار التغييرات

```bash
# Backend
dotnet test

# Frontend
npm test
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

### Backend (.NET)

- اتبع C# Coding Conventions
- استخدم async/await للعمليات غير المتزامنة
- اكتب اختبارات وحدة لجميع الخدمات
- استخدم Dependency Injection

### Frontend (React/TypeScript)

- استخدم TypeScript لجميع الملفات
- اتبع ESLint و Prettier
- استخدم Functional Components مع Hooks
- اكتب اختبارات للمكونات المعقدة

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
- Email: dev@erpsystem.com

شكراً لمساهمتك! 🎉
