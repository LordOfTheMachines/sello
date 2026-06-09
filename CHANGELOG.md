# Sürüm Geçmişi

Sürümler [Semantic Versioning](https://semver.org/lang/tr/) izler.

## [0.2.0] — Tepsi paneli, ayarlar ve kendini-kaldırma
- **Sistem tepsisi paneli (tek pencere, sekmeli):** sağ-tık → **Takılı Kartlar · Sistem Kontrolü ·
  Ayarlar**. Tepsiye **sol çift-tık** doğrudan e-Devlet imza penceresini açar.
- **Takılı Kartlar:** kart sahibi, T.C. kimlik no, veren kurum, geçerlilik ve PIN durumu — kart
  takmanız yeterli, login/PIN gerekmez.
- **Sistem Kontrolü:** e-Adalet/UYAP (köprü + sunucu) ve e-Devlet bağlantılarını tek ekranda raporlar.
- **Ayarlar:** Windows ile başlat · boot'ta sessiz başla · otomatik güncelleme · kurulum
  görünürlüğü · **dil (TR/EN)** — kayıtlı, anında uygulanır.
- **Kendini kaldırma:** "Sello'yu kaldır" autostart, yerel veri ve uygulamayı makineden **tamamen** siler.
- **Tam Türkçe / İngilizce** arayüz; dil değişimi tüm pencerelere ve tepsi menüsüne **anında** yansır.
- Arka planda kararlılık: kalıcı teşhis günlüğü; kart sürücüsü yoklaması hafifletilip çökmeye karşı korumalı hale getirildi.

## [0.1.8] — UYAP (e-Adalet) desteği
- **UYAP (e-Adalet) tarayıcı imzası:** Sello tepside resident çalışır ve yerel bir imza köprüsü
  (127.0.0.1) açar; UYAP portallarındaki kartlı imza buradan alınır — **UYAP E-İmza** istemcisine
  bağımsız bir alternatif. UYAP E-İmza kuruluysa çakışmamak için köprü devre dışı kalır.
- e-Devlet ve UYAP artık **tek uygulamada** birleşik.

## [0.1.7]
- **Kullanım Sözleşmesi (EULA)** eklendi: ilk açılışta sözleşme (TR + EN) gösterilir, **kabul
  edilmeden uygulama kullanılamaz**. Yazılım tescilli/ücretsiz; yalnız kişisel/ticari olmayan
  kullanım; yeniden dağıtım yasak; "olduğu gibi", tüm sorumluluk kullanıcıda.

## [0.1.6]
- Güncelleme sonrası **uygulama simgesi kendiliğinden tazelenir** (Windows kabuğuna bildirim
  gönderilir); artık simge önbelleğini elle temizlemeye gerek yok.

## [0.1.5]
- Güncelleme artık exe'yi **yerinde** günceller: dosya masaüstündeyse simgenin **konumu korunur**
  (eskiden güncelleme sonrası masaüstündeki yeri değişebiliyordu).

## [0.1.4]
- Uygulama simgesi yenilendi: mühür temalı yeni logo (pencere, görev çubuğu ve dosya simgesi).

## [0.1.3]
- İç iyileştirmeler ve kararlılık.

## [0.1.2]
- Pencere başlığında sürüm gösterimi ("Sello vX.Y.Z").
- Güncelleme şeridi açıkken alttaki bilgi yazısının taşması düzeltildi (içerik kendi içinde sığar).
- Güncelleme sonrası eski sürüm (`.old`) eski süreç kapanır kapanmaz silinir (yeniden başlatma beklemeden).

## [0.1.1]
- Tek-exe **otomatik güncelleme** (ed25519 imza doğrulamalı) etkin.
- Küçük iyileştirmeler.

## [0.1.0] — ilk sürüm
İlk genel sürüm. e-Devlet e-imza giriş akışının Rust + Tauri ile tam portu.

**Özellikler**
- PKCS#11 ile akıllı kart erişimi (AKİS doğrulandı); PIN güvenlik kapıları (kilitli/son-deneme
  durumunda kartı kilitlememe).
- CAdES-BES CMS imzası (golden örnek ve openssl ile doğrulandı).
- e-Devlet protokolü (sürüm kontrolü, sözleşme çekme, imzalı veri gönderme); TLS açık.
- Resmî görünümlü arayüz; dağınık PIN tuşları (her basışta yeniden karışır).
- **Uyumluluk uyarısı:** e-Devlet sürümü beklenenden farklıysa açılışta uyarır (bloklamaz).
- **Tek dosya taşınabilir exe** (config gömülü) + NSIS kurulum.
- Otomatik güncelleme (imza doğrulamalı).

---
*Tarih biçimi: YYYY-AA-GG. Yeni sürümlerde en üste yeni bir başlık eklenir.*
