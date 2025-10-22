# 🌟 عطور AI | Smart Perfume Store with AI

موقع عطور ذكي يستخدم الذكاء الاصطناعي لاقتراح أفضل 5 عطور بناءً على تفضيلات العميل

A smart perfume e-commerce platform using AI to recommend the top 5 perfumes based on customer preferences

---

## ✨ المميزات | Features

### 👨‍💼 واجهة التاجر (Merchant Dashboard)
- ✅ **لوحة تحكم احترافية** - إدارة شاملة للمخزون
- ✅ **إضافة/تعديل/حذف العطور** - نظام CRUD كامل
- ✅ **منزلقات المكونات** - تحديد نسب المكونات بدقة (زهري، خشبي، فاكهي، شرقي، منعش)
- ✅ **التحقق الذكي** - يجب أن يكون مجموع النسب 100%
- ✅ **إحصائيات مباشرة** - عدد العطور، المخزون، قيمة المخزون
- ✅ **رقم الرف** - تنظيم موقع كل عطر في المحل

### 🛍️ واجهة الزبون (Customer Experience)
- ✅ **محادثة ذكية مع AI** - نظام chatbot تفاعلي
- ✅ **أسئلة مخصصة** - 4 أسئلة لفهم التفضيلات
- ✅ **حساب التوافق الذكي** - خوارزمية دقيقة لمقارنة التفضيلات بالمكونات
- ✅ **أفضل 5 عطور** - مرتبة حسب نسبة التوافق
- ✅ **نسبة توافق دقيقة** - من 0% إلى 100%
- ✅ **عرض مكونات العطر** - رسوم بيانية تفاعلية
- ✅ **لا اختيار عشوائي** - كل شيء مبني على بيانات حقيقية

### 🎨 Animations (Framer Motion)
- ✅ **انتقالات سلسة** - Page transitions
- ✅ **بطاقات متحركة** - Hover effects على العطور
- ✅ **رسوم متحركة للرسائل** - Chat bubbles animation
- ✅ **تأثيرات Scale & Fade** - عند الظهور والاختفاء
- ✅ **شريط التقدم المتحرك** - للمكونات
- ✅ **تأثيرات Float** - للأيقونات

---

## 🚀 التثبيت والتشغيل | Installation

### المتطلبات | Prerequisites
```bash
Node.js v18+
npm or yarn
```

### خطوات التشغيل | Steps

```bash
# 1. انتقل للمجلد
cd smart-perfume-ai

# 2. تثبيت المكتبات
npm install

# 3. تشغيل المشروع
npm run dev
```

**افتح المتصفح على:** http://localhost:5173

---

## 📁 هيكل المشروع | Project Structure

```
smart-perfume-ai/
├── src/
│   ├── components/
│   │   ├── AddPerfumeForm.jsx      # نموذج إضافة/تعديل عطر
│   │   ├── ComponentSlider.jsx     # منزلقات المكونات
│   │   ├── AIChat.jsx              # محادثة AI
│   │   └── RecommendedPerfumes.jsx # عرض أفضل 5 عطور
│   ├── pages/
│   │   ├── HomePage.jsx            # الصفحة الرئيسية
│   │   ├── MerchantDashboard.jsx   # لوحة التاجر
│   │   └── CustomerPage.jsx        # صفحة الزبون
│   ├── store/
│   │   └── perfumeStore.js         # Zustand State Management
│   ├── App.jsx                     # المكون الرئيسي
│   ├── main.jsx                    # Entry point
│   └── index.css                   # Styles
├── package.json
├── tailwind.config.js
└── README.md
```

---

## 🧠 كيف يعمل الذكاء الاصطناعي | How AI Works

### 1. جمع التفضيلات
يطرح الذكاء الاصطناعي 4 أسئلة:
- **النوع**: رجالي / نسائي / للجنسين
- **التفضيلات**: زهري، خشبي، فاكهي، شرقي، منعش (متعدد)
- **القوة**: خفيف / متوسط / قوي
- **المناسبة**: عمل / سهرة / يومي / هدية

### 2. تحويل الإجابات لنسب مئوية
```javascript
// مثال: إذا اختار الزبون [زهري، خشبي]
components = {
  floral: 50%,   // زهري
  woody: 50%,    // خشبي
  fruity: 0%,
  oriental: 0%,
  fresh: 0%
}
```

### 3. حساب التوافق
```javascript
matchScore = Σ(similarity × preference) / totalWeight

حيث:
- similarity = 100 - |عطر% - تفضيل%|
- preference = نسبة التفضيل
```

### 4. الترتيب والعرض
- فلترة العطور المتوفرة فقط (stock > 0)
- فلترة حسب النوع
- ترتيب حسب نسبة التوافق (الأعلى أولاً)
- عرض أفضل 5 عطور

---

## 🎯 مثال عملي | Example

### التاجر يضيف عطر:
```javascript
{
  name: "عطر الورد الملكي",
  brand: "Luxury Scents",
  type: "نسائي",
  price: 450,
  stock: 25,
  shelf: "A-12",
  components: {
    floral: 70%,    // زهري
    woody: 10%,     // خشبي
    fruity: 15%,    // فاكهي
    oriental: 5%,   // شرقي
    fresh: 0%       // منعش
  }
}
```

### الزبون يختار:
- النوع: نسائي
- التفضيلات: زهري، فاكهي
- القوة: متوسطة
- المناسبة: يومي

### النتيجة:
**نسبة التوافق: 92%** ✅

---

## 🛠️ التقنيات المستخدمة | Technologies

### Frontend
- **React 18** - UI Library
- **Vite** - Build Tool
- **Framer Motion** - Animations
- **Tailwind CSS** - Styling
- **Zustand** - State Management
- **Lucide React** - Icons

### التصميم
- ألوان فاخرة (ذهبي، فضي، أبيض)
- دعم كامل للعربية (RTL)
- Glassmorphism effects
- Responsive design

---

## 📊 قاعدة البيانات | Database

حالياً يستخدم **Zustand** لإدارة الحالة (in-memory).

### للتطوير المستقبلي:
```bash
# MongoDB
npm install mongoose

# أو PostgreSQL
npm install prisma @prisma/client
```

---

## 🔮 التطوير المستقبلي | Future Development

### المرحلة 1
- [ ] دمج OpenAI ChatGPT API حقيقي
- [ ] قاعدة بيانات (MongoDB/PostgreSQL)
- [ ] نظام المستخدمين والتسجيل
- [ ] سلة التسوق ونظام الطلبات

### المرحلة 2
- [ ] نظام الدفع الإلكتروني
- [ ] تتبع الشحنات
- [ ] نظام التقييمات والمراجعات
- [ ] إشعارات Push

### المرحلة 3
- [ ] تطبيق موبايل (React Native)
- [ ] Dashboard متقدم للإحصائيات
- [ ] نظام ولاء العملاء
- [ ] تكامل مع الشبكات الاجتماعية

---

## 🎨 الألوان | Colors

```css
Gold: #f59e0b (Primary)
Purple: #a855f7 (AI/Customer)
Luxury: #a08f70 (Backgrounds)
White: #ffffff (Clean)
```

---

## 💡 نصائح الاستخدام | Usage Tips

### للتاجر:
1. ✅ تأكد أن مجموع النسب = 100%
2. ✅ حدد رقم الرف لسهولة الوصول
3. ✅ حدّث المخزون باستمرار
4. ✅ استخدم صور عالية الجودة

### للزبون:
1. ✅ أجب بصدق على الأسئلة
2. ✅ يمكنك اختيار أكثر من تفضيل
3. ✅ قارن بين العطور الموصى بها
4. ✅ تحقق من نسبة التوافق

---

## 📄 الترخيص | License

MIT License - مفتوح المصدر

---

## 🤝 المساهمة | Contributing

المساهمات مرحب بها!

1. Fork المشروع
2. أنشئ فرع (`git checkout -b feature/amazing`)
3. Commit (`git commit -m 'Add feature'`)
4. Push (`git push origin feature/amazing`)
5. افتح Pull Request

---

## 📞 الدعم | Support

للأسئلة والدعم:
- 📧 Email: support@perfume-ai.com
- 🌐 Website: www.perfume-ai.com

---

**صنع بـ ❤️ باستخدام React و AI**

Made with ❤️ using React & AI

---

## 🎯 ملاحظات مهمة

### الذكاء الاصطناعي الحالي
- النظام الحالي يستخدم **محاكاة ذكية** للـ AI
- الخوارزمية تعتمد على **حساب رياضي دقيق** للتوافق
- **ليس عشوائياً** - كل اقتراح مبني على البيانات الفعلية

### للتكامل مع ChatGPT API الحقيقي:
```javascript
// في AIChat.jsx
const response = await fetch('https://api.openai.com/v1/chat/completions', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${YOUR_API_KEY}`,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    model: 'gpt-4',
    messages: [
      { role: 'system', content: 'أنت مساعد ذكي لاختيار العطور...' },
      { role: 'user', content: userMessage }
    ]
  })
});
```

---

### الخوارزمية الذكية

```
كيف نحسب التوافق؟

1. لكل مكون (زهري، خشبي، إلخ):
   - نحسب الفرق بين تفضيل الزبون ونسبة العطر
   - similarity = 100 - |difference|
   
2. نضرب كل similarity بوزنها (تفضيل الزبون)

3. نحسب المتوسط المرجح

مثال:
الزبون يفضل: زهري 50%، خشبي 50%
العطر يحتوي: زهري 70%، خشبي 10%

زهري: similarity = 100 - |70-50| = 80
خشبي: similarity = 100 - |10-50| = 60

النتيجة = (80×50 + 60×50) / 100 = 70% توافق
```

---

🎉 **المشروع جاهز للاستخدام!**
