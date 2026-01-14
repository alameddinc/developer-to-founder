# 04 – Design for Non-Designers: UI/UX & Güven İnşası

> **Haftanın Mottosu:** "Tasarım, ürünün nasıl göründüğü değil; nasıl çalıştığıdır." — Steve Jobs

Bu haftanın amacı Picasso olmak değil. Amacımız, kullanıcının **düşünmesine gerek kalmadan** ürünü kullanabilmesini sağlamak.

Çoğu geliştirici UI/UX'i "renk seçmek" veya "buton yuvarlatmak" sanır. Oysa UX, bir **mimari problemdir.**

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] "Bu buton neden mavi?" sorusuna "Canım istedi" yerine mantıklı bir cevap vereceksin.
* [ ] Kullanıcının ekrandaki gezinme rotasını (User Flow) kodlayabileceksin.
* [ ] **Güven (Trust)** kavramının, CSS'ten daha önemli olduğunu anlayacaksın.
* [ ] Kullanıcıyı "eğitmek" yerine, onun alışkanlıklarına "uyum sağlamayı" öğreneceksin.

---

## 🧠 UX Nedir? (Developer Edition)

> **UX = `try-catch` bloğudur.**

Kullanıcının hata yapmasını (exception) önlemek ve doğru yolu (happy path) en pürüzsüz hale getirmektir.

Eğer kullanıcı:
* Yanlış butona basıyorsa,
* "Şimdi ne olacak?" diye duraksıyorsa,
* Kaydetmeden çıkıyorsa;

Bug kullanıcıda değildir, **arayüzdedir.**

---

## 🔘 Hiyerarşi: Tek Bir Butonun Anatomisi

Ekranda üç aksiyon var: `İptal`, `Kaydet`, `Sil`.
Bunları yan yana, aynı renkte koymak, kullanıcıya "Rus Ruleti" oynatmaktır.

### ❌ Yanlış Tasarım (Flat Hierarchy)
```text
[ İPTAL ]  [ KAYDET ]  [ SİL ]
(Hepsi gri, hepsi aynı boy, yan yana)
```


_Kullanıcı: "Hangisine basacaktım? Elim çarparsa ne olur?"_

### ✅ Doğru Tasarım (Visual Hierarchy)
```
[  KAYDET  ]  <-- Primary (Mavi/Solid)
	[ İptal ]   <-- Secondary (Gri/Ghost)
		[ Sil ]   <-- Destructive (Kırmızı/Uzakta)
```

**UX Mesajı:**

-   **Mavi:** "Gitmek istediğin yer burası."
-   **Gri:** "Gerekirse buradayım ama acil değil."
-   **Kırmızı:** "Dikkat! Burası tehlikeli."

----------

## 🎨 Renk ve Font: Sanat Değil, Sinyalizasyon

Renkler süs değil, trafik ışığıdır.

**Mavi / Mor**
Güven, Stabilite, Action
Ana butonlar, Linkler, Header.

**Yeşil**
Başarı, Onay
"Kaydedildi", "Tamamlandı" mesajları.

**Kırmızı**
Tehlike, Hata, Yıkım
"Sil", "Hata Oluştu", "Hesabı Kapat".

**Gri**
Pasif, Nötr
İkincil metinler, Pasif butonlar.


> **Kural:** Bir ekranda en fazla **1 Ana Renk** ve **1 Font Ailesi** (Regular/Bold) kullan. Fazlası, profesyonellikten uzaklaştırır ve güveni kırar.

----------

## 📐 Layout: Kullanıcı Ekranı Nasıl Okur?

Kullanıcılar siteni okumaz, **tarar (scan).**

1.  **F-Pattern:** Göz sol üstten başlar, sağa gider, sonra aşağı iner.
2.  **Önem Sırası:**
    -   En kritik bilgi (Başlık/Değer) -> **En Üstte.**
    -   Ana Aksiyon (CTA) -> **Göz Hizasında.**
    -   Detaylar (Footer/Dipnot) -> **En Altta.**


❌ **Hata:** İlk ekranı (Above the Fold) "Hoşgeldiniz, biz 2020 yılında kurulduk..." yazısıyla doldurmak. ✅ **Doğru:** "Videolarını 10 saniyede temizle. [Hemen Başla]"

----------

## 🧠 Kullanıcı Alışkanlıkları: "Don't Make Me Think"

Kullanıcı kitlene göre arayüz değişir.

### Teknik Kullanıcı (Developer Tools)

-   **İstek:** Kontrol, yoğun bilgi, "Dark Mode".
-   **Tolerans:** Karmaşık ayarlardan korkmaz.
-   **Örnek:** VS Code, AWS Console.

### Teknik Olmayan Kullanıcı (B2C / SilentCut)
-   **İstek:** Hız, sadelik, "Sihirli Değnek".
-   **Tolerans:** Ayar görmekten nefret eder. Varsayılan (Default) neyse onu kullanır.
-   **Örnek:** Instagram, iPhone Kamera.

----------

## 🛠 Case Study: SilentCut'ta "Ayar Paradoksu"

**İlk Tasarım:** Ekranda `Threshold`, `Padding`, `Decibel Level` gibi 10 tane ffmpeg ayarı vardı. _Mantık:_ "Kullanıcı her şeyi kontrol etsin."

**Sonuç:** Kullanıcı kaçtı. "Ben ses mühendisi değilim, sadece sessizliği sil" dedi.

**Düzeltilmiş Tasarım:**
-   Tüm ayarlar gizlendi.
-   Tek bir seçenek: **"Hassasiyet: Düşük / Orta / Yüksek"**
-   Arka planda o karmaşık değerler otomatik atandı.

> **Ders:** İyi UX, karmaşıklığı yok etmez; karmaşıklığı **kullanıcıdan saklar.**

----------

## 🔐 Güven İnşası (Trust Signals)

Kullanıcı kredi kartını girecekse, sitenin "scam" (dolandırıcı) olmadığını hissetmeli.

-   **Belirsizlik = Güvensizlik.**
-   `Loading...` yerine -> `Videonuz işleniyor (%45)...`
-   `Hata oluştu` yerine -> `Dosya formatı desteklenmiyor, lütfen MP4 deneyin.`
-   `Satın Al` butonunun altına -> `İstediğin zaman iptal edebilirsin.`

----------

## ⚡️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] Ana Ekranı Parçala

Kağıt kalemi al. Ürününün ana ekranını çiz.
-   Ana Aksiyon (Primary Button) nerede?
-   Gözü yoran gereksiz bir element var mı? Sil.

### 2. [ ] Renk Anayasası

CSS dosyan veya Tailwind config'in için karar ver:

-   Primary Color: `...` (Neden bu renk?)
-   Danger Color: `...`
-   Success Color: `...`

### 3. [ ] "Aptal Kullanıcı" Testi (Kaba ama etkili)

Kendine şu soruyu sor:

> _"Hiçbir şey okumayan, aceleci ve dikkatsiz bir kullanıcı bu ekrana gelse, yanlışlıkla her şeyi silebilir mi?"_ Cevap evetse, o "Sil" butonunu sakla veya onay kutusu ekle.

----------

## ⛔️ Yasaklı Düşünceler (Anti-Patterns)

-   "Tasarımcı değilim, Bootstrap/Material varsayılanı kalsın." -> Ürünün "Hobi Projesi" gibi görünür.
-   "Kullanıcı dökümantasyonu okusun." -> Okumayacak.
-   "Değişik olsun diye menüyü aşağıya koydum." -> Standartlardan şaşma. Logo solda, menü sağda/üstte olur.

----------

## 🔜 Gelecek Hafta: MVP Kapsamı & Scope Creep

Haftaya "Neleri yapmayacağımıza" karar vereceğiz.

-   MVP (Minimum Lovable Product) sınırları.
-   Teknik Borç bilerek nerede alınır?
-   "Bu özellik neden yok?" sorusuna verilecek en iyi cevap.

----------

_Developer to Founder - Week 04_
