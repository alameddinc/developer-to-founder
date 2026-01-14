# 07 – Extras  
## Pratik CI/CD Şablonları, Deploy Akışları ve Platform-Özel İpuçları

Bu dosyanın amacı:
> 07. haftanın README’sini “konsept” seviyesinden çıkarıp,  
> **uygulanabilir, kopyalanabilir** pratik akışlar vermek.

Buradaki örnekler:
- Teknoloji bağımsız (Go/Node/Next fark etmez)
- Platform bağımsız (AWS/GCP/DO/PaaS fark etmez)
- “Solo founder” gerçekliğine uygun (minimum ama profesyonel)

---

# 1) Minimum CI Pipeline (Pseudo) – Her projeye uyar

## ✅ PR / push pipeline (kalite kapısı)
Amaç:
- Çöp kodu prod’a göndermemek
- Aynı zamanda yavaşlamamak

**Adımlar**
1. Checkout
2. Setup runtime (Go/Node vs.)
3. Install dependencies
4. Lint
5. Unit tests
6. Build artifact (opsiyonel)
7. (İsteğe bağlı) Docker build

**Kurallar**
- Test fail → merge yok
- Lint fail → merge yok
- Build fail → merge yok

> MVP’de bile “lint + test” seni hızlandırır.  
> Çünkü prod’da debug yerine PR’da düzeltirsin.

---

## ✅ Release / tag pipeline (prod yayın)
Amaç:
- Prod deploy’u standartlaştırmak
- Kimin deploy ettiği belirsiz olmasın

**Adımlar**
1. Tag ile tetiklenir (`v1.2.3`)
2. Build (artifact/Docker image)
3. Push image/registry
4. Deploy prod
5. Smoke test (1 endpoint)
6. (İsteğe bağlı) Slack/email bildirim

**En önemli kural**
> Prod deploy “tek komut / tek pipeline” olmalı.  
> “Ben ssh açıp bir şey yaptım” sürdürülemez.

---

# 2) Minimum GitHub Actions örnekleri (şablon mantığı)

Not: Aşağıdaki bloklar “tam YAML” değil, bilinçli olarak **şablon**.  
Kendi projenin diline göre step’leri değiştir.

## PR pipeline şablonu
- Trigger: `pull_request`
- Steps: test + lint + build

**Öneri**
- Go: `go test ./...`, `golangci-lint run`
- Node: `npm test`, `npm run lint`, `npm run build`

---

## Release pipeline şablonu
- Trigger: `push tags v*`
- Steps: docker build → push → deploy

> “Deploy step” platforma göre değişir.  
> Aşağıda VPS / PaaS / Serverless örnekleri var.

---

# 3) VPS (DigitalOcean/EC2/VM) için basit ve taşınabilir deploy akışı

## Model: Docker Compose + Nginx
Bu modelin amacı:
- Maksimum taşınabilirlik
- Minimum vendor bağımlılığı

### VPS tarafında (bir kere kurarsın)
- Docker / docker-compose
- Reverse proxy (Nginx / Caddy)
- `.env` dosyası veya secrets yaklaşımı
- Volume’lar (db data, uploads vs.)

### Deploy mantığı
1. CI image build eder, registry’ye push eder
2. VPS image’ı çeker
3. `docker compose up -d` ile günceller

---

## ✅ SSH ile “çek-güncelle” deploy (en pratik)
**Akış:**
- CI → VPS’ye SSH ile bağlan
- `docker pull`
- `docker compose up -d`
- `docker image prune` (opsiyonel)

**Avantaj**
- Aşırı basit
- Sürpriz az

**Risk**
- SSH anahtarı / yetki yönetimi düzgün olmalı

---

## Rollback (VPS için MVP seviyesi)
Rollback için iki yaklaşım:

### A) Önceki image tag’i
- `docker compose` dosyasında image tag’i `v1.2.2` yap
- `docker compose up -d`

### B) “latest” kullanma
> Prod’da `latest` kullanmak risk artırır.  
> Her zaman version tag kullan.

---

# 4) PaaS (Railway benzeri / Render / Fly / DO App Platform) ipuçları

Bu platformlar “hız” için çok iyi ama şu noktalara dikkat:

## ✅ 1) Environment değişkenleri standardı
- Lokal `.env.example` dosyası olsun
- Staging ve prod aynı anahtarları kullansın
- Eksik env varsa app boot etmesin

## ✅ 2) Migration stratejisi
- Deploy öncesi migration
- Veya app boot sırasında migration (riskli olabilir)
- MVP’de en basit yaklaşım:
  - release pipeline’da “migration job” step’i

## ✅ 3) Healthcheck şart
- PaaS’lar healthcheck ile restart eder
- `/healthz` gibi basit endpoint koy

## ✅ 4) Log erişimi
- UI üzerinden log var mı?
- Export / sink destekliyor mu?

> “Log göremiyorsan prod yoktur.”

---

# 5) Serverless deploy akışı (Cloud Run / Lambda benzeri)

Serverless seçiyorsan minimum hedef:
- Build → deploy → smoke test

## Cloud Run benzeri model
- Docker image build
- Registry’ye push
- Service deploy (revision)
- Traffic switch (opsiyonel)

**Rollback**
- Önceki revision’a trafik yönlendir

> Serverless’in en büyük artısı: rollback kolaylığıdır.

---

# 6) Lokal debug & run: MVP’de standartlaştır (ekipte hayat kurtarır)

## ✅ Tek komut hedefi
- `make dev`
- veya `docker compose up`

Bu komut şunları yapmalı:
- App
- DB (Postgres)
- Cache/queue (Redis)
- (Opsiyonel) object storage emulator (Minio)

## ✅ Log formatı
- her log’da `request_id`
- background job’da `job_id`
- kullanıcı varsa `user_id`

## ✅ Hata çıktısı
- Lokal ortamda: ayrıntılı error
- Prod ortamda: kullanıcıya sade mesaj + log’da detay

---

# 7) “MVP’den prod’a çıkma” mini kontrol listesi (pratik)

## Zorunlu
- HTTPS
- Domain + SSL
- Upload limit (dosya boyutu, format)
- Rate limiting (kaba bile olsa)
- Log erişimi
- DB backup (snapshot)
- Health endpoint

## Çok önerilen
- Error tracking (Sentry vb.)
- Uptime ping
- Basit runbook (krizde ne yapacağım)

---

# 8) CI/CD’de sık yapılan hatalar

❌ Prod deploy’u manuel yapmak  
❌ `latest` image kullanmak  
❌ Env’leri belgesiz bırakmak  
❌ Migration’ı unutmak  
❌ Rollback planı olmamak  
❌ Log/healthcheck olmadan prod’a çıkmak

> “Hızlı çıkayım” diye bunları atlamak,  
> ilk krizde 10x zaman kaybettirir.

---

# 9) Önerilen repo yapısı (teknoloji bağımsız)

- `/deploy`
  - `docker-compose.prod.yml`
  - `nginx/`
  - `scripts/`
- `.env.example`
- `Makefile` (veya `taskfile`)
- `.github/workflows/`
  - `ci.yml`
  - `release.yml`

Amaç:
> Projeyi devralan biri 30 dakikada deploy edebilsin.

---

# 10) Mini egzersiz (bu hafta için)

1) Lokal çalıştırma komutunu yaz (tek komut)
2) Staging env’yi tanımla
3) Prod deploy’ı pipeline’a bağla
4) Rollback adımını yaz
5) Smoke test endpoint’i ekle (`/healthz`)

Çıktı:
> “Ben bu ürünü her gün 5 dakikada publish ederim” seviyesine gelmek.

---
