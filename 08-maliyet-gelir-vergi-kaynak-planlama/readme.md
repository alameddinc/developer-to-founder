---
description: https://github.com/alameddinc/developer-to-founder
---

# 08 – Unit Economics & Finance: "100 TL Kazandım" Yanılgısı

> **Haftanın Mottosu:** "Ciro (Revenue) egodur, Kâr (Profit) gerçektir. Cebine girmeyen para, senin paran değildir."

{% embed url="https://open.spotify.com/episode/5MW3FafKUbm4EQlBN8TS1k?si=V2pWbEinSjaJotHItdXd-g" %}

Bu haftanın amacı muhasebeci olmak değil; muhasebecin seni uyarmadan önce batıp batmadığını anlamaktır. Çoğu indie hacker şu hatayı yapar: Sunucu maliyetini hesaplar, üzerine %20 ekler ve "Kâr ettim" sanır. Oysa vergi, komisyon, iade ve kur farkı o %20'yi çoktan yemiştir.

***

### 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:

* [ ] **"Net Profit"** ile **"Gross Revenue"** arasındaki uçurumu hesaplayabileceksin.
* [ ] Türkiye'de şirket kurmak vs. Yurt dışı (Stripe Atlas/Estonya) arasındaki farkı gerçekçi bir gözle göreceksin.
* [ ] **Merchant of Record (MoR)** kavramını (Paddle/Lemon Squeezy) ve neden solo founder için kritik olduğunu anlayacaksın.
* [ ] Bir kullanıcının sana maliyetini (COGS) kuruşu kuruşuna çıkarabileceksin.

***

## 1️⃣ The "100 TL Illusion": Para Nereye Gidiyor?

Bir kullanıcı sana 100 TL ödediğinde, zengin olduğunu sanabilirsin. Gel bu parayı "Waterfall" (Şelale) yöntemiyle eritelim.

_Senaryo: Türkiye'de yaşayan bir müşteriye 100 TL'lik satış yaptın._

| Adım                  | İşlem       | Kalan Tutar   | Açıklama                                                     |
| --------------------- | ----------- | ------------- | ------------------------------------------------------------ |
| **1. Satış**          | + 100.00 TL | **100.00 TL** | Müşterinin kredi kartından çekilen tutar.                    |
| **2. KDV (VAT)**      | - 16.67 TL  | **83.33 TL**  | Devletin payı (%20). Bu para senin hiç olmadı.               |
| **3. Komisyon**       | - 19.00 TL  | **64.33 TL**  | Ödeme altyapısı (Paddle/Stripe) + İşlem ücreti + Kur makası. |
| **4. Maliyet (COGS)** | - 12.00 TL  | **52.33 TL**  | Sunucu, API, Storage. (Ürünü çalıştırma maliyeti).           |
| **5. Gelir Vergisi**  | - 15.70 TL  | **36.63 TL**  | Şirket kârı üzerinden devlete ödenen vergi (Ort. %30 bandı). |
| **SONUÇ**             | **NET KÂR** | **36.63 TL**  | **Cebine giren gerçek para.**                                |

> **Acı Gerçek:** 100 TL ciro yaptığında aslında sadece **36 TL** kazandın. Eğer fiyatını buna göre belirlemezsen, ölçeklendikçe batarsın.

***

## 2️⃣ Maliyet Türleri: Neyi Hesaba Katmalısın?

Maliyet sadece AWS faturası değildir.

#### 1. COGS (Cost of Goods Sold) - Ürünün Maliyeti

Her yeni kullanıcı geldiğinde artan maliyetlerdir.

* Sunucu (CPU/RAM).
* Storage (S3/R2).
* API Kullanımı (OpenAI, Replicate vb.).
* _Bu maliyet, satış fiyatının %20-30'unu geçmemelidir._

#### 2. OpEx (Operational Expenses) - Dükkanın Maliyeti

Hiç satış yapmasan bile ödediğin paralar.

* Domain, Email servisi.
* Şirket muhasebe ücreti.
* Kendi maaşın (Evet, bunu da maliyet yazmalısın).

***

## 2.1 – Sunucu Maliyeti Satış Başına Nasıl Bölünür? (Kapasite Hesabı)

Burada yapılan en büyük hata şudur: _"Ayda 20$ sunucu parası veriyorum. Bu ay 1 müşteri geldi. O zaman müşterinin bana maliyeti 20$."_ **YANLIŞ.** Bu hesapla ürünün asla kârlı görünmez.

**Profesyonel Hesap Yöntemi: "Utilization Rate" (Kapasite Oranı)**

Sabit maliyetler (VPS, DB), **mevcut** kullanıcıya değil, **hedeflenen** kullanıcıya bölünür.

**Adım 1: Kapasiteni Belirle** Kiraladığın o 20$'lık sunucu, çökmeden kaç kullanıcıyı (veya işlemi) kaldırır? _Örnek: Sunucum ayda 1.000 video işleyebilir._

**Adım 2: Birim Maliyeti Bul** `Maliyet / Kapasite = Birim Başı Sabit Gider` _Örnek: 20$ / 1.000 Video = **0.02$** (Video başı sunucu maliyeti)_

**Sonuç:** Senin birim maliyetin **0.02$**'dır. Eğer sunucun boş duruyorsa, o 19.98$'lık fark "Ürün Maliyeti" değil, senin \*\*"Büyüme Maliyeti"\*\*n (Idle Cost) olur. Fiyatlandırmanı 0.02$'a göre yapmalısın, yoksa fiyatın şişer ve satamazsın.

> **Kural:** Maliyeti hesaplarken "Bugünkü 1 kullanıcıya" göre değil, "Başabaş noktası olan 100. kullanıcıya" göre hesap yap.

***

## 3️⃣ Şirketleşme: Ne Zaman ve Nerede?

Kod yazmak kolay, şirket kurmak karmaşıktır. İşte yazılımcı diliyle seçenekler:

### 🇹🇷 Seçenek A: Şahıs Şirketi (Solo Dev Başlangıç Paketi)

* **Kurulum:** 1 günde, e-devlet üzerinden. Çok ucuz.
* **Vergi:** Artan oranlı (%15 - %40). Çok kazanırsan devlet ortağın olur.
* **Kime Uygun?** MVP aşamasında, aylık geliri asgari ücretin 2-3 katını geçmeyenler için.

### 🇹🇷 Seçenek B: Limited / A.Ş. (Scale-Up Paketi)

* **Kurulum:** Pahalı ve bürokratik. Kapatmak çok zor.
* **Vergi:** Sabit Kurumlar Vergisi (%25). Gider gösterme imkanı geniş.
* **Kime Uygun?** Yatırım alacaklar veya düzenli yüksek gelir (aylık 100k+ TL) elde edenler için.

### 🇺🇸/🇪🇪 Seçenek C: Yurt Dışı (Stripe Atlas / Estonya)

* **Avantaj:** Stripe/PayPal kullanabilmek. Global prestij.
* **Risk:** Türkiye'de yaşıyorsan "Vergi Mukimliği" sorunu. Türkiye, "Burada yaşıyorsan vergini buraya ver" der. Çifte vergilendirme riski vardır.
* **Kime Uygun?** Gelirin %99'u yurt dışından geliyorsa ve iyi bir mali müşavirin varsa.

> **💡 Stripe Atlas Alternatifi:** Stripe Atlas ($500) yerine [LLC Class](https://llcclass.com/wyoming) gibi hizmetler Wyoming LLC kurulumunu $199'dan sunuyor. Registered agent, EIN ve operating agreement dahil — Stripe ve Mercury'e bağlanmak için gereken her şey tek pakette. [Registered agent nedir?](https://llcclass.com/what-is-llc-registered-agent)

> **Altın Kural:** İlk satışı yapmadan şirket kurma. Fatura kesmek zorunda kaldığın gün, şirket kurmak için en doğru gündür.

***

## 4️⃣ Merchant of Record (MoR) Nedir?

Solo founder için en büyük kurtarıcı: **Paddle** veya **Lemon Squeezy**.

Normalde (Stripe/Iyzico kullanırsan):

* Almanya'ya satarsan Almanya KDV'sini hesapla.
* ABD'ye satarsan eyalet vergisini hesapla.
* Bunları topla ve ilgili devletlere öde. (İMKANSIZ).

**MoR (Paddle/Lemon Squeezy) kullanırsan:**

* Onlar senin adına satar.
* Tüm vergileri onlar toplar ve öder.
* Sana ay sonunda tek bir "Hizmet Bedeli" faturası keser ve paranı yatar.
* **Komisyon:** Biraz yüksektir (%5 + 50¢) ama seni hapse girmekten veya muhasebe cehenneminden kurtarır.

***

## 5️⃣ Unit Economics & Pricing (Fiyatlandırma)

SilentCut.io örneği üzerinden gidelim.

**Senaryo:** Aylık $9 sabit abonelik. Sınırsız video işleme. **Risk:** Bir kullanıcı geldi, 50 tane 4K video yükledi.

* Sunucu maliyeti: $15
* Gelir: $9
* **Zarar:** -$6

**Çözüm:** Kullanım Bazlı Fiyatlandırma (Usage-Based) veya Kredi Sistemi.

* Kullanıcı 1 saatlik kredi alır ($10).
* Maliyetin bellidir ($2).
* Karın garantidir ($8).

> **Ders:** Maliyetin "Variable" (değişken) ise, fiyatın "Fixed" (sabit) olamaz. Batarsın.

***

## ⚡️ Haftalık Görevler (Commitment Checklist)

#### 1. \[ ] "Gerçek 100 TL" Tablonu Yap

Yukarıdaki tabloyu kendi ürünün için doldur.

* Komisyon oranın ne?
* Ortalama sunucu maliyetin ne?
* Eline net ne kalıyor?

#### 2. \[ ] Başabaş Noktası (Break-even) Hesabı

* Aylık sabit giderin (muhasebe + araçlar) ne kadar? (Örn: 5.000 TL)
* Ürün başı net kârın ne kadar? (Örn: 36 TL)
* 5000 / 36 = **138 Müşteri.**
* _Soru: İlk ay 138 müşteri bulabilir misin? Bulamazsan cepten yiyeceksin._

#### 3. \[ ] "MoR" Araştırması

Paddle ve Lemon Squeezy'yi incele. Türkiye'den kabul ediyorlar mı? Komisyonları ne? Senin iş modeline (Abonelik vs Tek Seferlik) uygun mu?

***

## ⛔️ Yasaklı Düşünceler (Anti-Patterns)

* **"Vergi vermesem olur mu?"** -> Olmaz. Devlet her zaman kazanır.
* **"Fiyatı düşük tutayım, sürümden kazanırım."** -> Sürümden kazanmak için Walmart olman lazım. Sen butiksin, kâr odaklı olmalısın.
* **"Şirketi kurayım, ürün sonra biter."** -> Her ay boş beyanname damga vergisi öderken motivasyonun biter. Önce satış, sonra şirket.

***

### 🔜 Gelecek Hafta: Proje Yönetimi & Disiplin

Para işlerini hallettik. Peki bu işleri nasıl takip edeceğiz?

* Jira mı, Trello mu, Notion mı?
* Git branch stratejisi.
* "Founder Mode"da kendi kendini yönetmek.

***

_Developer to Founder - Week 08_
