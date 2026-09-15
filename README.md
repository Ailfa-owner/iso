# Alif Linux 0.1.0 — VMware Fix AMD64

هذا المستودع يحتفظ ببيانات إصدار صورة Alif Linux 0.1.0 بصيغة ISO. بسبب حد GitHub البالغ 2 GiB لكل أصل Release، تم تقسيم الصورة إلى أجزاء داخل إصدار GitHub بدلاً من وضعها في Git مباشرة.

## تنزيل وإعادة التجميع

نزّل جميع الأجزاء من صفحة [الإصدار v0.1.0-vmware-fix](https://github.com/Ailfa-owner/iso/releases/tag/v0.1.0-vmware-fix)، ثم نفّذ:

```bash
cat alif-linux-0.1.0-vmware-fix-amd64.iso.part-* > alif-linux-0.1.0-vmware-fix-amd64.iso
sha256sum -c SHA256SUMS
```

البصمة المتوقعة للصورة الكاملة:

```text
a1465452add4896962dda3a3ec0092444e9ab9a02cb8cd420e96846db2eca290  alif-linux-0.1.0-vmware-fix-amd64.iso
```

## ملخص الفحص

تم فحص ISO 9660 وEl Torito وطبقة SquashFS وفهرس الملفات. فحص القطاعات بواسطة `xorriso -check_media` نجح بالكامل. الصورة تحتوي على إقلاع BIOS وUEFI، ونواة Ubuntu 24.04 ذات الإصدار `6.8.0-138-generic`، وطبقة نظام بحجم غير مضغوط يقارب 7.1 GB.

التفاصيل والعيوب القابلة للتحقق موجودة في [تقرير التدقيق](AUDIT_AR.md).
