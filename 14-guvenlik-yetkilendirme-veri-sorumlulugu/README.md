# 14 – Güvenlik, Yetkilendirme & Veri Sorumluluğu  
## “Hacklenmekten Değil, Rezil Olmaktan Kork”

Bu haftanın amacı:
> **MVP seviyesinde gerçekçi bir güvenlik anlayışı kurmak,  
> kullanıcı verisine karşı sorumluluğu kavramak  
> ve en sık yapılan ölümcül güvenlik hatalarından kaçınmak.**

Bu hafta:
- “Askerî seviye güvenlik” anlatmıyoruz
- Pentest eğitimi vermiyoruz
- Zero-trust mimari çizmiyoruz

Ama:
> MVP’yi batıran **basit ama ölümcül** güvenlik açıklarını  
> net bir şekilde konuşuyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- MVP için “yeterince güvenli”nin ne olduğunu anlayacak
- Auth, yetkilendirme ve veri ayrımını doğru yapacak
- Upload, ödeme ve job tabanlı sistemlerde riskleri tanıyacak
- Kişisel veri sorumluluğunun teknik + hukuki boyutunu kavrayacak
- “Sonra bakarız” denmemesi gereken güvenlik noktalarını ayırt edecek
- Güvenliği ürünü yavaşlatmadan ele almayı öğrenecek

---

## 🧠 Büyük yanılgı

> “Biz küçük bir ürünüz, kim bize saldıracak?”

Gerçek:
> Saldırılar **kişisel değildir**.  
> Otomatiktir.

Bot:
- Küçük ürün ayırt etmez
- Açık bulursa girer

> Küçük olmak,  
> daha az hedef olmak demek değildir.

---

# 1️⃣ MVP’de güvenlikten ne anlıyoruz?

MVP’de güvenlik:
- Her şeyi kilitlemek değildir
- Her riski sıfırlamak değildir

MVP’de güvenlik:
> **Kritik alanları açık bırakmamaktır.**

---

## MVP için asgari güvenlik hedefleri
- Yetkisiz erişim yok
- Veri sızıntısı yok
- Para yanlış işlemiyor
- Kullanıcı başkasının verisini göremiyor

Bunun üstü:
> nice to have.

---

# 2️⃣ Kimlik doğrulama (Authentication) ≠ Yetkilendirme (Authorization)

Bu ikisi en çok karıştırılan kavramlardır.

- **Authentication:** Sen kimsin?
- **Authorization:** Ne yapabilirsin?

### ❌ Yaygın hata
- Giriş yaptı → her şeyi yapabilir

### ✅ Doğru yaklaşım
- Giriş yaptı
- Rolü ne?
- Kaynağın sahibi mi?

> Auth doğru değilse,  
> ürün çöker.

---

# 3️⃣ Yetkilendirme hataları (en tehlikeliler)

En sık görülen açık:
> “Bu kaynağa gerçekten bu kullanıcı mı erişmeli?”

Örnek hatalar:
- `/api/jobs/{id}` → id’yi bilen herkes erişiyor
- Başkasının dosyasını indirebilme
- Tenant ayrımının olmaması

> Yetkilendirme bug’ı =  
> veri sızıntısı.

---

# 4️⃣ Upload, job ve async sistemlerde güvenlik

Bu tarz ürünlerde risk büyüktür.

## Riskli alanlar
- Dosya upload
- Arka plan job’ları
- İşlem sonuçları

### Asgari önlemler
- Dosya tipi kontrolü
- Boyut limiti
- Job sahibi kontrolü
- Output erişimi kontrolü

> “Dosya geldi” demek  
> “güvenli” demek değildir.

---

# 5️⃣ Ödeme & kota sistemlerinde güvenlik

Para olan yerde:
> Hata pahalıdır.

### Dikkat edilmesi gerekenler
- Client’tan gelen fiyatlara güvenme
- Token / kota server-side hesaplanır
- Idempotency (aynı işlem 2 kere olmasın)
- Log’lanabilir işlem akışı

> “Bir kere hata oldu”  
> finansal güveni bitirir.

---

# 6️⃣ Kişisel veri sorumluluğu (hafife alma)

Kişisel veri:
- E-posta
- IP
- Dosya içeriği
- Ödeme bilgileri

Şu soruyu sor:
> “Bu veri bana gerçekten lazım mı?”

### MVP için altın kural
- Gereksiz veri toplama
- Tutma süresini bil
- Silme yolu olsun

> Veri, sorumluluktur.  
> Yük gibidir.

---

# 7️⃣ Log’lar da kişisel veri olabilir

En sık yapılan hata:
- Log’a her şeyi basmak

❌ Yanlış
- Token
- Email
- Dosya path’leri

✅ Doğru
- Masking
- ID bazlı log
- Gerektiği kadar

> Log sızıntısı da  
> veri sızıntısıdır.

---

# 8️⃣ Güvenlikte “sonra yaparız” denmeyen yerler

Buralar **ilk günden doğru yapılmalı**:

- Auth & yetkilendirme
- Tenant ayrımı
- Ödeme hesaplama
- Upload sınırları
- Gizli anahtar yönetimi

Buralar ertelenebilir:
- Rate limiting tuning
- Advanced monitoring
- Detaylı audit log

---

# 9️⃣ SilentCut bağlamında düşünürsek

Bu tip ürünlerde:
- Dosya kime ait?
- Job kimin?
- Output’a kim erişebilir?

Yanlış olursa:
- Başkasının videosu indirilebilir
- Kota suistimali olur
- Hukuki risk doğar

> Güvenlik burada sadece teknik değil,  
> **etik** bir konudur.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ Ürünün kritik güvenlik alanlarını listele
- Auth
- Ödeme
- Upload
- Job

---

## 2️⃣ 3 olası güvenlik açığını yaz
- “Burada ne patlayabilir?”

---

## 3️⃣ Asgari güvenlik kurallarını tanımla
- MVP için

---

## 4️⃣ Topladığın verileri listele
- Hangisi gerçekten gerekli?

---

## 5️⃣ “Bunu ilk günden doğru yapmalıyım” dediğin 3 şeyi yaz

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- MVP seviyesinde sağlam güvenlik çerçevesi
- Yetkilendirme farkındalığı
- Veri sorumluluğu bilinci
- Daha az hukuki ve teknik risk

olmalı.

---

## ⚠️ Son söz

> Güvenlik,  
> seni yavaşlatmak için değil  
> **seni ayakta tutmak için vardır.**

---

## 🔜 Sonraki hafta (15. Hafta)

**15 – Monitoring, Logging & Kriz Yönetimi**

- Ne ölçülür, ne ölçülmez?
- Alarm yorgunluğu
- İlk prod krizi
- “Her şey çalışıyordu” anı

---
