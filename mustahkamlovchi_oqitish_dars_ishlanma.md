# 🤖 Dars Ishlanma
## Suniy Intelekt | Mustahkamlovchi O'qitish

---

# "Mustahkamlovchi O'qitishda Agent va Muhit O'zaro Tasiri"

---

> **Fan:** Suniy Intelekt
> **Sinf / Guruh:** Oliy ta'lim (Bakalavr, 3–4-kurs) yoki Magistratura
> **Dars davomiyligi:** 90 daqiqa (2 akademik soat)
> **Dars turi:** Nazariy-amaliy kombinatsiyalangan dars
> **O'qituvchi:** ___________________________
> **Sana:** ___________________________

---

## 📋 MUNDARIJA

1. [Darsning maqsad va vazifalari](#1-darsning-maqsad-va-vazifalari)
2. [Kalit tushunchalar](#2-kalit-tushunchalar)
3. [Mustahkamlovchi o'qitishga kirish](#3-mustahkamlovchi-oqitishga-kirish)
4. [Agent: tuzilishi va xususiyatlari](#4-agent-tuzilishi-va-xususiyatlari)
5. [Muhit (Environment): turlari va modellari](#5-muhit-environment-turlari-va-modellari)
6. [Agent va muhit o'zaro tasiri](#6-agent-va-muhit-ozaro-tasiri)
7. [Markov Qaror Jarayoni (MDP)](#7-markov-qaror-jarayoni-mdp)
8. [Mukofot funksiyasi va siyosat](#8-mukofot-funksiyasi-va-siyosat)
9. [Asosiy algoritmlar haqida umumiy ma'lumot](#9-asosiy-algoritmlar-haqida-umumiy-malumot)
10. [Real hayotdagi qo'llanmalar](#10-real-hayotdagi-qollanmalar)
11. [Amaliy mashg'ulot](#11-amaliy-mashgulot)
12. [Baholash va xulosa](#12-baholash-va-xulosa)
13. [Adabiyotlar](#13-adabiyotlar)

---

## 1. Darsning Maqsad va Vazifalari

### 🎯 Ta'limiy maqsad
Talabalar mustahkamlovchi o'qitish (Reinforcement Learning — RL) paradigmasining asosiy tushunchalarini, jumladan agent, muhit, holat, harakat, mukofot va siyosat tushunchalarini to'liq o'rganib, ular o'rtasidagi o'zaro ta'sirni chuqur tushunib oladilar.

### 📚 Vazifalari

| # | Vazifa | Natija |
|---|--------|--------|
| 1 | Agent va muhit tushunchalarini farqlash | Talaба ikkisini aniq ta'riflay oladi |
| 2 | O'zaro ta'sir tsiklini tushuntirish | Tsikl bosqichlarini tartibda ayta oladi |
| 3 | MDP modelini tushunish | Formulalarni izohlash va qo'llash |
| 4 | Mukofot funksiyasining roлini anglash | Yaxshi/yomon mukofot dizaynini baholash |
| 5 | Real qo'llanmalarni tahlil qilish | Kamida 3 ta misol keltirish |

### 🧠 Rivojlantiruvchi maqsad
Talabalarning analitik fikrlash qobiliyatini, muammolarni modellash ko'nikmalarini va algoritmik tafakkurini rivojlantirish.

### 🤝 Tarbiyaviy maqsad
Ilmiy izlanish madaniyatini, jamoaviy ishlash ko'nikmalarini va texnologiyani mas'uliyat bilan qo'llash hissini shakllantirish.

---

## 2. Kalit Tushunchalar

### 📖 Glossariy

```
Agent (Agent)           — muhit bilan o'zaro ta'sir qiladigan qaror qabul qiluvchi tizim
Muhit (Environment)     — agent harakat qiladigan tashqi olam yoki simulyatsiya
Holat (State, s)        — muhitning ma'lum bir vaqtdagi tavsifi
Harakat (Action, a)     — agentning muhitga ta'siri
Kuzatuv (Observation)   — agentning muhitdan olgan ma'lumoti
Mukofot (Reward, r)     — agentning harakati sifatini baholovchi signal
Siyosat (Policy, π)     — agentning holat→harakat xaritasi
Qaytim (Return, G)      — kelajakdagi mukofotlarning umumiy yig'indisi
Qiymat (Value, V)       — holatning uzoq muddatli foydasi
Q-funksiya              — holat-harakat juftligining qiymati
Epizod (Episode)        — boshlang'ich holatdan terminal holatgacha bo'lgan jarayon
Diskont koeffitsienti γ — kelajakdagi mukofotlarning joriy qiymatga nisbati
```

---

## 3. Mustahkamlovchi O'qitishga Kirish

### 3.1 O'qitishning uch paradigmasi

Suniy intellektda mashina o'qitishining uchta asosiy paradigmasi mavjud:

```
┌─────────────────────────────────────────────────────────────┐
│                   MASHINA O'QITISHI                         │
├──────────────────┬──────────────────┬───────────────────────┤
│  NAZORATLI       │  NAZORATСИЗ      │  MUSTAHKAMLOVCHI      │
│  O'QITISH        │  O'QITISH        │  O'QITISH             │
├──────────────────┼──────────────────┼───────────────────────┤
│ Yorliqli ma'lumot│ Yorliqsiz        │ Mukofot signali       │
│ Berilgan javob   │ ma'lumot         │ O'z-o'zini o'rgatish  │
│ Tasnif, regressiya│ Klasterlash     │ Qaror qabul qilish    │
└──────────────────┴──────────────────┴───────────────────────┘
```

### 3.2 Mustahkamlovchi o'qitish nima?

**Mustahkamlovchi o'qitish (RL)** — bu agent muhit bilan o'zaro ta'sir orqali, sinov va xato metodidan foydalangan holda, mukofotni maksimallashtirish strategiyasini mustaqil o'rganadigan mashina o'qitishi paradigmasi.

RL uchta asosiy savolga javob beradi:
- **Nima qilish kerak?** → Siyosat (Policy)
- **Qancha yaxshi?** → Qiymat funksiyasi (Value Function)
- **Nima sodir bo'ldi?** → Muhit modeli (Environment Model)

### 3.3 Biologik ilhom

RL inson va hayvonlar o'rganishi bilan chambarchas bog'liq:

| Biologik tushuncha | RL tushunchasi |
|---------------------|-----------------|
| Organizmning xatti-harakati | Agent siyosati |
| Atrof-muhit | Environment |
| Og'riq / zavq signali | Mukofot (Reward) |
| Miya neyron tizimi | Qiymat funksiyasi |
| Odat hosil qilish | Optimal siyosat |
| Pavlov refleksi | Temporal Difference |

> **Ivan Pavlov** tajribalaridan tortib **B.F. Skinner** operant konditsionerlash nazariyasigacha — bularning barchasi RL ning biologik asoslarini tashkil etadi.

---

## 4. Agent: Tuzilishi va Xususiyatlari

### 4.1 Agent ta'rifi

**Agent** — bu:
- Muhitni **kuzatadi** (observes)
- Kuzatuvlar asosida **qaror qabul qiladi** (decides)
- Muhitga **harakat** orqali ta'sir ko'rsatadi (acts)
- Mukofot asosida **o'rganadi** (learns)

### 4.2 Agentning ichki tuzilishi

```
┌─────────────────────────────────────────────┐
│                   AGENT                     │
│                                             │
│  ┌──────────┐    ┌──────────┐               │
│  │ Idrok    │───▶│  Holat   │               │
│  │ moduli   │    │ tasviri  │               │
│  └──────────┘    └────┬─────┘               │
│                       │                     │
│                  ┌────▼─────┐               │
│                  │ Qaror    │               │
│                  │ qabul    │               │
│                  │ qilish   │               │
│                  └────┬─────┘               │
│                       │                     │
│  ┌──────────┐    ┌────▼─────┐               │
│  │ O'rganish│◀───│ Harakat  │               │
│  │ moduli   │    │ moduli   │               │
│  └──────────┘    └──────────┘               │
└─────────────────────────────────────────────┘
```

### 4.3 Agent turlari

#### 4.3.1 Reflex agentlari
Eng oddiy agent turi — joriy kuzatuvga bevosita reaksiya ko'rsatadi.

```
Siyosat: π(s) → a
Misol:   Agar harorat > 30°C → konditsionerni yoq
```

**Kamchilik:** Tarix va kelajakni hisobga olmaydi.

#### 4.3.2 Model asosidagi agentlar
Muhitning ichki modelini saqlab, u orqali qaror qabul qiladi.

```
Ichki model: T(s, a, s') = P(s'|s, a)
Qaror:       π(s, ichki_model) → a
```

#### 4.3.3 Maqsad asosidagi agentlar
Maqsadga erishish uchun rejalashtirish amalga oshiradi.

```
Maqsad:  G* (terminal holat)
Qaror:   argmax_a [P(maqsad|s, a)]
```

#### 4.3.4 Foydalilik asosidagi agentlar
Foyda funksiyasini maksimallashtiradi — eng umumiy model.

```
Foyda: U(s) = V(s) = E[Σ γᵗ rₜ | s₀ = s, π]
Siyosat: π* = argmax_π V^π(s)
```

### 4.4 Agentning asosiy komponentlari

| Komponent | Vazifa | Matematikasi |
|-----------|--------|--------------|
| **Siyosat (π)** | Holat→Harakat xaritasi | π: S → A |
| **Qiymat funksiyasi (V)** | Holatni baholash | V(s) = E[G\|s] |
| **Q-funksiya** | Holat-harakat baholash | Q(s,a) = E[G\|s,a] |
| **Model** | Muhitni taxminlash | T, R funksiyalari |

---

## 5. Muhit (Environment): Turlari va Modellari

### 5.1 Muhit ta'rifi

Muhit — agentning tashqi olami. Agent har qanday vaqtda:
- Muhitning joriy **holatini** (yoki kuzatuvini) qabul qiladi
- Muhitga **harakat** orqali ta'sir qiladi
- Muhitdan **mukofot** oladi

### 5.2 Muhitlarning tasnifi

#### 5.2.1 To'liq vs Qisman kuzatiladigan muhit

| Xususiyat | To'liq kuzatiladigan | Qisman kuzatiladigan |
|-----------|----------------------|----------------------|
| Agent nima ko'radi | Butun holat | Kuzatuv ⊂ Holat |
| Misol | Shaxmat | Poker, robotika |
| Model | MDP | POMDP |
| Murakkablik | Past | Yuqori |

#### 5.2.2 Deterministik vs Stokastik muhit

```
Deterministik:   s' = f(s, a)           — bir xil natija
Stokastik:       s' ~ P(s'|s, a)        — ehtimoliy natija
```

**Misol:** Yo'naltirilgan robot (deterministik) vs havo nazorati (stokastik)

#### 5.2.3 Diskret vs Uzluksiz muhit

| | Diskret | Uzluksiz |
|-|---------|----------|
| **Holatlar** | Sanab bo'ladigan | Cheksiz ko'p |
| **Harakatlar** | Chegara'langan | R^n fazosi |
| **Misol** | O'yin taxtasi | Robot harakat |
| **Algoritmlar** | Q-Learning | PPO, DDPG |

#### 5.2.4 Statik vs Dinamik muhit

- **Statik:** Agent o'ylayotgan vaqtda muhit o'zgarmaydi
- **Dinamik:** Muhit agent harakatsiz ham o'zgaradi

#### 5.2.5 Episodik vs Davomiy muhit

```
Episodik:   s₀ → a₁ → s₁ → ... → sT (terminal)
            Har epizod mustaqil
Davomiy:    s₀ → a₁ → s₁ → a₂ → s₂ → ... (cheksiz)
```

### 5.3 OpenAI Gym va Muhit interfeyslari

Zamonaviy RL tadqiqotlarida standart muhit interfeysi:

```python
# Muhit yaratish
env = gym.make("CartPole-v1")

# Asosiy metodlar:
obs = env.reset()           # Boshlang'ich holat
obs, reward, done, info = env.step(action)  # Qadam
env.render()                # Vizualizatsiya
env.close()                 # Yopish
```

**Mashhur muhitlar:**

| Muhit | Tur | Maqsad |
|-------|-----|--------|
| CartPole | Klassik | Tayoqni muvozanatlash |
| MountainCar | Klassik | Tog'ga chiqish |
| Atari oyinlari | Vizual | O'yin o'ynash |
| MuJoCo | Robotika | Harakat nazorati |
| StarCraft II | Multi-agent | Strategiya |

---

## 6. Agent va Muhit O'zaro Tasiri

### 6.1 Asosiy o'zaro ta'sir tsikli

RL ning yurak urishi — **agent-muhit tsikli**:

```
                    ┌─────────────────────────────────┐
                    │                                 │
    ┌───────────┐   │  Holat (sₜ)                    │
    │           │◀──┤  Mukofot (rₜ)                  │
    │   AGENT   │   │                                 │
    │           │   │           MUHIT                 │
    │           ├──▶│                                 │
    └───────────┘   │  Harakat (aₜ)                  │
                    │                                 │
                    └─────────────────────────────────┘

    Vaqt:  t=0    t=1    t=2    t=3  ...
    Holat: s₀     s₁     s₂     s₃
    Harakat: a₀   a₁     a₂
    Mukofot: r₁   r₂     r₃
```

### 6.2 Tsiklning batafsil bosqichlari

**Bosqich 1 — Kuzatuv:**
```
Agent muhitdan sₜ holatini (yoki oₜ kuzatuvini) qabul qiladi.
```

**Bosqich 2 — Qaror:**
```
Agent siyosati asosida harakat tanlaydi:
    aₜ ~ π(·|sₜ)       (stokastik siyosat)
    aₜ = π(sₜ)          (deterministik siyosat)
```

**Bosqich 3 — Ta'sir:**
```
Agent aₜ harakatni muhitga uzatadi.
```

**Bosqich 4 — O'tish:**
```
Muhit yangi holatga o'tadi:
    sₜ₊₁ ~ P(·|sₜ, aₜ)
```

**Bosqich 5 — Mukofot:**
```
Muhit mukofot beradi:
    rₜ₊₁ = R(sₜ, aₜ, sₜ₊₁)
```

**Bosqich 6 — O'rganish:**
```
Agent (sₜ, aₜ, rₜ₊₁, sₜ₊₁) tajribasidan o'rganadi.
```

### 6.3 Tajriba to'plami

Agent o'qitish jarayonida tajribalar zanjirini hosil qiladi:

```
Trajectory (τ):  s₀, a₀, r₁, s₁, a₁, r₂, s₂, ..., sT

Qaytim (Return):
    Gₜ = rₜ₊₁ + rₜ₊₂ + rₜ₊₃ + ...       (diskountsiz)
    Gₜ = rₜ₊₁ + γrₜ₊₂ + γ²rₜ₊₃ + ...    (diskountli)

    Bu yerda: 0 ≤ γ ≤ 1 — diskont koeffitsienti
```

### 6.4 Diskont koeffitsienti γ ning roli

```
γ = 0.0  →  Faqat darhol mukofotga e'tibor
γ = 0.5  →  Qisqa muddatli fikrlash
γ = 0.9  →  Uzoq muddatli fikrlash
γ = 1.0  →  Barcha kelajak mukofotlar teng ahamiyatli
```

**Misolda ko'rish:**

```
Mukofotlar:  r₁=1, r₂=1, r₃=1, r₄=1

γ=0.9 bilan:
G₀ = 1 + 0.9(1) + 0.81(1) + 0.729(1)
   = 1 + 0.9 + 0.81 + 0.729 = 3.439

γ=0.5 bilan:
G₀ = 1 + 0.5 + 0.25 + 0.125 = 1.875
```

---

## 7. Markov Qaror Jarayoni (MDP)

### 7.1 Markov xususiyati

RL ning matematik asosi — **Markov xususiyati**:

> **"Kelajak faqat hozirgi holatga bog'liq, o'tmishga emas."**

```
Rasmiy:  P(sₜ₊₁ | sₜ, aₜ, sₜ₋₁, aₜ₋₁, ...) = P(sₜ₊₁ | sₜ, aₜ)
```

Bu xususiyat kelajakni bashorat qilish uchun faqat joriy holatning yetarli ekanligini anglatadi.

### 7.2 MDP formal ta'rifi

MDP beshta elementdan iborat **kortej**:

```
MDP = ⟨S, A, P, R, γ⟩

Bu yerda:
S  — Holatlar to'plami (State Space)
A  — Harakatlar to'plami (Action Space)
P  — O'tish ehtimolligi: P(s'|s,a) = P[Sₜ₊₁=s'|Sₜ=s, Aₜ=a]
R  — Mukofot funksiyasi: R(s,a,s') yoki R(s,a)
γ  — Diskont koeffitsienti: γ ∈ [0,1]
```

### 7.3 O'tish matritsasi

Diskret holatlarda o'tish ehtimolliklari **matritsada** ifodalanadi:

```
         s'₁   s'₂   s'₃
    s₁ [ 0.7   0.2   0.1 ]
P = s₂ [ 0.0   0.5   0.5 ]   (harakat a uchun)
    s₃ [ 0.3   0.3   0.4 ]

Shartlar: Σ_{s'} P(s'|s,a) = 1  ∀s,a
```

### 7.4 MDP da siyosat va qiymat funksiyalari

#### Siyosat (Policy)

```
Deterministik:  π(s) = a           — holatga harakat
Stokastik:      π(a|s) = P[Aₜ=a|Sₜ=s]  — ehtimoliy harakat
```

#### Holat qiymat funksiyasi (V-function)

```
V^π(s) = E_π [Gₜ | Sₜ = s]
       = E_π [Σₖ₌₀^∞ γᵏ Rₜ₊ₖ₊₁ | Sₜ = s]
```

#### Harakat qiymat funksiyasi (Q-function)

```
Q^π(s,a) = E_π [Gₜ | Sₜ = s, Aₜ = a]
          = E_π [Σₖ₌₀^∞ γᵏ Rₜ₊ₖ₊₁ | Sₜ = s, Aₜ = a]
```

#### V va Q o'rtasidagi bog'liqlik

```
V^π(s) = Σₐ π(a|s) · Q^π(s,a)

Q^π(s,a) = R(s,a) + γ Σ_{s'} P(s'|s,a) · V^π(s')
```

### 7.5 Bellman tenglamalari

**Richard Bellman** (1957) tomonidan yaratilgan rekursiv tenglamalar — RL ning asosi:

#### Bellman kutish tenglamasi:

```
V^π(s) = Σₐ π(a|s) [R(s,a) + γ Σ_{s'} P(s'|s,a) V^π(s')]
```

#### Bellman optimallik tenglamasi:

```
V*(s) = max_a [R(s,a) + γ Σ_{s'} P(s'|s,a) V*(s')]

Q*(s,a) = R(s,a) + γ Σ_{s'} P(s'|s,a) max_{a'} Q*(s',a')
```

### 7.6 Optimal siyosat

```
π*(s) = argmax_a Q*(s,a) = argmax_a [R(s,a) + γ Σ_{s'} P(s'|s,a) V*(s')]
```

**Teorema:** Har qanday MDP uchun kamida bitta optimal deterministik siyosat π* mavjud.

---

## 8. Mukofot Funksiyasi va Siyosat

### 8.1 Mukofot funksiyasining ahamiyati

Mukofot (Reward) — agentning harakati qanchalik yaxshi yoki yomon ekanligini bildiradigan signal. U RL ning **asosiy yo'l ko'rsatuvchi** elementi.

```
Mukofot turlari:

Zichlik:    r = -1 (har qadam uchun)    → tez harakat qilishga undaydi
Natija:     r = +100 (maqsadga etar.)   → faqat muvaffaqiyatni baholaydi
Aralash:    r = -0.1 + 10·[maqsad]      → ikkalasi birlashgan
```

### 8.2 Mukofot dizaynining muhimligi

> **"Reward Shaping"** — mukofot funksiyasini to'g'ri loyihalash RL ning eng murakkab qismlaridan biridir.

**Yomon mukofot dizayni misollari:**

```
❌ Muammo 1 — Mukofot buzilishi (Reward Hacking):
   Maqsad:   O'yinda maksimal ball to'pla
   Dizayn:   Ball uchun r = +1
   Natija:   Agent o'yinni manipulyatsiya qiladi
              (masalan, bir joyda qolib, ezerak harakatlar qiladi)

❌ Muammo 2 — Qisqa muddatli o'ylash:
   Maqsad:   Uzoq muddatli foyda
   Dizayn:   γ = 0 (diskount yo'q)
   Natija:   Agent faqat joriy mukofotni ko'radi
```

**Yaxshi mukofot dizayn tamoyillari:**

| Tamoyil | Ta'rif |
|---------|--------|
| Maqsad moslik | Mukofot haqiqiy maqsadni aks ettirsin |
| Qisqalik | Kamroq murakkab — yaxshiroq |
| Zichlik | Tez-tez signal berish o'rganishni tezlashtiradi |
| Kuchayish | Ijobiy xatti-harakatlarni rag'batlantirsin |

### 8.3 Siyosatni optimallashtirish

O'qitish maqsadi — kumulativ mukofotni maksimallashtiruvchi siyosatni topish:

```
π* = argmax_π E_π [Σₜ₌₀^∞ γᵗ Rₜ₊₁]
```

#### On-Policy vs Off-Policy o'rganish

```
On-Policy:   Agent o'zi ishlaytirgan siyosatdan o'rganadi
             Misol: SARSA, PPO
             π_behavior = π_target

Off-Policy:  Agent boshqa siyosatdan olgan ma'lumotdan o'rganadi
             Misol: Q-Learning, DQN
             π_behavior ≠ π_target
```

---

## 9. Asosiy Algoritmlar Haqida Umumiy Ma'lumot

### 9.1 RL algoritmlarining tasnifi

```
                    RL ALGORITMLAR
                         │
          ┌──────────────┴──────────────┐
          │                             │
    Model-Based                   Model-Free
          │                             │
    ┌─────┴─────┐              ┌────────┴────────┐
    │           │              │                 │
  Dyna-Q    World            Value-          Policy-
            Models          Based           Based
                          │                 │
                   ┌──────┴──────┐     ┌────┴─────┐
                   │             │     │          │
              Q-Learning      SARSA  REINFORCE   PPO
              DQN            TD(λ)  Actor-Critic TRPO
```

### 9.2 Asosiy algoritmlar tavsifi

#### 9.2.1 Q-Learning

Eng mashhur model-free, off-policy algoritm:

```
Yangilash qoidasi:
Q(s,a) ← Q(s,a) + α [r + γ·max_{a'} Q(s',a') - Q(s,a)]

Bu yerda:
α — o'rganish tezligi (learning rate)
r + γ·max Q(s',a') — TD maqsad (target)
Q(s,a) — joriy taxmin
TD xatosi: δ = r + γ·max Q(s',a') - Q(s,a)
```

#### 9.2.2 SARSA (On-Policy TD)

```
Q(s,a) ← Q(s,a) + α [r + γ·Q(s',a') - Q(s,a)]

Farq: a' keyingi haqiqiy harakat (max emas)
      Bu SARSA ni konservativ qiladi
```

#### 9.2.3 Deep Q-Network (DQN)

DeepMind (2013) — Atari o'yinlarida insondan o'tib ketdi:

```
Asosiy yangiliklar:
1. Experience Replay Buffer — tajribalarni saqlash va qayta ishlatish
2. Target Network — barqaror o'qitish uchun alohida tarmoq
3. CNN — piksellardan o'rganish

Loss: L(θ) = E[(r + γ max_{a'} Q(s',a';θ⁻) - Q(s,a;θ))²]
```

#### 9.2.4 Policy Gradient Metodlar

Siyosatni to'g'ridan-to'g'ri optimallashtiradi:

```
REINFORCE:
∇_θ J(θ) = E_π [∇_θ log π_θ(a|s) · Gₜ]

PPO (Proximal Policy Optimization):
L^CLIP(θ) = E[min(rₜ(θ)Â, clip(rₜ(θ), 1-ε, 1+ε)Â)]
```

#### 9.2.5 Actor-Critic arxitekturasi

```
┌─────────────┐       ┌─────────────┐
│   ACTOR     │       │   CRITIC    │
│  π_θ(a|s)  │       │   V_w(s)   │
│             │       │             │
│  Siyosatni  │       │  Holatni   │
│  yangilaydi │       │  baholaydi  │
└──────┬──────┘       └──────┬──────┘
       │    TD xatosi δ      │
       └────────────────────▶│
                             ▼
                      Afzallik: A(s,a) = Q(s,a) - V(s)
```

### 9.3 Algoritmlarni tanlash qo'llanmasi

| Holat | Tavsiya etiladigan algoritm |
|-------|---------------------------|
| Kichik diskret muhit | Q-Learning, SARSA |
| Katta diskret muhit | DQN, Double DQN |
| Uzluksiz harakat fazosi | PPO, SAC, DDPG |
| Ko'p agentlar | MADDPG, QMIX |
| Muhit modeli mavjud | Dyna-Q, Model-Based RL |
| Xavfli muhit | Constrained RL, Safe RL |

---

## 10. Real Hayotdagi Qo'llanmalar

### 10.1 O'yin sohasida

**DeepMind AlphaGo (2016):**
- 2500 yillik Go o'yinida dunyо chempionini yutdi
- RL + Monte Carlo Tree Search + Deep Learning
- O'z-o'ziga qarshi o'ynash orqali o'rganish

**OpenAI Five (2019):**
- Dota 2 da professional komandalarni yutdi
- 180 yil ekvivalenti har kecha o'z-o'ziga o'ynash
- Multi-agent RL

**AlphaStar (2019):**
- StarCraft II da grandmaster darajasiga yetdi

### 10.2 Robototexnikada

| Qo'llanma | Agent | Muhit | Maqsad |
|-----------|-------|-------|--------|
| Manipulyatsiya | Robot qo'l | Fizik simulatsiya | Ob'ektni ushlash |
| Yurish | Humanoid robot | Yerlik sirt | Harakatlanish |
| Uchish | Dron | Havo fazosi | Manzilga yetish |
| Avtomobil | Avtopilit | Yo'l | Xavfsiz haydash |

### 10.3 Tibbiyotda

- **Dori dozasini optimallashtirish** — bemorga individual doz tanlash
- **Kasallik davolash strategiyasi** — uzoq muddatli davolash rejasi
- **Tibbiy tasvirlarni tahlil qilish** — diagnostika agentlari
- **Radiatsiya davolash rejalashtirish** — optimal nurlanish dozasi

### 10.4 Moliya sohasida

```
Maqsad:     Portfel qiymatini maksimallashtirish
Agent:      Trading boti
Holat:      Bozor narxlari, texnik ko'rsatkichlar
Harakatlar: Sotib olish, sotish, kutish
Mukofot:    Daromad / zarar
```

### 10.5 Tabiiy til ishlovida

- **ChatGPT/Claude** — RLHF (Reinforcement Learning from Human Feedback)
- Dialog tizimlar — konversatsiya siyosati
- Tarjima — kalitli so'z tanlash strategiyasi

### 10.6 Energetikada

**Google DeepMind — Ma'lumot markazi sovutish (2016):**
- RL agenti ma'lumot markazi energiyasini 40% qisqartirdi
- Holat: temperatura, sovutish parametrlari
- Harakat: sovutish tizimi sozlamalari
- Mukofot: energiya samaradorligi

---

## 11. Amaliy Mashg'ulot

> ⏱ **Vaqt:** 20–25 daqiqa | 👥 **Shakl:** 2–3 kishilik guruhlar

### 📌 Mashg'ulot: CartPole Masalasini Modellashtirish

#### Vazifa tavsifi

CartPole — klassik RL muammosi. Vagon ustidagi tayoqni muvozanatlash kerak.

```
Holat vektori:  s = [x, ẋ, θ, θ̇]
                    │   │  │   │
                    │   │  │   └── Tayoq burchak tezligi
                    │   │  └────── Tayoq burchagi
                    │   └───────── Vagon tezligi
                    └───────────── Vagon pozitsiyasi

Harakatlar:  A = {0: Chapga, 1: O'ngga}

Mukofot:     r = +1 (har qadam uchun tayoq tik tursa)
             r = 0  (tayoq yiqilsa yoki chegara oshsa)

Maqsad:      200 qadam davomida tayoqni tik saqlash
```

#### Guruh topshirig'i (15 daqiqa)

**1-guruh — MDP modellashtirish:**
- Holat fazosini chizing va ta'riflang
- Harakat to'plamini sanab chiqing
- Mukofot funksiyasini rasmiylashtiring
- Terminal shartlarni aniqlang

**2-guruh — Siyosat dizayni:**
- Tasodifiy siyosat vs greedy siyosatni taqqoslang
- ε-greedy siyosatni tushuntiring
- Ε qiymati qanday o'zgarishi kerakligini muhokama qiling

**3-guruh — O'rganish strategiyasi:**
- Q-jadvali qanday ko'rinishi kerakligini chizing
- Birinchi 10 qadam uchun Q-jadvalini to'ldiring
- Yangilash formulasini qo'llang

#### Kod namunasi (qisqa, faqat tushunish uchun)

```python
import gym
import numpy as np

# Muhit yaratish
env = gym.make('CartPole-v1')

# Oddiy tasodifiy agent
obs = env.reset()
total_reward = 0

for step in range(200):
    # Tasodifiy harakat tanlash
    action = env.action_space.sample()
    
    # Qadam amalga oshirish
    obs, reward, done, info = env.step(action)
    total_reward += reward
    
    if done:
        print(f"Epizod tugadi. Qadam: {step}, Jami mukofot: {total_reward}")
        break

env.close()
```

#### Muhokama savollari (5–7 daqiqa)

1. Tasodifiy agent necha qadam ushlab turishi mumkin? Nima uchun?
2. Q-jadvali necha qator va ustundan iborat bo'lishi kerak?
3. Mukofotni `r = θ²` (burchak kvadrati, manfiy) qilsak nima o'zgaradi?
4. Uzluksiz holat fazosi uchun Q-jadvali ishlamaydi — nega?

---

## 12. Baholash va Xulosa

### 12.1 Dars yakunida tekshirish savollari

Har bir talaba quyidagi savollarga javob bera olishi kerak:

```
✅ Asosiy darajа:
   □ Agent nima? Muhit nima? Farqi?
   □ RL tsiklining 6 bosqichini tartibda ayting
   □ Mukofot nima uchun kerak?
   □ MDP ning 5 elementini sanang

✅ O'rta daraja:
   □ Markov xususiyatini tushuntiring
   □ V(s) va Q(s,a) farqi nima?
   □ Bellman tenglamasini yozib tushuntiring
   □ On-policy va off-policy nima?

✅ Yuqori daraja:
   □ γ=0 va γ=1 qachon ishlatiladi?
   □ Reward hacking nima va qanday oldini olish mumkin?
   □ DQN Q-Learningdan qanday farqlanadi?
   □ Actor-Critic arxitekturasini tushuntiring
```

### 12.2 Dars xulosasi

```
┌─────────────────────────────────────────────────────────┐
│                  DARS XULOSASI                          │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  RL = Agent + Muhit + Mukofot + Siyosat                │
│                                                         │
│  Agent:   Kuzatadi → Qaror qabul qiladi → Harakat      │
│  Muhit:   Holat → O'tish → Mukofot beradi              │
│  MDP:     ⟨S, A, P, R, γ⟩                             │
│  Maqsad:  π* = argmax_π E[Σ γᵗ rₜ]                    │
│                                                         │
│  Bellman: V*(s) = max_a[R + γΣP·V*(s')]                │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

### 12.3 Keyingi dars uchun

**Uyga vazifa:**
1. MDP kortejini o'z qiziqishingiz sohasidan bir misol uchun to'liq ta'riflang (holat, harakat, mukofot, o'tish, diskont). Yozing va tushuntiring.
2. Q-Learning algoritmini qo'lda (kichik 3×3 labirint uchun) bajarib, Q-jadvalini to'ldiring.

**Keyingi dars mavzulari:**
- Temporal Difference o'qitish (TD(0), TD(n), TD(λ))
- Q-Learning algoritmi batafsil tahlili
- Deep RL: DQN arxitekturasi

---

## 13. Adabiyotlar

### 📚 Asosiy adabiyotlar

| # | Manba | Izoh |
|---|-------|------|
| 1 | **Sutton, R.S. & Barto, A.G.** — *Reinforcement Learning: An Introduction* (2018) | RL ning Injili |
| 2 | **Mnih et al.** — *Human-level control through deep RL* (Nature, 2015) | DQN maqolasi |
| 3 | **Silver et al.** — *Mastering the game of Go* (Nature, 2016) | AlphaGo maqolasi |
| 4 | **Schulman et al.** — *Proximal Policy Optimization* (2017) | PPO algoritmi |
| 5 | **OpenAI Spinning Up** — spinningup.openai.com | Amaliy kurs |

### 🌐 Online resurslar

- **DeepMind RL kursи** — www.deepmind.com/learning-resources
- **Stanford CS234** — Reinforcement Learning Course
- **David Silver's RL Course** — YouTube (UCL/DeepMind)
- **OpenAI Gym dokumentatsiyasi** — gymnasium.farama.org
- **Stable Baselines3** — stable-baselines3.readthedocs.io

### 📖 O'zbek tilida tavsiyalar

- O'zbekiston sun'iy intellekt markazining resurslar to'plami
- INHA University Tashkent — AI laboratoriyasi materiallari

---

<div align="center">

---

*Ushbu dars ishlanma **Suniy Intelekt** kursi uchun tayyorlangan*
*Mualliflik huquqi © 2025 | Barcha huquqlar himoyalangan*

---

</div>
