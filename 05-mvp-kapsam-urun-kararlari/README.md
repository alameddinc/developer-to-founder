# 05 – MVP Kapsamı & Ürün Kararları  
## En Az Ürün Değil, En Az Risk

Bu haftanın amacı:
> **En az kodu yazmak değil,  
> en büyük belirsizlikleri en erken test etmek.**

MVP:
- “Küçük ürün” değildir
- “Eksik ürün” değildir
- “Çirkin ama çalışıyor” hiç değildir

> **MVP = Yanlış ürünü yapma riskini azaltan ilk çalışan versiyon**

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- MVP’nin ne olduğunu **doğru tanımıyla** kavrayacak
- “MVP’ye ne girer?” sorusuna **profesyonel yöntemlerle** cevap verebilecek
- Özellik tartışmalarını veriyle bitirecek
- Teknik borcu **bilinçli şekilde** almayı öğrenecek
- “Hızlı MVP için Next.js mi, sonra Go/React mı?” sorusuna net bakabilecek
- Rewrite korkusu olmadan ilerleyebilecek

---

## 🧠 En yaygın MVP yanılgıları

❌ “MVP = az özellik”  
❌ “MVP = herkes için ürün”  
❌ “MVP’de kalite önemli değil”  
❌ “Bunu sonra ekleriz”  

Gerçek:
> Yanlış MVP,  
> doğru fikri bile öldürür.

---

## 🧩 MVP’nin GERÇEK amacı (3 temel soru)

Her MVP şu üç sorudan **en az birini** net test etmelidir:

1️⃣ **Bu problem gerçekten var mı?**  
2️⃣ **İnsanlar bu çözümü gerçekten kullanıyor mu?**  
3️⃣ **Para vermeye niyetli mi?**

Bu sorulardan hiçbiri test edilmiyorsa:
> O şey MVP değildir.

---

# 🧠 Profesyoneller MVP kararını nasıl veriyor?

Bu bölüm, ekiplerin en çok takıldığı soruya cevap verir:
> “Ne MVP’ye girer, ne girmez?”

---

## 1️⃣ Risk-First MVP (Profesyonel yaklaşım)

Profesyoneller MVP’yi **özellik listesi** gibi yapmaz.  
Önce **en büyük riskleri** çıkarır.

### Tipik risk kategorileri
- **Değer riski:** Kullanıcı gerçekten istiyor mu?
- **Kullanılabilirlik riski:** Kullanıcı kullanabiliyor mu?
- **Ödeme riski:** Para vermeye niyetli mi?
- **Teknik risk:** Bu gerçekten çalışıyor mu?
- **Operasyon riski:** Ben bunu sürdürebiliyor muyum?

> MVP’ye giren şey:  
> **Bu risklerden birini doğrudan test eden en küçük parça**

---

## 2️⃣ Walking Skeleton (Çalışan iskelet)

Profesyoneller MVP’yi:
- “Tam ürün” diye değil
- **Uçtan uca çalışan en küçük iskelet** olarak kurar

Örnek:
- Kullanıcı gelir
- Tek bir ana işi yapar
- Net bir sonuç alır

Bu zincir çalışıyorsa:
- MVP vardır

Bu zincir yoksa:
- Elindeki şey demo olabilir

---

## 3️⃣ One Metric MVP (Tek metrik odak)

MVP’nin başarısı:
- “Beğenildi mi?” değildir

Profesyoneller **tek bir ana metrik** seçer:

Örnek:
- Upload yapanların % kaçı işlemi başlatıyor?
- İşlem başlatanların % kaçı sonucu indiriyor?
- Fiyat ekranını görenlerin % kaçı ödeme yapıyor?

> MVP’ye giren şeyler =  
> bu metriği hareket ettirenler

---

## 4️⃣ MoSCoW yöntemi (ekipleri sakinleştirir)

Her özellik şu gruplardan birine girer:

- **Must-have:** olmazsa ürün çalışmıyor
- **Should-have:** olmazsa olur ama can yakar
- **Could-have:** güzel olur
- **Won’t-have (şimdilik):** bilinçli yok

> MVP = Must-have + çok az Should-have

---

## 5️⃣ Feature → Job-to-be-Done çevirisi

Biri “şu feature da olsun” dediğinde sor:

> “Kullanıcı bu feature ile hangi işi bitiriyor?”

Cevap net değilse:
- Feature MVP dışı

Örnek:
- “Dashboard olsun” → Hangi iş? → Belirsiz → ❌
- “Sonucu indir” → İş: çıktı almak → ✅

---

## 🧪 SilentCut Case Study – MVP’de BİLİNÇLİ OLARAK OLMAYANLAR

İlk MVP’de olmayanlar:
- Kullanıcı hesapları
- Abonelik sistemi
- Dashboard
- Gelişmiş ayarlar
- Bildirimler

Neden?
> Test edilen risk şuydu:  
> “Bu işi otomatik yapmak gerçekten değerli mi?”

---

## ⚖️ MVP Kapsamı Nasıl Belirlenir? (Net kural)

Her özellik için sor:

> “Bu özellik olmazsa,  
> ana risk yine de test edilir mi?”

- **Evet** → MVP dışı
- **Hayır** → MVP içi

---

## 🧱 Kill List (Öldürülen Özellikler)

MVP süreci:
> Özellik ekleme değil,  
> **özellik öldürme** sürecidir.

Tipik kill list:
- Dark mode
- Çoklu dil
- Profil sayfası
- Sosyal özellikler
- Bildirim sistemi

Hepsi güzel ama:
> **Bu hafta değil.**

---

# 🧠 Teknik borç: Nerede alınır, nerede ALINMAZ?

### ✅ Alınabilir teknik borç
- UI geçici çözümler
- Hard-coded ayarlar
- Manuel süreçler
- Basit pipeline

### ❌ Alınmaması gereken teknik borç
- Veri modeli
- Güvenlik
- Geri dönülemez mimari kararlar
- Vendor lock-in

> MVP hız demektir,  
> ama geleceği yakmak değildir.

---

## 🧪 SilentCut – Bilinçli teknik borç örneği

Alınan:
- Manuel işlem
- Basit job akışı

Alınmayan:
- Dosya güvenliği
- Veri kaybı riski
- Geri dönülemez altyapı

---

# 🧠 MVP Stack’i vs Ürün Stack’i

Bu soru **çok sorulacak**, net cevaplayalım.

---

## “Hızlı MVP için Next.js ile çıkalım mı?”

**Çoğu solo founder için: EVET.**

Neden?
- Tek repo
- Hızlı iterasyon
- Landing + ürün birlikte
- Deploy kolay

Ama şartla:
> **Geri dönülemez karar alma.**

---

## “Sonra Go + React’a geçmek zorunda mıyız?”

Hayır. Zorunluluk yok.

### Geçmek için iyi sebepler
- Trafik çok arttı
- Ağır background job ihtiyacı
- Takım büyüdü
- Performans / maliyet avantajı net
- Güvenlik / izolasyon ihtiyacı

### Geçmek için kötü sebepler
- “Go daha cool”
- “Mimari mükemmel olsun”
- “Rakip böyle yapmış”

---

## Profesyoneller stack değişimini nasıl yapıyor?

### Strangler Fig Pattern
- Rewrite yok
- Parça parça taşıma

Örnek:
- Önce tek bir endpoint’i ayır
- Zamanla kritik yolları taşı
- Monoliti küçült

> Rewrite = yüksek risk  
> Strangler = kontrollü evrim

---

## MVP stack seçimi için 5 pratik soru

1. 2–4 haftada canlıya çıkabilir miyim?
2. Debug kolay mı?
3. Deploy kolay mı?
4. Maliyeti tahmin edebiliyor muyum?
5. Kilitlenme yaratıyor mu?

Çoğu “evet” ise:
> Stack yeterince iyi.

---

## 🛠️ Bu haftanın görevleri

### 1️⃣ Ana riski yaz
> “Bu MVP ile test ettiğim ana risk: …”

---

### 2️⃣ MVP kapsamını yaz
İki liste:

**VAR**
- Olmazsa olmazlar

**YOK**
- Bilinçli olarak eklenmeyenler

---

### 3️⃣ Teknik borç kararlarını yaz
- Ne geçici?
- Ne zaman düzelecek?

---

### 4️⃣ MVP karar tablosu (çok işe yarar)

| Özellik | Test edilen risk | MVP metriğine etkisi | Alternatif ucuz yol | Karar |
|-------|------------------|---------------------|---------------------|-------|

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Net MVP tanımı
- Kill list
- Test edilen riskler
- Bilinçli teknik borç listesi
- Stack kararlarının gerekçesi

olmalı.

---

## ⚠️ Son uyarı

MVP sonrası şu cümle çok gelecek:
> “Bir de şunu ekleyelim…”

Diren.

Çünkü:
> MVP,  
> odaklanma disiplinidir.

---

## 🔜 Sonraki hafta

**06 – Teknik Mimari & Teknoloji Seçimi**

- Monolit vs mikroservis
- Erken mimari hatalar
- Vendor lock-in tuzakları
- SilentCut altyapı kararları

---

> **Son söz:**  
> MVP hızlı yapılır.  
> Ama rastgele yapılmaz.
