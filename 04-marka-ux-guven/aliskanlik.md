---
description: https://github.com/alameddinc/developer-to-founder
---

# 04.2 – Don't Re-Invent the Wheel: Kullanıcı Alışkanlıklarını Miras Almak

> **Haftanın Mottosu (Part 2):** "Kullanıcılar zamanlarının çoğunu senin sitende değil, diğer sitelerde geçirirler. Bu yüzden senin sitenin de diğerleri gibi çalışmasını beklerler." — Jakob Nielsen (Jakob's Law)

Bu bölümün amacı: **Kullanıcıyı eğitmek zorunda kalmamaktır.** Eğitim masraflıdır. Kullanıcının zaten bildiği kas hafızasını (Muscle Memory) projenize `extend` etmek varken, neden sıfırdan `class` yazasınız?

***

## 🧠 "Habit Inheritance" (Alışkanlık Mirası) Nedir?

Yazılımda nasıl ki `BaseController`dan miras alıp ortak fonksiyonları tekrar yazmıyorsak, UX'te de devlerden miras alırız.

* **Kopya Çekmek:** Tasarımı, renkleri, logoyu çalmaktır. (Hırsızlık)
* **Miras Almak:** Akışı, buton yerleşimini, beklentiyi almaktır. (Standart)

> **Gerçek:** Dünyanın en yenilikçi uygulaması olduğunu iddia eden Instagram bile, "beğenme" ve "kaydırma" alışkanlıklarını Facebook ve Tinder'dan miras almıştır.

***

## 🛒 E-Ticaret Anayasası: Neden "Sepet" Sağ Üsttedir?

E-ticaret siteleri sıkıcı derecede birbirine benzer. Neden? Çünkü orada **para** vardır. Para harcanan yerde kullanıcı **sürpriz** istemez.

Bir e-ticaret sitesinde "Sepet" ikonunu sol alta koyarsan:

1. Bu bir inovasyon değildir.
2. Bu bir "Tasarım Hatası"dır.
3. Sonuç: Ciro kaybı.

### Kutsal UX Standartları (Dokunma Yanarsın)

| Eleman           | Beklenen Konum/Davranış      | Neden?                                                   |
| ---------------- | ---------------------------- | -------------------------------------------------------- |
| **Logo**         | Sol Üst                      | Ana sayfaya dönmek için evrensel kaçış butonu.           |
| **Sepet/Profil** | Sağ Üst                      | Kullanıcı ekranı tararken çıkışı veya sonucu orada arar. |
| **Linkler**      | Mavi/Altı Çizili/Farklı Renk | Tıklanabilir olduğu belli olmalı.                        |
| **Mobilde Menü** | Hamburger (≡) veya Alt Bar   | Başparmak erişim alanı.                                  |

***

## 🧪 Case Study: SilentCut.io ve "Upload" Refleksi

SilentCut.io'ta bir "Video Yükleme" süreci tasarlarken iki yol vardı:

**Yol A (Over-Engineering / Yenilikçi):**

* Ekranda uçuşan partiküller.
* "Videonu Sahneye Davet Et" yazan bir buton.
* Yükleme bitince konfetiler.

**Yol B (Miras Alan / Standart):**

* Kesikli çizgilerle (Dashed Border) bir kutu.
* Ortada bir "Bulut/Yükle" ikonu.
* Metin: "Dosyanı buraya sürükle veya seç."
* Yüklenirken: Yeşil bir Progress Bar.

**Karar:** Yol B seçildi. **Sonuç:** Kullanıcı ne yapacağını 0.1 saniyede anladı. "Nasıl yükleniyor?" sorusu hiç gelmedi. Çünkü kullanıcı bunu Google Drive'dan, WeTransfer'den, Dropbox'tan zaten biliyordu.

***

## 🔁 Kopyalamak vs. Esinlenmek (Cheat Sheet)

Neyi alıp neyi almayacağını karıştıranlar için basit bir tablo:

| ✅ Miras Al (Inherit)                             | ❌ Kopyalama (Clone)                                            |
| ------------------------------------------------ | -------------------------------------------------------------- |
| **User Flow:** Sepet -> Adres -> Ödeme           | **Microcopy:** Rakibin yazdığı hata mesajının aynısını yazmak. |
| **Layout:** Menü yerleşimi, Footer yapısı.       | **Visual Identity:** Rakibin renk paleti ve fontu.             |
| **Terminology:** "Giriş Yap", "Kaydol", "İndir". | **Tone of Voice:** Rakibin espri anlayışını taklit etmek.      |

***

## ⚠️ Ne Zaman "Override" Edebilirsin?

Miras aldığın alışkanlığı ne zaman bozabilirsin? Sadece ve sadece **yeni yöntem eskisinden 10 kat daha iyiyse.**

* **Örnek:** Tinder'ın "Sola/Sağa Kaydırma" (Swipe) özelliği.
  * Eski yöntem: Profili aç -> İncele -> Butona tıkla -> Geri dön.
  * Yeni yöntem: Kaydır. (10x Hız).
  * _Bu bir devrimdi, ama riskliydi. Tuttu._

Eğer senin çözümün sadece "farklı" ama "daha iyi" değilse, **standarda sadık kal.**

***

## 🛠️ Haftalık Egzersiz: Pattern Hunt

Kendi ürünün için şu analizi yap:

### 1. \[ ] Rakip Davranış Analizi

Benim problemimi çözen en büyük 3 siteye gir. Şunlara bak:

* "Kaydol" butonu nerede?
* Ayarlar menüsü nerede?
* İşlem bittiğinde ne gösteriyorlar?

### 2. \[ ] "Bilinçli Miras" Listesi

* _"Kullanıcılarım \[X] sitesine alışkın olduğu için, ben de \[Y] özelliğini aynı yere koyacağım."_
* Bunu `README` veya tasarım notlarına ekle.

### 3. \[ ] "Sürtünme" (Friction) Testi

Tasarımına bak ve sor:

* _"Burada kullanıcının duraksayıp 'Acaba?' diyeceği bir yer var mı?"_
* Varsa, o kısmı standartlaştır.

***

_Developer to Founder - Week 04 (Part 2)_
