# AHD Matematik ve Kodlama Semineri

Bu uygulama [AhdCode](https://github.com/aliharundaldalli/AhdCode) **v0.5.0**
ile yazılmış ayrı bir demo deposudur.

Hatay’da **27–30 Eylül 2026** için çok sayfalı yerel seminer defteri:
ana sayfa, kayıt, giriş ve seminer metni.

HTTP, HTML, Cookie, SessionStore, SQLite ve Env kullanır. Apache, MAMP veya
nginx gerekmez.

Bu depo **v0.2.0** sürümüdür. v0.1.0 tek SQLite oturum satırı kullanıyordu;
v0.2.0, AhdCode v0.5.0 Web State ile tarayıcı başına bellek içi oturum ekler.

## Gereksinimler

- Kurulu **AhdCode v0.5.0** (`ahdcode --version`)
- SQLite yardımcısı **`ahdsqlite`** (HTTP, çerez ve oturum için yardımcı process yok)
- Tarayıcı (yazı tipleri Google Fonts CDN’den yüklenir)

## Ne gösterir?

- Birden fazla kesin HTTP yolu (`/`, `/kayit`, `/giris`, `/panel`)
- `Env.load(".env")` ile başlık / host / port
- Kayıt ve giriş; seminer metni bir kez
- Ana sayfadaki listede her ad **bir kez**
- Kullanıcı metnini `HTML.text` / `HTML.element` ile güvenli basmak
- Tarayıcı başına bellek içi oturum: çerezde yalnızca opak bir id,
  `user_id` sunucuda `SessionStore` içinde

Kullanıcılar ve seminer metinleri SQLite’da kalır. Giriş durumu süreç
belleğindedir: programı durdurunca herkes çıkar, kayıtlı adlar durur.

Bu bir kimlik doğrulama çerçevesi değildir. İki tarayıcı aynı anda ayrı
kişiler olarak giriş yapabilir; birinin çıkışı diğerini düşürmez.

## Dosyalar

```text
app.ahd
.env.example
README.md
LICENSE
data/seminer.db    # ilk çalıştırmada oluşur
```

AhdCode `.env` dosyasını kendiliğinden okumaz. Program `Env.load(".env")` çağırır.

## `.env` anahtarları

| Anahtar | Anlamı | Örnek |
|---|---|---|
| `APP_TITLE` | Başlık | `AHD Matematik ve Kodlama Semineri` |
| `APP_HOST` | Adres | `127.0.0.1` |
| `APP_PORT` | Port | `8081` |
| `DB_PATH` | SQLite dosyası | `data/seminer.db` |

```bash
cp .env.example .env
```

## Çalıştırma

```bash
ahdcode run app.ahd
```

Tarayıcı:

[http://127.0.0.1:8081/](http://127.0.0.1:8081/)

İzleme (watch) modu henüz yok. `app.ahd` veya `.env` değişince programı
durdurup yeniden çalıştırın. Durdurmak için terminalde `Ctrl+C`.

## Derleme

```bash
ahdcode build app.ahd
./app
```

Yerel ikili hâlâ `ahdsqlite` yardımcısına ihtiyaç duyar.

## Dil

[AhdCode](https://github.com/aliharundaldalli/AhdCode)
