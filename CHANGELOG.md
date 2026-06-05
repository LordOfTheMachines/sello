# Sürüm Geçmişi

Sürümler [Semantic Versioning](https://semver.org/lang/tr/) izler.

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
