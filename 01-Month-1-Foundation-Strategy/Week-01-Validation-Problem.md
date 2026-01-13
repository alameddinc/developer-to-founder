# 📅 Hafta 1: Fikir Doğrulama ve Problem Keşfi

> **"Kimsenin istemediği şeyi mükemmel şekilde yapmak, hiçbir şey yapmamaktan daha kötüdür."**
> — **The Build Trap** (Melissa Perri)

---

## 🎯 Bu Haftanın Hedefleri

Kod yazmadan önce, **gerçek bir problemi** ve **bu problemi yaşayan insanları** bulmak. Çünkü mühendisler olarak en büyük yanılgımız şudur:

> *"Harika bir fikrim var, hemen kodlamaya başlayayım."*

Bu düşünce, sizi **The Build Trap**'e (İnşa Tuzağı) götürür. Ay sonunda elinizde kimsenin kullanmadığı mükemmel bir kod yığını olur.

### Bu haftanın sonunda elinizde olacaklar:
- ✅ **Doğrulanmış bir problem hipotezi** (Problem Statement)
- ✅ **Hedef kitlenizle yapılmış en az 10 müşteri görüşmesi** (Customer Interviews)
- ✅ **Pazar büyüklüğü tahmini** (TAM, SAM, SOM analizi)
- ✅ **Çözülmeye değer bir problem olduğuna dair kanıtlar**

---

## 🚨 Neden Validation Bu Kadar Kritik?

### Mühendislerin Düştüğü Klasik Tuzaklar:

#### 1️⃣ **"Ben bunu isterdim, o halde başkaları da ister."**
**Gerçek:** Kendi ihtiyaçlarınız, pazarın ihtiyaçlarını temsil etmeyebilir. Developer araçları yapıyorsanız, bu yaklaşım işe yarayabilir. Ancak farklı bir kitleniz varsa, **siz kullanıcınız değilsinizdir**.

**Örnek:** Dropbox kurucusu Drew Houston, kendi dosya senkronizasyon problemini çözdü. Ancak piyasaya sürmeden önce **yüzlerce kullanıcıyla görüştü** ve problem yaşadıklarını doğruladı.

#### 2️⃣ **"Teknoloji harika, elbette insanlar kullanır."**
**Gerçek:** Teknolojik mükemmeliyet ≠ Pazarlanabilir ürün. Google Wave teknik olarak muhteşemdi, ama kimse ne işe yaradığını anlamadı.

**Sonuç:** Ürün 2012'de kapatıldı.

#### 3️⃣ **"Lansman yapınca herkes gelir."**
**Gerçek:** "Build it and they will come" düşüncesi bir yanılsamadır. Lansman, sürecin başlangıcıdır, sonu değil.

---

## 📖 The Mom Test: Doğru Soruları Sormak

**The Mom Test** (Rob Fitzpatrick), müşteri görüşmelerinde **yanlış pozitif** sonuçlar almamak için geliştirilmiş bir yaklaşımdır.

### ❌ Yanlış Sorular (The Mom Test'i Geçemez):

| Yanlış Soru | Neden Yanlış? |
|-------------|---------------|
| *"Bu fikri beğenir misin?"* | İnsanlar incinmemek için "evet" der. Gerçek düşüncelerini almıyorsunuz. |
| *"Böyle bir ürün olsa kullanır mısın?"* | Hipoteze dayalı sorular güvenilmezdir. İnsanlar gelecekteki niyetlerini yanlış tahmin eder. |
| *"Bu özellik işine yarar mı?"* | Özellik odaklı sorular, gerçek problemi gizler. |

### ✅ Doğru Sorular (The Mom Test'i Geçer):

| Doğru Soru | Neden Doğru? |
|------------|--------------|
| *"Son bir ayda bu problemle ilgili yaşadığın somut bir örnek anlatır mısın?"* | **Geçmiş davranışlar** gelecek davranışların en iyi göstergesidir. |
| *"Şu anda bu problemi nasıl çözüyorsun?"* | Mevcut çözüm yolları, problem'in **ciddiyetini** gösterir. |
| *"Bu problemi çözmek için daha önce ne gibi şeyler denedin?"* | İnsanlar bir probleme **para/zaman harcamışsa**, o problem gerçektir. |
| *"Bu sorunun çözülmemesi sana ayda ne kadar zaman/para kaybettiriyor?"* | **Maliyet** sorusu, ödeme isteğini (willingness to pay) ortaya çıkarır. |

---

## 🔍 Problem Discovery: Gerçek Problemi Bulmak

Bir SaaS ürünü inşa ederken, **problem-solution fit** (problem-çözüm uyumu) olmadan hiçbir şey işe yaramaz.

### Problem Tespiti için 4 Aşamalı Framework:

#### **1. Problem Hipotezi Oluşturun**

> *"[Hedef Kitle] grubunun [Durum/Bağlam] sırasında yaşadığı [Problem], onların [Olumsuz Sonuç] ile karşılaşmasına neden oluyor."*

**Örnek:**
> *"Küçük SaaS şirketlerinin (1-10 kişi) müşteri destek taleplerini yönetirken yaşadığı dağınıklık, müşteri memnuniyetsizliğine ve churn'e (müşteri kaybı) yol açıyor."*

#### **2. Problem'in 3 Katmanını Keşfedin**

| Katman | Soru | Örnek |
|--------|------|-------|
| **Yüzey Problem** | İnsanların söyledikleri | *"E-postalar karışıyor."* |
| **Fonksiyonel Problem** | Gerçek ihtiyaç | *"Ekip olarak müşteri taleplerini takip edemiyoruz."* |
| **Duygusal Problem** | Asıl acı noktası | *"Müşteri kaybetmekten korkuyorum."* |

Duygusal problemler, **ödeme isteğini** (willingness to pay) tetikler.

#### **3. Problem Validation Metrikleri**

Bir problemin "çözülmeye değer" olduğunu anlamak için:

- **Frequency (Sıklık):** Bu problem ne sıklıkla yaşanıyor?
  → Günlük? Haftalık? Yıllık bir kez?

- **Severity (Şiddet):** Problem ne kadar acı verici?
  → Sadece rahatsız edici mi, yoksa işi durduruyor mu?

- **Willingness to Pay (Ödeme İsteği):** İnsanlar bu problemi çözmek için para harcıyor mu?
  → Mevcut bir çözüm (rakip, manuel süreç, freelancer) kullanıyorlarsa, problem gerçektir.

**Altın Kural:**
> *"Eğer insanlar bir probleme **şu anda** para/zaman harcıyorsa, o problem çözülmeye değerdir."*

#### **4. Early Adopter (Erken Benimseyenler) Segmentini Bulun**

İlk müşterileriniz, **herkes** olamaz. En acı çeken ve **en hızlı karar veren** segmenti hedefleyin.

**Örnek:**
- Genel Hedef: *"Tüm SaaS şirketleri"*
- Early Adopter: *"Ay başı 5-20 destek talebi alan, ekip olmadan tek başına çalışan SaaS founder'ları"*

---

## 📊 Pazar Araştırması: TAM, SAM, SOM Analizi

Bir mühendis olarak, **pazar büyüklüğünü** rakamlarla görmek istersiniz. İşte basit bir framework:

### TAM (Total Addressable Market) — Toplam Pazar
> *"Dünyada bu problemi yaşayan herkes benim ürünümü kullanırsa, ne kadar gelir elde ederim?"*

**Hesaplama:**
```
TAM = (Potansiyel Müşteri Sayısı) × (Yıllık Ödeme / Müşteri)
```

**Örnek:**
- Global SaaS şirket sayısı: **30,000**
- Ortalama yıllık ödeme: **$1,200**
- TAM = 30,000 × $1,200 = **$36M**

### SAM (Serviceable Addressable Market) — Erişilebilir Pazar
> *"Mevcut kaynaklarımla (dil, coğrafya, teknoloji) kimlere ulaşabilirim?"*

**Örnek:**
- Türkiye'deki SaaS şirketler: **500**
- SAM = 500 × $1,200 = **$600K**

### SOM (Serviceable Obtainable Market) — Elde Edilebilir Pazar
> *"İlk yıl gerçekçi olarak kaç müşteriyi kazanabilirim?"*

**Örnek:**
- İlk yıl hedef: **50 müşteri**
- SOM = 50 × $1,200 = **$60K** (MRR: $5K)

**Altın Kural:**
> *"SOM, ilk yılki gerçekçi hedefinizdir. SOM < $10K ise, ya fiyatlandırmanız düşük, ya da pazar çok küçük."*

---

## 🛠️ Bu Hafta Yapılacaklar (Actionable Checklist)

### **1. Problem Hipotezi Yazın (1-2 saat)**
- [ ] "[Hedef Kitle] [Durum] sırasında [Problem] yaşıyor" formatında bir cümle yazın.
- [ ] Bu problemin **sıklık, şiddet, ödeme isteği** metriklerini tahmin edin.

### **2. Hedef Kitleyi Tanımlayın (2-3 saat)**
- [ ] **Early Adopter** profilini çizin:
  - Demografik: Yaş, meslek, sektör?
  - Psikografik: Motivasyonları, korkuları neler?
  - Teknografik: Hangi araçları kullanıyorlar?

### **3. Minimum 10 Müşteri Görüşmesi Yapın (5-7 saat)**
- [ ] LinkedIn, Reddit, Twitter, Slack/Discord topluluklarında hedef kitlenizi bulun.
- [ ] **The Mom Test** prensiplerini kullanarak sorular hazırlayın.
- [ ] Görüşme notlarını kaydedin (Notion, Google Docs, vb.)

**İpucu:** Görüşmeleri kaydetmek için izin alın ve [Otter.ai](https://otter.ai) gibi araçlarla transkript alın.

### **4. Pazar Büyüklüğünü Hesaplayın (2-3 saat)**
- [ ] Google, Statista, Gartner raporları ile TAM/SAM tahminleri yapın.
- [ ] SOM için ilk yıl hedefini belirleyin.

### **5. Bulgularınızı Dokümante Edin (1-2 saat)**
- [ ] Görüşme özetlerini bir **Problem Validation Report** (PDF veya Notion sayfası) haline getirin.
- [ ] Şu soruları yanıtlayın:
  - Problem gerçek mi?
  - Pazar yeterince büyük mü?
  - İnsanlar ödemeye hazır mı?

---

## 🧰 Araçlar ve Kaynaklar

### **Müşteri Görüşmeleri için:**
- [Calendly](https://calendly.com) — Görüşme randevuları için.
- [Otter.ai](https://otter.ai) — Görüşmeleri transkript etmek için.
- [Typeform](https://typeform.com) — Ön anketler için.

### **Pazar Araştırması için:**
- [Statista](https://statista.com) — Sektör raporları.
- [Google Trends](https://trends.google.com) — Arama eğilimleri.
- [SimilarWeb](https://similarweb.com) — Rakip trafik analizi.

### **Okuma Listesi:**
- 📘 **The Mom Test** (Rob Fitzpatrick) — Müşteri görüşmelerinin İncil'i.
- 📘 **The Lean Startup** (Eric Ries) — Validation metodolojisi.
- 📘 **Crossing the Chasm** (Geoffrey Moore) — Early Adopter segmentasyonu.

---

## 🎓 Bu Haftanın Çıktıları

Hafta sonunda elinizde şunlar olmalı:

1. **Problem Statement Dökümanı**
   → "X grubunun Y durumunda yaşadığı Z problemi..."

2. **10 Müşteri Görüşmesi Özeti**
   → Her görüşmeden:
   - Problemin gerçek olduğuna dair kanıtlar.
   - Mevcut çözüm yolları (competitors veya manuel süreçler).
   - Ödeme isteği sinyalleri.

3. **TAM/SAM/SOM Analizi**
   → Pazar büyüklüğü rakamları ve kaynakları.

4. **Go / No-Go Kararı**
   → Bu problemi çözmeye değer mi?
   → Eğer "No" ise, **pivot** yapın. Eğer "Go" ise, Hafta 2'ye geçin.

---

## ⚠️ Yaygın Hatalar ve Nasıl Kaçınılır?

| Hata | Sonuç | Nasıl Kaçınılır? |
|------|-------|------------------|
| Sadece arkadaşlarla konuşmak | Yanlış pozitif feedback | Hedef kitlenizin olduğu forumlara, LinkedIn'e gidin. |
| "Fikir çalınır" korkusuyla kimseyle konuşmamak | Validation yapamama | Fikir değil, **execution** değerlidir. Paylaşın. |
| Görüşmelerde fikrinizi anlatmak | Bias (önyargı) yaratma | **Dinleyin**, anlatmayın. Sorular sorun. |
| 3-5 görüşme yapıp "yeterli" demek | Zayıf veri seti | Minimum 10 görüşme zorunlu. |

---

## 🚀 Bir Sonraki Adım: Hafta 2

Eğer bu haftanın sonunda **problem gerçek** ve **pazar yeterince büyük** ise, artık **Hedef Kitle (Audience)** ve **Rakip Analizi (Competitors)** safhasına geçebilirsiniz.

**Hafta 2'de:**
- Persona (İdeal müşteri profili) yaratımı.
- Rakip analizi (SWOT).
- Konumlandırma (Positioning) stratejisi.

---

**💡 Hatırlatma:**
> *"Mükemmel kodu yazmak kolaydır. Asıl zorluk, doğru problemi çözmektir."*

Kod yazmak için sabırsızlanıyorsanız, bu haftayı atlamayın. **Validation**, başarılı bir ürünün temel taşıdır.

---

**Hazırlayan:** Developer to Founder Playbook
**Lisans:** MIT
**Versiyon:** 1.0
**Güncellenme:** 2026-01-13
