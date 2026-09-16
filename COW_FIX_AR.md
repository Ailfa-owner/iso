# إصلاح Live OverlayFS في Alif Linux 0.1.4

## المشكلة

كان الإقلاع Live يتوقف داخل initramfs عند:

```text
/cow format specified as 'overlay' and no support found
```

## الإصلاح

تمت إعادة توليد `casper/initrd` من rootfs الحالي مع تضمين وحدات `overlay` و`loop` و`squashfs`، كما تم تعديل سكربت casper بحيث لا يتوقف مبكراً بعد فشل طلب `modprobe`، بل يواصل إلى اختبار mount الفعلي لـOverlayFS.

## التحقق

تم تشغيل QEMU بوضع serial لمدة 90 ثانية. النسخة المصححة:

- لم تطبع رسالة `/cow format specified as 'overlay' and no support found`.
- لم تدخل إلى موجه `(initramfs)`.
- لم يظهر Kernel Panic.
- وصلت إلى `basic.target` و`getty-pre.target` في systemd.

ظهرت رسائل فشل متكررة لخدمة `auditd` في بيئة QEMU، لكنها لم تمنع الوصول إلى أهداف systemd الأساسية، وتحتاج معالجة مستقلة لاحقاً.

تم أيضاً التحقق من `SHA256SUMS` داخل ISO، وكانت جميع الملفات الأساسية `OK`، مع الحفاظ على إقلاع BIOS وUEFI.

## بصمة ISO الكاملة

```text
c33259d300b72c9a0244e607881143611809ac977b4d956a7eda680f2e6b17cf  alif-linux-0.1.4-cow-fix-amd64.iso
```
