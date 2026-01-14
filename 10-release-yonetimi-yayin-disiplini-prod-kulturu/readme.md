# 10 – Release Yönetimi, Yayın Disiplini & Prod Kültürü  
## “Prod’a Çıkmak Bir Teknik İş Değil, Bir Yönetim Kararıdır”

Bu haftanın amacı:
> **Ürünü yayına alma sürecini korkulan bir an olmaktan çıkarıp,  
> kontrollü, tekrarlanabilir ve güvenli bir alışkanlığa dönüştürmek.**

Bu hafta:
- CI/CD pipeline kurmuyoruz (7. hafta)
- Spesifik cloud komutları yazmıyoruz
- Ama:
> **Gerçek hayatta prod’a çıkmak için gereken her refleksi kazanıyoruz**

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Release ile deploy arasındaki farkı net ayırabilecek
- “Bunu prod’a almalı mıyım?” sorusuna bilinçli cevap verebilecek
- Tek komutla deploy etmenin neden şart olduğunu anlayacak
- Lokal debug ve prod’a yakın testin release sürecindeki rolünü kavrayacak
- Feature’ları kontrollü şekilde yayınlayabilecek
- Hotfix, rollback ve prod krizlerini panik yapmadan yönetebilecek
- Prod ortamını “dokunulmaz” değil, “kontrollü” görecek

---

## 🧠 En yaygın ama öldürücü alışkanlık

> “Biraz daha düzeltelim, sonra çıkarız.”

Gerçek:
> Hiçbir release “tam hazır” olmaz.  
> Sadece **çıkan** ve **hiç çıkmayan** vardır.

Çıkmayan ürün:
> Öğrenemez.  
> Öğrenemeyen ürün ölür.

---

# 1️⃣ Deploy nedir, Release nedir? (net ayrım)

- **Deploy:** Kodun prod ortamına gönderilmesi
- **Release:** Kullanıcının bu değişiklikten fayda görmesi

Her deploy:
- release olmak zorunda değildir

Ama:
> Her release mutlaka bir deploy içerir.

### Örnek
- Kod prod’a gitti ama feature kapalı → deploy var, release yok
- Feature flag açıldı → release oldu

---

# 2️⃣ MVP aşamasında release felsefesi

MVP’de hedef:
- Mükemmel sistem
- Sıfır bug

değildir.

MVP’de hedef:
> **Hızlı öğrenme + düşük risk**

Bu yüzden:
- Küçük release
- Sık deploy
- Kolay geri alma

altın standarttır.

---

# 3️⃣ Ne zaman prod’a çıkılır?

### ❌ Yanlış zamanlar
- “Şu da bitsin”
- “Biraz daha refactor yapayım”
- “Haftaya daha iyi olur”

### ✅ Doğru zaman
- Bir iş **bittiğinde**
- Test edilebilir durumdaysa
- Geri alınabilir durumdaysa

> Deploy edilmemiş iş,  
> **bitmemiş iştir**.

---

# 4️⃣ Release’e ne girer, ne girmez?

## ✅ Release’e girebilecekler
- Tek bir kullanıcı değerini artıran değişiklik
- Küçük bug fix
- UX iyileştirmesi
- Performans düzeltmesi

## ❌ Release’e girmemesi gerekenler
- Yarım feature
- Büyük refactor (tek başına)
- Test edilmemiş edge case
- “Bir daha bakarız” kodu

Release:
> Temiz olmalıdır.  
> Çöp taşımaz.

---

# 5️⃣ Tek komutla deploy: Neden şart?

Bu hafta deploy script **yazmayı öğretmiyoruz**,  
ama şunu net söylüyoruz:

> **Tek komutla deploy edemiyorsan,  
> kriz anında deploy edemezsin.**

Bu komut:
- `make deploy`
- `./deploy.sh`
- `task deploy`
- CI pipeline’daki `release` job’ı

olabilir.

### Tek komut ne yapmalı?
Minimum:
1. Doğru sürümü seç
2. Build veya image pull
3. Prod’a deploy et
4. Basit smoke test çalıştır
5. Başarısızsa dur

> Manuel SSH, panik ve hata üretir.

---

# 6️⃣ Lokal debug & prod’a yakın test (release’in gizli temeli)

“Lokalde çalışıyor”:
> Prod için **yetersiz bir kriterdir**.

Release öncesi minimum beklenti:
- Prod’a **benzeyen** bir ortamda test

## MVP için yeterli pratik
- Docker (veya benzeri)
- `docker compose up` ile:
  - App
  - DB
  - Cache / queue
- `.env.example` standardı
- `/healthz` endpoint’i

Amaç:
> “Benim makinemde çalışıyor” yalanını azaltmak.

---

## Release öncesi lokal kontrol listesi
- Env eksikse app boot etmesin
- Migration adımı net mi?
- Log’lar anlamlı mı?
- Kritik akış uçtan uca çalışıyor mu?

---

# 7️⃣ Feature flag & kontrollü yayınlama

Feature flag:
- Büyük sistem olmak zorunda değil
- Basit bir config bile yeterli

Ne işe yarar?
- Feature’ı hazırla ama açma
- Kendin test et
- Küçük kullanıcı grubuna aç
- Gerekirse kapat

> Feature flag,  
> prod korkusunun sigortasıdır.

---

# 8️⃣ Hotfix nedir, ne değildir?

## Hotfix:
- Prod’daki kullanıcıyı **hemen** etkileyen hata
- Bekleyemez

### Hotfix özellikleri
- Küçük
- Hedefli
- Riskli refactor içermez

### ❌ Hotfix değildir
- Yeni feature
- “Madem buradayız” değişiklikleri
- Büyük mimari dokunuşlar

---

# 9️⃣ Kullanıcı varken deploy edilir mi?

**Evet.**

Ama bilinçli şekilde.

MVP seviyesinde kabul edilebilir:
- Kısa downtime
- Görsel bozulma

Kabul edilemez:
- Veri kaybı
- Yarım kalan ödeme / işlem

> Kullanıcı varken deploy etmeyi öğrenmeyen,  
> büyüyünce öğrenemez.

---

# 🔁 Rollback kültürü

Rollback:
- Başarısızlık değildir
- **Profesyonelliktir**

Release sonrası:
- Hata arttı mı?
- Metric bozuldu mu?
- Kullanıcı şikâyeti geldi mi?

Varsa:
> Geri al.  
> Analizi sonra yap.

---

# 📝 Release notu yazma alışkanlığı

Her release için:
- 3–5 maddelik not yeter

Örnek:
- Upload hızı iyileştirildi
- Mobilde buton sorunu düzeltildi
- Pricing metni netleştirildi

Amaç:
> Hafıza oluşturmak.

---

# 🧠 Prod korkusunu yönetmek (founder psikolojisi)

Prod korkusu:
- Normaldir
- Sağlıklıdır

Ama:
> Yönetilmezse ilerlemeyi durdurur.

Çözüm:
- Küçük release
- Sık deploy
- Geri alma planı
- Gözlem (15. haftada derinleşecek)

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ Release kriterlerini yaz
- Ne zaman prod’a çıkıyorsun?
- Hangi şartlar sağlanmalı?

---

## 2️⃣ Tek komut deploy yolunu tanımla
- Script mi?
- Make target mı?
- CI job mı?

---

## 3️⃣ Release checklist oluştur
- 5 maddelik

---

## 4️⃣ Bir hotfix senaryosu yaz
- “Prod’da şu olursa ne yaparım?”

---

## 5️⃣ Bu hafta en az 1 bilinçli deploy yap
- Küçük ama kontrollü

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Release disiplini
- Prod korkusunu yöneten refleks
- Tek komut deploy anlayışı
- Kontrollü yayınlama alışkanlığı

olmalı.

---

## ⚠️ Son söz

> Prod’a çıkamayan ürün,  
> **ürün değildir**.

---

## 🔜 Sonraki Faz

**3. Faz – Üretim Kalitesi & Operasyon (Hafta 11–15)**

İlk hafta:
> **11. Hafta – Domain, Veri Modeli & İş Kuralları**

Artık:
- “Çalışıyor” değil  
- **“Doğru çalışıyor mu?”** sorusunu soracağız.
