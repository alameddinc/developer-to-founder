# 08 – Maliyet, Gelir, Vergi & Kaynak Planlama  
## “Kazandım” Sanmak ile “Gerçekten Kazanmak” Arasındaki Fark

Bu haftanın amacı:
> **Ürünün sadece çalışıp çalışmadığını değil,  
> para kazandırıp kazandırmadığını anlamak.**

Birçok SaaS:
- Satış yapar
- Kullanıcı bulur
- Para alır  

ama:
> Vergi, komisyon, altyapı ve operasyon sonrası  
> **negatif kârla** çalışır.

Bu hafta:
- “100 TL sattım” ≠ “100 TL kazandım” gerçeğini netleştiriyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Bir satıştan **eline gerçekten ne kaldığını** hesaplayabilecek
- Gelirden düşen maliyetleri bilecek
- Vergi öncesi / vergi sonrası kâr farkını anlayacak
- Şirket kurmadan önce & sonra tabloyu görebilecek
- Türkiye vs yurt dışı şirket farklarını kavrayacak
- “Ne zaman şirket kurmalıyım?” sorusuna net cevap verecek

---

# 1️⃣ Maliyet türleri (kısa hatırlatma)

## 1. Saf (pure) ürün maliyetleri
- Compute (CPU / GPU)
- Storage
- Bandwidth
- Queue / background job
- API maliyetleri

## 2. Operasyonel maliyetler
- Monitoring / logging
- Email / SMS
- Destek süresi
- Domain / sertifika
- SaaS tool’ları

## 3. Gelirden düşen maliyetler (EN ÇOK ATLANAN)
- Ödeme sağlayıcı komisyonu
- Platform fee (marketplace)
- Chargeback / iade
- Döviz dönüşüm farkları

---

# 2️⃣ “100 TL sattım” gerçeği – adım adım hesap

Şimdi senin verdiğin örneği **doğru ve gerçekçi** şekilde yapalım.

> Varsayım:  
> Türkiye’de yaşayan bir kullanıcıdan **100 TL’lik SaaS token satışı**

---

## 1️⃣ KDV (Türkiye – %20)

- Brüt fiyat: **100 TL**
- KDV (%20): **16,67 TL**
- Net gelir (KDV hariç): **83,33 TL**

> KDV senin gelirin değildir.  
> Devlet adına tahsil edilir.

---

## 2️⃣ Ödeme sağlayıcı (Paddle örneği)

Paddle (ortalama):
- %5 komisyon
- + 0.5 USD işlem başı

Varsayım:
- Kur: 30 TL
- 0.5 USD ≈ 15 TL

Hesap:
- %5 → 4,17 TL
- Sabit ücret → 15 TL

**Toplam kesinti:** ~19 TL

Kalan:
- **83,33 – 19 ≈ 64 TL**

---

## 3️⃣ Ürün maliyeti (örnek)

Diyelim ki bu kullanıcı:
- Compute + storage + bandwidth = **12 TL**

Kalan:
- **64 – 12 = 52 TL**

---

## 4️⃣ Vergi (şirket YOK, bireysel gelir gibi düşünürsek)

Eğer şirket yoksa:
- Bu gelir **ticari gelir** sayılır
- %15–40 arası gelir vergisine girer (kademeli)

Basit ve muhafazakâr düşünelim:
- %30 efektif vergi

Vergi:
- **~16 TL**

Kalan:
- **~36 TL**

---

## 📌 Özet tablo

| Aşama | Tutar (TL) |
|----|-----------|
| Kullanıcı ödedi | 100 |
| KDV çıktı | -16,7 |
| Paddle | -19 |
| Ürün maliyeti | -12 |
| Vergi | -16 |
| **Gerçek kazanç** | **~36 TL** |

> 100 TL satış → **36 TL gerçek kazanç**

Bu oranı bilmiyorsan:
> Fiyatlandırma da, büyüme de **kör** olur.

---

# 3️⃣ Şirket kurulursa ne değişir?

İşte oyunu değiştiren nokta burası 👇

## ✅ Şirket varken avantajlar

### 1️⃣ Gider yazabilirsin
- Server
- Tool’lar
- Domain
- Ofis / internet (kısmen)
- Danışmanlık
- Reklam

Bu giderler:
> **Vergi matrahını düşürür**

---

### 2️⃣ Kurumlar vergisi (Türkiye)
- %25 (2025 itibarıyla)

Ama:
- Giderler düştükten sonra

Örnek:
- 52 TL kâr vardı
- 20 TL gider yazdın

Vergi:
- (52–20) × %25 = **8 TL**

Net:
- **~44 TL**

> Şirket → bireyden **daha avantajlı** hale gelir

---

### 3️⃣ KDV dengeleme
- Giderlerde ödediğin KDV
- Aldığın KDV’den düşülür

Bu da ciddi avantajdır.

---

# 4️⃣ Türkiye’de şirket türleri (kısa ama net)

## 1️⃣ Şahıs Şirketi
**Avantaj**
- Hızlı kurulur
- Ucuz
- Muhasebe kolay

**Dezavantaj**
- Gelir vergisi kademeli (%15–40)
- Büyüdükçe pahalılaşır
- Algısal olarak “küçük”

**Ne zaman uygun?**
- MVP
- Düşük gelir
- Hızlı başlamak

---

## 2️⃣ Limited Şirket
**Avantaj**
- Kurumlar vergisi (%25)
- Gider yazma geniş
- B2B için güvenilir

**Dezavantaj**
- Kuruluş & muhasebe maliyeti
- Kapanışı zor

**Ne zaman uygun?**
- Düzenli gelir başladıysa
- Aylık anlamlı ciro varsa

---

## 3️⃣ Anonim Şirket
**Avantaj**
- Yatırım alma
- Hisse devri kolay
- Prestij

**Dezavantaj**
- En pahalı yapı
- MVP için ağır

**Ne zaman?**
- Yatırım hedefi varsa

---

# 5️⃣ Yurt dışında şirket (Stripe Atlas, Estonya vb.)

## Avantajlar
- Global ödeme kolay
- Vergi planlaması
- Uluslararası algı

## Dezavantajlar
- Hukuk / muhasebe karmaşıklığı
- Türkiye’de yaşıyorsan **vergi mukimliği riski**
- Çifte vergilendirme ihtimali

> Yurt dışı şirket:
> - Ürün global
> - Gelir ciddi
> - Hukuki danışmanlık varsa  
> **mantıklı**

“Sadece vergi az” diye erken girilirse:
> baş ağrıtır.

---

# 6️⃣ Ne zaman şirket kurmalıyım? (altın soru)

## ❌ Çok erken şirket kurma
- Ürün yokken
- Satış yokken
- Fikir aşamasında

→ Gereksiz masraf

---

## ✅ Doğru zaman sinyalleri
- Düzenli ödeme almaya başladıysan
- Fiyatlandırma oturuyorsa
- Giderleri yazma ihtiyacı oluştuysa
- Hukuki risk oluşuyorsa

> Çoğu SaaS için:
> **ilk satış → 1–3 ay içinde şirket**

makul bir çizgidir.

---

# 7️⃣ MVP için zorunlu finans tablosu

Her katılımcı şunu doldurmalı:

### A) Bir satıştan kalan
- Brüt fiyat
- KDV
- Platform kesintisi
- Ürün maliyeti
- Vergi (şirketli / şirketsiz)

### B) Aylık senaryolar
- 10 kullanıcı
- 100 kullanıcı
- 1000 kullanıcı

Her biri için:
> **Net kâr / zarar**

---

# 🛠️ Bu haftanın görevleri (güncellenmiş)

## 1️⃣ 1 satıştan eline kalan tutarı hesapla
- Varsayım bile olsa yaz

---

## 2️⃣ Şirketli vs şirketsiz karşılaştır
- Hangisi daha mantıklı?

---

## 3️⃣ Fiyatlandırma bu tabloya göre mantıklı mı?
- Gerekirse fiyatı revize et

---

## 4️⃣ “Bu ürün büyürse” finansal stres testi yap
- Nerede patlar?
- Nerede kazanır?

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Gerçek kâr hesabı
- Vergi farkındalığı
- Şirket kurma kararı için zemin
- Fiyatlandırma gerçekliği

olmalı.

---

## ⚠️ Son söz

> Para kazandığını sanan  
> ama hesap yapmayan founder  
> **en geç fark edendir**.

---

## 🔜 Sonraki hafta (9. Hafta)

**09 – Versiyon Kontrolü & Proje Yönetimi**

- Git stratejileri
- Branch modelleri
- Kendi kendini yöneten founder
- Teknik işlerin yarım kalmasını engelleme

---
