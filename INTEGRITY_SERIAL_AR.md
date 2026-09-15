# الإصدار 0.1.2 — Checksums داخل ISO ووضع Serial Diagnostic

## Checksums داخل الصورة

أضيف الملف `/SHA256SUMS` إلى جذر ISO، ويتضمن بصمات SHA-256 لملفات الإقلاع والـkernel و`initrd` و`filesystem.squashfs` و`efi.img`. بعد إعادة استخراج ISO، تم تنفيذ:

```bash
sha256sum -c SHA256SUMS
```

وكانت النتيجة `OK` لجميع الملفات.

## وضع التشخيص التسلسلي

أضيف خيار GRUB باسم `Alif Linux 0.1 (serial diagnostic)`. يستخدم:

```text
console=tty0 console=ttyS0,115200n8
systemd.show_status=true
systemd.unit=multi-user.target
nomodeset
```

ويمكن اختباره في QEMU عبر `-serial stdio`، وبذلك تظهر نسخة kernel وسطر الإقلاع ورسائل systemd بدلاً من انتهاء الاختبار بصمت بسبب واجهة رسومية فقط.

## نتيجة اختبار QEMU

ظهر kernel وسطر الإقلاع بوضوح ولم يظهر Kernel Panic. لكن الإقلاع توقف لاحقاً داخل initramfs عند:

```text
/cow format specified as 'overlay' and no support found
(initramfs)
```

هذا عيب مستقل في مسار Live/overlay ويحتاج إصلاحاً لاحقاً؛ لذلك لا ينبغي اعتبار الإقلاع الكامل إلى سطح المكتب مثبتاً حتى معالجة `/cow` واختباره على QEMU وVMware.

## بصمة ISO الكاملة

```text
01daf9fcd150143b066785b8b7bceb7056cfc974059ff4af751a2373063a334c  alif-linux-0.1.2-serial-diagnostic-amd64.iso
```
