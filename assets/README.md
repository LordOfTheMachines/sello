# assets/ — görseller

Tanıtım sayfası (`../index.html`) ve README aşağıdaki dosyaları arar. Gerçek
ekran görüntülerini **bu adlarla** buraya bırak; eklenince sayfalar otomatik
olarak mockup yerine gerçek görüntüyü gösterir (kod değişikliği gerekmez):

| Dosya | Nerede görünür | İçerik |
|---|---|---|
| `shot-giris.png` | hero + ekran görüntüleri | Kart Tipi + İşlem Kodu (bağlantı kontrolü) ekranı |
| `shot-pin.png` | ekran görüntüleri | Dağınık PIN tuş takımı |
| `shot-sonuc.png` | ekran görüntüleri | "İmza tamamlandı" sonuç ekranı |

İpuçları:
- **PNG**, genişlik ~1000–1400 px, pencere kenarlığıyla birlikte temiz bir kırpma.
- Kişisel veri (gerçek İşlem Kodu, T.C. no, isim) görünmesin — test/örnek değerlerle çek.
- Dosya boyutunu küçük tut (gerekirse PNG sıkıştırma).

Üretilen vektör varlıklar (elle düzenlenebilir):
- `logo.svg` — mühür logosu (favicon, README başlığı, uygulama ikonu adayı)
- `banner.svg` — README üst banner'ı (mühür + "Sello" + slogan)
- `mockup.svg` — gerçek görüntü gelene kadar gösterilen temsilî arayüz
