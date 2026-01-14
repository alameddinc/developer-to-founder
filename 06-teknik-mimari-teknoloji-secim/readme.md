# 06 – Teknik Mimari & Teknoloji Seçimi  
## Doğru Dil Değil, Doğru İnsan + Doğru Zaman

Bu haftanın amacı:
> **Teknoloji seçimini trend, popülerlik veya “ileride lazım olur” korkusu ile değil,  
> ekip (veya sen) gerçekliği üzerinden yapmak.**

Profesyonel gerçek:
> Ürünler stack yüzünden değil,  
> **yanlış hız ve yanlış karar yüzünden** ölür.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- “Go ile başlamak mantıksız mı?” sorusuna **net ve gerekçeli** cevap verebilecek
- Takım/skill fit kavramını anlayacak
- Mimariyi **insan kapasitesiyle** birlikte düşünecek
- Erken “bir daha baştan yazmayalım” refleksinin risklerini fark edecek
- Go, Node, Next.js gibi teknolojileri **amaç–zaman–risk** çerçevesinde konumlandıracak
- Vendor lock-in ve geri dönülemez kararları ayırt edebilecek

---

## 🧠 En yaygın ama anlaşılır refleks

> “Ben Go ile yazayım.  
> Eğer tutarsa devam etmem kolay olur,  
> tekrar sıfırdan başlamayayım.”

Bu refleks:
- Mantıksız **değil**
- Ama **tek başına yeterli gerekçe de değil**

Asıl soru şu olmalı:
> “Go ile başlamak, **bugün** bana hız mı kazandırıyor,  
> yoksa sadece **ileride rahat edeyim** diye bugün yavaşlatıyor mu?”

---

# 1️⃣ Takım / Skill Fit Nedir? (En kritik ama en az konuşulan konu)

### Skill fit = Şu an kim kod yazıyor?

- Solo founder mısın?
- 2–3 kişilik küçük ekip misin?
- Herkes full-stack mi, yoksa roller ayrık mı?

Teknik gerçek:
> En iyi teknoloji,  
> **ekibin en az zorlandığı teknolojidir.**

---

## 🧠 Profesyonel bakış: İnsan > Teknoloji

Şu iki senaryoyu karşılaştıralım:

### Senaryo A
- Go ile:
  - Daha az bug yazıyorsun
  - Daha net kod yazıyorsun
  - Production’da daha rahatsın
  - Debug seni yormuyor

Ama:
- UI/landing yavaş ilerliyor

### Senaryo B
- Next.js ile:
  - Landing + ürün çok hızlı çıkıyor
  - Ama backend tarafında:
    - “Sonra düzeltirim” dediğin borçlar birikiyor
    - Uzun vadede huzursuzluk var

Profesyonel karar:
> **Seni daha az yoran stack, genelde doğru stack’tir.**

---

## ⚠️ Ama kritik uyarı (burada çoğu kişi hata yapar)

“Ben Go biliyorum” ile  
“Ben Go ile **aynı hızda** MVP çıkarırım”  
aynı şey değildir.

Eğer Go ile:
- MVP 2–4 hafta yerine 2–3 ay sürecekse  
→ bu **risklidir**

Çünkü MVP aşamasında:
> En pahalı şey performans değil, **geç kalmaktır**.

---

# 2️⃣ Go ile başlamak NE ZAMAN mantıklı?

Aşağıdaki maddelerden **en az 3’ü net “evet” ise**, Go ile başlamak **tamamen rasyoneldir**:

1. Go ile web + API + job yazmak seni yavaşlatmıyor  
2. Ürün background job / queue / concurrency ağırlıklı  
3. Tek binary deploy ve düşük RAM senin için avantaj  
4. Debug, profiling ve production seni korkutmuyor  
5. “MVP sonrası rewrite” fikri seni psikolojik olarak yoruyor  

Bu durumda:
> Go senin için **erken optimizasyon değil**,  
> **erken huzur** sağlar.

---

# 3️⃣ Go ile başlamak NE ZAMAN riskli?

Şu durumlarda risk artar:

- UI / landing / marketing sayfaları kritik ama Go ile yavaş
- Ürün hâlâ ciddi pivot ihtimali taşıyor
- Kullanıcı geri bildirimi için hızlı A/B denemeler gerekiyor
- “Her şeyi düzgün yapayım” refleksi ağır basıyor

Burada risk:
> “Bir daha baştan yazmayayım” diye  
> **ilk seferde geç çıkmak**

---

# 4️⃣ Profesyonel denge modeli (çok kullanılan)

Birçok deneyimli founder şu modeli kullanır:

### 🎯 Çekirdek iş mantığı (core)
- Go
- Modüler monolit
- Uzun ömürlü
- “Bir daha yazmak istemediğin” kısım

### 🎨 Deney & iterasyon katmanı
- Next.js / React
- Landing
- UX denemeleri
- A/B testleri

Bu modelde:
- “Sıfırdan başlamıyorsun”
- Ama “her şeyi baştan Go ile yapmak zorunda da kalmıyorsun”

> Profesyoneller “tek doğru stack” değil,  
> **doğru sınırlar** kurar.

---

# 5️⃣ “Sonra Go + React’a geçmek zorunda mıyım?” sorusu

Hayır.  
“Zorunda” değilsin.

Geçmek için **iyi sebepler**:
- Trafik ciddi arttı
- Background processing büyüdü
- Takım genişledi
- Performans / maliyet farkı netleşti
- Güvenlik / izolasyon ihtiyacı arttı

Geçmek için **kötü sebepler**:
- “Go daha cool”
- “Başta yanlış yaptık hissi”
- “Rakip böyle”

> Stack değişimi bir **teknoloji kararı değil**,  
> **ürün olgunluk kararıdır**.

---

# 6️⃣ Mimariyi “geri dönülebilir” kurmak (asıl ustalık)

Go ile başlasan bile şunları yap:

- Modüler yapı (package sınırları net)
- Interface’ler üzerinden bağımlılık
- Storage / queue / mail soyutlaması
- İş mantığını framework’e gömmeme

Bunları yaparsan:
- Rewrite değil
- **Evrim** yaparsın

---

# 7️⃣ Profesyonel karar soruları (kendine sor)

Aşağıdakileri yazılı cevapla:

1. Bu projede beni en çok yoran şey ne?
2. Hangi stack’te daha az mental yüküm var?
3. MVP’ye 1 ay geç çıkmak bana ne kaybettirir?
4. Rewrite ihtimali mi, geç çıkma ihtimali mi daha korkutucu?
5. Bu projeyi 6 ay sonra hâlâ ben mi taşıyacağım?

Cevaplar:
> Stack kararını zaten söylüyor.

---

# 🧪 SilentCut bağlamında düşünürsek

SilentCut gibi ürünlerde:
- İşin zor kısmı UI değil
- **Processing pipeline**
- **Queue**
- **Maliyet kontrolü**

Bu yüzden:
- Core Go olması çok mantıklı
- UI katmanı ayrı ve hızlı evrilebilir olabilir

---

## 🛠️ Bu haftanın görevleri (güncellenmiş)

### 1️⃣ Skill fit değerlendirmesi yaz
- Ben hangi stack’te daha üretkenim?
- Nerede yavaşlıyorum?

---

### 2️⃣ Mimari karar cümlesi yaz
> “Bu aşamada X stack’ini seçiyorum çünkü …  
> Şu sinyaller gelirse tekrar değerlendiririm: …”

---

### 3️⃣ Geri dönülemez karar listesi
Bu hafta **bilinçli olarak almadığın** kararlar:
- Mikroservis
- Kubernetes
- Cloud’a gömülü iş mantığı
- Gereksiz soyutlama

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Stack kararının gerekçesi
- Skill fit analizi
- Mimari sınırlar
- Yeniden değerlendirme kriterleri

olmalı.

---

## ⚠️ Son uyarı

> En iyi teknoloji,  
> seni **en uzun süre yormayan** teknolojidir.

---

## 🔜 Sonraki hafta

**07 – Altyapı, Hosting & Vendor Lock-in Yönetimi**

- VPS vs PaaS vs Serverless
- CI/CD ile altyapı ilişkisi
- Storage / DB / Queue seçimleri
- Lock-in’i pratikte azaltmak

---
