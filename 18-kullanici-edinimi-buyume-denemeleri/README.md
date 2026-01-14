# 18 – Growth Engineering: Kullanıcı Edinimi & Büyüme Denemeleri

> **Haftanın Mottosu:** "Kod yazmak ürünü inşa eder. Pazarlama ise ürünü satar. 'İnşa edersen gelirler' (Build it and they will come) sözü, Hollywood filmlerinde geçen bir yalandır."

Bu haftanın amacı; pazarlama gurusu olmak değil, **"Traffic Acquisition" (Trafik Edinimi)** sistemini bir mühendis gibi kurgulamaktır.
Reklam vermek "para yakmak" değildir; reklam vermek **"veri satın almaktır".**

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] **Paid (Paralı)** ve **Organic (Organik)** kanalları, AWS Lambda ve Dedicated Server farkı gibi teknik bir gözle ayıracaksın.
* [ ] **CAC (Müşteri Edinme Maliyeti)** hesabını yaparak, reklam verince batıp batmayacağını göreceksin.
* [ ] Blog yazmak yerine **"Engineering as Marketing"** (Yan Araçlar) ile trafik çekmeyi öğreneceksin.
* [ ] **Cold Outreach** (Soğuk Temas) ile spam yapmadan potansiyel müşteriye ulaşacaksın.

---

# 1️⃣ Paid vs. Organic: Developer Analojisi

Pazarlama kanalları ikiye ayrılır. Hangisini seçeceğin, **zamanına** ve **parana** bağlıdır.

| Kanal Tipi | Analoji | Özellik | Örnek |
| :--- | :--- | :--- | :--- |
| **Paid (Reklam)** | **AWS Lambda** | Musluğu açarsın akar, kapatırsın durur. Hızlıdır ama her saniyesi para yazar. | Google Ads, Meta Ads, Reddit Ads. |
| **Organic (SEO/İçerik)** | **Kendi Sunucunu Kurmak** | Kurması zordur, zaman alır (aylar sürer). Ama bir kere kurunca maliyeti çok düşüktür. | Blog, YouTube, Twitter, Free Tools. |

> **MVP Stratejisi:** İlk 1 ay **Paid** (Hızlı öğrenmek için), sonraki aylar **Organic** (Sürdürülebilirlik için).

---

# 2️⃣ Google Ads: Niyet Satın Almak

Google Ads, problemini **zaten arayan** insanları bulur.
* *Örnek:* "Video sessizlik silme programı" diye aratan birinin cüzdanı masanın üzerindedir.

**Deney Kurulumu (50$ Bütçe İle):**
1.  **Keyword:** Rakiplerinin adını veya problemini hedefle (`remove silence mp4`).
2.  **Negatif Keyword:** `free`, `crack`, `indir` kelimelerini engelle. (Para vermeyecek adamı tıklatma).
3.  **Hedef:** Ana sayfaya değil, o sorunu anlatan özel bir Landing Page'e yönlendir.

> **Amaç:** 50$ harcadım, 50 kişi geldi, 5'i kayıt oldu. -> **CAC = 10$.** (Bu rakamı öğrenmek için reklam veriyorsun).

---

# 3️⃣ Organic: Engineering as Marketing (Kodlayarak Büyümek)

Geliştiriciler blog yazmaktan sıkılır. Ama kod yazmayı severler.
HubSpot veya Ahrefs gibi devler böyle büyüdü.

**Taktik:** Ana ürünün "SilentCut" paralı. Ama "Video Bitrate Calculator" diye **ücretsiz** ve basit bir araç yap.
1.  İnsanlar "Video bitrate hesaplama" diye aratır.
2.  Senin ücretsiz aracını kullanır.
3.  Sayfada "Bu arada, videondaki sessizlikleri de silmek ister misin?" banner'ını görür.

> **Sonuç:** SEO uyumlu, faydalı ve sürekli trafik çeken bir "Lead Magnet" (Müşteri Mıknatısı).

---

# 4️⃣ Cold Outreach: Sniper Atışı

Reklam, tüfekle rastgele ateş etmektir. Cold Outreach (DM/Mail), sniper atışıdır.

**Kime:** YouTube kanalının "Hakkında" kısmında e-postası olan içerik üreticileri.
**Mesaj:** (Kısa ve Net).

> "Selam [İsim],
> Kanalındaki [X] videonu izledim, içerik süper.
> Ancak videoda çok fazla sessiz duraklama var, bu izleyiciyi sıkabilir.
> Geliştirdiğim SilentCut aracı ile senin videonun 5 dakikasını temizledim, farkı gör: [Link].
> İşine yararsa sana 1 aylık ücretsiz kod: [KOD]."

**Püf Nokta:** Asla "Toplu Mail" atma. Kişiye özel olsun. Videoyu gerçekten işle. Emek ver.

---

# 5️⃣ The Death Formula: CAC > LTV

Büyümenin matematiği şudur:

* **CAC (Customer Acquisition Cost):** Bir müşteriyi ikna etmek için harcadığın para (Reklam / Gelen Müşteri). Örn: $20.
* **LTV (Lifetime Value):** O müşterinin sana ömrü boyunca ödeyeceği para. Örn: $15.

Eğer **CAC ($20) > LTV ($15)** ise:
> **Tebrikler, her yeni müşteride $5 zarar ediyorsun.** Ne kadar büyürsen o kadar hızlı batarsın.

**Çözüm:** Ya reklamı ucuzlat (Organic kanallara geç) ya da fiyatı artır (LTV'yi yükselt).

---

# 6️⃣ Case Study: SilentCut Büyüme Deneyleri

**Hipotez:** "YouTuberlar montaj yaparken en çok zamanı sessizlikleri silmeye harcıyor."

**Deney 1 (Google Ads):**
* Anahtar Kelime: "Premiere Pro silence remover plugin".
* Bütçe: $50.
* Sonuç: Tıklama başı maliyet (CPC) çok yüksek ($2). Pahalı geldi. Durduruldu.

**Deney 2 (Twitter/X - Organic):**
* İçerik: "Yapay zeka ile videomu nasıl %40 kısalttım?" (Video thread).
* Sonuç: 100 Retweet. 500 Ziyaretçi. Bedava trafik. Başarılı.

**Deney 3 (Free Tool):**
* Araç: "Video Silence Detector" (Videonuzu yükleyin, ne kadarının sessiz olduğunu analiz etsin. İndirmek yok, sadece analiz).
* Sonuç: İnsanlar merak edip yükledi. %20'si "Temizlemek için Tıkla" diyip ana ürüne geçti.

---

# 🛠️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] 1 Adet "Paid" Deneyi Yap
Bütçe: 500 TL (veya $20). Platform: Google veya Reddit.
* Sadece 3 gün çalıştır. Kaç kişi tıkladı, kaçı üye oldu? Veriyi not al.

### 2. [ ] 1 Adet "Cold DM" At
Hedef kitlenden 5 kişiye, yukarıdaki şablona benzer **kişiselleştirilmiş** bir mesaj at.
* Cevap oranı %0 ise mesajın kötüdür. %20 ise harikadır.

### 3. [ ] "Side Project" Fikri Bul
Ana ürününe trafik çekecek basit, ücretsiz bir araç fikri bul. (Hesap makinesi, Analiz aracı, Liste vb.).

### 4. [ ] CAC Hesabı Yap
Şu ana kadar (varsa) harcadığın para / Müşteri sayısı.
* Bu rakam, ürün fiyatından düşük mü?

---

# ⛔️ Yasaklı Davranışlar (Anti-Patterns)

* **"Influencer'a Para Vermek":** MVP aşamasında büyük YouTuber'lara para verme. Onların kitlesi çok geniştir, senin nişine uymaz. Parana yazık olur.
* **"Sürekli Platform Değiştirmek":** 2 gün Google dene, 2 gün Facebook dene... Algoritma öğrenemez. Bir kanala en az 1-2 hafta şans ver.
* **"Spam Yapmak":** İnsanların DM kutusuna "Linkime tıkla" yazıp kaçmak. Markanı öldürürsün.

---

## 🔜 Gelecek Hafta: Ölçeklendirme ve Performans

Kullanıcıları bulduk (umarım). Şimdi trafik artınca sunucular ne yapacak?
* **19. Hafta:** **Scaling & Cost Management.**
* AWS faturası nasıl patlamaz?
* Veritabanı şişerse ne yapılır?
* "Premature Optimization" (Erken Optimizasyon) tuzağı.

---
*Developer to Founder - Week 18*
