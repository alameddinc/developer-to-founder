# 05 – The Art of Cutting: MVP Kapsamı & Scope Creep

> **Haftanın Mottosu:** "Mükemmel, iyinin düşmanıdır. MVP ise mükemmelin katilidir."

Bu haftanın amacı kod yazmak değil, **yazılacak kod miktarını acımasızca azaltmaktır.**

Çoğu geliştirici MVP'yi *"Minimum Version of Product"* sanır.
Oysa MVP: **"Minimum Viable Product"** (En Küçük **Yaşayabilir** Ürün) demektir.
* Yarım araba (tekerlek) bir yere gitmez.
* Ama bir kaykay (skateboard) seni A'dan B'ye götürür.

Amaç: Arabayı inşa etmeden önce, insanların A'dan B'ye gitmek isteyip istemediğini (Market Validation) test etmektir.

---

## 🎯 Haftanın Hedefleri (Learning Outcomes)

Bu modülü tamamladığında:
* [ ] "Bunu da ekleyelim, çok kolay" tuzağına (Scope Creep) düşmeyeceksin.
* [ ] Özellikleri "Lazım" ve "Çöp" olarak ayırabileceksin (MoSCoW Analizi).
* [ ] Teknik Borcu (Technical Debt) bilinçli bir **yatırım aracı** olarak kullanacaksın.
* [ ] Stack tartışmalarını (Next.js vs Go) "hız" odaklı bitireceksin.

---

## 🔪 Profesyonel Budama: "Risk-First" Yaklaşımı

Bir özelliği MVP'ye ekleyip eklemeyeceğine nasıl karar verirsin?
Yazı tura atarak değil, **riske bakarak.**

Her MVP şu 3 sorudan en az birini doğrulamak zorundadır:
1.  **Değer Riski:** İnsanlar bunu istiyor mu?
2.  **Kullanılabilirlik Riski:** İnsanlar bunu çözebiliyor mu?
3.  **Fizibilite Riski:** Ben bunu yapabilir miyim?

> **Kural:** Eğer bir özellik bu risklerden birini test etmiyorsa, o özellik **aksesuardır.** Ve MVP'de aksesuara yer yoktur.

---

## 🧠 Metodoloji: MoSCoW Analizi

Özellik listeni önüne al ve her birine şu etiketlerden birini yapıştır:

| Etiket | Anlamı | Örnek (Video App) |
| :--- | :--- | :--- |
| **Must Have** | Bu olmazsa ürün çalışmaz. (MVP) | Video Yükleme, İşleme, İndirme. |
| **Should Have** | Olsa iyi olur ama acıtmaz. (v1.1) | İlerleme Çubuğu, Hata Mesajları. |
| **Could Have** | Güzel özellik ama şart değil. (v2.0) | Dark Mode, Google Login, Geçmiş. |
| **Won't Have** | Şimdilik hayır. (Backlog) | Takım Yönetimi, API Erişimi. |

> **Acı Gerçek:** Geliştiricilerin "Must Have" dediklerinin %50'si aslında "Could Have"dir.

---

## 🛠 Case Study: SilentCut.io'ın "Çıplak" MVP'si

SilentCut.io ilk çıktığında şunlar **YOKTU**:
* ❌ Üyelik Sistemi (Login/Register).
* ❌ Ödeme Sistemi (Stripe).
* ❌ Dashboard / Geçmiş Videolar.
* ❌ Ayarlar Sayfası.

**Ne VARDI?**
* ✅ Tek bir "Upload" kutusu.
* ✅ İşleyen bir algoritma.
* ✅ Sonucu gösteren bir "Demo" sayfası.
* ✅ Manuel ödeme linki (Email ile).

**Neden?**
Çünkü test edilen risk şuydu: *"İnsanlar sessizlik silme kalitesini beğenecek mi?"*
Login sayfası yapmak, bu riski test etmez. Sadece zaman kaybettirir.

---

## 🏗 Teknik Borç: Ne Zaman Alınır?

Teknik borç, startup'ın kredi kartıdır. Doğru kullanırsan seni hızlandırır, yanlış kullanırsan batırır.

### ✅ Bilinçli Borç (Smart Debt)
* **Hard-coded Ayarlar:** Admin paneli yazmak yerine config dosyasından yönetmek.
* **Manuel Onboarding:** Otomatik mail sistemi kurmak yerine Gmail'den elle atmak.
* **Monolitik Yapı:** Mikroservis yerine tek repo (Next.js) kullanmak.

### ❌ Tehlikeli Borç (Toxic Debt)
* **Güvenlik Açıkları:** Auth kontrolü yapmamak.
* **Veri Kaybı:** Yedekleme yapmamak.
* **Spagetti Kod:** Okunamaz kod yazmak (Hızlı yazmak, pis yazmak demek değildir).

---

## ⚔️ Stack Savaşları: Next.js vs The World

**Soru:** "Hızlı MVP için Next.js ile çıkıp sonra Go/Rust'a dönmeli miyim?"

**Cevap:**
1.  **Evet, Next.js (veya bildiğin en hızlı stack) ile çık.** Çünkü senin darboğazın CPU değil, **zaman.**
2.  **Hayır, rewrite yapmak zorunda değilsin.** Ürün tutarsa, sadece darboğaz olan %5'lik kısmı (örn: video işleme servisini) Go'ya taşırsın. (Strangler Pattern).

> **Altın Kural:** Mükemmel mimari, hiç kullanıcısı olmayan bir mezarlıktır.

---

## ⚡️ Haftalık Görevler (Commitment Checklist)

### 1. [ ] Risk Analizi
Kağıdı ikiye böl.
* **Sol:** Ürünün batmasına sebep olabilecek en büyük risk ne? (Örn: Kimse video yüklemez.)
* **Sağ:** Bu riski test etmek için gereken **tek** özellik ne?

### 2. [ ] The Kill List (Öldürülecekler)
Mevcut özellik listenden en az 3 maddeyi **sil.**
* *Örnek: "Dark mode'u sildim.", "Şifremi unuttum ekranını sildim (mail atsınlar)."*

### 3. [ ] "One Metric" Seçimi
MVP'nin başarısını neyle ölçeceksin? (Sadece 1 tane).
* [ ] Ziyaretçi Sayısı (Yanlış - Vanity Metric)
* [ ] Tamamlanan İşlem Sayısı (Doğru - Actionable Metric)

---

## ⛔️ Yasaklı Cümleler (Scope Creep Alerts)

* *"Bunu eklemek sadece 2 saatimi alır."* -> O 2 saatler birleşip 2 ay olur.
* *"Ama rakipte bu özellik var."* -> Rakip 5 yıldır piyasada, sen 5 gündür.
* *"Kullanıcılar belki ister."* -> "Belki" yok. Veri gelene kadar varsayım yok.

---

## 🔜 Gelecek Hafta: Teknik Mimari & Altyapı

Haftaya kodun derinliklerine iniyoruz:
* Monolit mi, Mikroservis mi? (Cevap muhtemelen Monolit).
* Veritabanı seçimi: SQL vs NoSQL.
* Vendor Lock-in (Bağımlılık) ne kadar kötü?

---
*Developer to Founder - Week 05*
