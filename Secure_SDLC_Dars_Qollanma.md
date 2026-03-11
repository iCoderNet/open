# 🔐 Kiber Xavfsizlik | Dars Qo'llanma
# Mavzu: Secure SDLC — Xavfsiz Dasturiy Ta'minot Ishlab Chiqish Jarayoni

> **Daraja:** O'rta va yuqori  
> **Davomiyligi:** 90–120 daqiqa  
> **Tayyorlagan:** Kiber Xavfsizlik bo'yicha o'qituvchi  
> **Maqsad:** Talabalarga dasturiy ta'minot hayotiy tsikli davomida xavfsizlikni qanday ta'minlash kerakligini to'liq tushuntirish

---

## 📋 Mundarija

1. [Kirish va motivatsiya](#1-kirish-va-motivatsiya)
2. [SDLC nima? Oddiy taqqoslash orqali](#2-sdlc-nima)
3. [Nima uchun xavfsizlik kerak? Statistika va haqiqiy misollar](#3-nima-uchun-xavfsizlik-kerak)
4. [Secure SDLC modellari](#4-secure-sdlc-modellari)
5. [Har bir bosqich: Chuqur tahlil](#5-har-bir-bosqich-chuqur-tahlil)
6. [Threat Modeling — Tahdidlarni modellashtirish](#6-threat-modeling)
7. [Security Testing turlari](#7-security-testing-turlari)
8. [DevSecOps — Zamonaviy yondashuv](#8-devsecops)
9. [Xavfsizlik standartlari va freymvorklari](#9-xavfsizlik-standartlari)
10. [Amaliy topshiriq](#10-amaliy-topshiriq)
11. [Xulosa va takrorlash savollari](#11-xulosa)

---

## 1. Kirish va Motivatsiya

### 🏗️ Taqqoslash: Bino qurish vs Dastur yozish

Tasavvur qiling: Bir me'mor bino qurmoqchi. U ikki xil yo'l tuta oladi:

**Yo'l A (Noto'g'ri):**
> Avval butun binoni qurib bo'ladi, keyin "Hmm, eshiklar qulfmi? Derazalar mustahkami?" deb o'ylaydi. Muammolar topilsa, devorlarni buzib, qayta quradi. Bu **qimmat, sekin va xavfli**.

**Yo'l B (To'g'ri):**
> Loyiha boshlashdan oldin: "Zilzilaga chidamlimi? Yong'in yo'laklari bormi? Qulflar xavfsizmi?" deb rejalashtiradi. Har bir qavatni qurganida tekshiradi. Natija — **mustahkam, xavfsiz, arzon**.

Xuddi shunday, dasturiy ta'minotda ham:

| | Noto'g'ri yondashuv | Secure SDLC |
|---|---|---|
| **Xavfsizlik qachon?** | Oxirida, chiqarishdan oldin | Har bir bosqichda |
| **Muammo topilsa?** | Butun kodni qayta yozish | Kichik tuzatish |
| **Xarajat** | 100x qimmat | Arzon |
| **Xavf** | Juda yuqori | Minimal |

> **💡 Asosiy g'oya:** Xavfsizlik — oxirda qo'shiladigan "lak" emas, balki **poydevordan boshlanadigan** jarayon.

---

## 2. SDLC Nima?

### Software Development Life Cycle — Dasturiy Ta'minot Hayotiy Tsikli

SDLC — bu dastur tug'ilishidan tortib, "o'lim"igacha bo'lgan barcha bosqichlarning rasmiy jarayoni.

### 🔄 Klassik SDLC bosqichlari:

```
  [1. Rejalashtirish]
         ↓
  [2. Tahlil / Talablar]
         ↓
  [3. Loyihalash / Design]
         ↓
  [4. Ishlab chiqish / Coding]
         ↓
  [5. Sinov / Testing]
         ↓
  [6. Joylash / Deployment]
         ↓
  [7. Qo'llab-quvvatlash / Maintenance]
         ↓
    (tsikl takrorlanadi)
```

### 🍕 Pizzaga o'xshatish:

| SDLC bosqichi | Pizza tayyorlash |
|---|---|
| Rejalashtirish | Qanday pizza? Qancha odamga? |
| Talablar | Ingredientlar ro'yxati |
| Design | Resept, qorishma tartibi |
| Coding | Xamir yasash, pishirish |
| Testing | Tatib ko'rish |
| Deployment | Stolga qo'yish |
| Maintenance | Qolganini saqlab qo'yish |

### ❗ Muammo qayerda?

**Oddiy SDLC** da xavfsizlik faqat 5-bosqich (Testing) da o'ylangan. Bu juda kech!

**Secure SDLC** da xavfsizlik **har bir bosqichda** o'ylangan.

---

## 3. Nima Uchun Xavfsizlik Kerak?

### 📊 Dahshatli statistika

> **IBM "Cost of a Data Breach" 2023 hisoboti:**
> - O'rtacha ma'lumotlar buzilishi narxi: **$4.45 million**
> - Buzilishni aniqlash va to'xtatish uchun o'rtacha vaqt: **277 kun**
> - Dasturda topilgan xatolikni tuzatish narxi:
>   - **Loyiha bosqichida:** $1
>   - **Kodlash bosqichida:** $10
>   - **Test bosqichida:** $100
>   - **Chiqarilgandan keyin:** $10,000+

### 🕰️ "Muammoni erta topish qoidasi" (Rule of Ten)

```
Loyiha → Dizayn → Kod → Test → Chiqarish
  $1  →   $10  → $100 → $1,000 → $10,000
```

Bu **10x qoida** deyiladi — har bir bosqich o'tganda tuzatish narxi 10 baravar oshadi.

### 🌍 Haqiqiy dunyo misollari

#### Misol 1: Equifax buzilishi (2017)
- **Nima bo'ldi?** Apache Struts frameworkida ma'lum zaiflik bor edi
- **Nima qilishmadi?** Patch (yangilanish) o'z vaqtida o'rnatilmadi
- **Oqibat:** 147 million amerikalikning shaxsiy ma'lumotlari o'g'irlandi
- **Zarar:** $575 million jarima + obro' yo'qotish
- **Secure SDLC bo'lganda:** Patch management jarayoni bu muammoni oldini olar edi

#### Misol 2: Log4Shell (2021)
- **Nima bo'ldi?** Java'ning mashhur Log4j kutubxonasida kritik zaiflik
- **Qancha ta'sirlandi?** Internetdagi dasturlarning ~44% ta'sirlandi
- **Secure SDLC bo'lganda:** Dependency scanning bu zaiflikni erta aniqlar edi

#### Misol 3: SolarWinds (2020)
- **Nima bo'ldi?** Supply chain hujumi — dasturning yangilanish jarayoniga kirib olindi
- **Qancha ta'sirlandi?** 18,000+ kompaniya, shu jumladan AQSh hukumati idoralari
- **Secure SDLC bo'lganda:** Build pipeline security bu hujumni to'xtatishi mumkin edi

---

## 4. Secure SDLC Modellari

### 4.1 Microsoft SDL (Security Development Lifecycle)

Microsoft 2004 yilda Trustworthy Computing tashabbusu doirasida ishlab chiqqan. Eng mashhur Secure SDLC modellaridan biri.

```
Training → Requirements → Design → Implementation → Verification → Release → Response
    ↑                                                                              |
    └──────────────────────────── Feedback loop ───────────────────────────────────┘
```

**Asosiy tamoyillar:**
- Har bir bosqichda aniq xavfsizlik faoliyatlari belgilangan
- Tahdidlarni modellashtirish majburiy
- Penetration testing chiqarishdan oldin shart

### 4.2 OWASP SAMM (Software Assurance Maturity Model)

OWASP tomonidan ishlab chiqilgan, 4 ta asosiy domain bo'yicha tashkilotning xavfsizlik darajasini o'lchaydi:

```
┌─────────────────────────────────────────────────────────┐
│                    OWASP SAMM                           │
├──────────────┬──────────────┬─────────────┬────────────┤
│  Governance  │   Design     │ Implementat │ Verificat  │
├──────────────┼──────────────┼─────────────┼────────────┤
│ • Strategy   │ • Threat     │ • Secure    │ • Architect│
│ • Policy     │   Assessment │   Build     │   Review   │
│ • Education  │ • Security   │ • Secure    │ • Code     │
│ • Compliance │   Requirem   │   Deploy    │   Review   │
│              │ • Architecture│ • Defect    │ • Security │
│              │              │   Manage    │   Testing  │
└──────────────┴──────────────┴─────────────┴────────────┘

Har bir domain 3 bosqichda o'lchanadi:
Bosqich 1 (Yetarli) → Bosqich 2 (Yaxshi) → Bosqich 3 (A'lo)
```

### 4.3 BSIMM (Building Security In Maturity Model)

Real kompaniyalarning xavfsizlik amaliyotlarini tahlil qilib yaratilgan model. 100+ kompaniya ma'lumotlari asosida.

**4 domain, 12 amaliyot:**
1. **Governance** (Boshqaruv): Strategy, Compliance, Training
2. **Intelligence** (Razvedka): Attack Models, Security Features, Research
3. **SSDL Touchpoints** (SSDL nuqtalari): Architecture Analysis, Code Review, Security Testing
4. **Deployment** (Joylash): Penetration Testing, Software Environment, Configuration & Vulnerability Management

### 4.4 Agile va Secure SDLC: "Security Sprint"

Agile metodologiyasida xavfsizlik qanday qo'shiladi?

```
Sprint rejalashtirish → Xavfsizlik talablari qo'shish
       ↓
  Sprint (2 hafta) → Har kuni SAST tekshiruvi
       ↓
  Sprint sharhi → Xavfsizlik ko'rib chiqish
       ↓
  Retrospektiv → Xavfsizlik saboqlari
```

**"Security as a User Story" — Xavfsizlikni foydalanuvchi tarixlari sifatida:**

```
Oddiy User Story:
"Foydalanuvchi sifatida, tizimga kirish uchun parol kiritmoqchiman"

Secure User Story:
"Foydalanuvchi sifatida, tizimga kirish uchun parol kiritmoqchiman,
SHUNDAY KI parolim brute-force hujumlaridan himoyalangan bo'lsin
va noto'g'ri kirishlar qayd etilsin"

Qabul qilish mezonlari (Acceptance Criteria):
✓ 5 marta noto'g'ri urinishdan keyin hisob bloklash
✓ Login urinishlari audit logga yoziladi
✓ Parol kamida 12 belgi, 1 ta maxsus belgi
✓ Brute-force himoyasi (rate limiting) mavjud
```

---

## 5. Har Bir Bosqich: Chuqur Tahlil

### 📍 BOSQICH 1: Rejalashtirish (Planning)

#### Bu bosqichda nima qilinadi?

**Maqsad:** Loyiha miqyosi, resurslar va xavfsizlik talablarini aniqlash

#### Xavfsizlik faoliyatlari:

**1. Xavfsizlik siyosatini aniqlash**
- Qanday ma'lumotlar saqlanadi? (PII, moliyaviy, tibbiy?)
- Qanday qonun-qoidalar qo'llaniladi? (GDPR, HIPAA, PCI DSS?)
- Xavfsizlik maqsad va talablari nima?

**2. Risk baholash**

```
Risk = Ehtimollik × Ta'sir

Masalan:
- SQL Injection ehtimolligi: Yuqori (8/10)
- SQL Injection ta'siri: Juda yuqori (9/10)
- Risk = 8 × 9 = 72 (Kritik)
```

**Risk matritsasi:**

```
         |  Kichik  |  O'rta  |  Katta  |  Kritik  |
---------|----------|---------|---------|----------|
Yuqori   | O'rta    | Yuqori  | Kritik  | Kritik   |
O'rta    | Kichik   | O'rta   | Yuqori  | Kritik   |
Past     | Kichik   | Kichik  | O'rta   | Yuqori   |
Juda past| Kichik   | Kichik  | Kichik  | O'rta    |
```

**3. Jamoa uchun xavfsizlik treningi rejasi**
- Ishlab chiquvchilar uchun: Secure coding
- Test muhandislari uchun: Security testing
- Arxitektorlar uchun: Secure design patterns

---

### 📍 BOSQICH 2: Talablar (Requirements)

#### 🛡️ Xavfsizlik talablarining 3 turi:

**1. Funksional xavfsizlik talablari**

Tizim NIMA QILISHI kerak:
- Foydalanuvchi autentifikatsiyasi bo'lishi kerak
- Faoliyatlar audit logga yozilishi kerak
- Ma'lumotlar shifrlangan holda saqlanishi kerak

**2. Funksional bo'lmagan xavfsizlik talablari**

Tizim QANDAY ISHLASHI kerak:
- Tizim DDoS hujumlariga bardosh berishi kerak
- Sessiya 30 daqiqasiz harakatdan keyin tugashi kerak

**3. Muvofiqlik talablari**

Qanday standartlarga rioya qilish kerak:
- OWASP Top 10 ga mos kelish
- GDPR ga muvofiqlik
- ISO 27001 sertifikati

#### CIA Triad — Xavfsizlikning 3 ustuni:

```
         🔐 Xavfsizlik
              ↑
    ┌─────────┼──────────┐
    ↓         ↓          ↓
Konfiden-  Yaxlitlik  Mavjudlik
  liyat    (Integrity)(Availab.)
(Confid.)
    ↓         ↓          ↓
Ma'lumot   Ma'lumot   Tizim har
faqat      o'zgarma-  doim ishlashi
ruxsatli   ganligi    kerak
odamlar    kerak
uchun
```

**Qo'riqlash misoli:**

| Xavf | Konfidensiallik | Yaxlitlik | Mavjudlik |
|------|-----------------|-----------|-----------|
| SQL Injection | ✓ (ma'lumot o'qish) | ✓ (ma'lumot o'zgartirish) | ✓ (DB o'chirish) |
| DDoS | ✗ | ✗ | ✓ |
| Man-in-the-Middle | ✓ | ✓ | ✗ |

---

### 📍 BOSQICH 3: Loyihalash (Design)

#### 🏛️ Xavfsiz Dizayn Tamoyillari

**Tamoyil 1: Minimal imtiyoz prinsipi (Principle of Least Privilege)**

> **Taqqoslash:** Kompaniyaning yangi xodimi barcha xonalarga kira olmaydi — faqat o'ziga kerakli xonalarga. Xuddi shunday, dastur komponentlari ham faqat kerakli resurslarga kirish huquqiga ega bo'lishi kerak.

```
❌ Noto'g'ri:
Veb dastur → Root huquqi bilan DB ga kiradi
             (Barcha jadvallarni o'chirishga ruxsat!)

✓ To'g'ri:
Veb dastur → Faqat kerakli jadval, faqat READ/WRITE ruxsati bilan
```

**Tamoyil 2: Chuqurlikda mudofaa (Defense in Depth)**

> **Taqqoslash:** O'rta asrlardagi qal'a — faqat bitta devor emas, xandaq + tashqi devor + ichki devor + minora + qo'riqchilar. Har bir qatlam mustaqil himoya qiladi.

```
Internet
   ↓
[Firewall - 1-qatlam]
   ↓
[WAF (Web Application Firewall) - 2-qatlam]
   ↓
[Load Balancer - 3-qatlam]
   ↓
[Application Server - 4-qatlam]
   ↓
[Database Firewall - 5-qatlam]
   ↓
[Encrypted Database - 6-qatlam]
```

**Tamoyil 3: Xavfsiz standart holat (Secure by Default)**

> **Taqqoslash:** Yangi smartfon sotib olsangiz, Bluetooth o'chirilgan holda keladi. Kerak bo'lsa, siz yoqasiz — teskari emas.

```
❌ Noto'g'ri default:
- Debug mode: ON
- Admin panel: hamma uchun ochiq
- Xatolar: foydalanuvchiga ko'rsatiladi

✓ To'g'ri default:
- Debug mode: OFF
- Admin panel: IP restriction
- Xatolar: faqat logga yoziladi
```

**Tamoyil 4: Ishonchning yo'qligi (Zero Trust Architecture)**

> **Taqqoslash:** "Ishon, lekin tekshir" emas, balki "Hech qachon ishonma, doim tekshir" — hatto ichki tarmoqdagi foydalanuvchilar ham.

```
Klassik model:          Zero Trust model:
Tashqi = Xavfli         Hamma = Potensial xavfli
Ichki = Ishonchli       Har so'rov = Autentifikatsiya
                        Har kirish = Avtorizatsiya
                        Har harakat = Monitoring
```

**Tamoyil 5: Hujum yuzasini kamaytirish (Attack Surface Reduction)**

> **Taqqoslash:** Uyingizning nechta eshigi va derazasi bo'lsa, o'g'ri kirishi uchun shuncha imkoniyat. Keraksiz eshiklarni yoping.

```
Attack Surface = Barcha kirish nuqtalari

Kamaytirish yo'llari:
• Keraksiz API endpoint'larni o'chirish
• Ishlatilmagan portlarni yopish
• Keraksiz servislarni o'chirish
• Eskirgan kutubxonalarni olib tashlash
```

#### Arxitektura diagrammasi: Xavfsiz 3-qavat arxitektura

```
┌─────────────────────────────────────────────────────┐
│                  INTERNET                           │
└─────────────────────┬───────────────────────────────┘
                      ↓
┌─────────────────────────────────────────────────────┐
│            PRESENTATION LAYER (DMZ)                 │
│  [CDN] → [WAF] → [Load Balancer] → [Web Servers]   │
│  • HTTPS only • DDoS himoya • Static content       │
└─────────────────────┬───────────────────────────────┘
                      ↓ (Firewall #1)
┌─────────────────────────────────────────────────────┐
│              APPLICATION LAYER                      │
│  [App Server 1] [App Server 2] [App Server 3]       │
│  • Input validation • Session management            │
│  • Business logic • Authentication                  │
└─────────────────────┬───────────────────────────────┘
                      ↓ (Firewall #2)
┌─────────────────────────────────────────────────────┐
│                DATA LAYER                           │
│  [Primary DB] ←→ [Replica DB] [Cache] [Backup]     │
│  • Encryption at rest • Access control              │
│  • Audit logging • Data masking                     │
└─────────────────────────────────────────────────────┘
```

---

### 📍 BOSQICH 4: Ishlab Chiqish (Implementation / Coding)

#### 💻 Xavfsiz Kod Yozish Standartlari

**OWASP Top 10 — Eng Ko'p Uchraydigan Zaifliklar (2021)**

```
A01: Broken Access Control         ← #1 ga ko'tarildi
A02: Cryptographic Failures        ← Shifrlash muammolari
A03: Injection                     ← SQL, NoSQL, Command...
A04: Insecure Design               ← Dizayn darajasidagi xato
A05: Security Misconfiguration     ← Noto'g'ri sozlash
A06: Vulnerable Components         ← Eskirgan kutubxonalar
A07: Auth & Session Failures       ← Autentifikatsiya xatolari
A08: Software & Data Integrity     ← Yaxlitlik tekshiruvi yo'q
A09: Security Logging Failures     ← Log yetarli emas
A10: SSRF                          ← Server-Side Request Forgery
```

#### Xavfli vs Xavfsiz Kod Misollari:

**1. SQL Injection**

```python
# ❌ XAVFLI — SQL Injection ga ochiq
def get_user(username):
    query = "SELECT * FROM users WHERE username = '" + username + "'"
    return db.execute(query)

# Haker kiritadi: ' OR '1'='1
# Natijadagi query: SELECT * FROM users WHERE username = '' OR '1'='1'
# Bu BARCHA foydalanuvchilarni qaytaradi!

# ✓ XAVFSIZ — Parametrli so'rov
def get_user(username):
    query = "SELECT * FROM users WHERE username = ?"
    return db.execute(query, (username,))
    # yoki ORM ishlatish:
    return User.objects.filter(username=username)
```

**2. Parol saqlash**

```python
# ❌ XAVFLI — Ochiq matnda saqlash
def save_password(password):
    user.password = password  # "qwerty123" — to'g'ridan-to'g'ri

# ❌ HAM XAVFLI — MD5 yoki SHA1 ishlatish
import hashlib
def save_password(password):
    user.password = hashlib.md5(password.encode()).hexdigest()
    # MD5 rainbow table hujumlariga zaif!

# ✓ XAVFSIZ — bcrypt, Argon2 yoki PBKDF2
import bcrypt
def save_password(password):
    salt = bcrypt.gensalt(rounds=12)
    hashed = bcrypt.hashpw(password.encode(), salt)
    user.password = hashed
    # bcrypt avtomatik salt qo'shadi, sekin ishlaydi (brute-force qiyin)
```

**3. XSS (Cross-Site Scripting)**

```javascript
// ❌ XAVFLI — foydalanuvchi kiritmasini to'g'ridan-to'g'ri ko'rsatish
function showMessage(userInput) {
    document.getElementById('msg').innerHTML = userInput;
    // Haker kiritadi: <script>document.cookie</script>
}

// ✓ XAVFSIZ — encoding ishlatish
function showMessage(userInput) {
    const div = document.getElementById('msg');
    div.textContent = userInput;  // innerHTML emas, textContent!
    // Yoki server tomonda DOMPurify / encoding ishlatish
}
```

**4. Sensitive ma'lumotlarni loglash**

```python
# ❌ XAVFLI
import logging
logging.info(f"Login urinish: username={username}, password={password}")
# Log faylida parollar saqlanib qoladi!

# ✓ XAVFSIZ
logging.info(f"Login urinish: username={username}")
logging.debug(f"Login muvaffaqiyatli: user_id={user.id}")
# Parol HECH QACHON loglanmaydi
```

#### Kod ko'rish checklisti (Code Review Security Checklist):

```
AUTENTIFIKATSIYA
□ Parollar bcrypt/Argon2 bilan hashlanganmi?
□ Multi-factor authentication mavjudmi?
□ Brute-force himoyasi bormi?
□ "Parolni unutdim" xavfsizmi?

AVTORIZATSIYA
□ Har bir API endpoint da ruxsat tekshiruvi bormi?
□ Gorizontal imtiyoz oshirishdan himoyalanganmi?
□ (User A, User B ning ma'lumotlarini o'qiy oladimi?)

INPUT VALIDATSIYA
□ Barcha kiritma tekshirilganmi?
□ Parametrli so'rovlar ishlatilganmi?
□ Fayl yuklashda tur tekshiruvimi?

KRIPTOGRAFIYA
□ HTTPS ishlatilganmi?
□ Zaif algoritm (MD5, SHA1, DES) ishlatilmaganmi?
□ Kalitlar xavfsiz saqlanganmi?

LOGLASH
□ Xavfsizlik hodisalari loglanganmi?
□ Sensitive ma'lumotlar loglanmaganmi?
□ Log fayllar himoyalanganmi?
```

---

### 📍 BOSQICH 5: Sinov (Testing)

Ushbu bosqich [7-bo'lim](#7-security-testing-turlari) da chuqurroq yoritilgan.

**Asosiy xavfsizlik test turlari:**

```
SAST (Static Analysis)     — Kod ishlamasdan tekshirish
DAST (Dynamic Analysis)    — Ishlab turgan dasturni tekshirish
IAST (Interactive)         — Aralash usul
SCA (Component Analysis)   — Kutubxonalar tekshiruvi
Penetration Testing        — Hujumchi nuqtai nazaridan
```

---

### 📍 BOSQICH 6: Joylash (Deployment)

#### 🚀 Xavfsiz Deployment Amaliyotlari

**1. Konfiguratsiya boshqarish**

```
Production konfiguratsiyasi:
✓ Debug mode = OFF
✓ Xato xabarlari = foydalanuvchiga ko'rsatilmaydi
✓ Default parollar = o'zgartirilgan
✓ Keraksiz servislar = o'chirilgan
✓ Firewall qoidalari = minimal ruxsat
```

**2. Maxfiy ma'lumotlar (Secrets Management)**

```
❌ NOTO'G'RI:
# config.py faylida
DATABASE_URL = "postgres://admin:password123@db:5432/mydb"
API_KEY = "sk-1234567890abcdef"

# va bu kod GitHub ga push qilinadi!

✓ TO'G'RI:
# Environment variable dan o'qish
import os
DATABASE_URL = os.environ.get('DATABASE_URL')
API_KEY = os.environ.get('API_KEY')

# Yoki HashiCorp Vault, AWS Secrets Manager ishlatish
```

**3. Container xavfsizligi (Docker)**

```dockerfile
# ❌ XAVFLI Dockerfile
FROM ubuntu:latest
USER root
RUN apt-get install everything
EXPOSE 22  # SSH port ochiq!

# ✓ XAVFSIZ Dockerfile
FROM ubuntu:22.04-minimal  # Minimal base image
RUN useradd -r -s /bin/false appuser
USER appuser  # Root bo'lmagan foydalanuvchi
COPY --chown=appuser:appuser . /app
EXPOSE 8080  # Faqat kerakli port
HEALTHCHECK --interval=30s CMD curl -f http://localhost:8080/health
```

**4. CI/CD Pipeline xavfsizligi**

```yaml
# GitHub Actions xavfsiz pipeline misoli
name: Secure CI/CD Pipeline

on: [push, pull_request]

jobs:
  security-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      # 1. SAST tekshiruvi
      - name: Run SAST
        uses: github/codeql-action/analyze@v2
      
      # 2. Kutubxona zaifliklarini tekshirish
      - name: Dependency Check
        run: npm audit --audit-level=high
      
      # 3. Container image skaneri
      - name: Scan Docker Image
        uses: aquasecurity/trivy-action@master
      
      # 4. Secrets tekshiruvi
      - name: Check for secrets
        uses: trufflesecurity/trufflehog@main
```

---

### 📍 BOSQICH 7: Qo'llab-quvvatlash (Maintenance)

#### 🔧 Ongoing Security Activities

**1. Patch Management (Yangilanishlarni boshqarish)**

```
Zaiflik topildi
      ↓
CVE score baholash (CVSS)
      ↓
  ┌───┴───┐
CVSS 9-10  CVSS 7-8.9  CVSS < 7
(Kritik)   (Yuqori)    (O'rta/Past)
  ↓          ↓           ↓
24 soat    7 kun       30 kun
ichida    ichida       ichida
patch      patch        patch
```

**2. Incident Response (Hodisalarga javob)**

```
DETECT (Aniqlash)
    ↓
CONTAIN (Izolyatsiya)
    ↓
ERADICATE (Yo'q qilish)
    ↓
RECOVER (Tiklash)
    ↓
LESSONS LEARNED (Saboq olish)
    ↓
(Jarayonni yaxshilash)
```

**3. Xavfsizlik monitoring**

```
Log yig'ish → SIEM (Security Information & Event Management)
                ↓
           Korrelyatsiya
                ↓
           Anomaliya aniqlash
                ↓
           Alert → SOC jamoasi
                ↓
           Tekshiruv va javob
```

---

## 6. Threat Modeling

### Tahdidlarni Modellashtirish nima?

> **Taqqoslash:** Siz yangi uyga ko'chib o'tmoqchisiz. Qo'riqni rejalashtirishdan oldin o'ylaysiz: "Qaerdan o'g'ri kirishi mumkin? Qaysi derazalar zaif? Qo'shnilar kim?" Bu **threat modeling** bilan bir xil jarayon.

Threat modeling — dasturni yaratishdan **oldin** potensial xavflarni aniqlash va ular bilan kurashish strategiyasini belgilash jarayoni.

### STRIDE modeli (Microsoft tomonidan ishlab chiqilgan)

| Harf | Xavf turi | Ta'rif | CIA ta'siri |
|------|-----------|--------|-------------|
| **S** | Spoofing | Boshqa identitet ostida harakat qilish | Autentifikatsiya |
| **T** | Tampering | Ma'lumotlarni ruxsatsiz o'zgartirish | Yaxlitlik |
| **R** | Repudiation | Harakatni rad etish imkoniyati | Inkorsizlik |
| **I** | Information Disclosure | Ma'lumot sizib chiqishi | Konfidensiallik |
| **D** | Denial of Service | Xizmatni to'xtatish | Mavjudlik |
| **E** | Elevation of Privilege | Huquqlarni oshirish | Avtorizatsiya |

### STRIDE misolida: Onlayn bank tizimi

```
Tizim: Foydalanuvchi → [Login Sahifa] → [Bank API] → [Database]

S - Spoofing:    Haker boshqa user nomi bilan tizimga kirish
T - Tampering:   Tranzaksiya miqdorini o'zgartirish
R - Repudiation: "Men bu o'tkazmani qilmadim" deyish
I - Info Disc:   Hisoblar ma'lumotlari o'g'irlash
D - DoS:         Login sahifasini ishdan chiqarish
E - Elevation:   Oddiy user → Admin huquq olish
```

### PASTA (Process for Attack Simulation and Threat Analysis)

7 bosqichli, xavf markazlashgan threat modeling metodologiyasi:

```
Bosqich 1: Biznes maqsadlarini aniqlash
Bosqich 2: Texnik doirani aniqlash
Bosqich 3: Dasturni dekompozitsiya qilish
Bosqich 4: Tahdid tahlili
Bosqich 5: Zaiflik tahlili
Bosqich 6: Hujum modellashtirish
Bosqich 7: Risk va ta'sir tahlili
```

### DREAD — Risk baholash modeli

```
D - Damage Potential     (Zarar darajasi): 0-10
R - Reproducibility      (Takrorlanishi):  0-10
E - Exploitability       (Ekspluatatsiya): 0-10
A - Affected Users       (Ta'sirlangan):   0-10
D - Discoverability      (Topilishi):      0-10

Risk Score = (D + R + E + A + D) / 5

Masalan: SQL Injection
D = 9, R = 10, E = 8, A = 9, D = 7
Risk = (9+10+8+9+7)/5 = 8.6 → KRITIK
```

### Threat Modeling jarayoni — Qadamba-qadam:

```
1. TIZIMNI TUSHUNISH
   "Nima quryapmiz?"
   → Data flow diagram (DFD) chizish
   → Trust boundary larni belgilash

2. TAHDIDLARNI ANIQLASH
   "Nima noto'g'ri ketishi mumkin?"
   → STRIDE bo'yicha tahlil
   → Brainstorming sessiyasi

3. TAHDIDLARNI BAHOLASH
   "Qaysi tahdid muhimroq?"
   → DREAD yoki CVSS bilan baholash
   → Prioritizatsiya

4. CHORALARNI BELGILASH
   "Nima qilamiz?"
   → Har bir tahdid uchun mitigation
   → Implementatsiya rejasi

5. TEKSHIRISH
   "Choralar samarali?"
   → Penetration test
   → Audit
```

---

## 7. Security Testing Turlari

### 🔍 SAST — Static Application Security Testing

> **Taqqoslash:** Tibbiy rentgen — bemor kasallikni sezmaguncha, shifokor oldindan skelet va a'zolarni ko'rishi. SAST ham — dastur ishlamasdan, kod "skeleti"ni tekshiradi.

**Qanday ishlaydi?**
- Manba kod tahlil qilinadi
- Zaiflik patternlari qidiriladi
- Kod ishga tushirilmaydi

**Afzalliklari:**
- CI/CD ga integratsiya oson
- Tez ishlaydi
- Kodni yozayotganda xato topiladi

**Kamchiliklari:**
- Ko'p noto'g'ri ijobiy natija (false positive)
- Runtime muammolarini topa olmaydi

**Mashhur SAST vositalari:**

| Vosita | Til | Litsenziya |
|--------|-----|------------|
| SonarQube | 30+ til | Open source / Commercial |
| Checkmarx | 30+ til | Commercial |
| Veracode | 30+ til | Commercial |
| Bandit | Python | Open source |
| ESLint Security | JavaScript | Open source |
| Semgrep | 30+ til | Open source |
| CodeQL | 10+ til | Open source (GitHub) |

---

### 🔍 DAST — Dynamic Application Security Testing

> **Taqqoslash:** Shifokor bemorni og'riq sezayotgan joyini tekshiradi — yashab turgan tanani testlaydi. DAST ham — ishlab turgan dasturni tekshiradi.

**Qanday ishlaydi?**
- Ishlab turgan dasturga hujum simulatsiyasi
- Kiritma yuboradi, javobni tahlil qiladi
- Tizimni "outside-in" ko'radi

**Afzalliklari:**
- Runtime muammolarni topadi
- Real muhitda test
- Til mustaqil (qaysi tilda yozilganidan qat'iy nazar)

**Kamchiliklari:**
- Sekin ishlaydi
- Ba'zi zaifliklarni o'tkizib yuboradi
- Production muhitda xavfli bo'lishi mumkin

**Mashhur DAST vositalari:**

| Vosita | Maqsad | Litsenziya |
|--------|--------|------------|
| OWASP ZAP | Veb dasturlar | Open source |
| Burp Suite | Veb dasturlar | Commercial (Community free) |
| Nikto | Veb serverlar | Open source |
| Acunetix | Veb dasturlar | Commercial |
| Nessus | Tarmoq/Tizim | Commercial |

---

### 🔍 SCA — Software Composition Analysis

> **Taqqoslash:** Mahsulot tarkibini (ingredient list) tekshirish — sotib olgan ovqatdagi allergik moddalarni aniqlash. SCA ham — dasturingizdagi kutubxonalardagi zaifliklarni aniqlaydi.

**Nima tekshiradi?**
- Open source kutubxonalar
- Litsenziya muvofiqligi
- Ma'lum CVE lar

**Mashhur SCA vositalari:**

| Vosita | Litsenziya |
|--------|------------|
| OWASP Dependency-Check | Open source |
| Snyk | Open source / Commercial |
| WhiteSource | Commercial |
| npm audit | Open source (Node.js) |
| pip-audit | Open source (Python) |

---

### 🔍 Penetration Testing (Pen Test)

> **Taqqoslash:** Bank xavfsizligini tekshirish uchun o'z "o'g'ri"larini yuborish — ular kirish imkoniyatini topsa, haqiqiy o'g'rilar ham topadi. Pen testing ham shu — maxsus mutaxassislar hujumchi rolini o'ynaydi.

**Pen Test turlari:**

```
BLACK BOX          GREY BOX           WHITE BOX
(Qora quticha)     (Kulrang quticha)  (Oq quticha)

Haker nuqtai       Cheklangan         To'liq
nazaridan          ma'lumot bilan     ma'lumot bilan

Ma'lumot yo'q   →  Qisman ma'lumot → To'liq ma'lumot
(haqiqiy hujum)    (intern yoki        (audit)
                   hamkor)
```

**PTES (Penetration Testing Execution Standard) bosqichlari:**

```
1. Pre-engagement (Oldingi tayyorgarlik)
   → Doira, qoidalar, ruxsatnomalar

2. Intelligence Gathering (Ma'lumot yig'ish)
   → OSINT, tarmoq xaritasi, texnologiyalar

3. Threat Modeling (Tahdid modellashtirish)
   → Potensial hujum yo'llari

4. Vulnerability Analysis (Zaiflik tahlili)
   → Skanerlash, zaifliklarni aniqlash

5. Exploitation (Ekspluatatsiya)
   → Zaifliklardan foydalanish

6. Post Exploitation (Keyingi bosqich)
   → Lateral movement, privilege escalation

7. Reporting (Hisobot)
   → Executive summary + Technical details
```

**Pen Test hisoboti tuzilmasi:**

```
EXECUTIVE SUMMARY (Rahbarlar uchun)
• Test maqsadi
• Asosiy topilmalar (raqamlar bilan)
• Kritik xatarlar

TEXNIK HISOBOT (Mutaxassislar uchun)
• Har bir zaiflik:
  - Tavsif
  - Qanday topildi
  - Risk darajasi (CVSS)
  - Ekspluatatsiya yo'li (PoC)
  - Tuzatish tavsiyasi
  
TAVSIYALAR
• Qisqa muddatli (darhol)
• O'rta muddatli (1-3 oy)
• Uzoq muddatli (6-12 oy)
```

---

### 🔍 IAST — Interactive Application Security Testing

> SAST va DAST ning kombinatsiyasi — dastur ichidan kuzatadi, tashqaridan hujum qiladi. Eng aniq natijalar beradi.

```
SAST  +  DAST  =  IAST
Kod      Runtime   Kombinatsiya
tahlil   test      → Eng kam false positive
```

---

## 8. DevSecOps

### DevOps nima va DevSecOps qanday farqlanadi?

**DevOps:**
```
Dev (Ishlab chiquvchilar) + Ops (Operatsion jamoa)
→ Tez chiqarish, doimiy integratsiya
```

**DevSecOps:**
```
Dev + Sec (Xavfsizlik) + Ops
→ Xavfsizlik jarayonga integratsiya qilingan
→ "Shift Left Security" — xavfsizlikni chapga siljitish
```

> **Taqqoslash:** DevOps — tez pishirilgan ovqat. DevSecOps — tez pishirilgan, lekin sanitariya qoidalariga mos ovqat.

### "Shift Left" tushunchasi

```
ESKI YONDASHUV (Shift Right):
Dev → Dev → Dev → Dev → [TEST] → [SECURITY] → Prod
                                      ↑
                              Xavfsizlik shu yerda!
                              (kech, qimmat)

YANGI YONDASHUV (Shift Left):
[SEC]→[SEC]→[SEC]→[SEC]→[SEC]→[SEC]→ Prod
  ↑     ↑     ↑     ↑     ↑     ↑
Xavfsizlik har bosqichda integratsiya qilingan!
(erta, arzon)
```

### DevSecOps Pipeline — To'liq misol

```
┌─────────────────────────────────────────────────────────────┐
│                    DEVSEOPS PIPELINE                        │
├──────────┬───────────┬──────────┬──────────┬───────────────┤
│  PLAN    │  CODE     │  BUILD   │  TEST    │  DEPLOY       │
├──────────┼───────────┼──────────┼──────────┼───────────────┤
│• Threat  │• IDE      │• SAST    │• DAST    │• Config check │
│  Modeling│  plugins  │• SCA     │• IAST    │• Compliance   │
│• Security│• Pre-     │• Secrets │• Pen test│• Runtime prot │
│  training│  commit   │  scanning│• Fuzzing │• Monitoring   │
│• Secure  │  hooks    │• Licence │          │• Incident resp│
│  stories │• Code     │  check   │          │               │
│          │  review   │          │          │               │
└──────────┴───────────┴──────────┴──────────┴───────────────┘
     ↑                                                    |
     └──────────── Continuous Feedback ───────────────────┘
```

### DevSecOps madaniyati — "Security Champions" dasturi

**Security Champions** — har bir jamoada xavfsizlik bo'yicha "advokat" va bilim manbayi.

```
SOC / Security Team
        ↓ bilim uzatish
Security Champions (Har jamoadan 1-2 kishi)
        ↓ bilim uzatish
Barcha Ishlab Chiquvchilar

Natija:
• Xavfsizlik bilimlari tarqaladi
• Jamoalar o'z xavfsizliklarini o'zlari boshqaradi
• Security team bottleneck bo'lmaydi
```

---

## 9. Xavfsizlik Standartlari va Freymvorklari

### 9.1 ISO/IEC 27001 — ISMS

**Information Security Management System** — xavfsizlik boshqaruv tizimi standarti.

```
ISO 27001 talablari:
• Xavfsizlik siyosati
• Risk baholash
• Risk ishlov berish
• Nazorat choralari (114 ta nazorat, A.5 - A.18)
• Monitoring va audit
• Doimiy yaxshilanish
```

### 9.2 NIST Cybersecurity Framework

AQSh Milliy Standartlar va Texnologiyalar Instituti freymvorki:

```
IDENTIFY → PROTECT → DETECT → RESPOND → RECOVER
   ↓          ↓         ↓         ↓         ↓
Asset       Access    Anomaly  Incident  Recovery
Management  Control   Detection Response  Planning
```

### 9.3 PCI DSS — To'lov Kartochkasi Sanoati Standarti

Kredit karta ma'lumotlarini qayta ishlash uchun:

```
12 ta asosiy talab:
1. Firewall o'rnatish
2. Default parollarni o'zgartirish
3. Karta ma'lumotlarini himoyalash
4. Uzatishda shifrlash
5. Antivirus ishlatish
6. Xavfsiz tizimlarni saqlash
7. Kirish huquqlarini cheklash
8. Identifikatsiya tizimi
9. Fizik kirishni cheklash
10. Kirishlarni monitoring qilish
11. Muntazam xavfsizlik testi
12. Xavfsizlik siyosatini saqlash
```

### 9.4 GDPR va Ma'lumotlarni Himoya Qilish

Evropa Ittifoqining umumiy ma'lumotlarni himoya qilish qoidalari:

```
Asosiy tamoyillar:
• Privacy by Design — dizayndan boshlab maxfiylik
• Data Minimization — faqat kerakli ma'lumot
• Purpose Limitation — faqat maqsad uchun
• Storage Limitation — zarur vaqt uchun
• Integrity & Confidentiality — CIA triad

Sanksiyalar:
• Global yillik daromadning 4% yoki
• €20 million (qaysi katta bo'lsa)
```

### 9.5 CVSS — Umumiy Zaiflik Baholash Tizimi

Common Vulnerability Scoring System — zaifliklarni standart usulda baholash:

```
CVSS v3.1 Baholash tarkibi:

BASE SCORE (0-10):
• Attack Vector (AV): Network/Adjacent/Local/Physical
• Attack Complexity (AC): Low/High
• Privileges Required (PR): None/Low/High
• User Interaction (UI): None/Required
• Scope (S): Unchanged/Changed
• Confidentiality (C): None/Low/High
• Integrity (I): None/Low/High
• Availability (A): None/Low/High

Natija:
0.0     → Yo'q
0.1-3.9 → Past
4.0-6.9 → O'rta
7.0-8.9 → Yuqori
9.0-10.0→ Kritik
```

---

## 10. Amaliy Topshiriq

### 🎯 Laboratoriya ishi: Onlayn do'kon tizimini Secure SDLC bo'yicha tahlil qilish

**Ssenariy:** Siz yangi onlayn do'kon loyihasi xavfsizlik arxitektori sifatida qo'shildingiz. Quyidagi vazifalarni bajaring:

---

**Vazifa 1: Threat Modeling (15 ball)**

Quyidagi tizim uchun STRIDE bo'yicha tahdidlar jadvalini to'ldiring:

```
Tizim: Onlayn Do'kon
Komponentlar:
• Veb sayt (foydalanuvchi interfeysi)
• Autentifikatsiya servisi
• Mahsulot katalogi
• Savat va buyurtma tizimi
• To'lov servisi
• Ma'lumotlar bazasi
```

| # | Komponent | Tahdid turi (STRIDE) | Tahdid tavsifi | Mitigation |
|---|-----------|---------------------|----------------|------------|
| 1 | To'lov servisi | S - Spoofing | ? | ? |
| 2 | Mahsulot katalogi | T - Tampering | ? | ? |
| 3 | Autentifikatsiya | E - Elevation | ? | ? |
| 4 | Ma'lumotlar bazasi | I - Info Disclosure | ? | ? |
| ... | ... | ... | ... | ... |

---

**Vazifa 2: Xavfsiz Talablar (10 ball)**

Quyidagi funksional talablar uchun xavfsizlik talablarini yozing:

```
Funksional talab: "Foydalanuvchi tizimga kira olishi kerak"

Sizning xavfsizlik talabingiz:
1. _______________
2. _______________
3. _______________
```

---

**Vazifa 3: Zaiflikni aniqlash (15 ball)**

Quyidagi PHP kodni ko'rib chiqing va kamida 3 ta xavfsizlik muammosini toping:

```php
<?php
$username = $_GET['username'];
$password = $_GET['password'];

$query = "SELECT * FROM users WHERE username='$username' AND password='$password'";
$result = mysql_query($query);

if(mysql_num_rows($result) > 0) {
    $_SESSION['user'] = $username;
    echo "Xush kelibsiz, " . $username;
    
    // Log
    file_put_contents("logs.txt", "Login: $username, $password \n", FILE_APPEND);
}
?>
```

---

**Vazifa 4: Xavfsiz Kod Yozish (20 ball)**

Yuqoridagi kodni xavfsiz holga keltiring (Python Flask yoki PHP da):

---

## 11. Xulosa

### 📚 Asosiy tushunchalar takrori

```
SECURE SDLC = Xavfsizlik + Dastur hayotiy tsikli

Asosiy tamoyillar:
┌─────────────────────────────────────────────┐
│ 1. Xavfsizlik — loyiha BOSHIDAN boshlash    │
│ 2. Har bir bosqichda xavfsizlik faoliyati   │
│ 3. "Shift Left" — erta topish, arzon tuzat  │
│ 4. Defense in Depth — qatma-qat himoya      │
│ 5. Least Privilege — minimal ruxsat         │
│ 6. Threat Modeling — tahdidlarni oldindan   │
│ 7. DevSecOps — jamoa madaniyati             │
└─────────────────────────────────────────────┘
```

### ❓ Takrorlash savollari

**Nazariy savollar:**

1. Secure SDLC va oddiy SDLC ning asosiy farqi nima?
2. "Shift Left Security" tushunchasini izohlang va nima uchun muhimligini tushuntiring.
3. STRIDE modelining har bir harfi nimani anglatadi? Misol keltiring.
4. SAST, DAST va IAST ning farqi nima? Qachon qaysi birini ishlatish kerak?
5. "Defense in Depth" prinsipi nima? Real hayotdan misol keltiring.
6. DevSecOps va DevOps ning farqi nima?
7. CIA Triad nima? Har bir elementni tushuntiring.
8. CVSS skori 9.5 bo'lgan zaiflikka qancha vaqt ichida patch o'rnatilishi kerak?

**Tahlil savollari:**

9. 2017 yildagi Equifax buzilishi Secure SDLC qo'llanilganda oldini olish mumkin bo'larmi? Qanday?
10. Onlayn bank tizimi uchun eng muhim 5 ta xavfsizlik talabini aniqlang va asoslang.
11. Qaysi turdagi tizimlar uchun Black Box, qaysilari uchun White Box penetration test qo'llaniladi?

---

### 📖 Qo'shimcha o'qish manbalari

**Rasmiy hujjatlar:**
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [Microsoft SDL](https://www.microsoft.com/en-us/securityengineering/sdl)
- [OWASP SAMM](https://owaspsamm.org/)

**Kitoblar:**
- "The Web Application Hacker's Handbook" — Stuttard & Pinto
- "Software Security: Building Security In" — McGraw
- "Threat Modeling: Designing for Security" — Shostack
- "The DevOps Handbook" — Kim, Humble, Debois, Willis

**Sertifikatlar:**
- CSSLP (Certified Secure Software Lifecycle Professional) — ISC²
- GWEB (GIAC Web Application Defender)
- CASE (Certified Application Security Engineer)

---

### 🎯 Keyingi dars mavzusi

**"OWASP Top 10 — Eng Ko'p Uchraydigan Veb Zaifliklar"**

Har bir zaiflik uchun:
- Tavsif va misol
- Zaiflikdan foydalanish usuli (PoC)
- Himoya choralari
- Laboratoriya ishi (WebGoat / DVWA da amaliyot)

---

*© Kiber Xavfsizlik kursi dars qo'llanmasi | Barcha huquqlar himoyalangan*

---

> **Eslatma:** Bu qo'llanma o'quv maqsadlari uchun tayyorlangan. Tajribali mutaxassislar tomonidan nazorat ostida qo'llanilishi tavsiya etiladi. Haqiqiy tizimlarga ruxsatsiz kirish qonuniy jazoga tortiladi.
