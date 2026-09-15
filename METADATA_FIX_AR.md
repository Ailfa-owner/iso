# إصلاح معلومات المشروع في Alif Linux 0.1.3

تم تحديث `/etc/os-release` داخل صورة النظام وإضافة الروابط التالية:

```text
HOME_URL="https://github.com/Ailfa-owner/iso"
DOCUMENTATION_URL="https://github.com/Ailfa-owner/iso/blob/main/README.md"
SUPPORT_URL="https://github.com/Ailfa-owner/iso/issues"
BUG_REPORT_URL="https://github.com/Ailfa-owner/iso/issues/new"
```

تم التحقق من وجود هذه القيم داخل SquashFS، كما تم التحقق من checksums الداخلية لكل ملفات الإقلاع والـkernel و`initrd` و`filesystem.squashfs`. الصورة ما زالت تحتوي على إقلاع BIOS وUEFI، وتحافظ على إصلاح كلمة المرور وتكامل VMware ووضع serial diagnostic.

بصمة الصورة الكاملة:

```text
271efefc0055fd0a4440408b6fd25dc34732efe9b131144e5e5b6272c2a56b2a  alif-linux-0.1.3-metadata-fix-amd64.iso
```
