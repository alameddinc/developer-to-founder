# 11 – Domain, Veri Modeli & İş Kuralları  
## “Çalışan Kod Yetmez, Doğru Model Şart”

Bu haftanın amacı:
> **Ürünün kalbini oluşturan domain’i ve veri modelini  
> erken dönemde yanlış kurmamak.**

Bu hafta:
- Framework konuşmuyoruz
- “Hangi DB?” tartışmıyoruz
- DDD dersi vermiyoruz

Ama:
> Yanlış veri modelinin  
> neden en pahalı hata olduğunu netleştiriyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Domain kavramını net anlayacak
- Ürünün “çekirdek işini” ayırt edebilecek
- Veri modelini UI’dan bağımsız düşünebilecek
- İş kurallarını koda nasıl yedireceğini bilecek
- Geri dönülmesi zor hatalardan kaçınacak
- MVP’de “yeterince iyi” model kurabilecek

---

## 🧠 Büyük yanılgı

> “Şimdilik basit tutalım, sonra düzeltiriz.”

Gerçek:
> Basitlik ile **yanlışlık** aynı şey değildir.

Yanlış veri modeli:
- Refactor ile düzelmez
- Migration ile acı verir
- Büyüdükçe patlar

---

# 1️⃣ Domain nedir? (akademik değil, pratik)

Domain:
> Ürünün **para kazandığı işi** temsil eden kavramlar bütünüdür.

Domain:
- UI değildir
- API endpoint değildir
- Database tablosu değildir

Domain:
> “Bu ürün hangi işi çözüyor?” sorusunun cevabıdır.

---

## Örnek
Bir video işleme ürünü için:

- Domain: video, işlem, çıktı, kota
- Domain olmayan: buton rengi, animasyon, layout

> Domain’i karıştırırsan,  
> ürün büyüyemez.

---

# 2️⃣ Çekirdek domain’i bulmak (en önemli adım)

Kendine şunu sor:
> “Bu ürünün olmazsa olmaz işi ne?”

Örnekler:
- SilentCut → sessizlik tespiti & kırpma
- SaaS CRM → müşteri & etkileşim
- E-ticaret → sipariş & ödeme

Her üründe:
- **1 çekirdek domain**
- 2–3 destekleyici domain vardır

> Yanlış yere yatırım yapma.

---

# 3️⃣ Veri modeli: UI’dan BAĞIMSIZ düşün

En yaygın hata:
> UI’da gördüğünü tabloya çevirmek.

Bu yanlıştır.

### ❌ Yanlış yaklaşım
- “Bu ekranda şu var, tablo da öyle olsun”

### ✅ Doğru yaklaşım
- “Bu işin doğasında ne var?”

---

## Veri modeli düşünürken sorulacak sorular

- Bu nesne **zamanla değişir mi?**
- Geçmişini saklamalı mıyım?
- Silinir mi, yoksa arşivlenir mi?
- Tekil mi, çoğul mu?
- Sahibi kim?

> Bu sorular migration acısını azaltır.

---

# 4️⃣ İş kuralları: if-else çöplüğü yapma

İş kuralları:
- “Kim ne zaman ne yapabilir?”
- “Hangi durumda hata verilir?”
- “Hangi durum kabul edilemez?”

### ❌ Yanlış
- Controller içinde if-else
- UI’da kontrol
- DB trigger’a gömme

### ✅ Doğru
- İş kurallarını **tek yerde** topla
- Test edilebilir yap
- UI’dan bağımsız tut

> UI değişir,  
> iş kuralı kalır.

---

# 5️⃣ MVP için “yeterince iyi” veri modeli

MVP’de:
- Her ihtimali düşünme
- Ama **geri dönülemez** hatalardan kaçın

## MVP için altın kurallar
- ID’ler değişmez
- Audit alanları ekle (`created_at`, `updated_at`)
- Soft delete ihtimalini düşün
- User / tenant ayrımını baştan düşün

> Bunlar maliyeti düşük,  
> faydası yüksek kararlardır.

---

# 6️⃣ En sık yapılan ölümcül hatalar

❌ Her şeyi JSON’a gömmek  
❌ İş kuralını frontend’e bırakmak  
❌ “Sonra migration yaparız” demek  
❌ Çekirdek domain’i ertelemek  
❌ Gereksiz genelleme yapmak  

> Genelleme erken yapılırsa,  
> karmaşa üretir.

---

# 7️⃣ SilentCut bağlamında düşünürsek

Sessizlik kırpma ürünü için:

### Çekirdek domain
- Media
- Segment
- Processing job
- Output

### Destekleyici domain
- Kullanıcı
- Kota / token
- Faturalama
- Bildirim

Yanlış olurdu:
- UI ayarlarını domain’e sokmak
- Segmentleri JSON blob yapmak
- Job state’lerini UI’ya göre şekillendirmek

---

# 8️⃣ Domain + veri modeli = uzun vadeli hız

İyi model:
- İlk başta yavaş gibi hissettirir
- Sonra seni hızlandırır

Kötü model:
- İlk başta hızlı hissettirir
- Sonra seni kilitler

> Founder olarak görevin:
> **ilk hız değil, sürdürülebilir hız**.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ Çekirdek domain’i yaz
- 1 cümleyle

---

## 2️⃣ 5 ana domain nesnesini listele
- Her biri için sorumluluk yaz

---

## 3️⃣ 3 temel iş kuralını yaz
- “Şu durumda şu OLMAZ”

---

## 4️⃣ Veri modeli için risk listesi çıkar
- Neresi geri dönülmez?

---

## 5️⃣ UI’dan bağımsız model çiz
- Kağıt, Miro, not fark etmez

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Net bir domain tanımı
- Temiz bir veri modeli taslağı
- İş kuralları listesi
- Daha az migration riski

olmalı.

---

## ⚠️ Son söz

> Domain’i yanlış kuran,  
> kodu ne kadar güzel yazarsa yazsın  
> **ilerleyemez**.

---

## 🔜 Sonraki hafta (12. Hafta)

**12 – Kullanıcı Akışları, Frontend & Deneyim Tutarlılığı**

- Akış ≠ ekran
- Kullanıcıyı hata yapmaya itmemek
- Empty / loading / error state’ler
- Mobil & masaüstü farkları

---
