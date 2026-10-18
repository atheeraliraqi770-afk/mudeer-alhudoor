# مدير الحضور — مشروع Android WebView

هذا مشروع مصدر Android قابل للبناء عبر Android SDK/Gradle، وليس ملف APK جاهزاً. واجهة الويب المرفقة تتصل بـ Firebase حسب الإعدادات التي أدخلتها.

## إنشاء APK من GitHub (من الهاتف ممكن)
1. فك ضغط ملف ZIP وارفع محتوياته إلى مستودع GitHub جديد، مع جعل `settings.gradle` في جذر المستودع.
2. افتح تبويب Actions واسمح بتشغيل workflows إن طلب منك.
3. شغّل `Build Android APK` عبر Run workflow (أو ادفع commit إلى main).
4. بعد نجاح البناء، افتح تشغيل workflow وانزل إلى Artifacts وحمّل `mudeer-alhudoor-debug-apk`.
5. فك ضغط الـ artifact، وانقل `app-debug.apk` إلى الهاتف وثبّته. قد يطلب Android السماح بالتثبيت من هذا المصدر.

## قبل الاستخدام الحقيقي
- هذا APK تجريبي غير موقّع للنشر التجاري؛ مناسب للاختبار فقط.
- لا تعتبر مزامنة Firebase جاهزة حتى تضبط Authentication وحسابات المستخدمين وقواعد RTDB بشكل آمن وتختبرها على جهازين.
- يجب إضافة عقدة `users/{UID}` للمدير بصلاحية `role: manager` و`active: true` من جهة موثوقة، ومراجعة قواعد `firebase.rules.example.json`.
- بعض ميزات الويب مثل الطباعة إلى PDF قد تعتمد على سلوك WebView، ويجب اختبارها.
- لا ترفع مفاتيح خدمة Firebase أو كلمات مرور إلى GitHub. إعدادات Firebase Web ليست مفتاح Admin، لكن قواعد قاعدة البيانات هي الحماية الحقيقية.
- راجع `app.js` وسلوك صلاحيات المستخدمين قبل إدخال بيانات مالية حقيقية.

## المكونات
- واجهة RTL عربية محلية داخل APK.
- WebViewAssetLoader لتقديم الملفات محلياً ضمن HTTPS آمن.
- اتصال Firebase Web SDK عبر الإنترنت.
