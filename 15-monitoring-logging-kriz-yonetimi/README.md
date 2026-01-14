# 15 – Monitoring, Logging & Kriz Yönetimi  
## “Sorun Olmaması Değil, Sorunu Fark Etmek Önemlidir”

Bu haftanın amacı:
> **Ürünün gerçekten çalışıp çalışmadığını anlayabilmek,  
> sorunları kullanıcıdan önce fark etmek  
> ve ilk prod krizinde panik yapmadan hareket edebilmek.**

Bu hafta:
- Vendor spesifik monitoring anlatmıyoruz
- Dashboard fetişi yapmıyoruz
- “Her şeyi ölçelim” demiyoruz

Ama:
> Gerçek hayatta işe yarayan  
> **minimal ve etkili gözlem kültürü** kuruyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Monitoring ile logging farkını net ayıracak
- MVP için neyin ölçülmesi gerektiğini bilecek
- Alarm yorgunluğundan kaçınacak
- Log’ları debug için kullanabilecek
- İlk prod krizini nasıl yöneteceğini bilecek
- “Her şey çalışıyordu” cümlesini daha az kuracak

---

## 🧠 Büyük yanılgı

> “Kullanıcı şikâyet ederse bakarız.”

Gerçek:
> Kullanıcı şikâyet ettiğinde  
> **çoktan geç kalmışsındır**.

İyi ürün:
- Sorunu kullanıcıdan önce fark eder.

---

# 1️⃣ Monitoring nedir, Logging nedir?

Bu ikisi sık karıştırılır ama farklıdır.

- **Monitoring:** Sistem şu an sağlıklı mı?
- **Logging:** Bir şey bozulduysa neden bozuldu?

> Monitoring “bir şey yanlış” der  
> Logging “neden yanlış” der

---

# 2️⃣ MVP için monitoring yaklaşımı (sade ama etkili)

MVP’de:
- Her metriği ölçmeye çalışma
- En kritik 3–5 metriği seç

## MVP için olmazsa olmaz metrikler
- Sistem ayakta mı? (uptime)
- Error rate arttı mı?
- Kritik işlem süreleri
- Background job başarısı
- Ödeme / işlem başarısı

> Ölçemediğin şeyi yönetemezsin  
> ama ölçtüğün her şey de önemli değildir.

---

# 3️⃣ Sağlık endpoint’leri (küçük ama çok güçlü)

Her MVP’de:
- `/health`
- `/healthz`

gibi basit endpoint’ler olmalı.

Ne yapmalı?
- DB bağlantısı var mı?
- Kritik servisler ayakta mı?

Bu endpoint:
- Monitoring’in temelidir
- Deploy sonrası kontrol aracıdır

---

# 4️⃣ Logging: Debug için yazılır, arşiv için değil

En yaygın hata:
> “Her şeyi loglayalım.”

Bu yanlıştır.

### Log’lar ne için yazılır?
- Hata anını anlamak
- Akışı takip etmek
- Kriz sonrası analiz

### Log’larda OLMAMASI gerekenler
- Kişisel veri
- Token
- Şifre
- Dosya içeriği

> Log = kanıt,  
> ama suç unsuru da olabilir.

---

# 5️⃣ İyi log nasıl olur?

İyi log:
- Anlamlıdır
- Kısa ama açıklayıcıdır
- Context içerir

Örnek:
- user_id
- request_id
- job_id
- işlem aşaması

❌ “Bir hata oluştu”  
✅ “upload_failed: size_limit_exceeded, user_id=123”

---

# 6️⃣ Alarm yorgunluğu (çok tehlikeli)

Her alarm:
- Dikkat böler
- Stres yaratır

Yanlış yaklaşım:
- Her error için alarm

Doğru yaklaşım:
- Kullanıcıyı etkileyen durumlar için alarm
- Trend bazlı alarm
- Sessiz ama anlamlı alarm

> Alarm varsa,  
> gerçekten bakmalısın.

---

# 7️⃣ İlk prod krizi: Ne olur, ne yapılır?

İlk kriz genelde:
- Upload çalışmaz
- Job’lar takılır
- Ödeme patlar
- Sistem yavaşlar

### Yanlış refleks
- Panik
- Rastgele deploy
- “Bir şeyler deneyeyim”

### Doğru refleks
1. Etki alanını belirle
2. Geri alabiliyor musun bak
3. Kullanıcıyı bilgilendir
4. Sonra analiz yap

> Krizde hız değil,  
> **soğukkanlılık** kazandırır.

---

# 8️⃣ Kriz sonrası yapılması gerekenler

Kriz bittikten sonra:
- “Bir daha olmasın” demek yetmez

Yapılacaklar:
- Kısa post-mortem yaz
- Kök neden analizi yap
- Gerekirse alarm ekle
- Gerekirse test ekle

Ama:
> Suçlu arama.  
> Sistem düzelt.

---

# 9️⃣ SilentCut bağlamında düşünürsek

Bu tarz ürünlerde:
- Job queue tıkanması
- Uzun süren işlemler
- Upload timeout’ları

İyi monitoring:
- Job sayısını
- Ortalama işlem süresini
- Başarısız job oranını gösterir

> Krizi kullanıcıdan değil,  
> panelden öğren.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ Ölçülecek 5 kritik metriği yaz
- Gerçekten önemli olanlar

---

## 2️⃣ Bir health check tanımla
- Ne kontrol edecek?

---

## 3️⃣ Log formatını belirle
- Hangi alanlar olacak?

---

## 4️⃣ 1 alarm senaryosu yaz
- Ne olursa alarm çalar?

---

## 5️⃣ “Prod krizi olursa ne yaparım?” planı yaz
- 5 adım

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Minimal monitoring stratejisi
- Anlamlı logging alışkanlığı
- Kriz anında panik yapmayan refleks
- Daha az sürpriz

olmalı.

---

## ⚠️ Son söz

> Sorun çıkmayan sistem yoktur.  
> Sorunu fark edemeyen sistem vardır.

---

## 🔚 3. Faz Sonu

Bu hafta ile:
- Üretim kalitesi
- Operasyonel farkındalık
- Kriz yönetimi

tamamlandı.

---

## 🔜 4. Faz – Ölçüm, Büyüme & Sürdürülebilirlik (Hafta 16–20)

Bir sonraki hafta:
> **16 – Analitik, Kullanıcı Davranışı & Doğru Metrikler**

Artık:
- Sadece “çalışıyor mu?” değil  
- **“işe yarıyor mu?”** diyeceğiz.
