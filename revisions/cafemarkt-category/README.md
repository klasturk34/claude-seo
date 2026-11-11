# Cafemarkt pasta dolabı — SEO revizyon paketi

**Durum: HAZIRLANDI, CANLIYA UYGULANMADI.**

Hedef kategori: https://www.cafemarkt.com/pasta-soguk-teshir-dolaplari (kategori 554).
Bu paket 80/100 puanlı V2 raporundaki düzeltmeler için hazırlanmıştır. Siteye yazma yetkisi veren T-Soft bağlantısı veya gerçek tema kaynakları mevcut değil. GitHub'a dosya eklemek Cafemarkt'ı güncellemez. Hazırlık sonrası canlı SEO puanı yeniden ölçülmedi.

## Hazırlanan dosyalar

| Dosya | Kullanımı |
|---|---|
| `meta-alanlari.json` | Title, description, OG/Twitter, tek H1 ve mevcut breadcrumb adı. JSON'un tamamını sayfaya script olarak koymayın; alanlara değerleri girin. |
| `kategori-ust.html` | Tek H1 ve yaklaşık 80 sözcüklük giriş. Ürün listesinin üstteki kategori açıklama alanına konur. |
| `kategori-alt.html` | Mevcut metni koruyan rehber; Gtech / By Kitchen teknik tablosu eklenmiş, nötr dolap H2'si düzeltilmiş. Alt açıklamanın tamamıyla değiştirilir. |
| `category.css` | Sayfalama taşması, tablet footer sosyal link taşması, karşılaştırma tablosu ve resim alan rezervasyonu. Yalnız `body.cm-category-554` kapsamında çalışır. |
| `category-ui.js` | Bu kategori yolunda body kapsam sınıfı, mobil kapalı filtre ve mevcut Filtre bağlantısının aynı paneli açması. Metadata/canonical üretmez. |
| `server_rules.py` | Canonical, mevcut graph zenginleştirme ve gerçek yayın zamanından sitemap üretimi için test edilmiş platformdan bağımsız referans. T-Soft şablon dosyası değildir; platform diline uyarlanmalıdır. |
| `urun-aciklamalari.json` / `.csv` | İlk listedeki 32 ürünün kendi sayfalarındaki kısa özelliklerinden alınan schema açıklamaları. Fiyat ve stok içermez. |
| `schema-ornek.json` | Mevcut graph üzerinde CollectionPage / ItemList @id ve 32 description örneği. **Statik örnektir, canlı fiyat/stok içerdiği için doğrudan yayınlamayın.** Referans kodu canlı katalog verisiyle kullanın. |
| `hreflang-family.json` | Bu dört dilin aynı URL kümesi; x-default TR ana URL. |
| `test-sonuclari.json` | Kaynak HTML'nin yalnız test tarayıcısındaki yanıtının değiştirildiği yerel test sonuçları. Canlı test değildir. |

## T-Soft'ta uygulanacak sıra

1. Kategori 554 SEO alanları, üst/alt açıklama ve mevcut şablonların yedeğini alın. Erişim geldikten sonra gerçek dosya isimleri/alan eşlemeleri belirlenir; bu pakette dosya adı uydurulmadı.
2. Metadata değerlerini ilgili SEO alanlarına girin; OG/Twitter alanları aynı değerleri kullanmalı. URL/slug değişmez.
3. Mevcut breadcrumb içindeki `<h1 class="breadcrumb-item">Soğuk Teşhir Dolapları</h1>` öğesini aynı metni koruyan `<span class="breadcrumb-item" aria-current="page">…</span>` ile değiştirin. Yeni H1 `kategori-ust.html` içindedir. İki H1 bırakmayın; diğer kategorilerde bu değişikliği koşulsuz uygulamayın.
4. Üst ve alt kategori alanlarını ayrı HTML dosyalarıyla değiştirin. Başka modüllere ikinci bir kopya eklemeyin. Karşılaştırma verileri ürün sayfalarından doğrulandı: Gtech 78 L / 452×406×1116 mm; By Kitchen 98 L / 425×404×1080 mm. Rafların kullanılabilir iç ölçüsü ve kapı yönü kaynakta kesinleşmediği için tabloda uydurulmadı.
5. Bu kategori için body'ye `cm-category-554` sınıfını tercihen sunucuda ekleyin. CSS'i tema stillerinden sonra, JS'yi defer ile bir kez yükleyin. JS bu sınıfı kendisi de ekler; sunucuda eklemek görsel sıçramayı azaltır. CMS kategori editörü script/style siliyorsa bunları açıklama alanına yapıştırmayın; tema varlıklarına ekleyin.
6. Head canonical etiketini **sunucuda** düzeltin. Filtresiz 1. sayfa ana URL'ye; `?pg=2/3/8` kendi URL'sine işaret eder. Aynı sayfa numarasının tekrarlı/geçersiz değerleri router'da ele alınır. Filtre/sıralama parametreleri için bu referans `None` döndürür; mevcut politikayı körlemesine silmez. Kural filtreli URL'lere uygulanmış sayılmaz.
7. Kategori JSON-LD döngüsünde her ürünün güncel kısa açıklamasını gerçek katalogdan okuyun; CSV ilk sayfadaki 32 ürün için yardımcı veridir. Sonraki sayfalardaki ürünlere ilk sayfa listesi kopyalanmaz. Bu kısa açıklamalar tam ürün detay metninin yerine içe aktarılmaz. Fiyat, stok, iade politikası mevcut canlı kaynaktan kalır. Graph'a ikinci bağımsız ürün listesi eklemeyin.
8. CollectionPage ve ItemList ID'lerini canonical sayfa URL'sinden üretin. Kategori sayfasının tümünü tek Product olarak etiketlemeyin. FAQPage/HowTo eklenmedi.
9. Dil kümesinin HTML ve sitemap x-default hedefini TR ana URL ile eşleştirin. ?pg=N için yalnız gerçekten eşdeğer dil/sayfa adresleri varsa hreflang yayınlayın; bütün sayfa 2'leri dil ana sayfalarına bağlamayın.
10. Kategori sitemap lastmod değerini **gerçek içerik yayın kaydından** üretin. Paket hazırlama tarihi veya her isteğin şimdiki zamanı kullanılmaz. `sitemap_category_entry()` tek URL girdisi döndürür; bütün sitemap'in yerine yüklenmez. Diğer kategoriler değiştirilmez.

## Görseller ve mobil davranış

Testte asıl 360/390 px taşma nedeni sayfalama satırıydı. Satırı sarmak 390→438 ve 360→423 genişlemelerini düzeltti. 768 px'de ek taşma footer sosyal bağlantılarından geliyordu; bu satır da sarıldı. Global `overflow-x:hidden` ile taşma gizlenmedi. Çerez tercih fonksiyonları veya izin metni değiştirilmedi.

Ürün görsel kapsayıcısına kare alan rezervasyonu / contain uygulandı. Bu, kaynak dosyanın oranını esnetmez. Tema üretiminde gerçek intrinsik width/height değerlerinin de yazılması önerilir; bu değerler bilinmeden topluca uydurulmadı. Mevcut lazy yükleyici korunur. İlk ekran LCP öğesi ölçülmeden bütün resimleri eager yapmayın. CSS alan rezervasyonu CWV geçişini kanıtlamaz.

Mobil filtreyi saran details öğesi aynı Vue düğümünü taşır; kopya filtre veya sahte form oluşturulmaz. Desktop görünümde açık, mobilde kapalı başlar. Mevcut “Filtre” bağlantısı paneli açar. Gerçek T-Soft kaynağı geldiğinde mümkünse platformun kendi drawer bileşeni üzerinden eşdeğer değişiklik yapılır; gerçek tema ile yeniden test zorunludur.

## Hâlâ gerekli doğrulamalar

- **T-Soft yetkili erişimi veya tema deposu:** canlı alanlara yazma, gerçek şablon uyarlaması, yayın ve rollback için gerekir. Şifreyi chat'e yazmayın.
- **Operasyon:** kullanıcının verdiği 3 iş günü gönderim bilgisi korunmuştur. Ürüne/stoğa göre istisnaları varsa operasyon ekibi belirtmeli. Yeni bir teslimat garantisi eklenmedi.
- **Ürün uzmanı:** iki modelin kullanılabilir raf ölçüsü ve kapı yönü kaynakta kesin değil; bilinmeyen değerler tahmin edilmedi.
- **GSC / GA4:** bu oturumda yetkili veri kaynağı yok. Baz dönem, yayın sonrası CTR ve ürün tıklamaları henüz alınmadı.
- **PageSpeed / CrUX:** önceki raporda HTTP 429 vardı; performans geçişi veya puan artışı iddia edilmez.
- Canlı yayından sonra ana URL + sayfa 2/3/8 kaynak HTML, filtre etkileşimi, sepet akışı, çerez tercihleri, 360/390/768/1440 px, Rich Results Test ve sitemap yeniden doğrulanmalı.

Bu paket canlıya uygulanmış bir revizyonun kanıtı değil; erişim engeli kalkınca uygulanacak somut değişikliklerdir.
