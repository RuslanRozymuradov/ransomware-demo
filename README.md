# Ransomware & Quishing (QR Phishing) Demo

Herkes restoranlarda veya stantlarda gördüğü QR kodları hiç düşünmeden okutuyor. Peki ya o kod bir menüye değil de zararlı bir yazılıma gidiyorsa? 

Bu repo, siber güvenlik etkinliklerinde insanlara "Quishing" (QR Phishing) tehlikesini uygulamalı olarak yaşatmak için hazırladığım interaktif bir simülasyon projesidir. Ziyaretçi QR kodu okuttuğunda cihazının hacklendiğini ve dosyalarının şifrelendiğini sanıyor, ufak bir paniğin ardından ekranda eğitici bir farkındalık mesajıyla karşılaşıyor.

## Dosyalar Ne İşe Yarıyor?

* **`index.html` (Oltalama Ekranı):** Kurbanın QR kodu okuttuğu an açılan sahte terminal sayfası. Mobil uyumlu hazırlandı. Matrix tarzı bir animasyonla başlar, sahte bir şifreleme süreci yürütür ve kırmızı alarm verir. Panik bittikten sonra yeşil, güvenli ekrana geçip "Kaynağını bilmediğiniz kodları okutmayın" dersini verir. Kod çalıştığı an arka planda sayaca çaktırmadan +1 yazar.
* **`count.html` (Canlı Skor Tablosu):** Sergi alanındaki dev ekrana yansıtmalık dashboard. Sayfayı yenilemeye (F5) hiç gerek kalmadan, birisi QR'ı okuttuğu saniye ekrandaki sayı otomatik artar. Sergi başlamadan önceki test taramalarını silmek için kendi içinde çalışan bir "Sıfırla" butonu var (gerçek veriyi silmez, tarayıcıda offset tutar).

## Altyapı & Nasıl Çalışır?

Arka planda sunucu maliyeti veya karmaşık bir backend yok. Tamamen statik ve sunucusuz (serverless) bir yapı kurdum:

* **Hosting:** GitHub Pages. Sadece dosyaları yükleyip linki alıyorsunuz.
* **Veritabanı:** Firebase Realtime Database. Neden statik API değil de Firebase? Çünkü tarayıcıların CORS politikalarına veya AdBlocker engellerine takılmıyor. Üstelik WebSockets kullandığı için sayacı anlık (real-time) güncelliyor.
* **Kendi Kurulumun:** Projeyi çatallayıp (fork) kullanmak istersen, Firebase'den ücretsiz bir Realtime Database açıp kendi `firebaseConfig` bilgilerini HTML dosyalarının en altına yapıştırman yeterli. Veritabanı kurallarından "Test Mode"u açmayı unutma.

---
**Geliştirici:** Ruslan Rozymuradov
*Cyber RDI Engineer*
