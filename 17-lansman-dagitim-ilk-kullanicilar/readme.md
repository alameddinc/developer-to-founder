# 17 – Hello World: Lansman, Dağıtım & İlk 100 Kullanıcı

> **Haftanın Mottosu:** "Lansman bir havai fişek gösterisi değildir. Lansman, boş bir odada mikrofonu eline alıp konuşmaya başlamaktır. İlk başta kimse dinlemez, sesini duyurmak zaman alır."

Bu haftanın amacı; ürünü GitHub'dan çıkarıp insanların önüne atmaktır.
Geliştiricilerin fantezisi şudur: *"Product Hunt'a koyarım, viral olurum, Stripe bildirimleri susmaz."*
Gerçek şudur: *"Product Hunt'a koyarsın, 50 kişi gelir, 3'ü kayıt olur, 0'ı ödeme yapar."*

Bu hafta bu sessizliği nasıl kıracağımızı konuşacağız.

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] **Soft Launch** (Sessiz) ile **Hard Launch** (Gürültülü) arasındaki stratejik farkı anlayacaksın.
* [ ] **"Do Things That Don't Scale"** (Ölçeklenmeyen Şeyleri Yap) prensibiyle ilk 100 kullanıcıyı *tek tek* bulacaksın.
* [ ] Product Hunt'ın bir "iş modeli" değil, bir "backlink ve prestij kaynağı" olduğunu kavrayacaksın.
* [ ] Lansman günü teknik olarak çuvallamamak için **OG Tags** ve **Support** hazırlığı yapacaksın.

---

# 1️⃣ Lansman Türleri: Hangi Yoldan Gidiyoruz?

Lansman, "Deploy" tuşuna basmak değildir. Stratejik bir karardır.

### A) Soft Launch (Beta / Sessiz Lansman)
* **Kime:** Arkadaşlara, Twitter'daki takipçilere, ilgili Discord gruplarına.
* **Amaç:** Bug avlamak ve UX hatalarını görmek.
* **Beklenti:** Para kazanmak değil, "sistem çalışıyor mu?" testini geçmek.
* **Taktik:** "Kapalı Beta", "Davetiye Usulü". (İnsanlar giremedikleri yere girmek isterler).

### B) Hard Launch (Showtime)
* **Kime:** Product Hunt, Hacker News, Reddit, Genel Sosyal Medya.
* **Amaç:** SEO için backlink almak, "Early Adopter" bulmak, Social Proof (Sosyal Kanıt) oluşturmak.
* **Risk:** Ürün kötüyse, kötü ilk izlenim kalıcıdır.

> **Öneri:** Önce 2 hafta Soft Launch yap, en büyük hataları çöz. Sonra Hard Launch yap.

---

# 2️⃣ İlk 100 Kullanıcı: El Yordamı (Hand-to-Hand Combat)

Paul Graham'ın efsanevi tavsiyesi: **"Ölçeklenmeyen Şeyler Yap."**

Sen Google değilsin. Reklam verip bekleyemezsin. İlk kullanıcılarını **tek tek** bulup içeri sokmalısın.

### Nasıl Yapılır? (Utangaç Developer Rehberi)
1.  **DM At:** Hedef kitlendeki insanları bul (Twitter/LinkedIn). *"Merhaba, X problemini yaşadığını gördüm. Ben bunu çözen Y aracını yaptım. Sana ücretsiz üyelik versem dener misin?"* de. (Satış yapma, yardım et).
2.  **Niş Komüniteler:** Reddit (r/webdev, r/youtubers), IndieHackers, ilgili Facebook grupları. *"Reklam yapmaya gelmedim, şunu geliştirdim, sizce işe yarar mı?"* diye sor.
3.  **Kendi Networkün:** LinkedIn'de "Ben bunu yaptım" diye paylaş. Utanma.

---

# 3️⃣ Product Hunt: Beklenti Yönetimi

Product Hunt (PH), indie hacker'ların mezuniyet töreni gibidir. Güzeldir ama hayat kurtarmaz.

**Gerçekler:**
* PH kullanıcılarının çoğu **diğer geliştiricilerdir**. Müşterin fırıncılar ise PH'de yoklar.
* PH'den gelen trafik **"turist"** trafiğidir. Bakar ve çıkar. Dönüşüm (Conversion) düşüktür.

**Neden Yapmalı?**
1.  Google'da üst sıralarda çıkmak için çok güçlü bir Backlink sağlar.
2.  Yatırımcılar veya teknoloji basını orayı takip eder.
3.  "Product of the Day" rozeti siteye hava katar (Trust Signal).

---

# 4️⃣ Teknik Lansman Hazırlığı (Launch Checklist)

Lansman günü sitenin patlamaması ve doğru görünmesi için:

1.  **Open Graph (OG) Tags:** Linki Twitter'a veya WhatsApp'a attığında güzel bir resim ve açıklama çıkıyor mu? (`metatags.io` ile kontrol et).
2.  **Support Kanalı:** Sitenin sağ altına bir Chat (Crisp/Tawk.to) veya net bir "Destek" maili koy. Hata alan kullanıcı küfür etmez, mail atar.
3.  **Analytics:** PostHog/Google Analytics çalışıyor mu? Gelen trafiğin nereden geldiğini göremezsen kör uçuş yaparsın.
4.  **Hoşgeldin Maili:** Kayıt olana otomatik "Merhaba" maili gidiyor mu?

---

# 5️⃣ Case Study: SilentCut.io Lansman Stratejisi (Hayali Case)

**Hedef Kitle:** Küçük YouTuberlar ve Podcast Yayıncıları.

**Adım 1 (Soft Launch):**
* r/NewTubers subreddit'inde bir post: *"Video editlemekten nefret ediyorum, o yüzden bunu yazdım. Bedava denemek isteyen?"*
* **Sonuç:** 20 Tester, 5 kritik bug raporu, 1 sadık kullanıcı.

**Adım 2 (Hard Launch):**
* Product Hunt lansmanı.
* Twitter'da ` #buildinpublic` etiketiyle sürecin hikayesi.
* **Sonuç:** 500 ziyaretçi, 50 kayıt, 2 ödeme. (Rakamlar küçük görünse de başlangıç için harika).

**Adım 3 (Cold Outreach):**
* YouTube'da abonesi 10k-50k arası olan kanalların "About" kısmındaki maillere kişisel e-posta: *"Son videondaki sessizlikleri SilentCut.io ile temizledim, işte sonuç. Denemek istersen link burada."*

---

# 🛠️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] OG Görseli Tasarla
Canva veya Figma'da 1200x630 boyutunda, ürünün ekran görüntüsü ve sloganı olan bir görsel yap. Meta etiketlerine ekle.

### 2. [ ] "Lansman Tweeti" Taslağı
Sadece link atma. Hikaye anlat.
* *"Başladığımda X sorunum vardı. 2 aydır Y üzerinde çalışıyorum. Bugün canlıya alıyorum. İşte SilentCut.io..."*

### 3. [ ] 10 Kişiye DM At
Potansiyel müşterin olabilecek 10 kişiyi belirle ve onlara spam olmayan, samimi bir mesaj at.

### 4. [ ] Product Hunt Hesabı
Hesabın yoksa aç. 1 hafta boyunca aktif ol (başka ürünlere oy ver, yorum yap). Yeni açılan hesaplar lansman yaparsa spama düşebilir.

---

# ⛔️ Yasaklı Davranışlar (Anti-Patterns)

* **"Spam Yapmak":** İlgisiz Facebook gruplarına link yapıştırıp kaçmak.
* **"Bot Basmak":** Product Hunt oyları satın almak. (Banlanırsın ve markan lekelenir).
* **"Mükemmeli Beklemek":** "Şu özellik de bitsin öyle duyurayım" dersen asla duyuramazsın. Utanç verici olsa bile duyur.

---

## 🔜 Gelecek Hafta: Büyüme Denemeleri

Lansmanı yaptık, ilk dalga geldi ve geçti. Şimdi gerçek hayat başlıyor.
* **18. Hafta:** **Acquisition Channels (Edinim Kanalları).**
* SEO mu, Reklam mı, İçerik mi?
* "Growth Hacking" efsaneleri ve gerçekleri.

---
*Developer to Founder - Week 17*
