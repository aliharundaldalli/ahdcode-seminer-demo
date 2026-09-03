# AHD Matematik ve Kodlama Semineri

Bu uygulama [AhdCode](https://github.com/aliharundaldalli/AhdCode) **v0.10.0**
ile yazılmış ayrı bir demo deposudur.

Hatay’da **27–30 Eylül 2026** için çok sayfalı yerel seminer defteri:
ana sayfa, kayıt, giriş, panel özeti ve Open-Meteo hava kartı.

`Security` (Argon2id şifre, CSRF token, `secureEqual`), Session, SQLite,
HTTP Client, HTML, Env ve SMTP kullanır.

## Gereksinimler

- Kurulu **AhdCode v0.10.0** (`ahdcode --version`)
- SQLite yardımcısı **`ahdsqlite`**
- Tarayıcı
- Ana sayfa hava kartı için çıkan HTTPS (Open-Meteo)
- Şifre sıfırlama postası için `.env` içinde SMTP bilgileri

## Ne gösterir?

- Ayrı `/kayit` ve `/giris` sayfaları (navbar da buna göre)
- Kullanıcı adı + şifre; şifre `Security.passwordHash` ile saklanır
- Formlarda oturum CSRF token’ı ve `Security.secureEqual`
- Panelde özet adı + yazılan metin veya PDF yükleme
- PDF diskte uzantısız saklanır; indirme `HTTP.download` ile `.pdf` / `.txt`
- Şifremi unuttum: SMTP `.env` üzerinden sıfırlama bağlantısı

## `.env` anahtarları

| Anahtar | Anlamı |
|---|---|
| `APP_TITLE` | Başlık |
| `APP_HOST` | Adres |
| `APP_PORT` | Port |
| `DB_PATH` | SQLite dosyası |
| `WEATHER_URL` | Hava API adresi |
| `SMTP_HOST` | Örn. `smtp.gmail.com` |
| `SMTP_PORT` | Örn. `587` |
| `SMTP_SECURITY` | `starttls` / `tls` / `none` |
| `SMTP_USERNAME` | SMTP kullanıcı |
| `SMTP_PASSWORD` | SMTP parolası (Gmail: uygulama şifresi) |
| `SMTP_FROM` | Gönderen adresi; boşsa kullanıcı adı kullanılır |

```bash
cp .env.example .env
```

`SMTP_PASSWORD` değerini kendiniz yazın. Gerçek parolayı `app.ahd` içine koymayın.

## Çalıştırma

```bash
ahdcode run app.ahd
```

Tarayıcı: [http://127.0.0.1:8081/](http://127.0.0.1:8081/)

Durdurmak için terminalde `Ctrl+C`.
