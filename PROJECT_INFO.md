# Görsel Küçültücü — Proje Bilgisi

## Ne yapar
Birden çok görselin dosya boyutunu, çözünürlüğünü ve formatını değiştirmeden küçültür (iLoveIMG / TinyPNG mantığı). Tamamen tarayıcıda çalışır; görseller hiçbir sunucuya yüklenmez.

## Dosyalar
| Dosya | Açıklama |
|---|---|
| `gorsel-kucult.html` | Uygulamanın tamamı (tek dosya, kurulum yok) |
| `PROJECT_INFO.md` | Bu belge |

## Kullanım
1. `gorsel-kucult.html` dosyasını Chrome veya Edge ile aç.
2. Görselleri sürükle bırak ya da kutuya tıklayıp seç.
3. Sıkıştırma seviyesini seç → **Küçült** (dosyalar sırayla işlenir).
4. **İndir** → İndirilenler klasörünü onayla → `kucultulmus-YYYY-MM-DD-SSDD` klasörüne kaydedilir.

## Sıkıştırma yöntemi
| Format | Kodek | Not |
|---|---|---|
| JPG | MozJPEG (jSquash / Squoosh, WASM) | progressive + trellis |
| PNG | UPNG — 256/128 renk palet | pngquant/TinyPNG mantığı, şeffaflık korunur |
| WebP | libwebp (jSquash, WASM) | method 6 |

Seviyeler: **Az** = kalite 85 · **Önerilen** = 75 · **Çok** = 60 (PNG'de 128 renk).
Sonuç orijinalden büyükse orijinal dosya korunur.

## Teknoloji
- Saf HTML + JavaScript (ES module), derleme yok.
- CDN bağımlılıkları: `@jsquash/jpeg@1.4.0`, `@jsquash/webp@1.4.0` (unpkg), `upng-js@2.1.0` (jsDelivr), `pako@1.0.11` (cdnjs).
- Kaydetme: File System Access API (`showDirectoryPicker`).

## Gereksinimler ve sınırlar
- İnternet bağlantısı gerekir (kodekler CDN'den yüklenir).
- Klasöre kaydetme yalnızca Chrome / Edge'de; Firefox'ta dosyalar tek tek iner.
- Tarayıcı güvenliği gereği İndirilenler klasörü bir kez elle onaylanmalı.
- Desteklenen formatlar: JPG, PNG, WebP (GIF, HEIC, SVG yok).
- Çok büyük görsellerde (50 MP+) tarayıcı belleği yetmeyebilir.

## Durum
- Sürüm: 1.0 (2026-11-13)
- Tarayıcıda uçtan uca test **henüz yapılmadı**.

## Olası geliştirmeler
- Kodekleri yerel klasöre alıp çevrimdışı çalışma
- ZIP olarak indirme seçeneği
- Önce/sonra önizleme
