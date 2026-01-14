# 09 – Project Management for One: Git, Trello & Founder Disiplini

> **Haftanın Mottosu:** "Plansız çalışan bir deha, planlı çalışan bir aptaldan daha az iş üretir."

Bu haftanın amacı; seni Jira ticket'larına boğmak değil, **"Ne yapıyordum ben?"** sorusunu hayatından çıkarmaktır.
Solo founder veya küçük ekipken en büyük düşmanın **bağlam kaybıdır (context switching).** Bir an kod yazarken, bir an fatura keserken, bir an bug düzeltirken bulursun kendini. Bu kaos, düzenli bir sistemle yönetilmezse tükenmişlik (burnout) garantidir.

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] **GitFlow** gibi karmaşık yapılar yerine, tek kişilik dev kadro için **Feature Branch** veya **Trunk Based** akışını oturtacaksın.
* [ ] Fikirlerini çöp kutusuna değil, **"Icebox"**a (Buzluk) atmayı öğreneceksin.
* [ ] "Definition of Done" (Bitti Tanımı) kavramını netleştireceksin. (Kod bitti ≠ İş bitti).
* [ ] Kendi kendinin QA (Quality Assurance) ekibi olmayı öğreneceksin.

---

# 1️⃣ Git Stratejisi: Solo Founder Nasıl Çalışmalı?

Kurumsal şirketlerdeki `release/v1.2`, `hotfix/xy`, `develop` dalları senin için zaman kaybıdır. Ama `main` dalına direkt commit atmak da intihardır.

### Önerilen Model: "Basitleştirilmiş Feature Branch"

1.  **Main (Master):** Burası kutsaldır. Buradaki kod her zaman **Canlıya (Production)** çıkabilir durumda olmalıdır.
2.  **Feature Branch:** Her yeni özellik veya fix için yeni dal aç.
    * `feat/video-upload`
    * `fix/login-error`
    * `chore/update-deps`
3.  **Kural:** İşi bitir, test et, `main`'e merge et, dalı sil.

> **Neden?** Çünkü bir özellik üzerinde çalışırken (`feat/dark-mode`), acil bir hata (`fix/payment-crash`) çıkarsa, dark mode kodlarını canlıya almadan hatayı düzeltebilmelisin.

---

# 2️⃣ Görev Yönetimi: The Anti-Jira Approach

Jira, yöneticilerin seni takip etmesi içindir. Trello/Notion/Linear ise senin işi bitirmen içindir.

### 3 Kutu Tekniği (Kanban)

Board'unda sadece şu kolonlar olsun:

| Kolon | Anlamı | Kural |
| :--- | :--- | :--- |
| **1. Todo (Backlog)** | Yapılacak her şey. | Burası karışık olabilir, sorun değil. |
| **2. This Week (Sprint)** | Bu hafta bitecekler. | **Pazartesi sabahı** buraya 3-5 madde çek ve kilitle. Hafta ortası ekleme yapma. |
| **3. In Progress** | Şu an kodladığım. | **Sadece 1 tane** kart olabilir. Aynı anda 2 iş yapma. |
| **4. Done** | Bitenler. | Cuma günü buraya bakıp kendini tebrik et. |

### 🧠 The "Icebox" (Fikir Mezarlığı Değil, Park Alanı)
Aklına harika bir fikir geldi: *"Referans sistemi yapalım!"*
Bunu hemen `Todo`ya atma. Ayrı bir sayfa (`Ideas` veya `Icebox`) aç ve oraya yaz.
* **Kural:** Fikirler demlenmelidir. 1 hafta sonra baktığında hala heyecanlanıyorsan `Todo`ya alırsın.

---

# 3️⃣ Definition of Done (DoD): İş Ne Zaman Biter?

Geliştiricilerin en büyük yalanı: *"Kod bitti, sadece testi kaldı."*
Bu, *"Yemek bitti, sadece pişmesi kaldı"* demek gibidir.

Senin için **"Bitti"** şu anlama gelmeli:
1.  Kod yazıldı.
2.  Lokalde çalıştı.
3.  `Main` dalına merge edildi.
4.  Canlı ortamda (Production/Staging) görüldü.

> **Disiplin:** Bu 4 madde tamamlanmadan Trello kartını "Done" kolonuna çekme.

---

# 4️⃣ QA for One: Test Mühendisi Sensin

Otomasyon testleri (Unit/Integration) harikadır ama MVP aşamasında %100 kapsama (coverage) hayaldir.

### Manuel Test Ritüeli (Smoke Testing)
Her deploy sonrası şu 3 şeyi **gerçek bir cihazda** (Chrome DevTools mobil görünümünde değil, elindeki telefonda) dene:
1.  **Critical Path:** Yeni kullanıcı kaydolup, ana işlemi (video yükleme) yapabiliyor mu?
2.  **Payment:** Ödeme sayfası açılıyor mu? (Kart girmene gerek yok, sayfa patlamasın yeter).
3.  **Layout:** Butonlar ekranın dışına taşıyor mu?

> **Founder Körlüğü:** Kendi bilgisayarında (localhost) her şey çalışır. Çünkü cache var, cookie var, admin yetkisi var. Testi **Gizli Sekme (Incognito)** veya **Telefondan** yap.

---

# 5️⃣ Haftalık Çalışma Ritmi (Founder's Rhythm)

Patron yoksa, mesai de yoktur. Bu tehlikelidir çünkü ya hiç çalışmazsın ya da hep çalışırsın.

* **Pazartesi (Planlama):** Kahveni al, `Backlog`'a bak. Bu hafta en kritik 3 iş ne? Onları `This Week`'e çek. Kod yazma, plan yap.
* **Salı - Perşembe (Deep Work):** Sadece koda odaklan. Telefonu sessize al.
* **Cuma (Maintenance & Release):** Kodlamayı bırak. Deploy yap. Bugları temizle. Dokümantasyonu güncelle. Hafta sonuna kafan rahat gir.

> **Tavsiye:** Cuma akşamı 17:00'de deploy yapma. Hafta sonun zehir olur. Perşembe akşamı veya Cuma sabahı yap.

---

# 🧪 Case Study: SilentCut.io'ta Kaos Yönetimi

**Sorun:**
SilentCut.io'ı geliştirirken bir yandan "Video işleme çok yavaş" şikayetleri geliyor, bir yandan "Ses UIda Kayıyor" deniyordu.
Ben ne yaptım? Hepsine aynı anda saldırdım ve veritabanını bozdum.

**Çözüm (Ders Alındı):**
1.  **Labeling:** İşleri etiketledim. `bug/critical` (Video yavaş) vs `ui/minor` (ses UI'da kayıyor).
2.  **Priority:** Önce sistemi kilitleyen (kritik) bug çözüldü. Logo 3 gün yamuk kaldı, kimse ölmedi.
3.  **Focus:** Video işleme kodunu yazarken, frontend dosyalarına dokunmadım.

---

# 🛠️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] Yönetim Aracını Seç ve Kur
Trello, Notion, GitHub Projects veya Linear. Birini seç. (Basitlik > Özellik).
* Kolonları aç: `Backlog`, `This Week`, `Doing`, `Done`.

### 2. [ ] Backlog Temizliği
Aklındaki her şeyi (feature, bug, hayal) backlog'a dök. Sonra %80'ini `Icebox` (Buzluk) sayfasına taşı. `This Week` için sadece 3-5 tane bırak.

### 3. [ ] Git Temizliği
Projede bekleyen, merge edilmemiş, unutulmuş `dal` (branch) var mı? Hepsini ya merge et ya sil. `Main` tertemiz olsun.

### 4. [ ] "Release Day" Belirle
Haftanın hangi günü deploy yapacaksın? (Örn: Perşembe sabahları). Bunu takvime işle.

---

# ⛔️ Yasaklı Davranışlar (Anti-Patterns)

* **"Shiny Object Syndrome":** O an yaptığın işi bırakıp, aklına gelen yeni ve havalı bir özelliği kodlamaya başlamak. (Bunu `Icebox`a at).
* **"Main'de Kodlamak":** *"Küçük bir değişiklik ya"* diyip `git push origin main` yapmak.
* **"Sonsuz Backlog":** Backlog'unda 500 madde varsa, o bir plan değil, suçluluk listesidir. Sil gitsin.

---

## 🔜 Gelecek Hafta: Launch Prep & Go-to-Market (Lansman Hazırlığı)

Artık teknik ve yönetimsel altyapımız tamam. Ürünü dünyaya açma vakti yaklaşıyor.
* 10. Hafta'da teknik CI/CD yerine (onu 7'de hallettik), **"Ürünü Yayına Hazırlama (Launch Checklist)"** ve **"Soft Launch"** stratejilerini konuşalım mı?
* Beta kullanıcıları, Feedback döngüsü ve "Waitlist" yönetimi.

---
*Developer to Founder - Week 09*
