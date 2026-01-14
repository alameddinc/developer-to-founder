# 09 – Versiyon Kontrolü, Proje Yönetimi & Founder Disiplini  
## “Ürünü Değil, Kendini Yönetemezsen Ürün de Yürümez”

Bu haftanın amacı:
> **Solo veya küçük ekipte çalışan bir geliştiricinin  
> hem kodu hem kendini hem de ürünün geleceğini yönetebilir hale gelmesi.**

Bu hafta:
- Git sadece bir araç
- Asıl mesele **düzen, takip ve bitirme alışkanlığı**
- MVP sonrası kaosun önüne geçme haftası

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Kendi için sürdürülebilir TODO list’ler oluşturabilecek
- MVP sonrası fikir ve notlarını kaybetmeyecek
- “Sonra bakarız” çöplüğünü kontrol altına alacak
- Test düşünmeye erken başlayacak (ama boğulmayacak)
- Farklı cihaz ve senaryolarda test refleksi kazanacak
- Versiyonlama + iş yönetimini birlikte düşünecek

---

## 🧠 Büyük gerçek

> Bazende ürünler:
> - Yanlış mimariden değil  
> - Yanlış pazarlamadan değil  
>  
> **takipsizlikten** ölür.

---

# 1️⃣ Versiyon kontrolü = değişim yönetimi (kısa hatırlatma)

Git:
- Sadece kod saklama aracı değildir
- **Geri dönebilme cesareti** verir

Temel kural:
> `main` her zaman deploy edilebilir olmalı.

Ama bu hafta Git’i **tek başına bırakıyoruz**, çünkü yetmez.

---

# 2️⃣ Founder için kişisel TODO list: şart mı?

**Evet. Ama doğru şekilde.**

## ❌ Yanlış TODO kullanımı
- Sonsuz liste
- Her şey “yüksek öncelik”
- Aylarca dokunulmayan maddeler

Bu:
> Moral bozar, odak öldürür.

---

## ✅ Doğru TODO yaklaşımı (founder versiyonu)

### 3 ayrı liste kullan
1️⃣ **Şimdi** (aktif – max 3 madde)  
2️⃣ **Sonra** (yakın gelecek)  
3️⃣ **Fikirler / Belki** (park alanı)

> Her şeyi “şimdi”ye koyma.  
> Şimdi listesi kutsaldır.

---

## MVP sonrası için not almak gerekli mi?
**Kesinlikle evet.**

Ama:
- TODO’ya atılmaz
- Ayrı bir yere yazılır

Örnek:
- “Kullanıcılar pricing’i anlamıyor olabilir”
- “Export isteyen oldu”
- “Mobilde upload zor”

Bunlar:
> **Henüz iş değil**, sinyaldir.

---

# 3️⃣ Feature fikirleri: backlog’a atmalı mıyım?

Evet, ama **etiketleyerek**.

### Önerilen etiketler
- `post-mvp`
- `user-feedback`
- `nice-to-have`
- `riskli`
- `deney`

Bu sayede:
- MVP’yi bozmaz
- Ama unutmazsın

> Unutulan fikir değil,  
> **kontrolsüz fikir** öldürür.

---

# 4️⃣ Test düşünmek: Ne kadar erken?

### ❌ Yanlış uç
- “MVP’de teste gerek yok”

### ❌ Diğer yanlış uç
- “Her şeyin testini yazalım”

### ✅ Sağlıklı orta yol

Bu hafta testten beklenti:
> **Senaryo düşünme**

---

## Test case düşünme (kod yazmadan)

Her ana özellik için şunu sor:
- Mutlu senaryo (happy path)
- Yanlış input
- Yarım kalan işlem
- Aynı işlemi 2 kez yaparsa ne olur?

Bunları:
- Kod yazmadan
- Not olarak yazman yeterli

---

# 5️⃣ Cihaz & ortam testleri: MVP seviyesinde ne yeterli?

Kimse senden şunu beklemiyor:
- 20 cihaz
- 10 tarayıcı
- Otomasyon cenneti

Ama **şunlar şart**:

## Minimum test seti
- Desktop (Chrome)
- Mobil tarayıcı (iOS veya Android)
- Küçük ekran (responsive)
- Yavaş internet simülasyonu

Özellikle:
- Upload
- Ödeme
- Formlar

> Founder körlüğü burada çok olur.  
> Kendi cihazın her zaman yalan söyler.

---

# 6️⃣ “Sonra yaparız” listesi (çok kritik)

Bu liste:
- MVP’yi korur
- Aklını rahatlatır

İçine şunlar girer:
- Büyük refactor
- Gelişmiş ayarlar
- Güzel ama gereksiz UX
- Edge case’ler

Ama:
> Bu listeye bakıp **iş yapma**.  
> Sadece bil ki oradalar.

---

# 7️⃣ Haftalık çalışma düzeni (güncellenmiş)

### Pazartesi
- Aktif TODO’yu seç (max 3)
- Test senaryolarını gözden geçir

### Günlük
- Yeni fikir gelirse → “Fikirler” listesine at
- Aktif iş değiştirme

### Cuma
- Deploy
- Şu 3 soruya cevap yaz:
  - Ne yaptım?
  - Ne öğrendim?
  - Ne kafamı karıştırdı?

---

# 8️⃣ Versiyonlama + iş disiplini birlikte

Her deploy:
- Bir versiyon
- Bir öğrenme
- Bir kapanan iş demek

Bu yüzden:
> Deploy olmayan iş = bitmemiş iştir.

---

# 🧪 SilentCut bağlamında düşünürsek

Bu tarz ürünlerde:
- “Bir tık daha iyileştireyim” tuzağı çok güçlü
- Testler genelde upload/processing etrafında yoğunlaşır
- Mobil test atlanır (hata!)

Disiplin:
- Küçük feature
- Sık deploy
- Not al, hemen yapma

---

# 🛠️ Bu haftanın görevleri (güncellenmiş)

## 1️⃣ Kişisel TODO sistemini kur
- Şimdi / Sonra / Fikirler

---

## 2️⃣ MVP sonrası not alanı oluştur
- Ayrı bir doküman
- TODO’dan bağımsız

---

## 3️⃣ 5 ana feature için test senaryosu yaz
- Kod yok
- Senaryo var

---

## 4️⃣ En az 2 cihazda test yap
- Desktop + mobil

---

## 5️⃣ Bu hafta en az 1 deploy yap
- Küçük bile olsa

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Kontrol altında bir backlog
- Kaybolmayan fikirler
- Daha az yarım iş
- Daha az sürpriz bug
- Daha yüksek mental rahatlık

olmalı.

---

## ⚠️ Son söz

> Disiplin seni kısıtlamaz.  
> Disiplin seni **özgürleştirir**.

---

## 🔜 Sonraki hafta (10. Hafta)

**10 – CI/CD & Yayına Alma (Ürün Odaklı)**

- Deploy ritmi
- Hotfix & rollback
- “Her gün deploy edilir mi?”
- Korkmadan prod’a çıkmak

---
