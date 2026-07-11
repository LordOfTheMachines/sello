# Sürüm Geçmişi

Sürümler [Semantic Versioning](https://semver.org/lang/tr/) izler.

## [0.8.6] — Öz-bütünlük mührü (tamper koruması)
- **Uygulama artık kendi bütünlüğünü doğruluyor:** Resmî `sello-app.exe`, gövdesi üzerinden alınmış
  bir **ed25519 mührüyle** imzalanır. Uygulama her imzadan önce kendi dosyasını doğrular; exe
  **değiştirilmiş / kötü niyetle enjekte edilmişse imzalama net bir mesajla REDDEDİLİR** (kart
  kilitlenmez, PIN sorulmaz) — dört modda da (e-Devlet · UYAP · PTT KEP · UETS). Sessizce bozuk imza
  ÜRETİLMEZ; güvenli yön olan "reddet" seçilir.
- **Dosya doğrulama (SHA-256) yayınlandı:** İndirdiğiniz exe'nin gerçekliğini artık siteden ve sürüm
  notundan **SHA-256** özetiyle kendiniz doğrulayabilirsiniz. Sello'yu yalnızca resmî kaynaktan indirin.
- **İkili sertleştirme:** Derleme yollarındaki build-makinesi kullanıcı adı anonimleştirildi; sembol
  bilgisi çıkarıldı. İşlevsel etki yok.
- İmza / CMS / e-imza protokol yolları (**e-Devlet · UYAP · PTT KEP · UETS**) **değişmedi** — bu sürüm
  imza-öncesi bir güvenlik kapısı ve tamper caydırıcısı ekler.

## [0.8.5] — Kararlılık: soğuk-bağlantı dayanıklılığı
- **"error sending request" / anlık bağlantı hatası giderildi:** Bazen (özellikle uygulama yeni
  açıldığında) gerçek bir sorun olmadığı hâlde, sunucuya ilk bağlantı **soğuk** olduğu için
  "İmzalama hatası" veya "Kart okunamadı" alınabiliyordu. Artık bağlantı kurulamazsa Sello
  **otomatik yeniden dener** → çoğu durumda ilk seferde çalışır. **Güvenli tasarım:** yeniden
  gönderim yalnız **bağlantı hiç kurulamadığında** (imzalı veri sunucuya gitmemişken) yapılır →
  **çift-gönderim imkânsız**; belirsiz durumlarda tekrar gönderilmez.
- **Kart okuma dayanıklılığı:** Kart yeni takıldığında / okuyucu uyanırken oluşan anlık okuma
  hatası sessizce yeniden denenir.
- **Otomatik güncelleme daha sağlam:** Arka plan denetimi artık pencere açık olsun olmasın
  periyodik çalışır; ilk denemede ağ dalgalanması olursa kendini toparlar, uygulama açıkken
  çıkan yeni sürümü de alır.
- **Güncelleme uyarısı düzeltmesi:** Ayarlardan otomatik güncellemeyi açıp kapatınca uyarı şeridi
  artık doğru belirir/kaybolur (elle yenileme gerekmez).
- Başarılı bağlantıda **ek gecikme yoktur**; yeniden deneme yalnız gerçek hatada devreye girer.
  İmza / CMS / e-imza protokol yolları (**e-Devlet · UYAP · PTT KEP · UETS**) **değişmedi**.

## [0.8.4] — Güvenlik sertleştirmesi
- **Sertifika iptal kontrolünde iç-ağ koruması:** Sello, imza öncesi sertifikanın iptal listesini (CRL)
  kontrol ederken artık yalnızca **genel internet adreslerine** bağlanır; sertifikada belirtilen adres
  yerel ağa / localhost'a / bulut metadata adresine **yönlendirilemez** (SSRF sertleştirmesi). Bu kontrol
  "fail-open"dır — imzayı asla engellemez, yalnızca güvenliği artırır.
- **Otomatik güncelleme kaynağı sabitlendi:** güncelleme **yalnızca resmî depodan** gelir; uygulamanın
  yanına yerleştirilen bir ayar dosyası güncellemeyi başka bir kaynağa yönlendiremez (sürüm düşürme /
  sahte güncelleme koruması). İmza doğrulaması (ed25519) her zamanki gibi açıktır.
- **İç dokümantasyon güncellendi** (makine kimliği modeli, mimari). Kullanıcıyı etkileyen bir değişiklik yok.
- İmza / CMS / e-imza protokol yolları (**e-Devlet · UYAP · PTT KEP · UETS**) **değişmedi** — bu sürüm
  yalnızca bir güvenlik sertleştirmesidir.

## [0.8.3] — Sessiz otomatik güncelleme, akıcı e-Adalet/UYAP akışı ve güvenlik sertleştirmesi
- **Otomatik güncelleme artık sessiz ve arka planda:** "Otomatik güncelleme" açıkken (varsayılan) yeni
  sürüm açılışta **kendiliğinden** indirilip kurulur ve uygulama yeniden başlar — tıklamanız gereken bir
  şey yok. Kapatırsanız güncelleme size **belirgin bir şeritle** duyurulur (indirme çubuğu + saatlik
  hatırlatma bildirimi), kararı siz verirsiniz.
- **e-Adalet / UYAP geçişi kolaylaştı:** UYAP portalları için gereken köprüyü, kurulu **UYAP E-İmza**
  istemcisi engelliyorsa Sello bunu açılışta **tek tıkla, sessizce** (siyah komut penceresi açılmadan)
  kaldırıp kendini yeniden başlatır; köprü anında devreye girer. İşlem sırasında ilerleme şeridiyle
  bilgilendirilirsiniz.
- **Bağlantı kontrolü kendini toparlar:** açılışta bağlantı henüz kurulmadıysa gösterilen kırmızı ışık,
  bağlantı sağlanınca **kendiliğinden yeşile** döner — elle yenilemeye gerek yok.
- **Güvenlik sertleştirmeleri (saldırgan gözüyle denetim sonrası):** dış kaynaklardan veri çekiminde
  ek koruma (yönlendirme/boyut sınırları), yerel imza köprüsü için kimlik-sızıntısına karşı ek doğrulama
  ve WebView2 kurulum dosyasının **imza doğrulaması**. PIN ve imzalı veri yine hiçbir yere loglanmaz;
  TLS doğrulaması her yerde açıktır.
- İmza / CMS / e-imza protokol yolları (**e-Devlet · UYAP · PTT KEP · UETS**) değişmedi.

## [0.8.2] — Uyumluluk: VC++ Redistributable gereksinimi kaldırıldı
- **"VCRUNTIME140_1.dll bulunamadı" hatası giderildi:** bazı temiz Windows makinelerinde Sello, Microsoft
  Visual C++ Redistributable kurulu olmadığında açılmıyordu. C runtime artık doğrudan exe'ye **statik
  gömülü** — Visual C++ Redistributable **hiç gerekmez**; Sello yine tek dosya ve hiçbir ek kurulum
  yapılmadan çalışır (dosya yalnızca ~0,5 MB büyüdü).
- **WebView2 otomatik kontrol + kurulum:** arayüz bileşeni (WebView2) eksik olan nadir makinelerde Sello,
  açılışta resmî Microsoft kurulumunu kendisi indirip kurar.
- İmza / CMS / e-imza protokol yolları (**e-Devlet · UYAP · PTT KEP · UETS**) değişmedi; bu sürüm yalnızca
  bir dağıtım/uyumluluk düzeltmesidir.

## [0.8.1] — Kararlılık: handle sızıntısı giderildi
- **Uzun süre açık kalan Sello'da kaynak (handle) birikmesi giderildi:** tepside sürekli çalışan
  uygulama, kart tak/çıkar durumunu izlerken zamanla Windows "handle" biriktiriyordu (boştayken bile).
  Kart izleme artık doğrudan Windows akıllı-kart altyapısıyla (PC/SC) **olay-tabanlı** yapılıyor —
  sürekli yoklama yok. Birikme **sıfırlandı** ve kart tak/çıkar algılama **anlık** hâle geldi.
- İmza / CMS / e-imza protokol yolları (**e-Devlet · UYAP · PTT KEP · UETS**) değişmeden korundu.

## [0.8.0] — Daha akıcı imza + güven deposu izleme
- **İmza akışı hızlandırıldı:** sertifika iptal kontrolü (CRL) artık kart kilidini tutmadan,
  arka planda yapılıyor — yavaş veya soğuk ağda imza atarken bekleme belirgin biçimde azaldı.
- **Güven deposu izleme:** Sello, Türk ESHS güven deposunun (KamuSM kök sertifika listesi)
  güncellenip güncellenmediğini günde bir kez sessizce kontrol eder; bir değişiklik olursa
  güncelleme gerektiğine dair işaret bırakır. Bir güvenlik kararı vermez, yalnız bilgilendirir;
  TLS doğrulaması açıktır.
- Çekirdek kod sadeleştirildi, test kapsamı genişledi. Çalışan tüm imza yolları
  (**e-Devlet · UYAP · PTT KEP · UETS**) değişmeden korundu.

## [0.7.0] — İmza-öncesi sertifika güvenlik ön-filtresi
- **Sertifika güvenlik ön-kontrolü** eklendi: e-imza atmadan önce sertifikanın **süresi** ve
  **iptal durumu (CRL)** sessizce kontrol edilir; geçersizse imza yapılmadan net uyarı verilir.
  **e-Devlet, UYAP, PTT KEP ve UETS** modlarının hepsinde geçerli.
- **Takılı Kartlar**'da geçerlilik renk gradyanı: son 3 ay **sarı** → 2 ay **turuncu** → 1 ay
  **açık kırmızı** → dolmuş **koyu kırmızı**.
- Güvenli tasarım: kök sertifikalar uygulamaya **gömülü**, kontrol **yalnız bellekte** (disk yok),
  CRL imzası CA ile doğrulanır; **"fail-open"** (yalnız kesin dolmuş/iptalli durdurur; kontrol
  yapılamazsa imza engellenmez, son merci sunucudur).
- e-Devlet ↔ KEP ↔ UETS geçişlerinde form artık **sabit pozisyonda** kalır (hizalama düzeltmesi).

## [0.6.0] — PTT UETS / e-Tebligat e-imza desteği
- **PTT UETS (Ulusal Elektronik Tebligat Sistemi — e-Tebligat) e-imzası** eklendi: pencerede
  üstten **e-Devlet / PTT KEP / UETS** geçişi (üçüncü mod). e-Tebligat işleminde gördüğünüz
  **6 haneli İşlem Kodu** ile kartınız ve PIN'inizle imzalarsınız — akış e-Devlet/KEP ile aynıdır
  (gerçek kartla doğrulandı). RSA ve EC (ECDSA) kartlar; CAdES-BES, sunucu saatli imza zamanı.
- **Sistem Kontrolü**ne **UETS / e-Tebligat** sunucu kontrolü eklendi (yeşil/kırmızı ışık).
- **e-Devlet ve PTT KEP modları aynen korundu** — mevcut akışlarda değişiklik yok.

## [0.5.0] — PTT KEP webmail e-imza desteği
- **PTT KEP webmail e-imzası** eklendi: pencerede üstten **KEP / e-Devlet** geçişi. PTT KEP
  webmail'de gördüğünüz **İşlem Kodu** ile kartınız ve PIN'inizle giriş imzası — akış e-Devlet
  ile aynıdır (gerçek kartla doğrulandı).
- **Sistem Kontrolü**ne **PTT KEP** sunucu kontrolü eklendi (yeşil/kırmızı ışık).
- Bağlantı durumları daha anlaşılır metinlerle gösterilir ("Bağlantı sağlandı/kurulamadı");
  Türkçe ⇄ İngilizce dil geçişi iyileştirildi.

## [0.4.0] — Sürüm/bakım koruması ve kararlılık
- e-İmza sisteminde bakım/güncelleme olduğunda kullanıcıyı bilgilendiren koruma; çeşitli
  kararlılık iyileştirmeleri.

## [0.3.1] — EC (ECDSA) kart desteği + sunucu saatli imza zamanı
- **EC (ECDSA, P-256/P-384) e-imza kartları** desteklendi; imza zamanı sunucu saatinden alınır.

## [0.3.0] — UYAP Bilirkişi Portalı belge imzası
- **UYAP Bilirkişi Portalı** belge imzası (signdigest) eklendi; tutanak/belge kartla imzalanır.

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
