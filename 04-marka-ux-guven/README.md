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
