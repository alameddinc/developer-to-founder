---
description: https://github.com/alameddinc/developer-to-founder
---

# 01 – Debugging the Idea: Fikir Doğrulama & Problem Keşfi

> **Haftanın Mottosu:** "Kod yazmak, problemi anlamaktan daha kolaydır. Bu yüzden çoğu geliştirici yanlış şeyi inşa eder."

{% embed url="https://open.spotify.com/episode/2oD6YcPk4i56UmlKYJImxb?si=WlrIuQ9WS8Sd6AWcjFMeFw" %}

Bu haftanın amacı bir **ürün geliştirmek** değil; **yanlış bir ürünü geliştirmekten kaçınmaktır.**

Çoğu startup veya indie proje teknik yetersizlikten batmaz. **Kimsenin ihtiyaç duymadığı bir problemi, mükemmel bir kodla çözdükleri için batarlar.**

***

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:

* [ ] Çözmek istediğin problemi **tek bir cümleyle** tanımlayabileceksin.
* [ ] "Güzel fikir" ile "Pazar problemi" arasındaki farkı ayırt edebileceksin.
* [ ] Kendi fikrine aşık olmaktan vazgeçip, **probleme aşık olmayı** öğreneceksin.
* [ ] Fikrini sadece ticari değil, **yasal, etik ve toplumsal** riskler açısından analiz edip "Tamam mı, Devam mı?" kararı verebileceksin.
* [ ] Kullanıcı görüşmelerinde "yalan duyma" (false positive) riskini minimize edeceksin.

***

## 🛑 En Büyük Tuzak: "Scratching Your Own Itch" Yanılgısı

Yazılımcıların en sık kurduğu cümle:

> _"Benim buna ihtiyacım vardı, kesin başkalarının da vardır."_

Bu varsayım %50 ihtimalle doğrudur, %50 ihtimalle ise sadece **senin hobindir.**

Kendi ihtiyacını genele yaymak ve doğrulama yapmadan IDE'yi açmak, bir girişimcinin yapabileceği en pahalı hatadır. Bu repo, seni bu hatadan korumak (debug etmek) için tasarlandı.

***

## 🔍 Problem Nedir? (Yanlış vs. Doğru Tanımlar)

Bir problem tanımı "çözüm" içermez. Problem, acının kendisidir.

| ❌ Yanlış Tanım (Çözüm Odaklı)          | ✅ Doğru Tanım (Acı Odaklı)                                          |
| -------------------------------------- | ------------------------------------------------------------------- |
| "Bir yapay zeka uygulaması yapacağım." | "İnsanlar X sürecinde çok vakit kaybediyor."                        |
| "Şu rakibin daha ucuzunu yapacağım."   | "Mevcut çözümler küçük işletmeler için çok pahalı ve karmaşık."     |
| "Video editleme SaaS'ı fikrim var."    | "İçerik üreticiler, sessizlikleri temizlerken saatlerini harcıyor." |

### 📐 Altın Formül

Gerçek bir problem tanımı şu şablona uymalıdır:

> **"\[KİM], \[HANGİ DURUMDA], \[HANGİ PROBLEMİ] yaşıyor ve bu ona \[NEYE MAL OLUYOR] (Zaman/Para/Enerji)."**

***

## ⚖️ The "Black Mirror" Test: Etik ve Yasal Risk Analizi

Bir fikrin teknik olarak yapılabilir olması, **onu yapman gerektiği anlamına gelmez.** Arkadaşın sana "Süper bir fikrim var" diye geldiğinde, o fikrin illegal işlerde kullanılma ihtimali %90 ise, o fikir "süper" değil, **"saatli bombadır".**

Kod yazmadan önce şu **Risk Analizini** yap ve kendine karşı dürüst ol:

### 1. Kötüye Kullanım (Abuse) Senaryoları

Sistemi tasarladığın "İdeal Kullanıcı" (Happy Path) değil, **"Kötü Niyetli Kullanıcı"** (Dark Path) nasıl kullanır?

* _Örnek:_ Anonim SMS atma servisi yaptın. Zorbalar bunu okulda çocukları tehdit etmek için kullanır mı? (Evet).
* _Örnek:_ Deepfake video aracı yaptın. Dolandırıcılar bunu şantaj veya sahte haber için kullanır mı? (Evet).

### 2. Yasal Sınırlar (Legal Boundaries)

* Fikrin KVKK/GDPR gibi veri kanunlarına baştan aykırı mı?
* Finansal bir düzenlemeyi (BDDK/MASAK) deliyor mu?
* Telif haklarını (Copyright) ihlal ederek mi değer üretiyor?

### 🚦 Karar Mekanizması: Mitigate or Kill (Çöz veya Öldür)

Riskleri belirledikten sonra 2 seçeneğin var:

* **Seçenek A: Önlem Al (Mitigate):** "Bu riski teknoloji veya süreçle engelleyebilir miyim?"
  * _Örnek:_ SMS servisi için -> "Anonimliği kaldırırım, gönderenin kimliği doğrulanmalı ve loglanmalı." (Çözüm bulundu).
* **Seçenek B: Projeyi Öldür (Kill):** "Bu riski engelleyemiyorum. Ürün doğası gereği suça veya zarara açık."
  * _Karar:_ **Projeyi İptal Et.** (Bu bir başarısızlık değil, topluma karşı sorumluluktur).

> **Unutma:** Yasal veya etik açığı olan bir proje, büyüdükçe bir şirket değil, **bir suç örgütü** potansiyeli taşır.

***

## 🛠 Case Study: SilentCut.io (Gerçek Dünya Örneği)

SilentCut.io yola çıkarken hipotez şuydu: _"Videolardaki sessizlikleri kesmek zor iş, bunu otomatize edelim."_

Ancak "problem" analiz edildiğinde detaylar ortaya çıktı:

* **Yanlış Hedef:** TikTok/Reels çekenler (Videolar zaten kısa, kesmek sorun değil).
* **Doğru Hedef:** YouTube için 20+ dk "talking head" videosu çekenler, podcast yayıncıları, zoom toplantı kayıtlarını tekrar izlemek ihtiyacında olanlar ve gün aşırı video atacak ama editor tutabilecek maddi imkanı olmayanlar ve en niş senaryoda ise editorleri olan ama seri içerik çıkartması gereken ajanslar.
* **Acı Noktası:** Editör kullanmayan üreticiler, videonun içeriğine değil, teknik temizliğe vakit harcıyor. Dikkatleri dağılıyor.

**Sonuç:** Problem "herkesin" değil, **spesifik bir grubun (Solo Creators)**, **spesifik bir durumda (Long-form content)** yaşadığı **zaman kaybıydı.**

***

## 🧠 The Mom Test: Anneni Bile Kandıramayacağın Sorular

Girişimcilik kitaplarının kutsal kasesi "The Mom Test"in özeti şudur: **İnsanlara fikrini sorarsan, seni kırmamak için yalan söylerler.**

Amacın fikrini satmak değil, onların hayatındaki "buglar"ı (yaşadıkları sorunları) bulmaktır.

### Soru Sorma Sanatı

| ❌ Kötü Soru (Övgü Arar)                 | ✅ İyi Soru (Gerçek Arar)                              |
| --------------------------------------- | ----------------------------------------------------- |
| "Böyle bir ürün yapsam kullanır mısın?" | "Bu problemi en son ne zaman yaşadın?"                |
| "Sence bu fikir güzel mi?"              | "Bunu çözmek için şu an ne kullanıyorsun?"            |
| "Buna 10$ verir misin?"                 | "Bu problemi çözmek için daha önce para harcadın mı?" |

> **Unutma:** Geleceğe dair sorular ("Yapar mısın?") yalan üretir. Geçmişe dair sorular ("Yaptın mı?") veri üretir.

***

## 📉 Sahte Doğrulama (False Validation) Nedir?

Aşağıdakiler birer \*\*"Vanity Metric"\*\*tir (Şişirilmiş Ölçüm) ve fikrinin tutacağını kanıtlamaz:

* Twitter'da like almak / Retweet edilmek.
* Arkadaşlarının "Abi çok iyi fikir" demesi.
* Discord gruplarında heyecanlanılması.
* _Landing page olmadan_ yapılan anketler.

**Gerçek Doğrulama:** İnsanların cüzdanını çıkarması veya ciddi bir zaman/emek yatırımı yapmasıdır (Skin in the game).

***

## ⚡️ Haftalık Görevler (Commitment Checklist)

Bu hafta kod yazmak yok. Sokağa (veya Zoom'a) çıkıyoruz.

### 1. \[ ] Problem Cümlesini Yaz

Yukarıdaki formülü kullanarak problemini tek cümlede tanımla ve bir yere not et.

### 2. \[ ] "Black Mirror" ve Yasal Risk Testi

Kağıdı ikiye böl:

* **Sol:** "Bu uygulama en kötü ne için kullanılabilir?" (Kara Senaryolar).
* **Sağ:** "Bunu teknik veya hukuki olarak engelleyebilir miyim?" (Çözümler).
  * Eğer sağ taraf boş kalıyorsa, **projeyi iptal et.**

### 3. \[ ] 5 Kişiyle Görüş (User Interviews)

* Hedef kitlenden 5 kişi bul (LinkedIn, Twitter DM, Reddit, Forumlar).
* Arkadaşın veya annen olmasın.
* Ürününden bahsetmeden sadece dertlerini dinle.

### 4. \[ ] "Pain Level" (Acı Seviyesi) Testi

Görüşmelerden sonra şu soruya dürüstçe cevap ver:

> _"Ben bu ürünü yapmasam, bu insanlar hayatına 'bir şekilde' devam eder mi, yoksa çözüm için kıvranıyorlar mı?"_

* Cevap "Fark etmez" ise -> **Pivot.**
* Cevap "Çok zorlanıyorlar" ise -> **Devam.**

***

## ⛔️ Yasaklı İşlemler Listesi (Anti-Patterns)

Bu hafta şunları yaparsan, kendini kandırmış olursun:

1. IDE açmak / `git init` yazmak.
2. Database şeması tasarlamak.
3. Logo tasarlamak veya Domain satın almak.
4. UI Kit aramak.

> **Uyarı:** Yanlış problem için yazılan kod, teknik borçtan (Technical Debt) daha pahalıdır. O, **zaman borcudur** ve geri ödenemez.

***

## 🔜 Gelecek Hafta: Hedef Kitle & Pazar Analizi

Haftaya şunları konuşacağız:

* "Herkes benim müşterim" yalanından kurtulmak.
* Rakipleri doğru analiz etmek (Rakip varsa korkmalı mısın, sevinmeli misin?).
* SilentCut.io örneğinde rakip paniği neden gereksizdi?

***

_Developer to Founder - Week 01_
