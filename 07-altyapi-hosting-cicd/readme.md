# 07 – Altyapı, Hosting & CI/CD  
## Lokalden Production’a: Güvenli, Taşınabilir ve Yönetilebilir Kurulum

Bu haftanın amacı:
> **Ürünü sadece yazmak değil, güvenli şekilde çalıştırmak ve tekrar tekrar deploy edebilmek.**  
> Founder gerçekliği: “Kod yazmak” işin %50’si; **yayınlamak + işletmek** diğer %50.

Bu hafta özellikle şunları hedefliyoruz:
- Cloud bağımsız düşünmek (GCP/AWS/DigitalOcean/Railway benzeri)
- Vendor lock-in’i azaltmak
- MVP akışında “lokal → staging → prod” düzeni kurmak
- CI/CD’yi “kurumsal DevOps” gibi değil, **solo founder** gibi kurmak

---

## 🎯 Haftanın hedefi

Bu hafta sonunda katılımcı:

- Hosting seçeneklerini (VPS/PaaS/Serverless) doğru yerde kullanabilecek
- GCP + AWS’yi birlikte kullanırken “nerede ne var?” netleştirecek
- DigitalOcean gibi VPS/PaaS dünyasında deploy edebilecek
- Railway benzeri platformlarla hızlı MVP deploy’ı anlayacak
- CI/CD’nin minimum gerekli halini kurabilecek (test + build + deploy)
- Lokal debug → staging → production yayın akışını oturtacak
- Prod ortamında log/monitoring ve rollback planı yapacak

---

# 1) Hosting seçenekleri: Ne zaman hangisi?

## 1️⃣ VPS (DigitalOcean / Hetzner / VM / EC2 / Compute Engine)
**Ne zaman iyi?**
- Düşük maliyet
- Tam kontrol
- Tek makineyle hızlı ilerleme

**Artı**
- Basit: Docker compose ile bile yürür
- Taşınabilirlik yüksek

**Eksi**
- Patch, update, güvenlik sorumluluğu sende
- Monitoring/backup sorumluluğu sende

> Solo founder için “kontrollü basitlik” isteyenlerde çok iyi.

---

## 2️⃣ PaaS (Render / Fly.io / Railway benzeri / DO App Platform vb.)
**Ne zaman iyi?**
- Ops yükünü azaltmak istiyorsan
- Hızlı deploy + auto restart + domain/ssl kolaylığı istiyorsan

**Artı**
- Hızlı setup
- Daha az bakım

**Eksi**
- Sınırlamalar ve platform kuralları
- Bazı yerlerde lock-in riski

> MVP’de “hız” için harika, ama kritik bileşenleri taşınabilir kur.

---

## 3️⃣ Serverless (Cloud Run / Lambda / Functions)
**Ne zaman iyi?**
- Trafik dalgalıysa
- “0’dan başlat” maliyet avantajı varsa
- Background job + event temelli iş çoksa

**Artı**
- Auto scale
- Yönetim düşük

**Eksi**
- Soğuk başlangıç
- Observability ve IAM karmaşıklığı
- Lock-in riski artabilir

> Özellikle API + job trigger için güçlü, ama her şeyi serverless yapmak şart değil.

---

# 2) “Multi-cloud” (GCP + AWS birlikte) nasıl düşünülmeli?

MVP aşamasında multi-cloud “havalı” değil, çoğu zaman “yük” olabilir.  
Ama senin gibi ihtiyaçlarda (ör. BigQuery GCP’de, cache/Dynamo AWS’de vs.) gerçekçi.

### Profesyonel kural:
> Multi-cloud kararını **veri yerleşimi** ve **maliyet/perf** belirler.  
> “Yedek olsun” diye erken multi-cloud genelde gereksizdir.

### Sağlıklı yaklaşım:
- Birincil cloud: ana compute + ana network
- İkincil cloud: gerçekten mecbur olan parça
- Arayüzler/SDK bağımlılıklarını minimize et

---

# 3) Vendor lock-in’i azaltma (07’nin ana teması)

Lock-in genelde “servis”ten değil, **kodun içine gömülen varsayımlardan** gelir.

## Pratik önlemler:
- Storage: S3-uyumlu seç (S3/R2/Minio/DO Spaces)
- Queue: arayüz ile soyutla (PubSub/SQS/Rabbit/Redis queue)
- Email/SMS: provider’ı interface arkasına al
- Secrets: environment değişkenleri + secret manager (opsiyona bağlı)

> Amaç: “1 günde taşırım” değil, “taşınmak mümkün olsun”.

---

# 4) Lokal → Staging → Production: MVP akış standardı

## 0️⃣ Lokal ortam (developer experience)
Minimum hedef:
- Tek komutla ayağa kalkmalı
- Debug edilebilir olmalı

Örnek hedefler:
- `make dev` veya `docker compose up`
- DB + cache + app birlikte kalksın
- Hot reload mümkünse

### Lokal debug prensipleri
- Her request’e `request_id` bas
- Log’larda user_id/job_id taşı
- Hata mesajı geliştiriciye “ne yapacağını” söylemeli

> “Çalışmıyor” değil, “Nerede bozuldu?” görülebilmeli.

---

## 1️⃣ Staging (prod’e benzeyen test ortamı)
Staging’in amacı:
- Prod’e sürpriz taşımamak
- Migration, env, secrets, build farklarını görmek

Minimum staging kuralı:
- Aynı Docker image
- Aynı env formatı
- Aynı DB şeması (küçük veriyle)

---

## 2️⃣ Production
Prod’de amaç:
- Stabilite
- Geri dönüş planı (rollback)
- Observability

MVP’de prod şu üç şeye sahip olmalı:
1) Log’lar erişilebilir
2) Basit healthcheck
3) Crash edince yeniden başlatma

---

# 5) CI/CD: Solo founder için “minimum profesyonel” kurulum

CI/CD’yi “kurumsal” gibi değil, **1–3 kişilik ekip** gibi kuracağız.

## ✅ Minimum pipeline (önerilen)
**PR/Push olduğunda:**
1) Lint + test
2) Build (Docker image veya artifact)
3) Deploy staging (opsiyonel ama çok faydalı)

**Tag/Release olduğunda:**
1) Build
2) Deploy production
3) Smoke test (basit endpoint kontrolü)

> Bu kadar. Daha fazlası şu an şart değil.

---

## 🧱 CI/CD için karar noktaları (stack bağımsız)

### Build tipi
- Docker image önerilir (taşınabilirlik için)

### Registry
- GitHub Container Registry / Docker Hub / ECR / GCR

### Deploy stratejisi (MVP için)
- “Rolling” veya “replace”
- Blue/Green erken aşamada opsiyonel

### Secrets yönetimi
- CI secrets (GitHub Actions Secrets vb.)
- Prod secret manager (opsiyonel)

---

# 6) Platformlara göre pratik yerleşim (örnek modeller)

Bu bölüm “Vercel yoksa ne var?” sorusunu çözer.

## Model A – VPS + Docker Compose (çok taşınabilir)
- DigitalOcean droplet
- Nginx + app + db + redis (compose)
- GitHub Actions → SSH ile deploy veya docker pull + restart

**Artı:** taşınabilir, ucuz  
**Eksi:** bakım sende

---

## Model B – PaaS (Railway benzeri) + Managed DB
- App platform üzerinde deploy
- DB managed (Postgres)
- Object storage S3 uyumlu

**Artı:** hızlı, ops az  
**Eksi:** bazı limitler, fiyat büyüyebilir

---

## Model C – Serverless API + Background Jobs ayrı
- API: Cloud Run / Lambda
- Jobs: queue + worker
- Storage: S3 uyumlu
- DB: managed

**Artı:** scale iyi  
**Eksi:** IAM ve gözlemleme karmaşık

---

## Model D – Hybrid (GCP + AWS)
Örn:
- Data & analytics GCP (BQ)
- App compute AWS (ECS/EC2/Lambda)
- Storage S3 uyumlu

**Artı:** ihtiyaç bazlı optimum  
**Eksi:** karmaşıklık

> MVP’de hybrid kullanacaksan, “neden” dokümante et.

---

# 7) MVP’de “prod’a çıkma” kontrol listesi (gerçekçi)

## ✅ Zorunlu (MVP bile olsa)
- HTTPS (domain + SSL)
- Basic auth/session güvenliği
- Upload limitleri (size/type)
- Rate limit (en azından kaba)
- Logs erişimi
- Basit backup planı (DB snapshot)

## ✅ Çok önerilen
- Error tracking (Sentry vb.)
- Uptime check (basit ping)
- Minimal dashboard (CPU/RAM)

## ❌ Şimdilik gereksiz (çoğu ürün için)
- Kubernetes
- Service mesh
- Multi-region
- Tam SRE setup

---

# 🧪 SilentCut Case Study – Bu hafta neye denk geliyor?

SilentCut benzeri ürünlerde pratik ihtiyaçlar:
- Upload → processing → download
- Background job + worker
- Object storage (S3 uyumlu)
- CDN veya download performansı
- Maliyet görünürlüğü
- Burst trafik yönetimi

Bu yüzden “iyi MVP altyapısı” şuna benzer:
- UI/API hızlı deploy (PaaS veya VPS)
- Worker ayrı ölçeklenebilir (gerekirse)
- Storage S3 uyumlu (taşınabilir)

> İlk gün mikroservis değil, **doğru sınır ve doğru deploy** önemli.

---

# 🛠️ Bu haftanın görevleri

## 1️⃣ Kendi ürünün için “deployment modeli” seç
Aşağıdakilerden birini seç ve gerekçelendir:
- VPS + Docker
- PaaS + managed DB
- Serverless + worker
- Hybrid (GCP+AWS)

> Seçim kriteri: hız + maliyet + bakım yükü

---

## 2️⃣ Lokal geliştirme akışını tanımla (tek sayfa)
- Projeyi çalıştırma komutu
- Debug adımları
- Env variable formatı
- Minimum dependency list

---

## 3️⃣ Staging planı yaz
- Aynı image mi?
- Aynı env mi?
- Migration nasıl?

---

## 4️⃣ CI/CD pipeline taslağı çiz
- PR → test/build
- Tag → prod deploy
- Rollback planı

---

## ✅ Haftanın çıktıları

Bu hafta sonunda elinde:

- Seçtiğin hosting modelinin gerekçesi
- Lokal → staging → prod akışı
- Minimum CI/CD pipeline
- Lock-in azaltma planı
- Prod checklist

olmalı.

---

## ⚠️ Son uyarı

> Deployment düzeni olmayan ürün,  
> büyüyünce değil, **ilk kriz anında** kaybeder.

---

## 🔜 Sonraki hafta

**08 – Monitoring, Logging, Alerting & Operasyon**

- Log standardı (request_id, job_id)
- Metric’ler (latency, error, queue depth)
- Alerting (ne zaman sayfa atarsın?)
- Runbook (krizde ne yapacaksın?)
- MVP’de minimum observability

---
