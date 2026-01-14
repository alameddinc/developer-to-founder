# 14 – Minimum Viable Security: Güvenlik, KVKK & Veri Namusu

> **Haftanın Mottosu:** "Güven yıllar içinde inşa edilir, saniyeler içinde yıkılır. Hacklenmekten değil, kullanıcıya 'Pardon, verilerini çaldırdık' maili atmaktan kork."

Bu haftanın amacı, Pentagon'u koruyacak bir sistem kurmak değildir. (Zaten kuramazsın).
Amacımız; **"Kapıyı açık bırakmamaktır."**

Botlar ve script kiddie'ler (acemi hackerlar), özellikle yeni çıkan SaaS ürünlerini tarar. "Benim sitemi kim ne yapsın?" deme. Senin sunucunu Bitcoin madenciliği için, veritabanını ise dark web'de satmak için kullanırlar.

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] **AuthN** (Kimlik) ile **AuthZ** (Yetki) arasındaki farkı kod seviyesinde uygulayacaksın.
* [ ] **IDOR** (Insecure Direct Object References) açığını anlayıp, kullanıcıların birbirinin verisini görmesini engelleyeceksin.
* [ ] **KVKK / GDPR** uyumluluğunu bir "Avukat işi" olarak değil, "Veri Mimarisi" kararı olarak göreceksin.
* [ ] **Signed URLs** kullanarak dosya güvenliğini (S3/R2) sağlayacaksın.

---

# 1️⃣ AuthN vs AuthZ: En Büyük Kafa Karışıklığı

Geliştiricilerin %80'i burada hata yapar.

* **Authentication (AuthN):** "Sen kimsin?" (Cevap: Ben Ahmet'im, şifrem bu.)
* **Authorization (AuthZ):** "Bunu yapmaya yetkin var mı?" (Cevap: Ahmet olabilirsin ama bu faturayı silemezsin.)

### 🚨 En Yaygın Açık: IDOR
Kullanıcı giriş yapmıştır (AuthN tamamdır).
URL şöyledir: `app.com/invoice/123`
Kullanıcı URL'i `app.com/invoice/124` yapar.
**Eğer kodu şöyle yazdıysan Hacklendin:**

```javascript
// ❌ YANLIŞ (Sadece giriş yapmış mı diye bakıyor)
app.get('/invoice/:id', requireLogin, (req, res) => {
  const invoice = db.find(req.params.id);
  res.json(invoice);
});
```

**Olması Gereken:**
```javascript
// ✅ DOĞRU (Bu fatura bu adama mı ait diye bakıyor)
app.get('/invoice/:id', requireLogin, (req, res) => {
  const invoice = db.find(req.params.id);
  
  if (invoice.owner_id !== req.user.id) { // <-- KRİTİK KONTROL
     return res.status(403).send("Hadi oradan!");
  }
  
  res.json(invoice);
});
```


> **Ders:** Her veritabanı sorgusuna `WHERE owner_id = current_user` eklemezsen, verilerin halka açıktır.

----------

# 2️⃣ KVKK & GDPR: Hukuk Değil, Veri Diyeti

KVKK (TR) ve GDPR (EU), teknik olarak şunu der: **"Kullanmayacağın veriyi saklama."**

Bir geliştirici olarak sorumlulukların:

1.  **Data Minimization (Veri Diyeti):**
    -   Kullanıcının TC kimlik numarasına gerçekten ihtiyacın var mı? Yoksa sil.
    -   Doğum tarihi lazım mı? Değilse formdan çıkar.
    -   _Veri = Sorumluluktur. Ne kadar az veri, o kadar az risk._  
2.  **Right to be Forgotten (Unutulma Hakkı):**
    -   Kullanıcı "Hesabımı Sil" dediğinde, veritabanında `is_deleted = true` yapmak yetmez.  
    -   Kişisel verilerini (Email, Ad, Tel) ya **silmeli** ya da **anonimleştirmelisin** (Örn: `deleted_user_123@silindi.com`).  
3.  **Aydınlatma Metni & Çerezler:**
    -   Basit bir "Kabul Et" butonu koymak yetmez. Hangi çerezleri neden kullandığını bilen bir metin linki ekle. (Hazır generator'lar kullan).

----------

# 3️⃣ Dosya Güvenliği: "Public Bucket" Faciası

SilentCut.io gibi dosya işleyen ürünlerde en büyük risk, S3/R2 bucket'larını **"Public"** (Herkese açık) bırakmaktır.

**Senaryo:** Kullanıcı özel bir video yükledi. Linki tahmin edilebilir: `bucket.com/uploads/video_1.mp4`. Hacker, `video_2.mp4`'ü dener ve bulur.

**Çözüm: Signed URLs (İmzalı Linkler)**

1.  Bucket'ı tamamen **Private** yap.
2.  Kullanıcı dosyayı görmek istediğinde, Backend'den geçici (örn: 15 dakika geçerli) ve şifreli bir link üret.
    -   `bucket.com/video_1.mp4?token=xyz...&expires=170000`
3.  Bu linki sadece o kullanıcıya ver.

----------

# 4️⃣ Sır Saklama: Environment Variables

GitHub'da arama yaparsan binlerce AWS Key ve Stripe Secret bulabilirsin.

-   **Kural 1:** `.env` dosyası ASLA git'e atılmaz (`.gitignore`'a ekle).
-   **Kural 2:** Frontend kodunda (React/Vue) asla `SECRET_KEY` kullanılmaz. Tarayıcıya giden her kod, kullanıcı tarafından okunabilir. 
-   **Kural 3:** API Key'lerini kodun içine `const API_KEY = "123"` diye gömme.
 

----------

# 5️⃣ Case Study: SilentCut.io Güvenlik Kontrolü

SilentCut.io MVP'sinde nereler riskliydi?

1.  **Job Manipulation:** Kullanıcı bir işleme emri gönderirken `{ "priority": "high" }` parametresini elle ekleyip öne geçmeye çalışabilir. -> **Backend'de input validasyonu şart.**
    
2.  **Download Linkleri:** İşlenmiş videoların linkleri tahmin edilebilir mi? -> **UUID kullanıldı ve Signed URL yapıldı.**
    
3.  **Ödeme Bypass:** Ödeme başarılı olmadan işlem başlatılabilir mi? -> **Webhook doğrulaması (Stripe Signature Check) eklendi.**

----------

# 🛠️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] IDOR Testi Yap
Kendi uygulamana iki farklı kullanıcı ile üye ol.
-   Kullanıcı A'nın bir verisinin ID'sini al (URL'den veya Network tab'dan).
-   Kullanıcı B olarak giriş yap ve o ID'ye istek at.
-   Veriyi görebiliyor musun? Evet ise, **acil düzelt.**

### 2. [ ] Hassas Veri Taraması
Veritabanına bak. Şifreler `hash`lenmiş mi (bcrypt/argon2)? (Asla düz metin tutma). Gereksiz kişisel veri var mı?

### 3. [ ] Git Guardian Kontrolü
Repo'nda yanlışlıkla commit edilmiş bir API Key var mı? (GitHub'da geçmiş commitleri tarayan araçlar var, veya `gitgreps` ile kendin ara).

### 4. [ ] Basit KVKK Sayfası
Footer'a "Gizlilik Sözleşmesi" ve "Kullanıcı Sözleşmesi" linklerini ekle. İnternetten "SaaS Privacy Policy Generator" bulup taslak oluştur.

----------

# ⛔️ Yasaklı Davranışlar (Anti-Patterns)
-   **"Security through Obscurity":** "URL'i çok karmaşık yapayım, kimse bulamaz" demek güvenlik değildir.
-   **"Kendi Kriptonu Yazmak":** Şifreleme algoritması icat etme. Standartları (JWT, AES, HTTPS) kullan.
-   **"Frontend'de Validasyon Yettirmek":** Frontend validasyonu kullanıcı deneyimi içindir, Backend validasyonu güvenlik içindir. İkisi de şarttır.

----------

## 🔜 Gelecek Hafta: BÜYÜK FİNAL (Lansman & Operasyon)
Güvenliği sağladık, testleri yaptık, altyapıyı kurduk.
-   **15. Hafta:** **"Go Live!"**
-   Monitoring (İzleme), Logging, Kriz Yönetimi ve ilk kullanıcıları karşılama.
-   Ve bu yolculuğun (Developer to Founder) kapanışı.

----------

_Developer to Founder - Week 14_
