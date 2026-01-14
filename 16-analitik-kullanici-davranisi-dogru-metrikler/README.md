# 16 – Analitik, Kullanıcı Davranışı & Doğru Metrikler  
## “Ölçmeden Büyüme Olmaz, Yanlış Ölçerek de Yanlış Büyürsün”

Bu haftanın amacı:
> **Ürünün gerçekten değer üretip üretmediğini anlamak,  
> vanity metric’lerden kaçınmak  
> ve founder olarak doğru metriklere bakma refleksi kazanmak.**

Bu hafta:
- GA kurulumu adım adım anlatmıyoruz
- Dashboard fetişi yapmıyoruz
- “Her şeyi ölçelim” demiyoruz

Ama:
> Ürün kararlarını **veriye dayalı** almanın  
> temel zihniyetini kuruyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Analitik neden gereklidir net anlayacak
- Kullanıcı davranışı ile sayı arasındaki farkı görecek
- Vanity metric ile anlamlı metric’i ayırt edebilecek
- MVP için “az ama doğru” metrikleri seçecek
- GA ve benzeri araçlara **amaçla** yaklaşacak
- “Veri var ama karar yok” tuzağından kaçınacak

---

## 🧠 Büyük yanılgı

> “Ziyaretçi arttıysa ürün iyi gidiyor.”

Gerçek:
> Ziyaretçi artışı  
> **ürünün işe yaradığını göstermez**.

Önemli olan:
- Gelen kullanıcı ne yapıyor?
- Nerede takılıyor?
- Nerede bırakıyor?

---

# 1️⃣ Analitik ne için var?

Analitik:
- Rapor süslemek için değil
- Yatırımcı etkilemek için değil

Analitik:
> **Karar almak için vardır.**

Eğer bir metrik:
- Kararını değiştirmiyorsa  
> o metrik gereksizdir.

---

# 2️⃣ Kullanıcı davranışı ≠ tıklama sayısı

En yaygın hata:
> Kullanıcıyı sayılarla temsil etmek.

Ama kullanıcı:
- Bir yol izler
- Bir hedefe ulaşmaya çalışır
- Bir noktada vazgeçer

Analitik şunu sormalı:
> “Kullanıcı ne yapmaya çalışıyordu?”

---

# 3️⃣ Funnel (akış) düşüncesi

Her üründe en az bir ana funnel vardır.

Örnek (SaaS / araç ürünü):
1. Siteye geldi
2. Kayıt oldu
3. İlk aksiyonu yaptı
4. Sonuç aldı
5. Geri geldi

Bu zincirin her halkası:
- Ölçülebilir
- İyileştirilebilir

> Funnel bozuksa,  
> ürün bozuk demektir.

---

# 4️⃣ MVP için doğru metrik seti

MVP’de:
- Çok metrik = çok gürültü

### MVP için genelde yeterli metrikler
- Aktif kullanıcı (günlük / haftalık)
- İlk aksiyon oranı
- Funnel drop-off noktaları
- İşlem başarı oranı
- Geri dönüş (retention) sinyali

> “Kaç kişi geldi?” değil  
> “Kaçı değer aldı?” sorusu önemli.

---

# 5️⃣ Vanity metric’ler (uzak dur)

Vanity metric:
- İyi hissettirir
- Ama karar aldırmaz

Örnekler:
- Toplam kullanıcı sayısı
- Toplam sayfa görüntüleme
- Twitter takipçi sayısı
- Mail listesi (kullanılmıyorsa)

> Vanity metric = ego besini.

---

# 6️⃣ GA (ve benzeri araçlar) ne zaman, nasıl?

GA:
- Erken kurulur
- Geç ciddiye alınır

Ama:
> Olay (event) tanımı olmadan  
> GA çöplüktür.

### Sağlıklı yaklaşım
- Önce neyi ölçmek istediğini yaz
- Sonra event’leri tanımla
- Sonra aracı kur

> Araç, sorudan sonra gelir.

---

# 7️⃣ Event bazlı düşünme (çok kritik)

Sayfa değil, **olay** ölç.

Örnek event’ler:
- `signup_completed`
- `first_upload`
- `job_started`
- `job_finished`
- `download_clicked`

Her event için sor:
- Bu event hangi kararı destekliyor?

---

# 8️⃣ Analitik ile UX arasındaki ilişki

Analitik şunu söyler:
- Nerede sorun var

Ama şunu söylemez:
- Neden sorun var

Bu yüzden:
- Analitik + kullanıcı gözlemi birlikte yürür

> Sayı yön gösterir,  
> gözlem sebebi açıklar.

---

# 9️⃣ SilentCut bağlamında düşünürsek

Bu tip ürünlerde anlamlı metrikler:
- Upload başlatan / bitiren oranı
- Job tamamlanma süresi
- Sonuç indirilen job oranı
- Tekrar gelen kullanıcı sinyali

Anlamsız metrik:
- Landing page ziyaret sayısı (tek başına)

> İş değeri üreten aksiyonlar ölçülür.

---

# 10️⃣ Founder için metrik bakma disiplini

Önerilen ritim:
- Haftada 1 gün metriklere bak
- Her metrik için:
  - “Bu bana ne söylüyor?”
  - “Buna göre ne yapacağım?”

Eğer cevap yoksa:
> O metriği sil.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ Ürünün ana funnel’ını çiz
- 4–6 adım

---

## 2️⃣ 5 anlamlı metrik seç
- Vanity olmayan

---

## 3️⃣ 5 event tanımı yaz
- İsim + anlam

---

## 4️⃣ “Bu metriğe bakınca ne yaparım?” sorusunu cevapla
- Her metrik için

---

## 5️⃣ Ölçmeyeceğin 3 şeyi yaz
- Bilinçli olarak

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Net bir funnel modeli
- Az ama anlamlı metrik seti
- Analitiği karar aracı olarak kullanma refleksi
- Daha az gürültü, daha çok sinyal

olmalı.

---

## ⚠️ Son söz

> Ölçmeden büyüyemezsin.  
> Ama yanlış ölçerek de  
> **yanlış büyürsün**.

---

## 🔜 Sonraki hafta (17. Hafta)

**17 – Lansman, Dağıtım & İlk Kullanıcılar**

- Launch nedir, nedir değildir?
- Sessiz lansman
- İlk 100 kullanıcı
- Beklenti yönetimi

---
