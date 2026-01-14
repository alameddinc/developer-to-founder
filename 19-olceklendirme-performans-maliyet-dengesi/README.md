# 19 – Ölçeklendirme, Performans & Maliyet Dengesi  
## “Büyümek Daha Hızlı Çalışmak Değil, Daha Akıllı Çalışmaktır”

Bu haftanın amacı:
> **Ürün büyürken erken optimizasyon tuzaklarına düşmemek,  
> performans problemlerini doğru okumak  
> ve maliyetleri kontrol altında tutarak ölçeklenmeyi öğrenmek.**

Bu hafta:
- “Sistemimiz 1M kullanıcıya hazır mı?” hayali kurmuyoruz
- Mikroservis romantizmi yapmıyoruz
- Gereksiz optimizasyonlara girmiyoruz

Ama:
> Ürün gerçekten büyümeye başladığında  
> **nerelerin patladığını ve ne zaman müdahale edilmesi gerektiğini** netleştiriyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Ölçeklendirme kavramını doğru anlayacak
- Performans ≠ hız yanılgısından kurtulacak
- Erken optimizasyonun neden zararlı olduğunu kavrayacak
- Trafik artınca nerelerin patladığını bilecek
- Maliyet / performans dengesini okuyabilecek
- “Ne zaman optimize edilir?” sorusuna bilinçli cevap verecek

---

## 🧠 En yaygın ama pahalı hata

> “Büyürsek çöker, o yüzden baştan çok sağlam yapalım.”

Gerçek:
> Erken optimizasyon,  
> **büyüyememenin en pahalı yoludur**.

Çoğu ürün:
- Ölçeklenemediği için değil
- **Hiç ölçeklenemeden öldüğü için** batar.

---

# 1️⃣ Ölçeklendirme ne zaman konuşulur?

Ölçeklendirme:
- Trafik artınca konuşulur
- Gerçek veri varken konuşulur

❌ Yanlış zaman:
- Henüz kullanıcı yokken
- MVP aşamasında
- Ölçüm yokken

✅ Doğru zaman:
- Trafik artışı var
- Bottleneck görülüyor
- Maliyet hissediliyor

> Ölçeklendirme,  
> varsayımla değil **veriyle** yapılır.

---

# 2️⃣ Performans ≠ hız

Performans:
- Sadece response time değildir

Performans şunları kapsar:
- Stabilite
- Hata oranı
- Kuyrukların dolmaması
- Kullanıcı deneyiminin bozulmaması

> 200ms ama sürekli hata veren sistem,  
> yavaştır.

---

# 3️⃣ Trafik artınca en önce nereler patlar?

Çoğu üründe sırayla:

1. DB bağlantıları
2. Background job’lar
3. File upload / storage
4. Cache eksikliği
5. External API limitleri

> CPU nadiren ilk patlayan şeydir.

---

# 4️⃣ Ölçeklendirme öncesi yapılması gerekenler

Ölçeklendirmeden önce:
- Ölç
- Anla
- Sadeleştir

## Düşük maliyetli kazanımlar
- Gereksiz query’leri azalt
- N+1 problemlerini çöz
- Cache ekle (gereken yere)
- Timeout’ları doğru ayarla

> Kod iyileştirmesi çoğu zaman  
> sunucu artırmaktan ucuzdur.

---

# 5️⃣ Erken optimizasyon örnekleri (kaçın)

❌ Mikroservise bölmek  
❌ Event-driven mimari kurmak  
❌ Aşırı cache katmanı  
❌ “İleride lazım olur” index’leri  
❌ Gereksiz autoscaling  

> İhtiyaç yokken yapılan optimizasyon,  
> teknik borçtur.

---

# 6️⃣ Maliyet nereden gelir?

En büyük maliyet kalemleri:
- Compute (CPU / GPU)
- Storage
- Network (egress)
- 3rd party servisler
- Logging / monitoring

Maliyet artışı genelde:
> “Fark etmeden” olur.

---

# 7️⃣ Maliyet / performans dengesi nasıl kurulur?

Her karar için sor:
- Bu değişiklik performansı ne kadar artırıyor?
- Maliyeti ne kadar artırıyor?
- Kullanıcı gerçekten fark edecek mi?

Örnek:
> %5 hız için %50 maliyet  
> genelde **kötü bir takastır**.

---

# 8️⃣ Ölçeklendirme stratejileri (basit → karmaşık)

### 1️⃣ Dikey ölçekleme
- Daha güçlü makine
- En basit ve genelde yeterli

### 2️⃣ Yatay ölçekleme
- Daha fazla instance
- State yönetimi önemli

### 3️⃣ İş yükünü ayırma
- Background job’ları ayır
- Upload / processing ayrımı

> Karmaşıklık,  
> son çaredir.

---

# 9️⃣ SilentCut bağlamında düşünürsek

Bu tip ürünlerde:
- Job queue dolabilir
- GPU/CPU maliyeti hızla artar
- Upload trafiği pahalılaşır

Doğru yaklaşım:
- İşlem sürelerini ölç
- Ortalama mı, p95 mi bak?
- Gereksiz re-process’i önle
- Kota ve limitleri erken koy

> Ölçeklenmek sadece teknik değil,  
> **ürün kararıdır**.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ En pahalı 3 işlem noktanı yaz
- Gerçek veya tahmini

---

## 2️⃣ En olası 3 bottleneck’i listele
- Trafik artarsa neresi patlar?

---

## 3️⃣ Optimize ETMEYECEĞİN yerleri yaz
- Bilinçli olarak

---

## 4️⃣ Ölçeklendirme tetikleyicilerini tanımla
- “Şu olursa müdahale ederim”

---

## 5️⃣ Maliyet takibi için 1 basit kural koy
- Günlük / haftalık kontrol

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Ölçeklendirme farkındalığı
- Performans ≠ hız anlayışı
- Daha kontrollü maliyet bakışı
- Erken optimizasyondan korunma refleksi

olmalı.

---

## ⚠️ Son söz

> Büyümek güzeldir.  
> Ama **kontrolsüz büyüme**,  
> hızlı batmaktır.

---

## 🔜 Sonraki hafta (20. Hafta)

**20 – Teknik Borç, Ürün Olgunluğu & Uzun Vadeli Yol Haritası**

- MVP → ürün geçişi
- Ne zaman yeniden yazılır?
- Ne zaman yazılmaz?
- Ürünü kapatma kararı
- Founder olarak “bırakabilmek”

---
