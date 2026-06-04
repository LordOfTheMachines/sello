<p align="center">
  <img src="assets/banner.svg" alt="Sello — e-Devlet e-İmza" width="640" />
</p>

<p align="center">
  <b>E-Devlet'in <code>elektronik-imza.jar</code> uygulamasının hafif yerine geçen, tek dosya e-imza giriş uygulaması.</b><br/>
  Java / JVM / Web Start <b>gerektirmez</b> — Windows'un yerleşik tarayıcı motorunu (WebView2) kullanır.
</p>

<p align="center">
  <a href="../../releases/latest"><img src="https://img.shields.io/github/v/release/LordOfTheMachines/sello?label=s%C3%BCr%C3%BCm&color=1689CA" alt="Sürüm" /></a>
  <a href="../../releases"><img src="https://img.shields.io/github/downloads/LordOfTheMachines/sello/total?label=indirme&color=3f8f43" alt="İndirme" /></a>
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-1689CA?logo=windows&logoColor=white" alt="Windows 10/11" />
  <img src="https://img.shields.io/badge/Java-gerektirmez-2ea043" alt="Java gerektirmez" />
  <img src="https://img.shields.io/badge/Rust%20%2B%20Tauri-tek%20dosya-444?logo=tauri&logoColor=white" alt="Rust + Tauri" />
</p>

<p align="center">
  <a href="../../releases/latest"><b>⬇ Son sürümü indir</b></a> &nbsp;·&nbsp;
  <a href="https://lordofthemachines.github.io/sello/">Tanıtım sayfası</a> &nbsp;·&nbsp;
  <a href="CHANGELOG.md">Sürüm geçmişi</a>
</p>

<p align="center">
  <img src="assets/mockup.svg" alt="Sello arayüzü" width="680" />
</p>

> _Yukarıdaki görsel temsilîdir; gerçek ekran görüntüleri `assets/` altına eklendiğinde buraya gelir._

---

## ✨ Öne çıkanlar

| | |
|---|---|
| ⚡ **Java'sız & hızlı** | JVM, Web Start veya Python yok. Çift tıkla saniyeler içinde açılır. |
| 📦 **Tek dosya, taşınabilir** | Tek `.exe`. Kurulum gerekmez; USB'den bile çalışır. |
| 🔄 **Otomatik güncelleme** | Açılışta yeni sürümü görür, **dijital imzayla doğrular**, kendini yeniler. |
| 🛡️ **Kart güvenliği** | Yanlış/kilitli PIN'de giriş denenmez — kartı kilitleme riski yok. |
| 🔒 **TLS her zaman açık** | Sertifika doğrulaması kapatılmaz; PIN ve imzalı veri loglanmaz. |
| ✅ **Standart imza** | PKCS#11 (AKİS doğrulandı) + CAdES-BES CMS; openssl ile doğrulandı. |

## ⬇ İndirme

> **[➤ Son sürümü indir (Releases)](../../releases/latest)**

İki seçenek:
- **`sello-app.exe`** — **taşınabilir tek dosya** (kurulum yok, çift tıkla çalıştır). Kendini otomatik günceller.
- **`Sello_x.y.z_x64-setup.exe`** — kurulum (Başlat menüsüne ekler).

> **Önkoşul:** Windows 10/11 + akıllı kart okuyucusu ve middleware (AKİS için `akisp11.dll`).

## 🚀 Kullanım

1. **Kartı tak**, uygulamayı aç.
2. **Kart Tipi** seç + tarayıcıdaki **İşlem Kodu**'nu gir → **DEVAM**.
3. **Sözleşme**yi gör → **DEVAM** → **PIN** gir → **İMZALA**.
4. e-Devlet girişin tamamlanır.

## 🔄 Güncelleme

Uygulama açılışta yeni sürüm olup olmadığını kontrol eder; varsa **"Güncelle"** ile
kendini günceller (ed25519 **dijital imzayla doğrulanır**). Tek dosya portable sürüm de
kendini yeniler — installer gerekmez.

> Release'lerdeki `sello-app.exe.sig`, exe'nin imzasıdır; updater bununla dosyanın
> **değiştirilmediğini** doğrular. Açık paylaşılması gerekir ve güvenlik içindir.

## 🔒 Güvenlik ve gizlilik

- **TLS doğrulaması her zaman açık**; PIN loglanmaz, bellekte kısa tutulup silinir.
- Kartı kilitleme riski olan durumlarda (yanlış/kilitli PIN) giriş **denenmez**.
- İmza **kartın içinde** üretilir; kartın özel anahtarı hiçbir zaman dışarı çıkmaz.

## 📋 Sürüm geçmişi

Bkz. [CHANGELOG.md](CHANGELOG.md).

---

<p align="center"><sub>
Kişisel/kontrollü dağıtım. Kaynak kod ayrı tutulur; bu depo yalnız dağıtım içindir.
</sub></p>
