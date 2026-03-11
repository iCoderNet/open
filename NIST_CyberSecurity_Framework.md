# 🛡️ KIBER XAVFSIZLIK FANI — DARS QO'LLANMASI

## Mavzu: NIST CyberSecurity Framework Arxitekturasi

---

> **Fan:** Kiber Xavfsizlik  
> **Daraja:** O'rta va Yuqori daraja  
> **Dars davomiyligi:** 90 daqiqa (2 dars bloki)  
> **Maqsad:** NIST CSF arxitekturasini chuqur tushunish va tashkilotlarda qo'llash qobiliyatini rivojlantirish

---

## 📋 MUNDARIJA

1. [Kirish va Tarixiy Asos](#1-kirish-va-tarixiy-asos)
2. [NIST CSF Nima?](#2-nist-csf-nima)
3. [Framework Tuzilishi](#3-framework-tuzilishi)
4. [Core Funksiyalar — Asosiy 6 ta Ustun](#4-core-funksiyalar--asosiy-6-ta-ustun)
5. [Implementation Tiers — Amalga Oshirish Darajalari](#5-implementation-tiers--amalga-oshirish-darajalari)
6. [Framework Profile — Profil Tuzish](#6-framework-profile--profil-tuzish)
7. [NIST CSF 2.0 Yangiliklari](#7-nist-csf-20-yangiliklari)
8. [Boshqa Standartlar bilan Munosabat](#8-boshqa-standartlar-bilan-munosabat)
9. [Amaliy Topshiriqlar](#9-amaliy-topshiriqlar)
10. [Nazorat Savollari](#10-nazorat-savollari)
11. [Glossariy](#11-glossariy)

---

## 1. Kirish va Tarixiy Asos

### 1.1 Kiber Xavfsizlik Muammosining Kelib Chiqishi

XXI asrda raqamli texnologiyalarning jadal rivojlanishi bilan birga kiber tahdidlar ham keskin ortib bormoqda. 2013 yilda AQSh prezidenti Barack Obama **"Kritik Infratuzilmani Kiber Xavfsizligini Yaxshilash"** bo'yicha Prezidentlik Farmoni (Executive Order 13636) ni imzoladi. Bu farmon asosida NIST (National Institute of Standards and Technology) yangi kiber xavfsizlik standartini ishlab chiqish vazifasini oldi.

### 1.2 NIST Haqida

**NIST** — National Institute of Standards and Technology (Milliy Standartlar va Texnologiyalar Instituti) — AQSh Savdo Vazirligi tarkibiga kiruvchi federal agentlik. 1901-yilda tashkil etilgan bo'lib, texnologiya, o'lchovlar va standartlar sohasida tadqiqot olib boradi.

**Asosiy vazifalari:**
- Milliy va xalqaro standartlarni ishlab chiqish
- Ilmiy-tadqiqot ishlarini olib borish
- Texnologik innovatsiyalarni qo'llab-quvvatlash
- Kiberxavfsizlik yo'riqnomalarini nashr etish

### 1.3 CSF Yaratilish Jarayoni

| Yil | Voqea |
|-----|-------|
| 2013 | Executive Order 13636 imzolandi |
| 2013 | Sanoat vakillari, akademiyalar va hukumat muassasalari bilan konsultatsiyalar boshlandi |
| 2014 | **NIST CSF v1.0** rasman nashr etildi |
| 2018 | **NIST CSF v1.1** — kichik yangilanishlar (kiberxavfsizlik ta'minot zanjiri, autentifikatsiya) |
| 2024 | **NIST CSF v2.0** — katta yangilanish, "Govern" funksiyasi qo'shildi |

---

## 2. NIST CSF Nima?

### 2.1 Ta'rif

**NIST Cybersecurity Framework (CSF)** — tashkilotlarning kiber xavfsizlik xavflarini boshqarish, kamaytirish va ularga qarshi kurashish uchun mo'ljallangan **ixtiyoriy, moslashuvchan va narxga samarali** qo'llanma hisoblanadi.

> 💡 **Muhim eslatma:** CSF — bu majburiy qonun emas. U "eng yaxshi amaliyotlar" (best practices) to'plami bo'lib, har qanday soha va hajmdagi tashkilot uchun moslashtirilishi mumkin.

### 2.2 Framework ning Asosiy Maqsadlari

```
┌─────────────────────────────────────────────────────────────────┐
│                    NIST CSF MAQSADLARI                          │
├─────────────────────────────────────────────────────────────────┤
│  1. Kiber xavfsizlik holatini baholash                         │
│  2. Maqsadli xavfsizlik holatini belgilash                     │
│  3. Xavflarni doimiy monitoring qilish                         │
│  4. Xavfsizlik dasturlarini ustuvorlashtirish                  │
│  5. Ichki va tashqi manfaatdor tomonlar bilan muloqot          │
└─────────────────────────────────────────────────────────────────┘
```

### 2.3 CSF ning Afzalliklari

**Umumiyligi:** Sog'liqni saqlash, moliya, energetika, transport, ta'lim — har qanday sohada qo'llaniladi.

**Moslashuvchanligi:** Kichik biznesdan tortib ko'p milliarddollarlik korporatsiyalargacha moslashtiriladi.

**Xalqaro tan olinishi:** 100 dan ortiq mamlakatda qo'llanilmoqda. Yaponiya, Italiya, Israel, Birlashgan Arab Amirliklari va boshqa ko'plab davlatlar o'z milliy standartlarini NIST CSF asosida tuzishgan.

**Umumiy til:** Texnik mutaxassislar, top-menejment va hukumat organlari o'rtasida bitta tushunilgan til yaratadi.

**Xarajat samaradorligi:** Noldan boshlash o'rniga mavjud xavfsizlik mexanizmlarini tizimlashtiradi.

---

## 3. Framework Tuzilishi

### 3.1 Uch Asosiy Komponent

NIST CSF uchta asosiy komponentdan iborat:

```
╔══════════════════════════════════════════════════════════════╗
║                    NIST CSF ARXITEKTURASI                    ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║   ┌─────────────┐   ┌─────────────┐   ┌──────────────────┐ ║
║   │  FRAMEWORK  │   │IMPLEMENTATION│   │   FRAMEWORK      │ ║
║   │    CORE     │   │    TIERS     │   │    PROFILES      │ ║
║   │             │   │             │   │                  │ ║
║   │ Funksiyalar │   │  Tier 1-4   │   │ Joriy / Maqsad   │ ║
║   │ Kategoriyalar│  │  Darajalari │   │    Profillari    │ ║
║   │ Subkategoriyalar│            │   │                  │ ║
║   └─────────────┘   └─────────────┘   └──────────────────┘ ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

### 3.2 Framework Core (Asosiy Qismning) Tuzilishi

Framework Core — bu ierarxik tuzilma bo'lib, 4 darajadan iborat:

```
Framework Core
│
├── Funksiya (Function) — 6 ta (GOVERN, IDENTIFY, PROTECT, DETECT, RESPOND, RECOVER)
│   │
│   ├── Kategoriya (Category) — har bir funksiya ostida bir nechta
│   │   │
│   │   └── Subkategoriya (Subcategory) — aniq texnik yoki boshqaruv talablari
│   │       │
│   │       └── Ma'lumot manbai (Informative References) — bog'liq standartlar
```

**Misol:**

```
Funksiya: PROTECT (PR)
  └── Kategoriya: PR.AC — Identity Management, Authentication, Access Control
        └── Subkategoriya: PR.AC-1 — Identities and credentials are issued, managed, verified,
                                       revoked, and audited for authorized devices, users, and processes
              └── Ma'lumot manbalari: CIS CSC 1, 5, 15, 16; COBIT 5; ISO 27001; NIST SP 800-53
```

---

## 4. Core Funksiyalar — Asosiy 6 ta Ustun

### 4.1 Umumiy Ko'rinish

NIST CSF 2.0 da oltita asosiy funksiya mavjud:

```
                    ╔══════════════╗
                    ║    GOVERN    ║
                    ║     (GV)     ║
                    ╚══════╤═══════╝
                           │ Boshqarish & Strategiya
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
   ╔════════════╗  ╔══════════════╗  ╔════════════╗
   ║  IDENTIFY  ║  ║   PROTECT    ║  ║   DETECT   ║
   ║    (ID)    ║  ║    (PR)      ║  ║    (DE)    ║
   ╚════════════╝  ╚══════════════╝  ╚════════════╝
          │                                │
          └──────────────┬─────────────────┘
                         ▼
               ╔══════════════════╗
               ║     RESPOND      ║
               ║      (RS)        ║
               ╚══════════════════╝
                         │
                         ▼
               ╔══════════════════╗
               ║     RECOVER      ║
               ║      (RC)        ║
               ╚══════════════════╝
```

---

### 4.2 GOVERN (GV) — Boshqarish

> **CSF 2.0 da yangi qo'shilgan funksiya** — tashkilotning kiber xavfsizlikni boshqarish strategiyasini belgilaydi.

**Maqsad:** Tashkilotning kiber xavfsizlik bo'yicha maqsadlari, siyosati, vazifalari va mas'uliyati aniqlanadi va kuzatib boriladi.

**Asosiy Kategoriyalar:**

| Kategoriya Kodi | Nomi | Tavsif |
|----------------|------|--------|
| GV.OC | Organizational Context | Tashkilot maqsadlari va manfaatdor tomonlar ehtiyojlari |
| GV.RM | Risk Management Strategy | Xavf tolerantligi va ustuvorliklari |
| GV.RR | Roles, Responsibilities & Authorities | Mas'uliyat va vakolatlar taqsimoti |
| GV.PO | Policy | Kiber xavfsizlik siyosatini belgilash |
| GV.OV | Oversight | Kiber xavfsizlik natijalarini nazorat qilish |
| GV.SC | Cybersecurity Supply Chain Risk Management | Ta'minot zanjiri xavflarini boshqarish |

**Muhim Subkategoriyalar:**

- **GV.RM-01:** Xavf tolerantligi yozma shaklda belgilanadi va e'lon qilinadi
- **GV.OC-01:** Tashkilotning missiyasi kiber xavfsizlik xavf boshqaruvida hisobga olinadi
- **GV.RR-02:** Kiberxavfsizlik rollari va mas'uliyatlari belgilanadi, top-menejment tomonidan qo'llab-quvvatlanadi
- **GV.SC-01:** Ta'minot zanjiri xavf boshqaruvining maqsadlari belgilanadi

**Savol: Nima uchun Govern muhim?**
Oldingi CSF 1.1 da xavfsizlik asosan texnik choralar sifatida ko'rilgan. CSF 2.0 Govern funksiyasi orqali kiber xavfsizlik *biznes strategiyasining ajralmas qismi* ekanligini ta'kidlaydi.

---

### 4.3 IDENTIFY (ID) — Aniqlash

**Maqsad:** Tashkilotning aktivlari, muhiti, qobiliyatlari va xavflarini tushunish.

**Asosiya g'oya:** Nimani himoya qilishni bilmasdan uni himoya qilib bo'lmaydi.

**Asosiy Kategoriyalar:**

| Kategoriya Kodi | Nomi | Tavsif |
|----------------|------|--------|
| ID.AM | Asset Management | Barcha aktivlarni inventarizatsiya qilish |
| ID.RA | Risk Assessment | Xavflarni aniqlash va baholash |
| ID.IM | Improvement | Doimiy yaxshilanish jarayoni |

**ID.AM — Aktivlarni Boshqarish:**

Aktivlar quyidagi toifalarga bo'linadi:

```
AKTIVLAR TASNIFI
│
├── Moddiy aktivlar (Physical Assets)
│   ├── Serverlar, kompyuterlar, tarmoq qurilmalari
│   ├── IoT qurilmalari
│   └── Saqlash vositalari (hard disk, USB, tape)
│
├── Ma'lumotlar (Data Assets)
│   ├── Mijozlar ma'lumotlari (PII — Personally Identifiable Information)
│   ├── Moliyaviy ma'lumotlar
│   ├── Intellektual mulk
│   └── Operatsion ma'lumotlar
│
├── Dasturiy ta'minot (Software Assets)
│   ├── Operatsion tizimlar
│   ├── Ilovalar
│   └── Dasturlar litsenziyalari
│
└── Xizmatlar (Service Assets)
    ├── Bulut xizmatlari
    ├── Tashqi xizmat ko'rsatuvchilar
    └── Kritik biznes jarayonlar
```

**ID.RA — Xavflarni Baholash:**

Xavf baholash formulasi:
```
Xavf = Tahdid Ehtimoli × Zaiflik × Ta'sir (Oqibat)
Risk = Threat Likelihood × Vulnerability × Impact
```

Xavflarni ustuvorlashtirish matritsasi:

```
          │   Past   │  O'rta  │  Yuqori │
          │  Impact  │  Impact │  Impact │
──────────┼──────────┼─────────┼─────────┤
Yuqori    │  O'RTA   │ YUQORI  │ KRITIK  │
Ehtimol   │          │         │         │
──────────┼──────────┼─────────┼─────────┤
O'rta     │  PAST    │ O'RTA   │ YUQORI  │
Ehtimol   │          │         │         │
──────────┼──────────┼─────────┼─────────┤
Past      │  PAST    │  PAST   │ O'RTA   │
Ehtimol   │          │         │         │
```

---

### 4.4 PROTECT (PR) — Himoya Qilish

**Maqsad:** Muhim xizmatlarni yetkazib berish uchun tegishli himoya choralari ishlab chiqish va amalga oshirish.

**Asosiy Kategoriyalar:**

| Kategoriya Kodi | Nomi | Tavsif |
|----------------|------|--------|
| PR.AA | Identity Management, Authentication & Access Control | Identifikatsiya va kirish nazorati |
| PR.AT | Awareness and Training | Xodimlarni o'qitish |
| PR.DS | Data Security | Ma'lumotlarni himoya qilish |
| PR.PS | Platform Security | Platformalar va tizimlar xavfsizligi |
| PR.IR | Technology Infrastructure Resilience | Infratuzilma barqarorligi |

**PR.AA — Kirish Nazorati:**

Kirish nazorati prinsiplari:

```
LEAST PRIVILEGE (Minimal Imtiyozlar Prinsipi)
─────────────────────────────────────────────
Foydalanuvchi faqat o'z vazifasi uchun
zarur bo'lgan minimal resurslarga kirish
huquqiga ega bo'lishi kerak.

NEED-TO-KNOW (Bilishga Zaruriyat Prinsipi)
──────────────────────────────────────────
Ma'lumotlarga faqat ish zaruriyati bo'lganda
kirish ruxsati beriladi.

SEPARATION OF DUTIES (Vazifalar Ajratilishi)
────────────────────────────────────────────
Bitta shaxs muhim operatsiyani yolg'iz
amalga oshira olmasligi kerak.
```

**Autentifikatsiya Turlari:**

```
Biror narsa BILISH:        → Parol, PIN, xavfsizlik savoli
Biror narsaga EGA BO'LISH: → Smart karta, hardware token, telefon
Biror narsa BO'LISH:       → Barmoq izi, yuz tanish, retina skaneri

MFA (Ko'p Faktorli Autentifikatsiya) = 2 yoki undan ortiq faktorni birlashtirish
```

**PR.DS — Ma'lumotlarni Himoya Qilish:**

Ma'lumotlar holatlari bo'yicha himoya:

| Ma'lumot Holati | Ta'rif | Himoya Usuli |
|-----------------|--------|--------------|
| Data at Rest | Saqlangan ma'lumotlar | AES-256 shifrlash, disk shifrlash |
| Data in Transit | Uzatiladigan ma'lumotlar | TLS 1.3, VPN, HTTPS |
| Data in Use | Qayta ishlash jarayonidagi | Xotirani himoya qilish, SGX |

**Shifrlash Standartlari:**
- **AES (Advanced Encryption Standard):** Simmetrik shifrlash, 128/192/256 bit kalit
- **RSA:** Assimetrik shifrlash, public/private kalit juftligi
- **ECC (Elliptic Curve Cryptography):** RSA ga nisbatan qisqaroq kalit bilan bir xil xavfsizlik darajasi
- **TLS 1.3:** Transport Layer Security, eng so'nggi versiya, tezroq va xavfsizroq

---

### 4.5 DETECT (DE) — Aniqlash

**Maqsad:** Kiber xavfsizlik hodisalarini o'z vaqtida aniqlash.

**Asosiy Kategoriyalar:**

| Kategoriya Kodi | Nomi | Tavsif |
|----------------|------|--------|
| DE.CM | Continuous Monitoring | Doimiy monitoring |
| DE.AE | Adverse Event Analysis | Anomal hodisalarni tahlil qilish |

**DE.CM — Doimiy Monitoring:**

```
SOC (Security Operations Center) MONITORINGI
═══════════════════════════════════════════════
                                    
  Tarmoq         Log fayllar      Foydalanuvchi
  Trafigi    →   va Eventlar   →  Xatti-harakati
     │               │                │
     └───────────────┴────────────────┘
                      │
                      ▼
              ┌───────────────┐
              │  SIEM Tizimi  │
              │(Aggregation & │
              │  Correlation) │
              └───────────────┘
                      │
               Tashvishli hodisa
                aniqlangan ↓
              ┌───────────────┐
              │  SOC Analitik │
              │   Tekshiruvi  │
              └───────────────┘
```

**SIEM (Security Information and Event Management):**
- Bir nechta manbadan log ma'lumotlarini yig'adi
- Real-vaqt tahlil qiladi
- Korrelyatsiya qoidalari asosida alertlar beradi
- Mashhur SIEM tizimlari: Splunk, IBM QRadar, Microsoft Sentinel, Elastic SIEM

**DE.AE — Hodisalarni Tahlil Qilish:**

Anomaliyalarni aniqlash usullari:
- **Signature-based:** Ma'lum hujum imzolarini qidirish (IDS/IPS)
- **Anomaly-based:** Odatiy xatti-harakatdan chetlanishni aniqlash (UEBA)
- **Behavior-based:** Foydalanuvchi va tizim xatti-harakatlarini monitoring qilish

**IoC (Indicators of Compromise) — Buzilish Belgilari:**
- Noma'lum IP manzillardan ulanishlar
- G'ayrioddiy vaqtda tizimga kirish
- Katta hajmdagi ma'lumot uzatilishi
- Zararli fayllar hashlar (MD5, SHA-256)
- Noma'lum domen nomlariga murojaat

---

### 4.6 RESPOND (RS) — Javob Berish

**Maqsad:** Aniqlangan kiber xavfsizlik hodisasiga nisbatan tegishli choralar ko'rish.

**Asosiy Kategoriyalar:**

| Kategoriya Kodi | Nomi | Tavsif |
|----------------|------|--------|
| RS.MA | Incident Management | Hodisani boshqarish |
| RS.AN | Incident Analysis | Hodisani tahlil qilish |
| RS.CO | Incident Response Reporting and Communication | Xabar berish va muloqot |
| RS.MI | Incident Mitigation | Zararni kamaytirish |

**Hodisalarga Javob Berish Jarayoni (IR Life Cycle):**

```
╔═════════════╗     ╔══════════════╗     ╔════════════════╗
║  1. TAYYORLIK ║ → ║ 2. ANIQLASH  ║ → ║ 3. CHEKLASH    ║
║ (Preparation)║     ║(Identification)║   ║ (Containment)  ║
╚═════════════╝     ╚══════════════╝     ╚════════════════╝
                                                  │
╔═════════════╗     ╔══════════════╗     ╔════════▼═══════╗
║ 6. SABOQLAR ║ ← ║ 5. TIKLASH   ║ ← ║ 4. YO'Q QILISH ║
║  (Lessons   ║     ║  (Recovery)  ║     ║  (Eradication) ║
║  Learned)   ║     ╚══════════════╝     ╚════════════════╝
╚═════════════╝
```

**Hodisalarni Klassifikatsiya Qilish:**

| Daraja | Nom | Tavsif | Javob Vaqti |
|--------|-----|--------|-------------|
| P1 | Kritik | Biznes to'xtab qolgan, ma'lumotlar oqib chiqqan | < 1 soat |
| P2 | Yuqori | Katta ta'sir, asosiy tizimlar ta'sirlangan | < 4 soat |
| P3 | O'rta | Cheklangan ta'sir, ba'zi tizimlar ta'sirlangan | < 24 soat |
| P4 | Past | Minimal ta'sir, oddiy anomaliya | < 72 soat |

**Playbook — Hodisa Javob Berish Qo'llanmasi:**

Playbook — oldindan tayyor hodisa javob berish scripti. Har bir hodisa turi uchun alohida playbook mavjud:
- Ransomware hujumi playbooki
- DDoS hujumi playbooki
- Phishing playbooki
- Insider threat playbooki
- Data breach playbooki

---

### 4.7 RECOVER (RC) — Tiklash

**Maqsad:** Kiber xavfsizlik hodisasidan so'ng operatsiyalarni tiklash va zaifliklarni bartaraf etish.

**Asosiy Kategoriyalar:**

| Kategoriya Kodi | Nomi | Tavsif |
|----------------|------|--------|
| RC.RP | Incident Recovery Plan Execution | Tiklash rejasini bajarish |
| RC.CO | Incident Recovery Communication | Tiklash jarayonida muloqot |

**Tiklash Strategiyalari:**

**RTO va RPO:**
```
RPO (Recovery Point Objective) — Ma'lumot yo'qotish limiti
├── "Oxirgi 4 soat ichidagi ma'lumotlarni yo'qotishga rozi"
└── Backup chastotasini belgilaydi

RTO (Recovery Time Objective) — Tiklash vaqti limiti  
├── "Tizim 2 soat ichida ishga tushishi kerak"
└── DR (Disaster Recovery) imkoniyatini belgilaydi
```

**Backup Strategiyasi (3-2-1 Qoidasi):**
```
3 ta nusxa saqlash
  │
  ├── 2 ta TURLI xil ommaviy axborot vositasida (masalan, disk + lenta)
  │
  └── 1 ta TASHQARIDA (offsite, bulut yoki boshqa joylashuv)
```

**Business Continuity vs Disaster Recovery:**

| Xususiyat | Business Continuity (BC) | Disaster Recovery (DR) |
|-----------|--------------------------|------------------------|
| E'tibor | Biznesni davom ettirish | IT tizimlarini tiklash |
| Qamrov | Butun tashkilot | IT infratuzilmasi |
| Vaqt | Hodisa davomida | Hodisadan keyin |
| Maqsad | Uzilishsiz ishlash | Tizimlarni tiklash |

---

## 5. Implementation Tiers — Amalga Oshirish Darajalari

### 5.1 Tier Nima?

Tier — tashkilotning kiber xavfsizlikka yondashuvining **etuklik darajasi** va xavf boshqaruv amaliyotlarini tavsiflaydi.

> ⚠️ Muhim: Yuqori tier o'z-o'zidan "yaxshiroq" degani emas. Maqsad — tashkilotning biznes ehtiyojlari va xavf tolerantligiga mos tier ni tanlash.

### 5.2 To'rtta Tier Tavsifi

**TIER 1 — Partial (Qisman)**

```
┌─────────────────────────────────────────────────────────┐
│ TIER 1: PARTIAL                                         │
├─────────────────────────────────────────────────────────┤
│ Xavf boshqaruvi: Norasmiy, reaktiv (hodisa bo'lgandan  │
│                  keyingina harakat qilinadi)            │
│                                                         │
│ Integratsiya: Kiber xavfsizlik biznes maqsadlari bilan  │
│               bog'liq emas                              │
│                                                         │
│ Tashqi hamkorlik: Minimal yoki yo'q                     │
│                                                         │
│ Xususiyatlar:                                           │
│   • Yozma siyosat yo'q                                  │
│   • Ma'lum tahdidlargagina munosabat                    │
│   • Xodimlar xabardorligi past                          │
│   • Aktivlar inventarizatsiyasi to'liq emas             │
└─────────────────────────────────────────────────────────┘
```

**TIER 2 — Risk Informed (Xavf to'g'risida ma'lumotga ega)**

```
┌─────────────────────────────────────────────────────────┐
│ TIER 2: RISK INFORMED                                   │
├─────────────────────────────────────────────────────────┤
│ Xavf boshqaruvi: Xavf to'g'risida ma'lumot bor,        │
│                  lekin tashkilot darajasida siyosat     │
│                  belgilanmagan                          │
│                                                         │
│ Integratsiya: Ba'zi joylarda xavf to'g'risida           │
│               ma'lumot bor, lekin to'liq emas           │
│                                                         │
│ Xususiyatlar:                                           │
│   • Xavflar aniqlanadi lekin rasman boshqarilmaydi      │
│   • Xavfsizlik amaliyotlari ba'zi bo'limlarda bor       │
│   • Ba'zi rasmiy hujjatlar mavjud                       │
└─────────────────────────────────────────────────────────┘
```

**TIER 3 — Repeatable (Takrorlanuvchi)**

```
┌─────────────────────────────────────────────────────────┐
│ TIER 3: REPEATABLE                                      │
├─────────────────────────────────────────────────────────┤
│ Xavf boshqaruvi: Rasmiy siyosat va jarayonlar           │
│                  belgilangan va amalga oshirilgan        │
│                                                         │
│ Integratsiya: Kiber xavfsizlik xavf boshqaruvi          │
│               biznes strategiyasiga integratsiya         │
│               qilingan                                  │
│                                                         │
│ Xususiyatlar:                                           │
│   • Xavfsizlik jarayonlari hujjatlashtirilgan           │
│   • Muntazam treninglar o'tkaziladi                     │
│   • Tashqi hamkorlik o'rnatilgan                        │
│   • Xavflar doimiy monitoring qilinadi                  │
└─────────────────────────────────────────────────────────┘
```

**TIER 4 — Adaptive (Moslashuvchan)**

```
┌─────────────────────────────────────────────────────────┐
│ TIER 4: ADAPTIVE                                        │
├─────────────────────────────────────────────────────────┤
│ Xavf boshqaruvi: Ilg'or, proaktiv, real-vaqt            │
│                  moslashuvchan xavf boshqaruvi          │
│                                                         │
│ Integratsiya: Kiber xavfsizlik tashkilot madaniyatining │
│               ajralmas qismi                            │
│                                                         │
│ Xususiyatlar:                                           │
│   • Doimiy takomillashtirishga e'tibor beriladi         │
│   • Yangi tahdidlarga tez moslashish qobiliyati         │
│   • Tarmoq va hamjamiyat bilan faol ma'lumot almashish  │
│   • Machine learning va avtomatizatsiya qo'llaniladi    │
│   • Xavfsizlik metrikalari doimiy tahlil qilinadi       │
└─────────────────────────────────────────────────────────┘
```

### 5.3 Tier Tanlash Omillari

Tashkilot o'z Tier'ini aniqlashda quyidagi omillarni hisobga oladi:

1. **Joriy xavf boshqaruvi amaliyotlari** — hozir qanday jarayonlar mavjud?
2. **Tahdid muhiti** — tashkilot qanday turdagi tahdidlarga duch kelmoqda?
3. **Qonuniy va tartibga soluvchi talablar** — GDPR, HIPAA, PCI DSS kabi standartlar
4. **Tashkilot maqsadlari** — biznes strategiyasi va xavf tolerantligi
5. **Ta'minot zanjiri xavflari** — tashqi hamkorlar va yetkazib beruvchilar
6. **Resurslar** — byudjet, xodimlar, texnologik imkoniyatlar

---

## 6. Framework Profile — Profil Tuzish

### 6.1 Profil Nima?

**Framework Profile** — tashkilotning biznes talablari, xavf tolerantligi va resurslari asosida CSF Core funksiyalari va kategoriyalaridan tanlangan **shaxsiy kiber xavfsizlik yondashuvi**.

**Ikki turdagi Profil:**

```
JORIY PROFIL (Current Profile)         MAQSAD PROFIL (Target Profile)
─────────────────────────────          ──────────────────────────────
Hozirgi holat — tashkilot              Kerakli holat — tashkilot
kiber xavfsizligini qanday             kiber xavfsizligini qanday
boshqarayapti?                         boshqarishni xohlaydi?
         │                                        │
         └────────────────┬───────────────────────┘
                          ▼
                    GAP TAHLILI
               (Farqni aniqlash)
                          │
                          ▼
                  AMALGA OSHIRISH REJASI
               (Implementation Roadmap)
```

### 6.2 Profil Yaratish Qadamlari

**1-qadam:** Tashkilot maqsadlari va muhit tahlili
```
Savollar:
• Tashkilotning asosiy biznes maqsadlari nima?
• Qaysi xizmatlar kritik hisoblanadi?
• Qanday me'yoriy-huquqiy talablar mavjud?
• Manfaatdor tomonlarning xavfsizlik kutishlari nima?
```

**2-qadam:** Aktivlarni inventarizatsiya qilish
```
Barcha muhim aktivlarni aniqlash:
• Apparatura (hardware)
• Dasturiy ta'minot (software)
• Ma'lumotlar (data)
• Xizmatlar (services)
• Odamlar (people)
```

**3-qadam:** Joriy holat baholash (Current Profile)
```
Har bir CSF kategoriyasi bo'yicha:
• Bu kategoriya qanchalik muhim?
• Hozir bu kategoriya qanchalik amalga oshirilgan?
• Dokumentatsiya va nazorat mexanizmlari bormi?
```

**4-qadam:** Maqsad holat belgilash (Target Profile)
```
• Biznes maqsadlariga erishish uchun kerakli daraja
• Xavf tolerantligi asosida ustuvorliklar
• Resurslar va byudjet cheklovlari
```

**5-qadam:** Gap tahlili va yo'l haritasi
```
GAP = Target Profile - Current Profile

Yo'l haritasida:
• Qisqa muddatli (0-6 oy): Eng muhim zaifliklar
• O'rta muddatli (6-18 oy): Asosiy yaxshilanishlar
• Uzun muddatli (18+ oy): Strategik takomillashtirishlar
```

---

## 7. NIST CSF 2.0 Yangiliklari

### 7.1 CSF 1.1 vs CSF 2.0 Taqqoslash

| Xususiyat | CSF 1.1 (2018) | CSF 2.0 (2024) |
|-----------|----------------|----------------|
| Funksiyalar soni | 5 (ID, PR, DE, RS, RC) | 6 (+GOVERN) |
| Qamrov | Asosan kritik infratuzilma | Barcha tashkilotlar |
| Govern | Yo'q | Alohida funksiya sifatida |
| Ta'minot zanjiri | Minimal | Kengaytirilgan (GV.SC) |
| Amalga oshirish | Murakkab | Soddalashtirgilgan |
| Resurslar | Cheklangan | Kengaytirilgan (CSF Reference Tools) |
| Xalqaro miqyos | Ko'proq AQSh yo'nalishli | To'liq xalqaro |

### 7.2 GOVERN Funksiyasining Ahamiyati

CSF 2.0 ning eng katta yangiligi — **GOVERN** funksiyasining qo'shilishi.

**Nima uchun kerak bo'ldi?**

Tadqiqotlar shuni ko'rsatdiki, ko'pgina tashkilotlarda kiber xavfsizlik muammolari texnik muammo emas, balki **boshqaruv muammosi** edi:
- Top-menejment kiberxavfsizlikka e'tibor bermaydi
- Byudjet yetarli ajratilmaydi
- Mas'uliyat aniq belgilanmagan
- Kiber xavfsizlik strategiyaga kiritilmagan

**GOVERN funksiyasi hal etadigan asosiy savollar:**
```
✓ Kiberxavfsizlik bo'yicha kim mas'ul?
✓ Biznesning xavf tolerantligi qanday?
✓ Kiberxavfsizlik siyosati qanday belgilangan?
✓ Ta'minot zanjiridagi xavflar qanday boshqariladi?
✓ Kiberxavfsizlik natijalar qanday nazorat qilinadi?
```

### 7.3 CSF 2.0 da Ta'minot Zanjiri Xavflari

Hozirgi zamonaviy tahdidlarda ta'minot zanjiri (supply chain) hujumlari kuchaymoqda:
- **SolarWinds hujumi (2020):** 18,000 dan ortiq tashkilot ta'sirlandi
- **Log4j zaiflik (2021):** Millionlab tizim ta'sirlandi
- **MOVEit hujumi (2023):** Ko'plab davlat va tijorat tashkilotlari ta'sirlandi

CSF 2.0 GV.SC kategoriyasi quyidagilarni talab qiladi:
- Ta'minot zanjiri xavf boshqaruvini rasmiylashtirish
- Uchinchi tomon yetkazib beruvchilarni baholash
- Shartnoma talablarini belgilash
- Doimiy monitoring o'rnatish

---

## 8. Boshqa Standartlar bilan Munosabat

### 8.1 Asosiy Kiber Xavfsizlik Standartlari

```
┌─────────────────────────────────────────────────────────────────────┐
│                    KIBER XAVFSIZLIK STANDARTLARI EKOTIZIMI          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   ┌──────────────┐   ┌──────────────┐   ┌──────────────────────┐  │
│   │   ISO 27001  │   │   NIST CSF   │   │     SOC 2 Type II    │  │
│   │              │   │              │   │                      │  │
│   │ Xalqaro ISMS │   │  Moslashuvchan│  │  Moliyaviy va        │  │
│   │  standarti   │   │  Framework   │   │  xizmat tashkilotlari│  │
│   └──────────────┘   └──────────────┘   └──────────────────────┘  │
│                                                                     │
│   ┌──────────────┐   ┌──────────────┐   ┌──────────────────────┐  │
│   │   PCI DSS    │   │    HIPAA     │   │     CIS Controls     │  │
│   │              │   │              │   │                      │  │
│   │  To'lov karta │   │  Sog'liqni   │   │ Texnik xavfsizlik    │  │
│   │  xavfsizligi │   │  saqlash     │   │ nazorat ro'yxati     │  │
│   └──────────────┘   └──────────────┘   └──────────────────────┘  │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### 8.2 NIST CSF va ISO 27001 Taqqoslash

| Mezon | NIST CSF | ISO 27001 |
|-------|----------|-----------|
| Kelib chiqishi | AQSh (NIST) | Xalqaro (ISO/IEC) |
| Majburiyligi | Ixtiyoriy | Ixtiyoriy (sertifikatlanish mumkin) |
| Sertifikat | Yo'q | Ha (akkreditatsiya orqali) |
| Tuzilish | Funksiyalar/Kategoriyalar | Annex A nazorat ro'yxati |
| Moslashuvchanligi | Yuqori | O'rta |
| Batafsilligi | O'rta | Yuqori |
| Qo'llash osonligi | Oson | O'rta |
| Xalqaro tan olinish | Yuqori | Juda yuqori |

### 8.3 NIST CSF va CIS Controls Munosabati

**CIS Controls** — Xavfsizlik nazorat choralari ro'yxati, NIST CSF ni amalga oshirishda texnik ko'rsatmalar beradi.

```
NIST CSF Kategoriyasi        CIS Controls (v8)
──────────────────────────   ──────────────────────────────────
ID.AM (Asset Management)  →  CIS Control 1 (Inventory of Hardware)
                             CIS Control 2 (Inventory of Software)
PR.AA (Access Control)    →  CIS Control 5 (Account Management)
                             CIS Control 6 (Access Control Mgmt)
DE.CM (Monitoring)        →  CIS Control 8 (Audit Log Management)
                             CIS Control 13 (Network Monitoring)
RS.AN (Analysis)          →  CIS Control 17 (Incident Response)
```

### 8.4 GDPR va NIST CSF

GDPR (General Data Protection Regulation) — Yevropa shaxsiy ma'lumotlarni himoya qilish qonuni.

| GDPR Talabi | NIST CSF Yondashuvi |
|-------------|---------------------|
| Ma'lumotlarni himoya qilish | PR.DS kategoriyasi |
| Maxfiylik bo'yicha ta'sir baholash | ID.RA kategoriyasi |
| Hodisalarni bildirish (72 soat) | RS.CO kategoriyasi |
| Kirish nazorati | PR.AA kategoriyasi |
| Ma'lumotlarni minimizatsiya qilish | ID.AM kategoriyasi |

---

## 9. Amaliy Topshiriqlar

### 9.1 Topshiriq 1: Gap Tahlili

**Vazifa:** Quyidagi tashkilot stsenariysi uchun soddalashtirilgan gap tahlilini bajaring.

**Stsenariy:** "EduTech Startap" — 50 xodimli ta'lim texnologiyalari kompaniyasi. Mijozlar ma'lumotlari (PII) bilan ishlashadi. Hozirgi holat:
- Barcha xodimlar bir xil paroldan foydalanadi
- Ma'lumotlar shifrsiz saqlangan
- Log fayllar to'planmaydi
- Hodisaga javob berish rejasi yo'q
- Xodimlar phishing haqida biladimi — ma'lum emas

**Jadval to'ldirilsin:**

| CSF Funksiyasi | Kategoriya | Joriy Holat (1-5) | Maqsad Holat (1-5) | Gap | Ustuvorlik |
|----------------|------------|-------------------|-------------------|-----|-----------|
| PROTECT | PR.AA (Kirish nazorati) | ? | ? | ? | Yuqori/O'rta/Past |
| PROTECT | PR.DS (Ma'lumot himoyasi) | ? | ? | ? | |
| DETECT | DE.CM (Monitoring) | ? | ? | ? | |
| RESPOND | RS.MA (Hodisa boshqaruvi) | ? | ? | ? | |
| GOVERN | GV.OC (Tashkilot konteksti) | ? | ? | ? | |

### 9.2 Topshiriq 2: Incident Response Playbook

**Vaziya:** Siz sog'liqni saqlash tashkilotining CISO'sisiz. Ransomware hujumi sodir bo'ldi. NIST CSF RESPOND va RECOVER funksiyalari asosida:
1. Darhol amalga oshiriladigan 5 ta choraning ro'yxatini tuzing
2. Xabardor qilinishi kerak bo'lgan shaxslar/tashkilotlar ro'yxatini tuzing
3. Tiklash vaqtini (RTO) belgilang va asoslang

### 9.3 Topshiriq 3: Tier Baholash

**Vazifa:** O'zingiz yaxshi biladigan tashkilotni (maktab, korxona, idora) tanlang va uning joriy Tier darajasini aniqlang. Javobingizni quyidagi mezonlar bo'yicha asoslang:
- Xavf boshqaruvining rasmiy jarayoni bormi?
- Yozma xavfsizlik siyosati mavjudmi?
- Xodimlar treninglari o'tkaziladimi?
- Doimiy monitoring amalga oshiriladimi?
- Tashqi hamkorlik va ma'lumot almashish bormi?

---

## 10. Nazorat Savollari

### 10.1 Nazariy Savollar

**1-savol:** NIST CSF ning 3 asosiy komponentini nomlab, ularning o'zaro munosabatini tushuntiring.

**2-savol:** CSF 2.0 da qo'shilgan yangi funksiya qaysi va u nima sababdan zarur bo'ldi?

**3-savol:** Implementation Tier 2 va Tier 3 ning asosiy farqini izohlang.

**4-savol:** Framework Core tuzilishida "Subkategoriya" darajasi nimani anglatadi? Misol keltiring.

**5-savol:** NIST CSF ning majburiy bo'lmagan standart ekanligiga qaramay, ko'plab tashkilotlar tomonidan qo'llanilishining asosiy sabablarini izohlang.

**6-savol:** DETECT funksiyasida IoC (Indicators of Compromise) tushunchasini izohlang va 5 ta misolni keltiring.

**7-savol:** "3-2-1 backup qoidasi" nimani anglatadi? Nima uchun bu muhim?

**8-savol:** NIST CSF va ISO 27001 ning asosiy farqlarini jadval ko'rinishida taqqoslang.

**9-savol:** Ta'minot zanjiri xavflari nima? CSF 2.0 bu masalani qanday hal qiladi?

**10-savol:** Joriy Profil (Current Profile) va Maqsad Profil (Target Profile) o'rtasidagi farqni tushuntiring. Gap tahlili nima maqsadda o'tkaziladi?

### 10.2 Test Savollari

**1.** NIST CSF birinchi marta qachon nashr etildi?
- A) 2010  
- B) 2014 ✓  
- C) 2018  
- D) 2020  

**2.** CSF 1.1 da nechta asosiy funksiya mavjud edi?
- A) 4  
- B) 5 ✓  
- C) 6  
- D) 7  

**3.** Qaysi Tier "reaktiv" yondashuv bilan tavsiflanadi?
- A) Tier 4  
- B) Tier 3  
- C) Tier 2  
- D) Tier 1 ✓  

**4.** RPO nima?
- A) Tizimni tiklash vaqti  
- B) Qabul qilinishi mumkin bo'lgan ma'lumot yo'qotish miqdori ✓  
- C) Xavfni baholash usuli  
- D) Himoya darajasi  

**5.** SIEM tizimi qanday funksiyani bajaradi?
- A) Ma'lumotlarni shifrlaydi  
- B) Kirish nazoratini amalga oshiradi  
- C) Log ma'lumotlarini yig'adi va tahlil qiladi ✓  
- D) Tarmoqni segmentatsiya qiladi  

---

## 11. Glossariy

| Atama | Inglizcha | Ta'rif |
|-------|-----------|--------|
| Aktiv | Asset | Tashkilot uchun qimmatli bo'lgan har qanday narsa (ma'lumot, qurilma, dastur) |
| Tahdid | Threat | Tizimga zarar yetkazishi mumkin bo'lgan potentsial xavf |
| Zaiflik | Vulnerability | Sistemaning kamchiligi yoki zaifligi |
| Xavf | Risk | Tahdid va zaiflikning birlashishi natijasida yuzaga kelishi mumkin bo'lgan zarar |
| Nazorat | Control | Xavfni boshqarish uchun qo'llaniladigan texnik yoki boshqaruv chorasi |
| Hodisa | Incident | Tashkilot siyosatini buzadigan yoki xavfsizlikka tahdid soladigan voqea |
| Xavfsizlik devori | Firewall | Tarmoq trafigini filtrlash tizimi |
| Shifrlash | Encryption | Ma'lumotlarni maxfiy kalit yordamida o'qib bo'lmaydigan formatga o'tkazish |
| Autentifikatsiya | Authentication | Foydalanuvchi yoki tizim identligini tekshirish jarayoni |
| Avtorizatsiya | Authorization | Tasdiqlangan foydalanuvchiga resurslardan foydalanish ruxsatini berish |
| CISO | Chief Information Security Officer | Axborot xavfsizligi bo'yicha bosh xodim |
| SOC | Security Operations Center | Xavfsizlik operatsiyalari markazi |
| SIEM | Security Information and Event Management | Xavfsizlik ma'lumotlari va hodisalarni boshqarish tizimi |
| IDS/IPS | Intrusion Detection/Prevention System | Bosqinni aniqlash/oldini olish tizimi |
| VPN | Virtual Private Network | Virtual shaxsiy tarmoq |
| MFA | Multi-Factor Authentication | Ko'p faktorli autentifikatsiya |
| DLP | Data Loss Prevention | Ma'lumot yo'qolishini oldini olish |
| IoC | Indicators of Compromise | Buzilish belgilari |
| APT | Advanced Persistent Threat | Ilg'or doimiy tahdid |
| Zero Trust | — | Hech kimga ishonmaslik, hamma narsani tekshirish arxitekturasi |
| Penetration Testing | — | Tashkilot himoyasini sinash maqsadida amalga oshiriladigan nazorat ostidagi hujum |
| Phishing | — | Soxta elektron xabarlar orqali maxfiy ma'lumotlarni o'g'irlash urinishi |
| Ransomware | — | Ma'lumotlarni shifrlab, to'lov talab qiladigan zararli dastur |
| DDoS | Distributed Denial of Service | Tizimni haddan ortiq so'rovlar bilan yuklash hujumi |
| CVE | Common Vulnerabilities and Exposures | Umumiy zaifliklar va ta'sir qilish ro'yxati |
| CVSS | Common Vulnerability Scoring System | Zaifliklarni baholash tizimi |

---

## 📚 Qo'shimcha O'qish Uchun Manbalar

### Rasmiy Hujjatlar
- [NIST CSF 2.0 Rasmiy Hujjat](https://doi.org/10.6028/NIST.CSWP.29) — NIST
- [NIST SP 800-53](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final) — Xavfsizlik va maxfiylik nazorat choralari
- [NIST SP 800-37](https://csrc.nist.gov/publications/detail/sp/800-37/rev-2/final) — Xavf boshqaruvi framework

### Online Resurslar
- NIST Cybersecurity Framework rasmiy sayti: `https://www.nist.gov/cyberframework`
- CIS Controls: `https://www.cisecurity.org/controls`
- MITRE ATT&CK Framework: `https://attack.mitre.org`
- CISA (Cybersecurity & Infrastructure Security Agency): `https://www.cisa.gov`

### Sertifikatlar (Kelajak uchun)
| Sertifikat | Tashkilot | Daraja |
|-----------|-----------|--------|
| CompTIA Security+ | CompTIA | Boshlang'ich |
| CISSP | ISC² | Yuqori |
| CISM | ISACA | Yuqori |
| CEH | EC-Council | O'rta |
| OSCP | Offensive Security | O'rta-Yuqori |

---

## 📝 Dars Xulosasi

```
╔═══════════════════════════════════════════════════════════════╗
║              NIST CSF — ASOSIY FIKRLAR                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ NIST CSF — xavfga asoslangan, moslashuvchan framework    ║
║  ✅ 3 asosiy komponent: Core, Tiers, Profiles                ║
║  ✅ CSF 2.0 — 6 funksiya: GV, ID, PR, DE, RS, RC            ║
║  ✅ 4 ta Tier — tashkilotning etuklik darajasini bildiradi   ║
║  ✅ Current va Target Profiles orqali yo'l haritasi tuziladi ║
║  ✅ ISO 27001, CIS Controls, GDPR bilan uyg'un               ║
║  ✅ Govern — biznes va kiberxavfsizlikni bog'lovchi ko'prik  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

*Dars qo'llanmasi oxiri*  
*Kiber Xavfsizlik fani | NIST CSF Arxitekturasi mavzusi*  
*Yaratilgan sana: 2025 yil*
