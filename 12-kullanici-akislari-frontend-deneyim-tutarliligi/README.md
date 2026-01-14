# 12 – Kullanıcı Akışları, Frontend & Deneyim Tutarlılığı  
## “Ekran Değil, Akış Tasarla”

Bu haftanın amacı:
> **Kullanıcının ürünü nasıl kullandığını anlamak ve  
> onu hata yapmaya zorlamayan bir deneyim oluşturmak.**

Bu hafta:
- “Hangi framework?” konuşmuyoruz
- Pixel-perfect tasarım yapmıyoruz
- UI kit kurmuyoruz

Ama:
> **Yanlış akışın, doğru backend’i bile öldürdüğünü** netleştiriyoruz.

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Kullanıcı akışı ile ekran arasındaki farkı anlayacak
- “Mutlu yol” (happy path) tasarlamayı öğrenecek
- Kullanıcıyı hataya sürükleyen UI kalıplarını fark edecek
- Empty / loading / error state’leri bilinçli ele alacak
- Mobil ve masaüstü farklarını doğru yönetecek
- “Çalışıyor ama kullanılmıyor” tuzağından kaçınacak

---

## 🧠 En yaygın ama yıkıcı hata

> “Backend hazır, frontend’i hızlıca bağlayalım.”

Gerçek:
> Kullanıcı backend’i görmez.  
> **Akışı görür.**

Yanlış akış:
- Yanlış geri bildirim üretir
- Yanlış geri bildirim:
  - Yanlış ürün kararlarına yol açar

---

# 1️⃣ Akış nedir, ekran nedir?

- **Ekran:** UI’daki tek bir sayfa
- **Akış:** Kullanıcının bir hedefe ulaşmak için geçtiği adımlar zinciri

Örnek:
- “Upload ekranı” bir ekrandır
- “Upload → işlem → sonuç alma” bir **akıştır**

> Ürünler ekranlarla değil,  
> **akışlarla** kullanılır.

---

# 2️⃣ Mutlu yol (Happy Path) tasarımı

Her özellik için önce şu soruyu sor:
> “Her şey yolunda giderse kullanıcı ne yapar?”

Örnek (video işleme ürünü):
1. Siteye gelir
2. Dosya yükler
3. İşlem başlar
4. Sonucu görür
5. İndirir

Bu zincir:
- Kısa
- Açık
- Kesintisiz olmalıdır

> Önce mutlu yolu mükemmelleştir,  
> sonra edge case’lere bak.

---

# 3️⃣ Kullanıcıyı hata yapmaya iten UI kalıpları

## ❌ Yaygın hatalar
- Belirsiz buton metinleri (“Devam”, “Tamam”)
- Geri dönüşü olmayan aksiyonlar
- Ne olduğunu söylemeyen loading’ler
- Hata mesajı yerine sessizlik

## ✅ Sağlıklı yaklaşım
- Butonlar **aksiyon söyler**
  - “Videoyu Yükle”
  - “İşlemi Başlat”
- Geri dönüşü olan aksiyonlar
- Süreç boyunca kullanıcıya bilgi

> Kullanıcı hata yapıyorsa,  
> sorun çoğu zaman kullanıcı değil, UI’dır.

---

# 4️⃣ Empty, Loading ve Error state’ler (MVP’de bile şart)

### 1️⃣ Empty state
- “Henüz video yok”
- “İlk işlemini başlat”

Amaç:
> Kullanıcıyı boşlukta bırakmamak.

---

### 2️⃣ Loading state
- Ne oluyor?
- Ne kadar sürebilir?
- İptal edilebilir mi?

“Loading…” yeterli değildir.

---

### 3️⃣ Error state
- Ne oldu?
- Kullanıcı ne yapabilir?
- Tekrar denemeli mi?

❌ “Bir hata oluştu”  
✅ “Dosya çok büyük. Max: 500 MB”

---

# 5️⃣ Mobil vs Desktop: Aynı ürün, farklı kullanım

Mobilde kullanıcı:
- Daha sabırsız
- Daha az dikkatli
- Tek elle kullanıyor

### MVP için minimum farkındalık
- Mobilde upload daha zor
- Küçük ekran = daha az bilgi
- Büyük tablolar mobilde felaket

> “Responsive” olmak yetmez,  
> **mobil düşünmek** gerekir.

---

# 6️⃣ Kullanıcıya güven vermek (UX + psikoloji)

Kullanıcı şunları görmek ister:
- Ne olacak?
- Ne kadar sürecek?
- Kontrol bende mi?

Basit güven unsurları:
- Adım göstergesi
- Geri al / iptal
- Net metinler
- Tutarlı renkler

> Güven yoksa, kullanım da yoktur.

---

# 7️⃣ MVP’de yapılmaması gereken UX hataları

❌ Her şeyi tek ekrana sıkıştırmak  
❌ Kullanıcıdan gereksiz bilgi istemek  
❌ Hataları gizlemek  
❌ “Ben anladım” varsayımı  
❌ Desktop’ta çalışan şeyi mobile aynen koymak  

---

# 8️⃣ SilentCut bağlamında düşünürsek

Bu tarz ürünlerde kritik akış:
- Upload
- İşlem
- Sonuç

UX hatası:
- İşlem sırasında belirsizlik
- Sonuç hazır mı, değil mi anlaşılmaması
- Mobilde indirme sorunları

İyi UX:
> Kullanıcıyı bekletirken bile  
> ne olduğunu anlatır.

---

# 9️⃣ Frontend teknolojisi bu haftanın konusu değil

Bu hafta:
- React mı, Vue mu?
- Web mi, mobil mi?

tartışmıyoruz.

Çünkü:
> Yanlış akış,  
> doğru teknolojiyle de yanlıştır.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ 1 ana kullanıcı akışını çiz
- Ekran değil
- Adım adım

---

## 2️⃣ Bu akış için:
- Empty state
- Loading state
- Error state

yazılı olarak tanımla.

---

## 3️⃣ Mobilde en riskli adımı belirle
- Neden riskli?

---

## 4️⃣ UI’da kullanıcıyı zorlayan 3 nokta yaz
- “Burada hata yapabilir”

---

## 5️⃣ Bir kişiye ürünü kullandır
- Sessiz kal
- Not al

> En değerli UX testi budur.

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Net bir kullanıcı akışı
- Daha az kafa karıştıran UI
- Bilinçli state yönetimi
- Mobil farkındalığı

olmalı.

---

## ⚠️ Son söz

> Kullanıcıyı suçlayan ürün,  
> **kullanıcısız kalır**.

---

## 🔜 Sonraki hafta (13. Hafta)

**13 – Test Stratejisi, Kalite Eşiği & Teknik Borç**

- Nerede test yazılır?
- Nerede yazılmaz?
- Manuel test refleksi
- Teknik borç alma kararı

---
