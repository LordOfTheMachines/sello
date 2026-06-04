# Sello — e-Devlet e-İmza Uygulaması (hızlı, tek dosya)

E-Devlet'in `elektronik-imza.jar` uygulamasının yerine geçen, **hızlı ve hafif** bir e-imza
giriş uygulaması. **Java (JVM), Python veya Web Start GEREKTİRMEZ** — Windows'un yerleşik
tarayıcı motorunu (WebView2) kullanır. Arayüz resmî uygulamayla görsel olarak aynıdır.

## İndirme

> **[➤ Son sürümü indir (Releases)](../../releases/latest)**

İki seçenek:
- **`sello-app.exe`** — **taşınabilir tek dosya** (kurulum yok, çift tıkla çalıştır).
  Kendini otomatik günceller.
- **`Sello_x.y.z_x64-setup.exe`** — kurulum (Başlat menüsüne ekler).

> Önkoşul: Windows 10/11 + akıllı kart okuyucusu ve middleware (AKİS için `akisp11.dll`).

## Kullanım
1. Kartı tak, uygulamayı aç.
2. **Kart Tipi** seç + tarayıcıdaki **İşlem Kodu**'nu gir → **DEVAM**.
3. Sözleşmeyi gör → **DEVAM** → **PIN** gir → **İMZALA**.
4. e-Devlet girişin tamamlanır.

## Güncelleme
Uygulama açılışta yeni sürüm olup olmadığını kontrol eder; varsa **"Güncelle"** ile
kendini günceller (dijital imzayla doğrulanır). Tek dosya portable sürüm de kendini
yeniler — installer gerekmez.

## Güvenlik ve gizlilik
- TLS doğrulaması her zaman açıktır; PIN loglanmaz, bellekte kısa tutulup silinir.
- Kartı kilitleme riski olan durumlarda (yanlış/kilitli PIN) giriş denenmez.
- Açılışta yalnız **kurulum görünürlüğü** için anonim bir kayıt gönderilir (hash'li makine
  kimliği + bilgisayar/kullanıcı adı + sürüm). **PIN/imza/kişisel kimlik gönderilmez.**

## Sürüm geçmişi
Bkz. [CHANGELOG.md](CHANGELOG.md).

---
*Kişisel/kontrollü dağıtım. Kaynak kod ayrı tutulur; bu depo yalnız dağıtım içindir.*
