# هوية Alif Linux 0.1.6

تم اعتماد شعار ALIF الأزرق/الأبيض من الصورة المرجعية المرفقة وتطبيقه على نقاط الظهور الرئيسية في النظام.

## أماكن الشعار

| المكان | الملف أو الإعداد |
|---|---|
| قائمة GRUB | `/boot/grub/alif-background.jpg` مع `background_image` في `grub.cfg` |
| خلفية تسجيل الدخول | `/usr/share/backgrounds/alif/alif-login.jpg` عبر LightDM |
| خلفية سطح المكتب XFCE | `/usr/share/backgrounds/alif/alif-wallpaper.jpg` |
| شاشة Plymouth | شعار `/usr/share/plymouth/themes/homeworld/logo.png` داخل initrd المحدث |
| أيقونة النظام | `/usr/share/pixmaps/alif-logo.png` وأيقونات hicolor بقياسي 256 و512 بكسل |
| مثبت Calamares | `/usr/share/calamares/branding/alif/banner.png` |
| أصول العلامة | `/usr/share/backgrounds/alif/alif-logo-lockup.png` و`alif-brand-board.png` |

تم الإبقاء على قائمة GRUB النصية قابلة للقراءة، مع استخدام الخلفية الجديدة خلفها. كما تم الحفاظ على إقلاع BIOS وUEFI وإعادة بناء checksums داخل ISO.

## التحقق

- فحص قطاعات ISO: ناجح.
- BIOS وUEFI: موجودان في El Torito.
- ملفات الشعار داخل SquashFS: موجودة.
- LightDM وXFCE يشيران إلى الملفات الجديدة.
- `initrd` أُعيد توليده حتى يظهر شعار Plymouth أثناء الإقلاع.

## بصمة ISO

```text
ac3820b6b7a4825d01821649f2357bf05f017b57c2595e37b29271a454d57c45  alif-linux-0.1.6-alif-branding-amd64.iso
```
