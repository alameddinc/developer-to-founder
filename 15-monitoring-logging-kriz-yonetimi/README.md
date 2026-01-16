---
description: https://github.com/alameddinc/developer-to-founder
---

# 15 – Sleeping Soundly: Monitoring, Logging & Kriz Yönetimi

> **Haftanın Mottosu:** "Kullanıcılar senin QA (Test) ekibin değildir. Bir sorun olduğunda Twitter'dan değil, telefonundaki bildirimden öğrenmelisin."

Bu haftanın amacı; NASA komuta merkezi kurmak değil. Amacımız; **"Sistem çalışıyor mu?"** sorusunun cevabını 3 saniye içinde verebilmek ve gece rahat uyumaktır.

***

### 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:

* [ ] **Monitoring** (İzleme) ile **Logging** (Kayıt) arasındaki farkı doktor/hasta analojisiyle anlayacaksın.
* [ ] **"Structured Logging"** (JSON) kullanarak logları okunabilir hale getireceksin.
* [ ] **"Alert Fatigue"** (Alarm Yorgunluğu) tuzağına düşmeden, sadece _gerçek_ yangınlarda bildirim alacaksın.
* [ ] Bir kriz anında (Downtime) panik yapmadan uygulayacağın bir **Runbook** (Acil Durum Planı) hazırlayacaksın.

***

## 1️⃣ Monitoring vs. Logging: Doktor Analojisi

Bu ikisi karıştırılır ama amaçları farklıdır.

| Kavram         | Analoji            | Soru                            | Araç Örneği                          |
| -------------- | ------------------ | ------------------------------- | ------------------------------------ |
| **Monitoring** | Kalp Atış Monitörü | "Hasta yaşıyor mu? Nabız kaç?"  | UptimeRobot, BetterStack, CloudWatch |
| **Logging**    | Röntgen / MRI      | "Hastanın karnı neden ağrıyor?" | Sentry, Datadog, CloudWatch Logs     |

> **Kural:** Monitoring sana "Bozuldu" der. Logging sana "Şundan dolayı bozuldu" der.

***

## 2️⃣ The "Sentry" Stack: MVP İçin Tek Araç

Solo founder için en büyük lüks **Sentry** (veya benzeri LogRocket, BugSnag) kullanmaktır.

* **Neden?**
  * Sen loglara bakmazsın, Sentry sana mail atar.
  * Kullanıcının tarayıcısında, senin backend'inde, veritabanında ne hata olduysa hepsini yakalar.
  * _"Hata oldu"_ demez; _"Ahmet, Chrome'da, 'Öde' butonuna basınca 500 hatası aldı"_ der.

**MVP Kurulumu:**

1. **Frontend:** Sentry React/Vue SDK (JS hatalarını yakalar).
2. **Backend:** Sentry Node/Go/Python SDK (Sunucu hatalarını yakalar).
3. **Uptime:** Sadece `/health` endpoint'ini kontrol eden ücretsiz bir "Ping" servisi (UptimeRobot).

***

## 3️⃣ Structured Logging: `console.log`'u Bırak

Geliştiricilerin en kötü alışkanlığı: `console.log("Hata oldu:", error)`

Bu log production'da çöp olur. Çünkü aranamaz, filtrelenemez.

**Doğru Yöntem (JSON Logging):**

```javascript
// Kötü
console.log("Kullanıcı video yükleyemedi", user.id);

// İyi (Structured)
logger.error({
  event: "upload_failed",
  user_id: 123,
  file_size: "500mb",
  error_message: error.message,
  stack_trace: error.stack
});
```

_Neden?_ Çünkü yarın log sistemine girip `event="upload_failed" AND file_size > "100mb"` diye sorgu atabilirsin. Düz metinde bunu yapamazsın.

***

## 4️⃣ Sağlık Kontrolü: `/healthz` Endpoint'i

Uygulamanın hayatta olduğunu kanıtlayan basit bir API ucu yap.

```
app.get('/healthz', async (req, res) => {
  // 1. Veritabanına ping at
  // 2. Redis'e ping at
  
  if (dbIsAlive && redisIsAlive) {
    res.status(200).send("OK");
  } else {
    res.status(500).send("Sistem Hasta");
  }
})
```

Bu endpoint'i bir Uptime servisine (BetterStack / UptimeRobot) bağla. Eğer 200 dönmezse sana SMS atsın.

***

## 5️⃣ Kriz Yönetimi: "Sistem Çöktü" Runbook'u

Bir gün siten çökecek. O an elin ayağın titreyecek. O yüzden şimdiden bir "Acil Durum Reçetesi" yaz.

**Sistem Çöktüğünde Yapılacaklar (Örnek):**

1. **Nefes Al:** Panik yapma. Hata zaten oldu.
2. **Etki Analizi:** Herkes mi giremiyor, sadece login olanlar mı? (Monitoring'e bak).
3. **Kanama Durdurma:** Son deploy'u geri al (**Rollback**). Çoğu sorun son kod değişikliğinden kaynaklanır.
4. **İletişim:** Eğer kesinti 5 dakikayı geçerse, Twitter'dan veya Status Page'den "Sorunun farkındayız, çözüyoruz" yaz. Sessizlik güveni öldürür.
5. **Analiz:** Sistem ayağa kalkınca loglara bak ve kök nedeni (Root Cause) bul.

***

## 6️⃣ Alarm Yorgunluğu (Alert Fatigue)

Telefonun günde 50 kere "Hata var" diye ötüyorsa, bir süre sonra bakmazsın. Ve o bakmadığın bildirim, gerçek yangın olur.

**Alarm Kuralları:**

* **Warning (Uyarı):** Disk %80 dolu. -> _E-mail at. (Sabah bakarım)._
* **Critical (Kritik):** Ödeme sistemi yanıt vermiyor. -> _SMS at / Ara. (Gece 3 olsa bile uyanmalıyım)._

***

## 7️⃣ Case Study: SilentCut.io FFMPEG Faciası

**Olay:** SilentCut.io'ta bir test sırasında çok yüksek adette sessizlik barındıran bir video dosyası yükledi. **Sonuç:** FFMPEG işlemi sunucunun tüm RAM'ini yedi ve 1 saat boyunca işleyemedi Sunucu kilitlendi (OOM Kill).

**Eksik Olan Ne İdi?**

* **Monitoring:** RAM/CPU/GPU kullanımı %99'a geldiğinde uyarı yoktu.
* **Logging:** Neden çöktüğü loglanmamıştı, sadece "Process killed" yazıyordu.

**Ders:**

* Loglara `segment size, processing status` eklendi.
* Büyük dosyalar için özel formülasyon kullanıldı

***

## 🛠️ Haftalık Görevler (Commitment Checklist)

#### 1. \[ ] Sentry (veya benzeri) Kur

Frontend ve Backend'e bağla. Bilerek bir hata fırlat (`throw new Error("Test")`) ve panele düştüğünü gör.

#### 2. \[ ] `/healthz` Endpoint Yaz

Veritabanı bağlantısını kontrol eden basit bir route ekle.

#### 3. \[ ] Uptime Monitor Ayarla

UptimeRobot (ücretsiz) hesabı aç, `/healthz` adresini izlemeye al. Siteni durdur ve mail gelip gelmediğini dene.

#### 4. \[ ] Basit Runbook Yaz

Bir kağıda "Site çökerse ilk kimi arayacağım? (Kendimi), İlk nereye bakacağım?" adımlarını yaz.

***

## ⛔️ Yasaklı Davranışlar (Anti-Patterns)

* **"Kullanıcı yazar nasıl olsa."** -> Kullanıcı yazmaz, rakibe gider.
* **"Logları sunucuda dosyaya yazmak."** -> Sunucu ölürse, dosya da ölür. Logları dışarı (SaaS) gönder.
* **"Her 404 hatasında bana SMS at."** -> 1 günde delirirsin. Sadece 500 hatalarında SMS at.

***

### 🔚 3. Faz Tamamlandı!

Tebrikler! Artık;

1. Fikri doğruladın (Faz 1).
2. MVP'yi kodladın (Faz 2).
3. Altyapıyı, güvenliği ve operasyonu kurdun (Faz 3).

Şimdi sırada en heyecanlı (ve en zor) kısım var: **Büyüme & Analitik.** Ürün çalışıyor ama **"İşe yarıyor mu?"**

***

### 🔜 4. Faz – Ölçüm, Büyüme & Sürdürülebilirlik (Hafta 16–20)

* **16. Hafta:** **Product Analytics & Metrics.**
* Google Analytics yeterli mi? (Hayır).
* "Retention" (Elde tutma) neden "Acquisition" (Müşteri bulma) dan daha önemlidir?
* Funnel (Huni) analizi nasıl yapılır?

***

_Developer to Founder - Week 15_
