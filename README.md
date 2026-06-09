<p align="center">
  <img src="assets/banner.svg" alt="Sello — e-Devlet ve e-Adalet (UYAP) e-İmza" width="640" />
</p>

<p align="center">
  <b>e-Devlet e-imza girişi ile e-Adalet (UYAP) kartlı imzayı TEK uygulamada toplayan, Java'sız, tek dosya Windows e-imza uygulaması.</b><br/>
  Resmî <b>elektronik-imza.jar</b> ve <b>"Adalet E-imza"</b> istemcisinin hafif, kendini güncelleyen muadili — Windows'un yerleşik WebView2 motorunu kullanır.
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
  <img src="assets/shot-giris.png" alt="Sello e-Devlet e-imza giriş ekranı" width="680" />
</p>

---

## 🎯 İki sistem, tek uygulama

Sello, iki ayrı resmî e-imza istemcisinin işini tek programda görür — ikisi için ayrı yazılım kurmanıza gerek kalmaz:

| | |
|---|---|
| 🏛️ **e-Devlet e-İmza** | Tarayıcıda "e-imza ile giriş" adımını Sello penceresi üstlenir: kartı okur, sözleşmeyi gösterir, PIN'inizle imzalar, girişi tamamlar. *(elektronik-imza.jar muadili — Java yok.)* |
| ⚖️ **e-Adalet / UYAP** | Sello arka planda tepside durur ve yerel bir imza köprüsü açar; UYAP sayfalarındaki imza kartınızla bu köprüden alınır. *(Resmî "Adalet E-imza" istemcisinin muadili.)* Resmî istemci kuruluysa çakışmamak için köprü devre dışı kalır. |

## ✨ Öne çıkanlar

| | |
|---|---|
| ⚡ **Java'sız & hızlı** | JVM, Web Start veya Python yok. Çift tıkla saniyeler içinde açılır. |
| 📦 **Tek dosya, taşınabilir** | Tek `.exe`. Kurulum gerekmez; USB'den bile çalışır. |
| 🖥️ **Sistem tepsisinde arka planda** | Sol çift-tık → e-Devlet penceresi. Sağ-tık → **Takılı Kartlar · Sistem Kontrolü · Ayarlar** (tek pencere, sekmeli). |
| ⚙️ **Tam kullanıcı kontrolü** | "Windows ile başlat" Ayarlar'dan açılıp kapatılır; **kendini kaldırma** ile tüm izler temizlenir. |
| 🌐 **Türkçe / İngilizce** | Dil değişimi tüm pencerelere ve tepsi menüsüne **anında** yansır. |
| 🔄 **İmzalı otomatik güncelleme** | Açılışta yeni sürümü görür, **ed25519 imzasıyla doğrular**, kendini yeniler. |
| 🛡️ **Kart güvenliği** | PIN sayacını düşürmeden okur; **son deneme hakkında** otomatik giriş yapmaz. Kilitli/boş PIN gönderilmez. |
| 🔒 **TLS her zaman açık** | Sertifika doğrulaması kapatılmaz; PIN ve imzalı veri loglanmaz. |
| ✅ **Standart imza** | PKCS#11 (AKİS doğrulandı) + CAdES-BES CMS; openssl ile doğrulandı. |

## ⬇ İndirme

> **[➤ Son sürümü indir (Releases)](../../releases/latest)**

- **`sello-app.exe`** — **taşınabilir tek dosya** (kurulum yok, çift tıkla çalıştır). Kendini otomatik günceller.

> ⚠️ Yazılımı **yalnızca bu resmî kaynaktan** indirin; yeniden dağıtımı yasaktır. İndirip
> kullanarak **[Kullanım Sözleşmesi'ni (EULA)](LICENSE)** kabul etmiş olursunuz (uygulama ilk
> açılışta da onay ister).

> **Önkoşul:** Windows 10/11 + akıllı kart okuyucusu ve middleware (AKİS için `akisp11.dll`).

## 🚀 Kullanım

**e-Devlet'e giriş (dört adım):**

1. Kartı tak; tepsi simgesine **çift tıkla** Sello penceresini aç.
2. **Kart Tipi** seç + tarayıcıdaki **İşlem Kodu**'nu gir → **DEVAM**.
3. **Sözleşme**yi gör → **DEVAM** → **PIN** gir → **İMZALA**.
4. e-Devlet girişin tamamlanır.

**e-Adalet (UYAP) için:** Sello tepside açık olduğu sürece ekstra adım yok — tarayıcıdaki UYAP
imza penceresinde kartınız ve PIN'inizle imzalarsınız; Sello köprüsü imzayı arka planda üretir.

**Tepsi menüsü (sağ-tık):**

- **Takılı Kartlar** — kart sahibi, T.C. kimlik no, veren kurum, geçerlilik ve PIN durumu (login gerekmeden).
- **Sistem Kontrolü** — e-Adalet/UYAP (köprü + sunucu) ve e-Devlet bağlantılarını tek ekranda raporlar.
- **Ayarlar** — Windows ile başlat · sessiz boot · otomatik güncelleme · kurulum görünürlüğü · dil (TR/EN) · **Sello'yu kaldır**.

## 🔄 Güncelleme

Uygulama açılışta yeni sürüm olup olmadığını kontrol eder; varsa **"Güncelle"** ile kendini
günceller (ed25519 **dijital imzayla doğrulanır**). Tek dosya portable sürüm de kendini yeniler.

## 🗑️ Kaldırma

Tepsi → **Ayarlar → "Sello'yu kaldır"**: autostart kaydı, yerel veri ve uygulama makineden
**tamamen** kaldırılır. (Yalnız başlangıçtan çıkarmak isterseniz "Windows ile başlat"ı kapatmanız yeter.)

## 🔒 Güvenlik ve gizlilik

- **TLS doğrulaması her zaman açık**; PIN loglanmaz, bellekte kısa tutulup silinir.
- Kart **kilitliyse** veya **son deneme hakkındaysa** giriş otomatik denenmez; uyarı verilir (kartı
  kalıcı kilitlememek için). Boş/yanlış-uzunluk PIN gönderilmez.
- İmza **kartın içinde** üretilir; kartın özel anahtarı hiçbir zaman dışarı çıkmaz.
- UYAP köprüsü yalnız **127.0.0.1**'de ve yalnız **onaylı UYAP alan adlarına** açıktır.

## 📋 Sürüm geçmişi

Bkz. [CHANGELOG.md](CHANGELOG.md).

## 📄 Lisans

**Tescilli ücretsiz yazılım** (kaynak kod dağıtılmaz). Yalnızca **kişisel ve ticari olmayan**
kullanım içindir; **yeniden dağıtım yasaktır** (yalnız resmî kaynaktan indirin). Yazılım
**"olduğu gibi"** sunulur, **garanti verilmez** ve tüm sorumluluk/risk kullanıcıdadır. Tam metin:
**[LICENSE](LICENSE)** (TR + EN). İndirip kullanarak bu sözleşmeyi kabul etmiş olursunuz.

---

<p align="center"><sub>
© Mehmet Gilik · Kişisel/kontrollü dağıtım. Kaynak kod ayrı tutulur; bu depo yalnız dağıtım içindir.
</sub></p>
