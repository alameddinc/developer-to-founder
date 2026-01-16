---
description: https://github.com/alameddinc/developer-to-founder
---

# 10 – Shipping Culture: Release Yönetimi & Prod Disiplini

> **Haftanın Mottosu:** "Gerçek sanatçılar 'ship' eder. Yerel bilgisayarında çalışan mükemmel kodun pazar değeri kocaman bir sıfırdır." — Steve Jobs (Paraphrased)

Bu haftanın amacı CI/CD pipeline'ı tekrar kurmak değil (onu 7. haftada yaptık). Amaç; **Prod ortamına kod göndermeyi, korkulan bir "olay" olmaktan çıkarıp, sıkıcı bir "alışkanlık" haline getirmektir.**

***

### 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:

* [ ] **Deploy vs Release** farkını anlayıp, kodu göndermekle özelliği açmayı birbirinden ayıracaksın.
* [ ] "Cuma günü deploy yapılır mı?" sorusuna profesyonel bir cevap vereceksin.
* [ ] **Rollback** (Geri alma) planı olmayan bir işi asla canlıya almayacaksın.
* [ ] Basit bir **Feature Flag** yapısıyla, özellikleri kullanıcıdan gizlemeyi öğreneceksin.

***

## 1️⃣ Deploy != Release (Kritik Ayrım)

Çoğu geliştirici bu ikisini aynı sanır.

* **Deploy (Dağıtım):** Kodun sunucuya kopyalanması ve çalıştırılmasıdır. (Teknik bir işlem).
* **Release (Yayın):** Kullanıcının o özelliği görmeye ve kullanmaya başlamasıdır. (Ürün kararı).

**Neden Önemli?** Kodu Pazartesi günü deploy edebilirsin ama özelliği Çarşamba günü marketing kampanyasıyla "Release" edebilirsin.

> **Hedef:** Kodun canlıda olması, kullanıcının onu gördüğü anlamına gelmemeli.

***

## 2️⃣ Prod Korkusunu Yenmek: "The Friday Deploy Rule"

Founder'ların korkulu rüyası: _"Ya site çökerse?"_ Bu korku yüzünden haftalarca deploy yapmazlar. Biriken kod büyür, risk artar.

#### Kural 1: Küçük ve Sık Deploy

1000 satırlık kodu tek seferde atmak Rus Ruletidir. 10 satırlık kodu günde 10 kere atmak ise güvenlidir. Hata çıkarsa nerede olduğunu hemen bilirsin.

#### Kural 2: Read-Only Friday

Cuma günü deploy yapma.

* Cuma akşamı çıkan bug, hafta sonunu zehir eder.
* Pazartesi - Perşembe arası deploy günleridir.
* Cuma günü: Refactor, Dokümantasyon, Bug fix (Staging'de).

***

## 3️⃣ Feature Flags: MVP İçin Basit Yöntem

Karmaşık sistemlere (LaunchDarkly vb.) gerek yok. Kodun içine basit bir `if` bloğu koymak yeterlidir.

```javascript
// config.js veya .env
const FEATURES = {
  NEW_UPLOAD_FLOW: false, // Şimdilik kapalı
};

// Component.js
if (FEATURES.NEW_UPLOAD_FLOW) {
  return <NewUploader />;
} else {
  return <OldUploader />;
}
```

**Ne işe yarar?**

* Kodu `main` branch'ine atıp deploy edebilirsin.
* Kullanıcılar yeni özelliği görmez.
* Sen production'da `cookie` veya `query param` ile özelliği sadece kendine açıp test edebilirsin.
* Hazır olduğunda `true` yapıp herkese açarsın.

***

## 4️⃣ Hotfix & Rollback Kültürü

Her şey ters gittiğinde ne yapacaksın?

#### 🚨 Hotfix (Acil Yama)

* **Ne Zaman:** Ödeme sistemi çalışmıyor, Login bozuk, Veri kaybı riski var.
* **Nasıl:** `main` branch'inden bir dal (`hotfix/payment-error`) aç. Sadece o hatayı düzelt. Test et. Deploy et.
* **Kural:** Hotfix sırasında refactor yapılmaz. "Şunu da düzelteyim" denmez.

#### ⏪ Rollback (Geri Sarma)

Bazen hatayı düzeltmeye çalışmak yerine, **eski çalışan sürüme dönmek** en doğrusudur.

* PaaS kullanıyorsan (Vercel/Railway), tek tuşla "Önceki Deploya Dön" diyebilirsin.
* Bunu yapmaktan utanma. Kanamayı durdurmak, ameliyat etmekten önemlidir.

***

## 5️⃣ Release Notes (Hafıza Oluşturmak)

Kullanıcılar (veya 6 ay sonraki sen) neyin değiştiğini bilmek ister. GitHub Release veya basit bir `CHANGELOG.md` dosyası tut. **Şablon:**

```
## v1.0.2 (2025-10-24)
### ✨ Yenilikler
- Video yükleme hızında %20 artış.
- Yeni "Karanlık Mod" desteği (Beta).

### 🐛 Düzeltmeler
- Safari tarayıcısında butonun kaybolma sorunu giderildi.
```

***

## 6️⃣ Prod Ortamı: Kutsal Ama Dokunulmaz Değil

Prod ortamında hata ayıklamak (debug) zorunda kalabilirsin.

* **Loglar:** Her hata loglanmalı. `console.log("Hata")` değil, `console.error("Payment Failed", { userId: 123, error: e })`.
* **Health Check:** `/health` veya `/status` endpoint'in olsun. Sadece "OK" dönmesi bile monitoring için yeterlidir.

***

## 🛠️ Haftalık Görevler (Commitment Checklist)

#### 1. \[ ] Deploy Script'ini Kontrol Et

Tek bir komutla (örn: `git push` veya `npm run deploy`) prod'a çıkabiliyor musun? Manuel dosya kopyalama varsa, onu bu hafta bitir.

#### 2. \[ ] Rollback Planı

Platformunda (Vercel/Railway/VPS) bir önceki sürüme nasıl döneceğini öğren ve bir kere test et (Staging'de).

#### 3. \[ ] Basit Feature Flag

Bir sonraki özelliğini `if (false)` bloğu içine alarak deploy et. Kod canlıda ama özellik kapalı olsun. Sonra `true` yapıp aç.

#### 4. \[ ] Changelog Başlat

Projenin kök dizinine `CHANGELOG.md` ekle ve son yaptığın değişiklikleri yaz.

***

## ⛔️ Yasaklı Cümleler (Anti-Patterns)

* **"Lokalde çalışıyordu."** -> Kullanıcı lokalde yaşamıyor.
* **"Cuma akşamı atalım, hafta sonu kimse kullanmaz."** -> Murphy Kanunları devrede, en çok hafta sonu kullanılır.
* **"Canlıda düzeltiriz."** -> Canlıda sadece Hotfix yapılır, geliştirme yapılmaz.

***

### 🔜 Gelecek Hafta: Faz 3'e Geçiş (Üretim Kalitesi)

Artık ürün canlıda, süreçler oturdu. Şimdi kodun **iç kalitesine** odaklanacağız.

* **11. Hafta:** Domain Modeling, Veri Tutarlılığı ve "Business Logic"in doğru yere konulması. Spagetti koddan, bakımı yapılabilir koda geçiş.

***

Developer to Founder - Week 10
