# 13 – Strategic Quality: Test Stratejisi & Teknik Borç Yönetimi

> **Haftanın Mottosu:** "Test yazmak kodun doğru çalıştığını kanıtlamaz; sadece test ettiğin senaryoların bozuk olmadığını kanıtlar. MVP'de hedef %100 kapsama (coverage) değil, %100 kritik güvenliktir."

Bu haftanın amacı; TDD (Test Driven Development) fanatiği olmak değil, **"Risk Driven Development"** yapmaktır.
Solo founder veya küçük bir ekipsen, her satıra test yazacak vaktin yok. Ama ödeme sisteminin bozulmasına da tahammülün yok. Denge nerede?

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] **"Test Coverage"** metriğinin bir MVP için neden anlamsız (vanity metric) olduğunu anlayacaksın.
* [ ] **Volatile (Uçucu)** kod ile **Core (Çekirdek)** kod arasındaki farkı görüp, sadece çekirdeği test edeceksin.
* [ ] Teknik Borcu (Technical Debt) kötü bir şey olarak değil, **"Vadeyle Hız Satın Almak"** olarak göreceksin.
* [ ] **TODO Driven Development** ile borçlarını yönetmeyi öğreneceksin.

---

# 1️⃣ The "Testing Pyramid" for Founders (Ters Piramit)

Kurumsal dünyada: Unit > Integration > E2E.
Founder dünyasında bu değişir. Çünkü senin UI'ın sürekli değişiyor.

### 1. Neye ASLA Test Yazma? (The Volatile Zone)
* **UI Bileşenleri:** Buton rengi, margin, padding. (Yarın değişecek).
* **Standart CRUD:** Framework'ün zaten yaptığı işler (Django'nun save metodu, Next.js'in routing'i).
* **Deneysel Özellikler:** Tutup tutmayacağını bilmediğin "Dark Mode" özelliği.

### 2. Neye MUTLAKA Test Yaz? (The Money Zone)
* **Para:** Fiyat hesaplama, fatura kesme, kredi düşme.
* **Core Logic:** SilentCut.io için "Video süresi hesaplama" veya "Sessizlik algoritması".
* **Auth:** "User A, User B'nin verisini silebilir mi?" kontrolü.

> **Kural:** Kırıldığında sana **para kaybettirecek** veya **dava açtıracak** her şey test edilmelidir. Gerisi "olsa güzel olur"dur.

---

# 2️⃣ Unit Test vs. Integration Test: Hangisi?

Solo founder için en yüksek ROI (Yatırım Getirisi) **Integration Test**lerdedir.

* **Unit Test:** "Bu fonksiyon 2+2'yi topluyor mu?" (Çok detay, çok bakım ister).
* **Integration Test:** "Kullanıcı 'Satın Al'a basınca API çalışıyor, DB güncelleniyor ve Mail gidiyor mu?"

**Öneri:** MVP için **"Critical Path Testing"** yap.
Kullanıcının sisteme girip, ana işi yapıp, çıktığı o tek yolu (Happy Path) otomatik test et. Geri kalanını manuel test et.

---

# 3️⃣ Manuel Test Refleksi: "Developer Körlüğü"nden Çıkış

Otomasyon harikadır ama insan gözünün yerini tutmaz.
Her release öncesi şu 5 dakikalık ritüeli yap:

1.  **Incognito Mode:** Cache temizken site açılıyor mu?
2.  **Mobil Görünüm:** Telefondan butonlara basılıyor mu?
3.  **Hata Senaryosu:** İnterneti kesip butona basarsam ne oluyor?

> **Tavsiye:** Testi kendi bildiğin yoldan yapma. Rastgele tıkla. Kullanıcılar her zaman rastgele tıklar.

---

# 4️⃣ Teknik Borç: Bir Finansal Enstrüman

Teknik borç, startup'ın **Kredi Kartı**dır.
* Bugün hızlı çıkmak için borçlanırsın (Hızlı kod yazarsın).
* Yarın faiziyle ödersin (Refactor edersin).

### Borç Türleri

| Tür | Açıklama | Karar |
| :--- | :--- | :--- |
| **Bilinçli Borç** | "Şu an hardcode yapıyorum çünkü Cuma lansman var. Haftaya düzelteceğim." | ✅ **Kabul.** (Not alarak yap). |
| **Bilinçsiz Borç** | "Nasıl çalıştığını anlamadım ama kopyaladım yapıştırdım, çalıştı." | ❌ **Ret.** (Bu borç değil, mayın tarlasıdır). |
| **Zehirli Borç** | Veri güvenliğini veya tutarlılığını bozan yamalar. | ❌ **Ret.** (Asla alınmaz). |

### 🛠 Debt Management: `// TODO: DEBT`
Kodun içine yorum bırak:
`// TODO: DEBT - Burası hardcoded, kullanıcı sayısı 100 olunca DB'ye taşı.`
Böylece IDE'nde arattığında borcunu görürsün.

---

# 5️⃣ Kalite Eşiği (Quality Threshold)

Mükemmeli arama, **"Kabul Edilebilir"**i tanımla.

**MVP İçin Kalite Anayasası:**
1.  **Veri Kaybı Asla Olamaz:** Upload edilen video silinemez.
2.  **Para Hatası Asla Olamaz:** 10$ çekip 9 kredi yüklenemez.
3.  **UI Bozuk Olabilir:** Buton kayabilir, sorun değil.
4.  **Hız Yavaş Olabilir:** Video 10 dakikada işlenebilir, sorun değil (Yeter ki bilgi ver).

---

# 6️⃣ Case Study: SilentCut.io Test Stratejisi

SilentCut.io geliştirilirken:

* **FFmpeg Algoritması:** Karmaşık matematik. Buraya **Unit Test** yazıldı. Çünkü elle test etmek imkansızdı.
* **Ödeme Akışı:** Paddle entegrasyonu. Buraya **Integration Test** yazıldı.
* **Video Listeleme Sayfası:** Test **YAZILMADI**. Çünkü UI sürekli değişiyordu. Elle kontrol edildi.

*Sonuç:* Hızlı geliştirme, sıfır kritik bug. UI bugları oldu ama kullanıcılar bunu dert etmedi.

---

# 🛠️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] "No-Test" Listesi Hazırla
Projenin hangi kısımlarına test yazmayacağını belirle ve vicdan azabı çekmeyi bırak.
* *Örn: "Hakkımızda sayfası, Profil fotosu yükleme."*

### 2. [ ] 1 Kritik Test Yaz
Projenin kalbine (Ödeme veya Ana İşlem) sadece 1 tane Integration Test yaz.
* *"Input ver -> İşlem yap -> Sonuç doğru mu?"*

### 3. [ ] Borç Defteri Aç
Kodun içinde `TODO` veya `FIXME` olmayan, ama "içine sinmeyen" yerleri bul ve yorum satırı ekle.
* `// TODO: Refactor this when scaling to 1000 users.`

### 4. [ ] Manuel Test Senaryosu (Smoke Test)
Bir kağıda 5 madde yaz. Her deploydan sonra bunları elle dene.
1. Login ol.
2. Video yükle.
3. Kredi kartı ekranını aç.
4. Çıkış yap.

---

# ⛔️ Yasaklı Davranışlar (Anti-Patterns)

* **"Test Coverage %100 olsun."** -> Bunu sadece boş vakti olan kurumsal şirketler yapar.
* **"Sonra test yazarız."** -> Yalan. Asla yazmayacaksın. Kritik yere ŞİMDİ yaz.
* **"Mock Cehennemi":** Her şeyi mocklayıp (sahteleyip), gerçekte hiçbir şeyin çalışmadığı testler yazmak.

---

## 🔜 Gelecek Hafta: Güvenlik & Veri Sorumluluğu

Test ettik, borçlandık, hızlandık. Peki kapıyı kilitledik mi?
* 14. Hafta: "MVP'yi Hacklemek".
* Basit güvenlik önlemleri, Auth açıkları ve KVKK/GDPR için minimum gereksinimler.

---
*Developer to Founder - Week 13*
