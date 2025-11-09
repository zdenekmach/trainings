# Prompt Engineering - Quick Reference
## One-page cheatsheet

> **Print this!** Tenhle dokument ti dá 80% hodnoty za 5 minut čtení.

---

## 🎯 Zlaté pravidlo

**Začni jednoduše → Přidávej komplexitu jen když je potřeba**

```
Level 1 (Basic) → Level 2 (Structured) → Level 3 (Context) → Level 4 (Expert) → Level 5 (Advanced)
     ↑                                                                              ↑
 Většina úkolů                                                           Kritické úkoly
```

---

## 📝 5 Levelů promptů

| Level | Kdy použít | Co obsahuje | Příklad |
|-------|-----------|-------------|---------|
| **1 - Basic** | Jednoduché dotazy | Úkol v 1-2 větách | "Jaké jsou výhody Agile?" |
| **2 - Structured** | Potřebuji formát | + Formát + Délka | "Analyzuj... Formát: tabulka, max 500 slov" |
| **3 - Context** | Doménový úkol | + Kontext + Cílová skupina | "Kontext: B2B SaaS... Audience: CEO..." |
| **4 - Expert** | Specializovaný úkol | + Role + Metodologie | "Jsi senior BA... Proces: 1) 2) 3)" |
| **5 - Advanced** | Kritický úkol | + Příklady + Validace | "Jsi expert... Examples... Checklist..." |

---

## 🌳 Rozhodovací strom

```
Můj úkol je...

├─ Jednoduchý dotaz (info lookup)
│  └─ ✅ Level 1

├─ Potřebuji konkrétní formát/strukturu
│  └─ ✅ Level 2

├─ Vyžaduje pochopení business kontextu
│  └─ Je to kritický business úkol?
│      ├─ Ne → ✅ Level 3
│      └─ Ano → ⬇ pokračuj

├─ Potřebuji expertní perspektivu
│  └─ Je to strategické rozhodnutí?
│      ├─ Ne → ✅ Level 4
│      └─ Ano → ✅ Level 5

└─ Opakující se úkol (5x+ měsíčně)
   └─ 💡 Zvažuj Custom GPT / Skill
```

---

## ⚡ Základní prompt struktura

```markdown
**Úkol:**
[Co chceš - 1 věta, aktivní sloveso]

**Formát:**
[Jak má výstup vypadat]

**Délka:**
[Max X slov / Min Y stránek]
```

**Pokud není dobrý, přidej:**

```markdown
**Kontext:**
[Situace, pozadí, proč to děláš]

**Cílová skupina:**
[Pro koho je výstup]
```

**Stále nesedí? Přidej:**

```markdown
**Role:**
[Kdo má AI být - expert s charakteristikami]

**Proces:**
1. [Krok 1]
2. [Krok 2]
3. [Krok 3]
```

---

## 💡 Top 10 tipů

| # | Tip | Špatně ❌ | Dobře ✅ |
|---|-----|----------|----------|
| 1 | **Buď konkrétní, ne vague** | "Udělej to dobře" | "Max 500 slov, 3 sekce, tabulka s 5 řádky" |
| 2 | **Použij strukturu** | Wall of text | # Headings, bullet points |
| 3 | **Dej příklady, ne popisy** | "Kreativní headlines" | ✅ "Ship Faster, Break Less" ❌ "Innovative Solutions" |
| 4 | **Prioritizuj kontext** | Důležité info uprostřed | Důležité info na ZAČÁTEK nebo KONEC |
| 5 | **Definuj success** | "Analyzuj..." | "Success = min 5 findings, každý s řešením" |
| 6 | **Specifikuj délku** | "Napiš analýzu" | "Max 1 strana A4" nebo "Min 1000 slov" |
| 7 | **Dej omezení** | "Navrhni řešení" | "Budget 100k, timeline 2 měsíce, tým 3 lidé" |
| 8 | **Definuj audience** | "Vytvoř dokumentaci" | "Pro junior devs, bez žargonu, explain WHY" |
| 9 | **Iteruj!** | První pokus = finální | První pokus = draft → uprav → zkus znovu |
| 10 | **Začni jednoduše** | Rovnou Level 5 | Level 1 → přidávej podle potřeby |

---

## 🤖 Který model pro který úkol

| Úkol | #1 Volba | Proč |
|------|----------|------|
| **Analytická práce (dlouhá)** | Claude Sonnet 4 | Biggest context, depth |
| **Rychlé dotazy** | Gemini Flash | Rychlost + cena |
| **Komplexní reasoning** | ChatGPT o1 | Optimalizovaný pro logiku |
| **Kreativní psaní** | Claude Sonnet 4 | Nuancovaný jazyk |
| **Kódování** | Claude Sonnet 4 | Current leader |
| **Research s odkazy** | Perplexity | Search-first, citace |
| **Microsoft ekosystém** | MS Copilot | M365 integrace |
| **Video analýza** | Gemini 2.5 Pro | Jediný native video |

---

## 📊 Model-specific tipy

### Claude
- ✅ Použij XML tagy pro strukturu: `<context>...</context>`
- ✅ Požaduj "thinking": "Před odpovědí ukaž reasoning"
- ✅ Best pro: Long context, coding, creative writing

### ChatGPT
- ✅ o1: Minimal prompting (má vlastní reasoning)
- ✅ GPT-4.1: Few-shot learning (dej příklady)
- ✅ Best pro: Balanced use cases, custom GPTs

### Gemini
- ✅ Flash: Extra explicitní (je rychlý ale potřebuje guiding)
- ✅ Pro: Native video/audio support
- ✅ Best pro: Huge context (2M), video, batch processing

### Perplexity
- ✅ Specifikuj typy zdrojů: "Academic papers only"
- ✅ Explicitní depth: "Comprehensive analysis min 500 words"
- ✅ Best pro: Research s citacemi

---

## ⚠️ Top 5 chyb

| Chyba | Jak opravit |
|-------|-------------|
| **1. Předpokládání kontextu** | Explicitně vysvětli situaci - AI neví co ty víš |
| **2. Vague formát** | Dej konkrétní template/strukturu |
| **3. Moc komplexní hned** | Začni Level 1, postupně přidávej |
| **4. Zapomenuté iterace** | První výstup = DRAFT. Vždycky iteruj. |
| **5. Chybějící omezení** | Specifikuj constraints (budget, čas, resources) |

---

## 🚀 Quick Start Workflow

**1. Identifikuj level** (decision tree nahoře)

**2. Použij template:**
```markdown
**Úkol:** [co chceš]
**Formát:** [jak to má vypadat]
**Délka:** [kolik]

[+ Context pokud Level 3+]
[+ Role pokud Level 4+]
[+ Příklady pokud Level 5]
```

**3. Zkus prompt**

**4. Výstup není dobrý?**
   - Co konkrétně chybí?
   - Přidej tu sekci do promptu
   - Zkus znovu

**5. Výstup je dobrý?**
   - Ulož prompt jako template
   - Použij příště jako starting point

---

## 📚 Kde najdeš víc

**V tomto repozitáři:**
- `01-template-prompt-advanced.md` - Plná šablona
- `02-progressive-prompting-guide.md` - Detailní guide
- `03-model-specific-recommendations.md` - Srovnání modelů
- `04-practical-examples.md` - 5 real-world příkladů

---

## 💬 Často kladené otázky

**Q: Jak dlouhý má být prompt?**
A: Tak dlouhý, jak potřebuješ pro dobrý výstup. Ne delší. (Většina úkolů: Level 2-3 stačí)

**Q: Který model je "nejlepší"?**
A: Neexistuje. Záleží na use case. Pro většinu: Claude Sonnet 4 nebo GPT-4.1.

**Q: Mám používat celou šablonu vždycky?**
A: NE! Začni s minimem, přidávej postupně.

**Q: Co když první prompt nefunguje?**
A: To je normální. Identifikuj co chybí → přidej → zkus znovu. Prompt engineering = iterativní proces.

---

## ✅ Checklist před odesláním promptu

- [ ] Je úkol jasný? (1 věta co chci)
- [ ] Vím jaký formát chci?
- [ ] Je specifikovaná délka?
- [ ] Pokud potřebuji kontext, dal/a jsem ho?
- [ ] Pokud potřebuji expertizu, specifikoval/a jsem roli?
- [ ] Jsou definovaná omezení? (co NEDĚLAT)
- [ ] Pokud je to kritický úkol, mám příklady?

---

**TL;DR:**
1. Začni jednoduše (Level 1-2)
2. Buď konkrétní (ne vague)
3. Dej formát + délku
4. Iteruj (první pokus = draft)
5. Ulož funkční prompty jako templates

---

**Print-friendly verze:** Vytiskni tento dokument a měj u počítače. 80% use cases pokryješ s tímhle one-pagerem.

---

**Verze:** 1.0 | **Listopad 2025** | **Pro:** Školení Prompt Engineering
