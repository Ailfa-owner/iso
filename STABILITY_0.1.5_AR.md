# مرشح الاستقرار Alif Linux 0.1.5

تم تحسين جلسة Live لتجنب أخطاء الخدمات غير الضرورية في بيئات الافتراضية:

- تعطيل التشغيل التلقائي لـ `auditd.service` في صورة Live/سطح المكتب. الحزمة تبقى موجودة ويمكن تفعيلها يدوياً بعد تثبيت النظام عندما تكون بيئة kernel وaudit netlink متاحة.
- تعطيل `whoopsie.path` افتراضياً لتجنب فشل خدمة تقارير الأعطال في جلسة Live.
- إزالة ملف إعداد remote تجريبي من `auditd` كان يحتوي بيانات اعتماد وهمية.
- الاحتفاظ بإصلاح OverlayFS وإعادة توليد initrd.

## التحقق الآلي

تم تشغيل QEMU بوضع serial لمدة 90 ثانية. النتيجة:

- وصل النظام إلى `basic.target`.
- وصل إلى `getty-pre.target`.
- لم يظهر Kernel Panic.
- لم يظهر موجه `(initramfs)`.
- لم تظهر رسالة `/cow format specified as 'overlay' and no support found`.
- لم تعد تظهر أخطاء `auditd.service` أو `whoopsie.path` في الاختبار.

تم التحقق من checksums الداخلية لجميع ملفات الإقلاع والـkernel و`initrd` و`filesystem.squashfs`، كما تم الحفاظ على BIOS وUEFI.

## حدود التحقق

هذا يثبت سلامة مسار الإقلاع Live النصي وطبقة OverlayFS داخل QEMU. لا يثبت وحده عمل سطح المكتب الرسومي على عتاد حقيقي أو داخل VMware، ولا يغني عن اختبار المثبّت وإعادة التشغيل من القرص المثبت.

## بصمة ISO

```text
6ee6b9d1f3e2c5a3a5df8ada7804ea513661527970abecf79d8002b92eef31a8  alif-linux-0.1.5-stability-candidate-amd64.iso
```
