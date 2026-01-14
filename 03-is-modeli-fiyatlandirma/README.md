# 03 – Show Me The Money: İş Modeli & Fiyatlandırma

> **Haftanın Mottosu:** "İş modeli olmayan bir ürün, sadece sunucu faturası ödediğin pahalı bir hobidir."

Geçen hafta "Kime satacağız?" sorusunu çözdük. Bu hafta **"Nasıl para kazanacağız?"** sorusunu (Monetization Strategy) çözeceğiz.

Bir ürünün GitHub'da 10.000 star alması veya Product Hunt'ta günün birincisi olması harikadır. Ancak kasa eksi yazıyorsa, o proje ölü doğmuştur.

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] "Fiyatı sonra belirleriz" yalanından kurtulacaksın.
* [ ] Ürününün doğasına en uygun **Gelir Modelini (Revenue Model)** seçeceksin.
* [ ] Basit bir **Unit Economics** (Birim Ekonomisi) hesabı yaparak batıp batmayacağını ön göreceksin.
* [ ] Fiyatlandırmayı bir pazarlama kararı değil, **stratejik bir mühendislik kararı** olarak göreceksin.

---

## 🧠 En Büyük Founder Yanılgısı: "Önce Kullanıcı, Sonra Para"

Twitter/X'te gördüğün o viral olan ama batan startup'ların mezar taşına şöyle yazılır:
> *"Çok kullanıcımız vardı ama faturaları ödeyemedik."*

**Gerçekler:**
1.  **Ücretsiz Kullanıcı Yalan Söyler:** "Harika olmuş eline sağlık" der ama kullanmaz.
2.  **Ücretli Kullanıcı Dürüsttür:** Para veren kişi, cüzdanıyla oy kullanır. En iyi feedback, faturadır.
3.  **Para, Doğrulamadır:** Birisi henüz bitmemiş ürününe (MVP) para veriyorsa, PMF (Product-Market Fit) yolundasın demektir.

---

## 💰 İş Modeli: Paranın API Dokümantasyonu

İş modeli karmaşık bir MBA terimi değildir. Basitçe şudur:
> **KİM, NE İÇİN, NE ZAMAN ve NASIL ödüyor?**

Yazılımcı diliyle en yaygın modelleri inceleyelim:

### 1. Abonelik (SaaS / Subscription)
* **Mantık:** `cron job` gibi. Her ay düzenli ödeme.
* **Kullanım:** Slack, Netflix, Spotify.
* **Bug:** Kullanıcı o ay ürünü kullanmazsa "boşuna ödüyorum" der ve iptal eder (Churn).
* **Patch:** Sürekli değer üretmek zorundasın.

### 2. Kullanım Bazlı (Usage-Based / Pay-as-you-go)
* **Mantık:** AWS Lambda veya OpenAI API gibi. Kullandığın kadar öde.
* **Kullanım:** API servisleri, SMS gönderim toolları.
* **Bug:** Gelir tahminlemesi zordur (MRR dalgalanır).
* **Patch:** "Credits" (Kredi) sistemi ile ön ödeme almak.

### 3. Tek Seferlik (LTD - Lifetime Deal)
* **Mantık:** Eski usül lisans satışı. `npm install` ve bitiş.
* **Kullanım:** Desktop uygulamaları, pluginler.
* **Bug:** Para bir kere gelir, ama destek yükü sonsuza kadar sürer. Nakit akışını öldürür.

---

## 🛠 Case Study: SilentCut.io Fiyatlandırma Pivotu

**Hipotez v1:** *"Aylık $29 Abonelik yapalım."*
**Sonuç:** Çuvalladı.
**Neden:** Hedef kitlemiz olan YouTuber'lar her gün video atmıyor. Ayda 2 video atan adam, aboneliği "gereksiz masraf" gördü.

**Hipotez v2 (Pivot):** *"Kredi (Token) Sistemi."*
**Mantık:**
* 5 Dakika = 1 Kredi.
* Kullanıcı 30 kredi alsa bile, isterse 1 ayda harcar, isterse 1 yılda.
**Sonuç:** Satışlar arttı. Kullanıcı "kontrol bende" hissini sevdi.
**Subscription**: Eğer Kullanıcılar daha yoğun kullanım hedefliyorsa onlar için detaylı preview ve sınırsız işleme hakkı sağlandı.

> **Ders:** İş modelini, kullanıcının **tüketim alışkanlığına** (Frequency of Use) göre seçmelisin.

---

## 🧮 Unit Economics: Batışın Matematiği

Bakkal hesabı yapmadan kod yazarsan, büyüdükçe batarsın.

**Basit Formül:**
`Kar = (Müşteri Başına Gelir) - (Müşteri Başına Maliyet)`

Örnek (SilentCut.io):
* **Sunucu Maliyeti (GPU):** 1 saatlik video işlemek $0.50
* **Storage/Bandwidth:** $0.10
* **Toplam Maliyet (COGS):** $0.60

Eğer sen bu işlemi kullanıcıya **$0.50'ye satarsan**, her satışta **$0.10 zarar edersin.**
*"Sürümden kazanırız"* dersen, çok satarsan çok batarsın.

> **Kural:** Maliyetini bilmeyen, fiyatını belirleyemez.

---

## 🧠 Fiyatlandırma Psikolojisi: "Kaç Para?" vs "Değer Mi?"

Fiyatlandırma teknik bir hesaplama değil, **algı yönetimidir.**

**Yanlış Bakış:**
"Ben bu kodu yazmak için 100 saat harcadım, o yüzden pahalı olmalı." (Kullanıcının umurunda değil.)

**Doğru Bakış (Value-Based Pricing):**
"Bu yazılım senin 5 saatini kurtarıyor. Senin saatin $50 ise, ben sana $250 kazandırıyorum. O zaman bu ürün $30 eder."

### Fiyat Merdiveni (The Ladder)
Tek bir fiyat koyma. İnsanlara seçenek sunarak yönlendir.

1.  **Anchor (Çapa):** Pahalı Paket ($99). (Diğerlerinin ucuz görünmesini sağlar.)
2.  **Target (Hedef):** Satmak istediğin Paket ($29). "En Popüler" etiketi buradadır.
3.  **Entry (Giriş):** Deneme Paketi ($9).

---

## ⚡️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] İş Modelini Seç
Abonelik mi? Kredi sistemi mi? Tek seferlik mi? Karar ver ve nedenini bir cümleye yaz.
* *Örnek: "Benim ürünüm Usage-Based olacak çünkü kullanıcılar sadece proje bazlı ihtiyaç duyuyor."*

### 2. [ ] Bakkal Hesabı (Napkin Math)
* 1 Kullanıcı sana kaça mal oluyor? (Sunucu, API, vb.)
* Başabaş noktası (Break-even) için fiyat en az kaç olmalı?

### 3. [ ] "Pricing Table" Taslağı
Kağıt kalemi al, 3 kolon çiz:
* **Plan A:** (Giriş seviyesi - kısıtlı özellik)
* **Plan B:** (Ana hedef - full özellik)
* **Plan C:** (Ajans/Pro - toplu alım vs.)
Her birine bir fiyat etiketi yapıştır.

---

## ⛔️ Yasaklı Düşünceler (Anti-Patterns)

* **"Rakipten ucuz olayım yeter."** -> Kendini "kalitesiz" olarak konumlandırırsın. Fiyat rekabeti, dibe doğru bir yarıştır.
* **"Bedava vereyim, sonra reklam alırım."** -> Facebook değilsen bunu unut.
* **"Herkes için tek fiyat."** -> Kurumsal firmadan alacağın $500 ile öğrencinin vereceği $5 aynı kasaya girmez. Segmentlere ayır.

---

## 🔜 Gelecek Hafta: Marka, UX & Güven İnşası

Haftaya ürünü "güzelleştireceğiz" ama süs olsun diye değil, **güven** versin diye:
* İnsanlar kredi kartını neden tanımadıkları bir siteye girsin?
* "UI önemli değil, backend sağlam" yalanı.
* SilentCut.io'ta güven sinyalleri (Trust Signals) nasıl kurgulandı?

---
*Developer to Founder - Week 03*
