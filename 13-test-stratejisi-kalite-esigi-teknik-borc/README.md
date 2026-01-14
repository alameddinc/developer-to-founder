# 13 – Test Stratejisi, Kalite Eşiği & Teknik Borç  
## “Kalite, Ürünü Yavaşlatmamalı”

Bu haftanın amacı:
> **Test yazmayı amaç değil araç olarak görmek,  
> kalite ile hız arasında bilinçli denge kurmak  
> ve teknik borcu kontrolsüz değil, stratejik almak.**

Bu hafta:
- “%100 test coverage” peşinde koşmuyoruz
- Test framework karşılaştırmıyoruz
- Akademik test piramitleri ezberlemiyoruz

Ama:
> Gerçek hayatta ürün çıkaran profesyoneller  
> **testi nasıl konumlandırıyor** onu öğreniyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Test ≠ kalite yanılgısından kurtulacak
- Nerede test yazılmaması gerektiğini bilecek
- Manuel test refleksi kazanacak
- Teknik borcun kötü değil, **kontrolsüz** olduğunda tehlikeli olduğunu anlayacak
- “Şimdi mi, sonra mı?” kararlarını bilinçli verecek
- Ürünü yavaşlatmayan bir kalite eşiği tanımlayacak

---

## 🧠 Büyük yanılgı

> “Test yazarsak kalite olur.”

Gerçek:
> Test yazmak sadece **güvenlik ağıdır**.  
> Kalite ise **doğru kararlar zinciridir**.

Yanlış yerde yazılan test:
- Zaman kaybıdır
- Sahte güven verir
- Geliştirme hızını düşürür

---

# 1️⃣ Kalite nedir, test nedir?

- **Kalite:** Ürünün doğru işi, doğru şekilde yapması
- **Test:** Yanlış yaptığında erken fark etmeyi sağlayan araç

Test:
- Kalite üretmez
- Kaliteyi **korur**

> Kalite önce tasarımda,  
> test sonra gelir.

---

# 2️⃣ Nerede test yazILMAZ? (çok kritik)

MVP ve erken aşamada **bilerek test yazılmaması gereken yerler vardır**.

## ❌ Test yazılmaması gerekenler
- Hızla değişecek UI detayları
- Henüz oturmamış UX akışları
- Deneme amaçlı feature’lar
- “Büyük ihtimalle çöpe gidecek” kod

> Test, sabitleyici bir güçtür.  
> Sabitlemek istemediğin şeyi test etme.

---

# 3️⃣ Nerede test yazILIR?

## ✅ Test yazılması gereken yerler
- İş kuralları (para, kota, yetki)
- Geri dönülmesi zor logic
- Bug tekrar eden noktalar
- “Burası bozulursa felaket” dediğin yerler

Kural:
> **Acı veren yer test edilir.**

---

# 4️⃣ Manuel test refleksi (underrated ama hayati)

Birçok solo founder’ın süper gücü:
> **Manuel test**

Manuel test:
- Yavaştır
- Ama öğrenme sağlar

## Sağlıklı manuel test alışkanlığı
- Yeni feature sonrası:
  - Mutlu yol
  - 1–2 hata senaryosu
- Mobil + desktop dene
- Gerçek kullanıcı gibi davran

> “Ben biliyorum” diyerek test eden,  
> kullanıcıyı anlayamaz.

---

# 5️⃣ Test türleri (MVP perspektifiyle)

Bu eğitimde:
- Test piramidi ezberi yok

Ama pratik bakış var:

### 1️⃣ Unit test
- Saf iş kuralları
- Hızlı
- Değeri yüksek

### 2️⃣ Entegrasyon test
- Az ama kritik noktalarda
- Özellikle para, auth, job akışları

### 3️⃣ E2E test
- MVP’de **çok sınırlı**
- Kırılgan
- Bakımı pahalı

> MVP’de testin düşmanı:  
> **bakım maliyeti**.

---

# 6️⃣ Teknik borç: Düşman değil, araç

Teknik borç:
- Kötü değildir
- Kaçınılmazdır

Ama:
> **Bilinçsiz teknik borç öldürür.**

---

## Sağlıklı teknik borç nedir?
- Bilinçli alınır
- Yazılıdır
- Geri ödeme planı vardır

Örnek:
> “Şimdilik hardcode yapıyorum,  
> kullanıcı 100’ü geçerse refactor.”

---

## Zehirli teknik borç nedir?
- “Sonra bakarız”
- Kimsenin hatırlamadığı
- Testi olmayan
- Kritik yerde olan borç

---

# 7️⃣ “Şimdi mi, sonra mı?” karar çerçevesi

Her teknik karar için kendine sor:

1. Bu karar **geri dönülebilir mi?**
2. Yanlış olursa bedeli ne?
3. Bu karar öğrenmeyi hızlandırıyor mu?
4. Şimdi yapmazsam gerçekten risk var mı?

### Genel kural
- Geri dönülebilir → sonra
- Geri dönülemez → şimdi

---

# 8️⃣ Kalite eşiği tanımlamak (çok önemli)

Kalite eşiği:
> “Bu ürün bu seviyenin altına düşemez.”

MVP için örnek kalite eşiği:
- Veri kaybı yok
- Para yanlış hesaplanmaz
- İşlem yarıda kalmaz
- Hata kullanıcıya açıklanır

Bunun üstü:
> **Nice to have**.

---

# 9️⃣ SilentCut bağlamında düşünürsek

Bu tip ürünlerde:
- Job state’leri test edilir
- Kota / token hesapları detaylı test edilir
- Upload edge case’leri detaylı test edilir
- Panic'e düşebilecek case'ler detaylı test edilir

Ama:
- UI animasyonları detaylı test edilmez
- Deneysel ayarlar detaylı test edilmez.

> Kritik olan test edilir,  
> estetik olan değil.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ Test yazılmayacak alanları listele
- Bilinçli olarak

---

## 2️⃣ 3 kritik iş kuralını belirle
- Bunlar mutlaka test edilecek

---

## 3️⃣ Manuel test checklist yaz
- Release öncesi

---

## 4️⃣ 2 teknik borcu yazılı hale getir
- Ne zaman ödenecek?

---

## 5️⃣ Kendi kalite eşiğini tanımla
- “Burası asla bozulamaz”

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Net bir test stratejisi
- Bilinçli teknik borç listesi
- Yavaşlatmayan kalite anlayışı
- Daha az sahte güven

olmalı.

---

## ⚠️ Son söz

> Test yazmak seni yavaşlatıyorsa,  
> yanlış yerde yazıyorsundur.

---

## 🔜 Sonraki hafta (14. Hafta)

**14 – Güvenlik, Yetkilendirme & Veri Sorumluluğu**

- MVP’de minimum güvenlik
- En sık yapılan açıklar
- Upload, ödeme, auth riskleri
- Kişisel veri sorumluluğu

---
