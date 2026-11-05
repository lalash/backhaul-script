# Backhaul Script

اسکریپت مدیریت تانل **Backhaul Premium** (ریورس تانل بین سرور ایران و خارج).

## نصب

روی سرور لینوکسی (Ubuntu/Debian) با کاربر root اجرا کنید:

```bash
bash <(curl -Ls https://raw.githubusercontent.com/lalash/backhaul-script/main/backhaul.sh)
```

## پیش‌نیازها

- Linux با `systemd` و `apt-get` (برای نصب خودکار `jq`)
- دسترسی root
- معماری `x86_64`
- **لایسنس معتبر Backhaul Premium** برای IP سرور (هسته بدون لایسنس اجرا نمی‌شود)

## امکانات منو

1. ساخت تانل جدید (IRAN = Server / KHAREJ = Client)
2. مدیریت تانل‌ها (حذف، ری‌استارت، لاگ، وضعیت)
3. بررسی وضعیت همه سرویس‌ها
4. آپدیت هسته Backhaul
5. آپدیت اسکریپت (در این نسخه غیرفعال است)
6. حذف هسته

ترنسپورت‌های پشتیبانی‌شده: `tcp`, `tcpmux`, `xtcpmux`, `ws`, `wss`, `wsmux`, `wssmux`, `xwsmux`, `anytls`, `tun` (با encapsulation از نوع `tcp` یا `ipx`).

## مسیرها

| مورد | مسیر |
|---|---|
| هسته و کانفیگ‌ها | `/root/backhaul-core/` |
| کانفیگ هر تانل | `/root/backhaul-core/iran<PORT>.toml` یا `kharej<PORT>.toml` |
| سرویس systemd | `/etc/systemd/system/backhaul-iran<PORT>.service` |
| گواهی TLS خودامضا | `/root/backhaul-core/cert_files/` |

## نکات

- اسکریپت هسته (`backhaul_premium`) را از بخش [Releases](https://github.com/lalash/backhaul-script/releases) همین ریپو روی HTTPS دانلود می‌کند و SHA256 آن را بررسی می‌کند.
- فعلاً فقط نسخه `x86_64` (amd64) هسته موجود است.
- این نسخه، شکل خوانا (deobfuscate‌شده) اسکریپت اصلی است؛ تنها تغییر، منبع دانلود هسته است.
