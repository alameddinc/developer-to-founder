---
description: https://github.com/alameddinc/developer-to-founder
---

# 20 – The Crossroads: Teknik Borç, Olgunluk & Karar Anı

> **Haftanın Mottosu:** "Kod bir yüktür (Liability). Sadece insanların kullandığı kod bir varlıktır (Asset). Bir şeyi yeniden yazmaya karar verdiğinde, aslında 'Ben şu anki işimden sıkıldım' diyorsun."

Bu haftanın amacı; klavyenin başından kalkıp, pencereden dışarı bakmaktır. 20 haftadır koşuyoruz. Şimdi durup haritaya bakma zamanı: **Nereye geldik ve buradan nereye gideceğiz?**

***

### 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:

* [ ] **Teknik Borç Envanteri** çıkararak, hangi borcun "Faiz ödediğini", hangisinin "Hibe olduğunu" ayırt edeceksin.
* [ ] **"Rewrite" (Yeniden Yazma)** tuzağına düşmeden, gemiyi yüzdürürken tamir etmeyi (Refactoring) öğreneceksin.
* [ ] **Product-Market Fit (PMF)** sinyallerini okuyup, projeyi Büyütme, Dondurma veya Öldürme kararını **verilerle** vereceksin.
* [ ] **Sunk Cost Fallacy (Batık Maliyet Yanılgısı)** ile yüzleşeceksin.

***

## 1️⃣ Teknik Borç: Kredi Kartı Ekstresi

20 haftadır "Hızlı ol, sonra düzeltiriz" dedik. O gün geldi. Borçlarını bir Excel'e dök ve sınıflandır:

| Borç Tipi                         | Örnek                                         | Karar                                        |
| --------------------------------- | --------------------------------------------- | -------------------------------------------- |
| **Yönetilebilir (Konut Kredisi)** | "UI bileşenleri biraz karışık ama çalışıyor." | **DOKUNMA.** Kullanıcı görmüyor, zararı yok. |
| **Zehirli (Tefeci Borcu)**        | "Ödeme sistemi bazen çift çekim yapıyor."     | **HEMEN ÖDE.** Bu seni batırır.              |
| **Görsel (Makyaj)**               | "Kodun indentasyonu bozuk."                   | **YOK SAY.** (Prettier kur geç).             |

> **Kural:** Eğer bir teknik borç, **geliştirme hızını %50 düşürmüyorsa** veya **güvenlik açığı yaratmıyorsa**, o borçla yaşamayı öğren.

***

## 2️⃣ The Rewrite Trap: "Baştan Yazsak Düzelir" Yalanı

Geliştiricilerin en büyük fantezisi: _"Bu proje spagetti oldu. Next.js 18 çıktı, hadi her şeyi sıfırdan, tertemiz yazalım!"_

**Neden Yapmamalısın?**

1. **Netscape Dersi:** Netscape tarayıcısı "kodu temizlemek" için 2 yıl rewrite yaptı. O sırada Internet Explorer piyasayı sildi süpürdü. Netscape battı.
2. **Zaman Kaybı:** Yeniden yazarken yeni özellik ekleyemezsin. Rakip ilerler, sen yerinde sayarsın.
3. **Bilinmeyen Buglar:** Eski "çirkin" kodda, yılların tecrübesi ve düzeltilmiş bug'lar saklıdır. Yeni kod "temiz" ama "tecrübesiz"dir.

> **Strateji:** Rewrite yapma, **Refactor** yap. (Bkz: Week 6 - Strangler Fig Pattern).

***

## 3️⃣ MVP'den Çıktık mı? (PMF Sinyalleri)

Artık "MVP" etiketini kaldırmalı mısın?

**Sen bir "Ürün"sün eğer:**

* [ ] **Retention:** Kullanıcılar sen hatırlatmadan geri geliyorsa.
* [ ] **Revenue:** Tanımadığın insanlar cüzdanını çıkarıyorsa.
* [ ] **Ve En Önemlisi:**
* [ ] **Anger:** Sunucular çöktüğünde insanlar sinirlenip mail atıyorsa. (Kimse umursamıyorsa, ürün olmamışsın demektir).

***

## 4️⃣ Karar Matrisi: Scale, Sustain, Kill

Founder olarak en zor kararı verme vakti.

#### A) Scale (Büyüt)

* **Durum:** PMF sinyalleri yeşil. Para geliyor.
* **Aksiyon:** Şirketleş (Week 8). Reklam bütçesini artır (Week 18). Ekip kurmayı düşün.

#### B) Sustain (Lifestyle Business / Yan Proje)

* **Durum:** Az ama düzenli gelir var. Büyümüyor ama masrafını çıkarıp sana harçlık bırakıyor.
* **Aksiyon:** "Bakım Modu"na al. Otomasyonu artır. Haftada sadece 2 saat ayır. Bu senin pasif gelir kapın olsun.

#### C) Kill (Öldür / Pivot)

* **Durum:** 20 haftadır uğraşıyorsun, kimse para vermedi. Trafik yok. Heyecan bitti.
* **Aksiyon:** **Fişi Çek.**
  * Bu bir başarısızlık değildir.
  * 20 haftalık bir "Founder MBA" eğitimidir.
  * Kodlarını açık kaynak yap (Portfolyona koy).
  * Domain'in süresi dolmadan "Goodbye" maili at.

> **Batık Maliyet Yanılgısı:** "Ama çok emek verdim" diyerek ölü atı kamçılama. Attan in, yeni ata bin.

***

## 5️⃣ Roadmap: Feature Listesi Değil, Problem Listesi

Önümüzdeki 6 ay için "Şu buton, bu ekran" diye plan yapma.

**Now / Next / Later Formatı:**

* **Now (Bu Ay):** "Kullanıcıların %40'ı ödeme adımında takılıyor. Bunu çöz." (Problem odaklı).
* **Next (Gelecek Çeyrek):** "Kurumsal firmalar fatura istiyor. B2B altyapısına bak."
* **Later (Yıl Sonu):** "Mobil uygulama ihtiyacını değerlendir."

***

## 6️⃣ Case Study: SilentCut.io'ın Kaderi (Hayali)

**Durum:**

* YouTube API kotası sürekli doluyor (Teknik Borç).
* Gelir: Ayda $300 (Sunucu kirası $150). Kâr: $150.
* Büyüme: Duragan.

**Karar:**

* **Rewrite?** Hayır. Değmez.
* **Scale?** Hayır. Reklam maliyetini kurtarmıyor.
* **Karar:** **Sustain (Lifestyle).**
  * Sistem optimize edildi.
  * Destek talepleri otomatize edildi.
  * Founder yeni projeye başladı, SilentCut.io arkada "harçlık" üretmeye devam etti.

***

## 🛠️ Haftalık Görevler (Final Checklist)

#### 1. \[ ] Dürüstlük Aynası

Ürününün karşısına geç ve sor: _"Bu ürün dünyayı değiştiriyor mu, bana para kazandırıyor mu, yoksa sadece egomu mu tatmin ediyor?"_

#### 2. \[ ] Teknik Borç Temizliği (Hafta Sonu)

Sadece 1 gün ayır ve seni en çok gıcık eden o "Zehirli Borcu" temizle. Kod tabanın nefes alsın.

#### 3. \[ ] "Post-Mortem" veya "Roadmap" Yazısı

* Ürünü kapatıyorsan: "Neden başaramadım ve ne öğrendim?" (Blog yazısı).
* Devam ediyorsan: "SilentCut.io 2.0 Yol Haritası".

#### 4. \[ ] Mezuniyet Kutlaması

Kendine bir kahve ısmarla. 20 hafta boyunca disiplinle buraya kadar geldin. Sen artık sadece kod yazan biri değilsin. **Sen bir kurucusun.**

***

### ⚠️ Son Söz

> Başarı, Exit yapmak değildir. Başarı, milyon dolar değildir. Başarı; bir fikri alıp, kaostan geçirip, çalışan bir gerçekliğe dönüştürme iradesidir. Sen bunu başardın.

***

### 🎁 BONUS: Final Bölümü

Bu yolculuk teknik ve ticari olarak bitti. Ama bir de işin **"Ruhu"** var.

* Kazandığımız para helal mi?
* Ticarette " Bereket" (Barakah) metriği nedir?
* İslam ve Etik açısından bir Founder nasıl durmalı?

**Sırada: Developer to Founder - The Ethical Code.**

***

_Developer to Founder - Week 20_
