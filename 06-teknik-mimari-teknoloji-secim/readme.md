# 06 – Tech Stack Strategy: Doğru Dil Değil, Doğru Zaman

> **Haftanın Mottosu:** "Startuplar yanlış teknoloji seçtikleri için değil, kimse ürünlerini kullanmadığı için ölürler. Stack seçimi bir ego savaşı değil, bir hayatta kalma stratejisidir."

Bu haftanın amacı; GitHub trendlerine, "Hype" trenlerine veya "Google böyle yapıyor" makalelerine bakarak değil; **kendi ekibinin (veya kendinin) kas hafızasına** bakarak karar vermektir.

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] "Go ile başlarsam yavaşlar mıyım, Node ile başlarsam ileride pişman olur muyum?" paradoksundan kurtulacaksın.
* [ ] **Skill/Market Fit** (Yetenek/Pazar Uyumu) kavramını anlayacaksın.
* [ ] "Rewrite" (Yeniden Yazım) korkusunun yersiz olduğunu ve **Strangler Fig** yöntemiyle nasıl evrimleşebileceğini göreceksin.
* [ ] Mimariyi "teknolojik mükemmellik" için değil, "mental huzur" için kurgulayacaksın.

---

## 🧠 Skill Fit: En İyi Stack, Senin En Hızlı Olduğun Stack'tir

Mühendisler teknolojiyi karşılaştırır (Go vs Node). Kurucular ise çıktıyı karşılaştırır (1 ay vs 3 ay).

### Senaryo Analizi: Hız mı, Huzur mu?

| Senaryo | Teknoloji | Avantaj (Pros) | Risk (Cons) | Psikoloji |
| :--- | :--- | :--- | :--- | :--- |
| **A (Hız Odaklı)** | **Next.js / Node** | UI ve Backend tek repo. Çok hızlı MVP, zengin kütüphane. | Spagetti kod riski, yüksek RAM tüketimi, Type güvenliği sorunları. | "Çok hızlı çıktım ama kod biraz kirli, sonra başım ağrıyacak." |
| **B (Sağlamcı)** | **Go / Rust** | Type-safe, düşük RAM, yüksek performans, huzurlu backend. | UI ile entegrasyon eforu, daha fazla boilerplate, daha yavaş geliştirme. | "Kodum taş gibi ama arayüzü bitiremedim, pazar kaçıyor mu?" |

> **Karar Anı:** Eğer Go ile yazmak seni Next.js ile yazmaktan sadece %10-20 yavaşlatıyorsa; **Go seç.** O farka değer. Ama Go seni %200 yavaşlatacaksa (yeni öğreniyorsan), **uzak dur.**

---

## ⚠️ "Rewrite Phobia" (Yeniden Yazma Korkusu)

Çoğu geliştirici MVP'yi Go ile yazmak ister çünkü şu cümleyi kurar:
> *"Şimdi hızlı olsun diye Node ile yazıp, 6 ay sonra her şeyi çöpe atıp Go ile baştan yazmak istemiyorum."*

Bu yaklaşım mantıksız değildir, ancak eksiktir.
**Gerçek:** Başarılı ürünlerin %90'ı, scale ettikçe rewrite yer. Bu bir hata değil, **büyüme belirtisidir.**

### Go ile Başlamak NE ZAMAN Rasyoneldir?
Aşağıdaki maddelerden en az 3'ü senin için "Evet" ise, Go (veya benzeri robust diller) ile başla:
1.  [ ] Go ile CRUD ve API yazmak senin için "su içmek" kadar doğal ve hızlıysa.
2.  [ ] Ürün yoğun CPU işlemi, concurrency veya background job gerektiriyorsa (Video işleme, Data pipeline).
3.  [ ] Tek binary deploy etmek operasyonel yükünü hafifletiyorsa.
4.  [ ] "İleride rewrite yapma fikri" senin motivasyonunu şimdiden düşürüyorsa (Mental blokaj).

---

## 🏗 Profesyonel Mimari: The Hybrid Model

"Ya hep ya hiç" demek zorunda değilsin. Modern SaaS mimarilerinde hibrit yapı çok yaygındır.

**Frontend & Pazarlama (Hız Katmanı):**
* **Next.js / Vercel:** Landing page, auth, basit kullanıcı arayüzleri, ödeme formları.
* *Neden?* Çünkü SEO, A/B testleri ve UI kütüphaneleri burada çok güçlü.

**Core Logic & Worker (Güç Katmanı):**
* **Go / Python:** Ağır iş yükü, video işleme, veri analizi, kuyruk (queue) yönetimi.
* *Neden?* Çünkü Node.js burada tıkanabilir veya çok pahalıya patlayabilir.

> **Sonuç:** Frontend'i her hafta değiştirebilirsin (Next.js esnekliği), ama Backend'in çekirdeği sağlam kalır (Go stabilitesi).

---

## 🧪 Case Study: SilentCut.io Mimari Kararı

SilentCut.io'ta ekip (yani sen) şunu analiz etti:

* **Sorun:** Tarayıcıda ffmpeg çalıştırmak güvenilmez. Sunucuda video işlemek CPU/RAM canavarı.
* **Node.js Riski:** Büyük bir videoyu işlerken Event Loop bloklanabilir, diğer kullanıcılar hata alır.
* **Go Avantajı:** Goroutines ile binlerce videoyu paralel işlemek çok ucuz.

**Karar:**
1.  **Frontend:** Next.js (Hızlı UI gelişimi için).
2.  **Backend:** Go (API ve Worker).
3.  **İletişim:** Basit REST API + Pub/Sub.

*Bu bir "erken optimizasyon" değil, işin doğası gereği "zorunlu optimizasyon"du.*

---

## 🔄 "Sonra Nasıl Değiştireceğim?" (Strangler Fig Pattern)

Eğer Node.js ile başlayıp sonra Go'ya geçmek istersen, "Big Bang Rewrite" (Her şeyi kapatıp yeniden açmak) yapma.

**Strangler Fig (Boğucu İncir) Yöntemi:**
1.  Monolit uygulaman çalışmaya devam etsin.
2.  Sadece **en çok kaynak tüketen** veya **en sorunlu** tek bir fonksiyonu (örn: `processVideo`) Go ile mikroservis olarak yaz.
3.  Trafiği yavaşça oraya yönlendir.
4.  Zamanla eski monoliti parça parça "boğarak" yok et.

---

## ⚡️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] Skill Fit Testi
Dürüstçe cevapla ve not et:
* *"Ben en hızlı hangi dilde prototip çıkarırım?"* -> ...
* *"Hangi dilde production bug'ı çözmek beni daha az strese sokar?"* -> ...

### 2. [ ] Mimari Karar Cümlesi (Decision Record)
Şunu doldur ve `ARCHITECTURE.md` dosyana ekle:
> *"Projenin bu aşamasında [TEKNOLOJİ X]'i seçiyorum. Çünkü şu an benim için en kritik kaynak [HIZ / PERFORMANS / MALİYET]. Eğer [GÜNLÜK 10K KULLANICI / %50 CPU YÜKÜ] sınırına ulaşırsam, yapıyı değiştirmeyi değerlendireceğim."*

### 3. [ ] "Lock-in" Kontrolü
Seçtiğin teknoloji seni bir sağlayıcıya (örn: Firebase, AWS Lambda, Vercel Functions) göbekten bağlıyor mu?
* Eğer "Yarın sunucuyu değiştiremem" diyorsan, iş mantığını framework'ten soyutla (Hexagonal/Clean Architecture prensipleri).

---

## ⛔️ Yasaklı Düşünceler (Anti-Patterns)

* *"Google/Uber mikroservis kullanıyor, ben de kullanmalıyım."* -> Onların 5000 mühendisi var, senin yok.
* *"Bu dil çok popüler, geliştirici bulmam kolay olur."* -> Sen daha geliştirici alacak parayı kazanmadın. Kendine odaklan.
* *"Mükemmel olsun, 1 ay geç olsun."* -> O 1 ayda rakibin pazarı domine edebilir.

---

## 🔜 Gelecek Hafta: Altyapı, Hosting & Maliyet Yönetimi

Haftaya kodun çalıştığı yere, "Toprağa" iniyoruz:
* $5'lık VPS mi, yoksa Serverless mı?
* AWS faturaları nasıl patlamaz?
* Veritabanı (SQL/NoSQL) kararı ve Vendor Lock-in yönetimi.

---
*Developer to Founder - Week 06*
