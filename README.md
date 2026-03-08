# 🏪 نظام ERP المتكامل للمحلات التجارية

<p align="center">
  <img src="assets/logo.png" alt="ERP System Logo" width="200"/>
</p>

<p align="center">
  <a href="#-نظرة-عامة">نظرة عامة</a> •
  <a href="#-المميزات-الرئيسية">المميزات</a> •
  <a href="#-الوحدات-النظامية">الوحدات</a> •
  <a href="#-stack-التقني">Stack التقني</a> •
  <a href="#-خارطة-الطريق">خارطة الطريق</a> •
  <a href="#-التوثيق">التوثيق</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.0.0-blue.svg" alt="Version"/>
  <img src="https://img.shields.io/badge/Status-Development-green.svg" alt="Status"/>
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License"/>
  <img src="https://img.shields.io/badge/Platform-Web%20%7C%20Desktop-lightgrey.svg" alt="Platform"/>
</p>

---

## 📋 نظرة عامة

نظام **ERP المتكامل** هو حل برمجي شامل مصمم خصيصاً للمحلات التجارية والسوبر ماركت. يوفر النظام إدارة متكاملة لجميع العمليات التجارية والمحاسبية مع واجهة سهلة الاستخدام وأداء عالي.

### 🎯 الأهداف الرئيسية

- **⚡ الكفاءة**: تسريع العمليات اليومية وتقليل الوقت المهدور
- **📊 الشفافية**: رؤية شاملة لجميع العمليات في الوقت الفعلي
- **🔒 الأمان**: حماية البيانات والمعاملات بأعلى معايير الأمان
- **📈 القابلية للتوسع**: دعم النمو من فرع واحد إلى شبكة فروع

---

## ✨ المميزات الرئيسية

```mermaid
mindmap
  root((نظام ERP))
    المحاسبة
      شجرة حسابات متكاملة
      قيود يومية آلية
      قوائم مالية فورية
    المبيعات
      نقاط بيع سريعة
      فواتير إلكترونية
      عروض وخصومات
    المشتريات
      طلبات شراء
      إدارة الموردين
      مقارنة أسعار
    المخزون
      تتبع فوري
      جرد ذكي
      تنبيهات نفاد
    العملاء
      نظام ولاء
      نقاط مكافآت
      تحليل سلوكي
    التقارير
      لوحة تحكم
      تقارير ذكية
      تحليلات تنبؤية
```

---

## 🧩 الوحدات النظامية

| الوحدة | الوصف | الحالة |
|--------|-------|--------|
| 📊 [المحاسبة](docs/04-Accounting-System.md) | شجرة الحسابات، القيود اليومية، القوائم المالية | ✅ جاهز |
| 🛒 [المبيعات](docs/05-Sales-System.md) | نقاط البيع، الفواتير، المرتجعات | ✅ جاهز |
| 📦 [المشتريات](docs/06-Purchase-System.md) | طلبات الشراء، فواتير الموردين | ✅ جاهز |
| 📋 [المخزون](docs/07-Inventory-System.md) | المنتجات، المستودعات، الجرد | ✅ جاهز |
| 👥 [العملاء](docs/08-Customer-System.md) | إدارة العملاء، النقاط، الولاء | ✅ جاهز |
| 🏭 [الموردين](docs/09-Supplier-System.md) | تقييم الموردين، العقود | ✅ جاهز |
| 📈 [التقارير](docs/10-Reporting-System.md) | لوحة التحكم، التحليلات | ✅ جاهز |

---

## 🛠️ Stack التقني

### Frontend
```
React 18+ • TypeScript • Tailwind CSS • shadcn/ui • React Query • Zustand
```

### Backend
```
.NET 8 • ASP.NET Core • Entity Framework • PostgreSQL • Redis
```

### Infrastructure
```
Docker • Kubernetes • Nginx • RabbitMQ • SignalR
```

<p align="center">
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white" />
</p>

---

## 🗺️ خارطة الطريق

```mermaid
gantt
    title خارطة طريق التطوير
    dateFormat  YYYY-MM
    section المرحلة 1
    التحضير والتصميم    :done, a1, 2026-01, 2M
    section المرحلة 2
    التطوير الأساسي    :active, a2, after a1, 2M
    section المرحلة 3
    الوحدات الرئيسية   :a3, after a2, 2M
    section المرحلة 4
    التقارير والتحليلات :a4, after a3, 1M
    section المرحلة 5
    الاختبار والإطلاق   :a5, after a4, 1M
```

### المراحل التفصيلية

| المرحلة | المدة | المخرجات |
|---------|-------|----------|
| **الإطلاق** (3-4 أشهر) | يناير - أبريل | النظام الأساسي |
| **التعزيز** (2-3 أشهر) | مايو - يوليو | العروض، الولاء، الفروع |
| **الابتكار** (2-3 أشهر) | أغسطس - أكتوبر | موبايل، AI، تكاملات |
| **التوسع** (مستمر) | نوفمبر+ | تحسينات مستمرة |

---

## 📚 التوثيق

### 📖 الوثائق الرئيسية

| الوثيقة | الوصف |
|---------|-------|
| [📋 نظرة عامة](docs/01-System-Overview.md) | مقدمة شاملة عن النظام |
| [📊 تحليل الأعمال](docs/02-Business-Analysis.md) | تحليل المتطلبات والعمليات |
| [🧩 الوحدات النظامية](docs/03-System-Modules.md) | هيكل الوحدات والتكامل |
| [💾 قاعدة البيانات](docs/11-Database-Design.md) | تصميم قاعدة البيانات |
| [🏗️ بنية النظام](docs/12-System-Architecture.md) | البنية التقنية والتصميم |
| [🔒 الأمان](docs/15-Security-System.md) | استراتيجية الأمان |

### 🔧 الوثائق التقنية

| الوثيقة | الوصف |
|---------|-------|
| [⚙️ Stack التقني](docs/13-Technology-Stack.md) | التقنيات والأدوات |
| [🎨 تصميم الواجهات](docs/14-UI-UX-Design.md) | UI/UX ومبادئ التصميم |
| [🚀 بنية النشر](docs/18-Deployment-Architecture.md) | استراتيجية النشر |
| [📱 التوسع المستقبلي](docs/19-Future-Expansion.md) | خطط التطوير المستقبلية |

---

## 🏛️ بنية النظام

```mermaid
flowchart TB
    subgraph Frontend["🖥️ Frontend Layer"]
        Web[React Web App]
        Desktop[Electron Desktop]
        Mobile[Mobile App]
    end
    
    subgraph APILayer["🔌 API Layer"]
        Gateway[API Gateway]
        Auth[Auth Middleware]
        Rate[Rate Limiting]
    end
    
    subgraph Backend["⚙️ Backend Layer"]
        API[.NET Core API]
        Services[Business Services]
        Repos[Repositories]
    end
    
    subgraph Data["💾 Data Layer"]
        Postgres[(PostgreSQL)]
        Redis[(Redis Cache)]
        MinIO[MinIO Storage]
    end
    
    Web --> Gateway
    Desktop --> Gateway
    Mobile --> Gateway
    Gateway --> Auth --> Rate --> API
    API --> Services --> Repos
    Repos --> Postgres
    Repos --> Redis
    Repos --> MinIO
```

---

## 🚀 البدء السريع

### متطلبات النظام

- **Node.js** 18+
- **.NET SDK** 8.0+
- **PostgreSQL** 15+
- **Docker** (اختياري)

### خطوات التثبيت

```bash
# 1. استنساخ المستودع
git clone https://github.com/your-org/erp-system.git
cd erp-system

# 2. تثبيت تبعيات Frontend
cd src/ERP.Web
npm install

# 3. تثبيت تبعيات Backend
cd ../ERP.API
dotnet restore

# 4. تشغيل قاعدة البيانات
docker-compose up -d postgres redis

# 5. تشغيل التطبيق
dotnet run
```

---

## 👥 الفريق

| الدور | العدد |
|-------|-------|
| مدير المشروع | 1 |
| مطور Backend (.NET) | 2 |
| مطور Frontend (React) | 2 |
| مصمم UI/UX | 1 |
| مهندس QA | 1 |
| DBA | 1 (جزئي) |

---

## 📄 الترخيص

هذا المشروع مرخص بموجب [MIT License](LICENSE).

---

<p align="center">
  Made with ❤️ for Retail Excellence
</p>

<p align="center">
  <a href="mailto:contact@erpsystem.com">📧 تواصل معنا</a> •
  <a href="https://erpsystem.com">🌐 الموقع الرسمي</a> •
  <a href="https://docs.erpsystem.com">📖 التوثيق الكامل</a>
</p>
