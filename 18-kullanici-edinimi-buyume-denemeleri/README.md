# 18 – Growth Engineering: Kullanıcı Edinimi & Büyüme Denemeleri

> **Haftanın Mottosu:** "Kod yazmak ürünü inşa eder. Pazarlama ise ürünü satar. 'İnşa edersen gelirler' (Build it and they will come) sözü, Hollywood filmlerinde geçen bir yalandır."

Bu haftanın amacı; pazarlama gurusu olmak değil, **"Traffic Acquisition" (Trafik Edinimi)** sistemini bir mühendis gibi kurgulamaktır.
Reklam vermek "para yakmak" değildir; reklam vermek **"veri satın almaktır".**

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] **Paid (Paralı)** ve **Organic (Organik)** kanalları, AWS Lambda ve Dedicated Server farkı gibi teknik bir gözle ayıracaksın.
* [ ] **CPA, ROAS, CAC** gibi korkutucu kısaltmaların aslında basit birer "Verimlilik Denklemi" olduğunu anlayacaksın.
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

---

# 3️⃣ Organic: Engineering as Marketing (Kodlayarak Büyümek)

Geliştiriciler blog yazmaktan sıkılır. Ama kod yazmayı severler.
HubSpot veya Ahrefs gibi devler böyle büyüdü.

**Taktik:** Ana ürünün "SilentCut.io" paralı. Ama "Video Bitrate Calculator" diye **ücretsiz** ve basit bir araç yap.
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
> Geliştirdiğim SilentCut.io aracı ile senin videonun 5 dakikasını temizledim, farkı gör: [Link].
> İşine yararsa sana 1 aylık ücretsiz kod: [KOD]."

---

# 5️⃣ The Growth Math: CPA, ROAS & CAC

Pazarlama bir sanat değil, matematiktir. İşte formüller:

### A) CPA (Cost Per Action) - Aksiyon Başına Maliyet
Kullanıcının **müşteri olması gerekmez**, senin istediğin *herhangi* bir şeyi yapmasının maliyetidir.
* *Formül:* Harcanan Para / Toplam "Sign-up" Sayısı.
* *Örnek:* 100$ harcadın, 20 kişi **üye oldu**.
* **CPA = $5.** (Her üye sana 5 dolara mal oldu).

### B) CAC (Customer Acquisition Cost) - Müşteri Edinme Maliyeti
CPA'in abisidir. Sadece **para ödeyen** kullanıcıyı sayar.
* *Formül:* Harcanan Para / Ödeme Yapan Sayısı.
* *Örnek:* 100$ harcadın, o 20 üyeden sadece 2'si **satın aldı**.
* **CAC = $50.** (Her müşteri sana 50 dolara mal oldu).

### C) ROAS (Return on Ad Spend) - Reklam Harcamasının Getirisi
Reklamın bir "kumar makinesi" (Slot Machine) gibi düşün. 1$ atınca kaç $ veriyor?
* *Formül:* Reklamdan Gelen Ciro / Reklam Maliyeti.
* *Örnek:* 100$ harcadın, o 2 müşteriden toplam 300$ kazandın.
* **ROAS = 3x (veya %300).**

> **Altın Kural:**
> * **ROAS > 1** ise: Para kazanıyorsun, reklamı artır (Scale et).
> * **ROAS < 1** ise: Para yakıyorsun, reklamı durdur ve ürünü/fiyatı düzelt.

### D) Ölüm Formülü: CAC > LTV
* **LTV (Lifetime Value):** Müşterinin ömrü boyunca sana ödeyeceği toplam para.
* Eğer **CAC ($50) > LTV ($30)** ise, her satışta $20 zarar ediyorsun demektir. Büyüdükçe batarsın.

---

# 6️⃣ Case Study: SilentCut.io Büyüme Deneyleri

**Hipotez:** "YouTuberlar montaj yaparken en çok zamanı sessizlikleri silmeye harcıyor."

**Deney 1 (Google Ads):**
* Bütçe: $50.
* Sonuç: 10 Kayıt (CPA: $5). 0 Satış (CAC: Sonsuz).
* **Karar:** ROAS 0. Çok pahalı. Durduruldu.

**Deney 2 (Twitter/X - Organic):**
* İçerik: "Yapay zeka ile videomu nasıl %40 kısalttım?" (Video thread).
* Sonuç: 100 Retweet. 500 Ziyaretçi. Bedava trafik.
* **Karar:** ROAS Sonsuz (Maliyet 0). Başarılı. Buna yüklenilecek.

---

# 🛠️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] 1 Adet "Paid" Deneyi Yap
Bütçe: 500 TL (veya $20). Platform: Google veya Reddit.
* Sadece 3 gün çalıştır.
* **CPA**'ini hesapla. (Kaç TL harcadım / Kaç kişi üye oldu?)

### 2. [ ] 1 Adet "Cold DM" At
Hedef kitlenden 5 kişiye, kişiselleştirilmiş bir mesaj at.
* Cevap oranı %0 ise mesajın kötüdür. %20 ise harikadır.

### 3. [ ] "Side Project" Fikri Bul
Ana ürününe trafik çekecek basit, ücretsiz bir araç fikri bul. (Hesap makinesi, Analiz aracı, Liste vb.).

### 4. [ ] Matematiğini Kontrol Et
* Ürünün fiyatı (LTV tahmini), CPA hedefinden yüksek mi?
* Eğer ürünün $10 ise ve CPA $15 çıkıyorsa, reklam vermeyi bırakman gerekir.

---

# ⛔️ Yasaklı Davranışlar (Anti-Patterns)

* **"Influencer'a Para Vermek":** MVP aşamasında büyük YouTuber'lara para verme. Onların kitlesi çok geniştir, dönüşüm düşüktür.
* **"ROAS Hesaplamadan Reklamı Açık Unutmak":** Kredi kartı ekstresi gelince ağlarsın. Günlük kontrol et.
* **"Spam Yapmak":** İnsanların DM kutusuna "Linkime tıkla" yazıp kaçmak. Markanı öldürürsün.

---

## 🔜 Gelecek Hafta: Ölçeklendirme ve Performans

Kullanıcıları bulduk, reklam matematiğini çözdük. Şimdi trafik artınca sunucular ne yapacak?
* **19. Hafta:** **Scaling & Cost Management.**
* AWS faturası nasıl patlamaz?
* Veritabanı şişerse ne yapılır?
* "Premature Optimization" (Erken Optimizasyon) tuzağı.

---
*Developer to Founder - Week 18*
