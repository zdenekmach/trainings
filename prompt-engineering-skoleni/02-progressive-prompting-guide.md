# Progresivní průvodce tvorbou promptů
## Od jednoduchého dotazu ke komplexnímu promptu

> **Zlaté pravidlo:** Začni jednoduše. Přidávej komplexitu pouze když je potřeba.

---

## 📖 Obsah

1. [Úvod - Proč progresivní přístup](#úvod)
2. [Level 1 - Základní prompt](#level-1-základní-prompt)
3. [Level 2 - Strukturovaný prompt](#level-2-strukturovaný-prompt)
4. [Level 3 - Kontextový prompt](#level-3-kontextový-prompt)
5. [Level 4 - Expertní prompt](#level-4-expertní-prompt)
6. [Level 5 - Pokročilý prompt s technikami](#level-5-pokročilý-prompt)
7. [Rozhodovací strom - Kdy použít který level](#rozhodovací-strom)
8. [Best Practices](#best-practices)
9. [Časté chyby a jak se jim vyhnout](#časté-chyby)

---

## 🎯 Úvod

### Proč progresivní přístup?

**❌ Častá chyba:**
Začít s obrovským promptem na 500 slov při jednoduchém dotazu → AI je zahlcené, výstup je horší než by mohl být.

**✅ Správný přístup:**
Začni s minimálním promptem. Pokud výstup není dobrý, přidej další vrstvu (kontext, příklady, strukturu).

**Výhody:**
- ⚡ Rychlejší iterace
- 💰 Nižší náklady (méně tokenů)
- 🎯 Lepší výsledky (AI není zahlcené)
- 📈 Učíš se co pro tvůj use case funguje

---

## Level 1: Základní prompt
**Kdy použít:** Jednoduché dotazy, získání informací, brainstorming

### Šablona
```markdown
[Jasný, konkrétní požadavek v 1-2 větách]
```

### Struktura
- **Co chci:** 1 věta
- **Formát (volitelně):** 1 věta

### Příklad 1 - Získání informace

**Prompt:**
```
Jaké jsou hlavní výhody a nevýhody Agile metodologie pro malý tým (5 lidí)?
```

**Proč to funguje:**
- ✅ Jasná otázka
- ✅ Specifikovaný kontext (malý tým, 5 lidí)
- ✅ Explicitní co chci (výhody + nevýhody)

### Příklad 2 - Brainstorming

**Prompt:**
```
Vygeneruj 5 nápadů na názvy pro mobilní aplikaci, která pomáhá lidem najít lokální farmářské trhy.
```

**Proč to funguje:**
- ✅ Konkrétní počet (5 nápadů)
- ✅ Jasný účel aplikace
- ✅ Jednoduchý úkol

### Kdy přejít na Level 2?

**Signály, že Level 1 nestačí:**
- 🔴 Výstup je příliš obecný
- 🔴 AI nerespektuje tvůj požadovaný formát
- 🔴 Odpověď je příliš krátká nebo příliš dlouhá
- 🔴 Chybí struktura, kterou potřebuješ

---

## Level 2: Strukturovaný prompt
**Kdy použít:** Potřebuješ specifický formát, délku, nebo styl

### Šablona
```markdown
**Úkol:**
[Co chceš, aby AI udělalo]

**Formát výstupu:**
[Jak má výstup vypadat]

**Délka:**
[Kolik slov/bulletů/sekcí]
```

### Příklad 1 - Business analýza

**Prompt:**
```
**Úkol:**
Analyzuj tyto dva požadavky od stakeholderů a identifikuj konflikty.

[Požadavek stakeholdera A: ...]
[Požadavek stakeholdera B: ...]

**Formát výstupu:**
- Seznam konfliktů (každý 1 bullet point)
- Pro každý konflikt: popis + doporučené řešení

**Délka:**
Max 10 konfliktů, každý konflikt max 2 věty
```

**Co jsme přidali oproti Level 1:**
- ✅ Jasná struktura výstupu (seznam konfliktů)
- ✅ Specifikace formátu (bullet points, popis + řešení)
- ✅ Omezení délky (max 10, každý 2 věty)

### Příklad 2 - Kreativní úkol

**Prompt:**
```
**Úkol:**
Napiš popis produktu pro novou fitness aplikaci zaměřenou na busy profesionály.

**Tone of voice:**
Profesionální ale přátelský, motivační

**Formát:**
- 1 catchy headline (max 10 slov)
- 2-3 věty popis (co aplikace dělá)
- 3 klíčové benefity (bullet points)

**Délka:**
Max 100 slov celkem
```

**Co jsme přidali:**
- ✅ Tone of voice (jak má znít)
- ✅ Detailní struktura (headline + popis + benefity)
- ✅ Konkrétní délkové limity

### Kdy přejít na Level 3?

**Signály:**
- 🔴 AI nerozumí doméně/situaci
- 🔴 Výstup je generický, nezohledňuje specifika
- 🔴 Chybí pochopení "proč" to děláš
- 🔴 Potřebuješ AI aby rozuměla business kontextu

---

## Level 3: Kontextový prompt
**Kdy použít:** Úkol vyžaduje pochopení situace, domény, nebo byznysu

### Šablona
```markdown
**Kontext:**
[Situace, pozadí, proč to děláš]

**Cílová skupina:**
[Pro koho je výstup]

**Úkol:**
[Co konkrétně chceš]

**Formát:**
[Jak má výstup vypadat]
```

### Příklad 1 - Strategické rozhodnutí

**Prompt:**
```
**Kontext:**
Jsme farmaceutická firma v ČR s 50 zaměstnanci. Rozhodujeme se mezi Agile a Waterfall
přístupem pro vývoj nového interního CRM systému. Máme strict regulatory requirements
(validace, dokumentace), ale chceme být flexible pro změny v požadavcích.

**Cílová skupina:**
Senior management (netechnické pozadí)

**Úkol:**
Srovnej Agile vs. Waterfall pro náš specifický kontext. Doporuč přístup a zdůvodni.

**Formát:**
1. Srovnávací tabulka (kritéria relevantní pro farma: regulatory, flexibilita, dokumentace)
2. Doporučení (která metodologie + proč)
3. Rizika a jejich mitigace
Max 1 strana A4
```

**Co jsme přidali:**
- ✅ Detailní kontext (farma, 50 lidí, regulatory)
- ✅ Cílová skupina (senior mgmt, netechnické)
- ✅ Specifické požadavky (strict regulatory)
- ✅ Očekávání (srovnání + doporučení + rizika)

**Proč to funguje lépe:**
AI teď rozumí tvé specifické situaci a může dát relevantní odpověď místo obecného "Agile je flexibilní, Waterfall je strukturovaný".

### Příklad 2 - Analytický úkol

**Prompt:**
```
**Kontext:**
Analyzuji user feedback z posledního kvartálu (250+ komentářů) pro B2B SaaS produkt.
Potřebuju pripravit report pro product team aby věděli na co se zaměřit v Q1 2026.

**Cílová skupina:**
Product manager a engineering lead (technické pozadí)

**Úkol:**
Kategorizuj feedback do témat, identifikuj top 5 priorit, a navrhni konkrétní akce.

**Formát:**
# Feedback Analysis Q4 2025

## Top 5 Témat
[Pro každé téma: název, počet zmínek, sentiment, citace]

## Doporučené Priority (Q1 2026)
[Top 5 s reasoningem proč právě tyto]

## Akční kroky
[Pro každou prioritu: konkrétní krok + effort estimate]
```

**Co jsme přidali:**
- ✅ Business kontext (B2B SaaS, Q1 planning)
- ✅ Datový kontext (250+ komentářů, Q4)
- ✅ Účel (report pro product team)
- ✅ Detailní očekávaný formát s template

### Kdy přejít na Level 4?

**Signály:**
- 🔴 Potřebuješ specifickou expertní perspektivu
- 🔴 Výstup potřebuje určitý způsob myšlení (analytický/kreativní/strategický)
- 🔴 Chceš aby AI simuloval/a konkrétní roli
- 🔴 Tone/styl není správný

---

## Level 4: Expertní prompt
**Kdy použít:** Potřebuješ specifickou expertízu, perspektivu, nebo způsob myšlení

### Šablona
```markdown
**Role:**
[Kdo má AI být - konkrétní expert s charakteristikami]

**Kontext:**
[Situace a pozadí]

**Úkol:**
[Co konkrétně udělat]

**Proces:**
[Jak k tomu přistoupit - metodologie]

**Formát:**
[Struktura výstupu]
```

### Příklad 1 - Strategické rozhodnutí

**Prompt:**
```
**Role:**
Jsi senior business konzultant s 15 lety zkušeností v digital transformation
pro mid-size firmy (50-500 zaměstnanců). Tvůj přístup kombinuje strategické
myšlení s pragmatismem - vždy zvažuješ trade-offs mezi ideálem a realitou.

**Kontext:**
Klient je výrobní firma (200 zaměstnanců) v ČR. Plánují digitalizaci jejich
manuálních procesů (objednávky, inventář, reporting). Management je nadšený,
ale IT tým je skeptický (nedostatek zdrojů, předchozí failed projekty).

**Úkol:**
Navrhni high-level roadmap pro digital transformation s realistickým
přístupem který zohledňuje limity a získá buy-in od IT týmu.

**Proces:**
1. Identifikuj hlavní pain points a quick wins
2. Navrhni fázovaný přístup (3 fáze: pilot, expand, scale)
3. Pro každou fázi: scope, timeline, resources needed, risks
4. Navrhni jak získat IT tým on-board

**Formát:**
# Digital Transformation Roadmap

## Situation Analysis
[Pain points, constraints, stakeholder concerns]

## Fázovaný přístup
### Fáze 1: Pilot (Q1-Q2 2026)
- Scope: [co]
- Timeline: [kdy]
- Resources: [kdo, kolik]
- Quick wins: [co to přinese rychle]
- Risks + mitigation: [co může selhat]

[... fáze 2, 3]

## Strategie pro IT buy-in
[Konkrétní kroky jak zapojit IT tým]
```

**Co jsme přidali:**
- ✅ Detailní role s expertízou a přístupem
- ✅ Komplexní kontext s konfliktem (mgmt vs IT)
- ✅ Strukturovaný proces (4 kroky)
- ✅ Velmi detailní formát s konkrétními sekcemi

**Proč to funguje:**
AI teď přemýšlí v roli konzultanta který zná trade-offs, ne jako obecný advisor. Výstup bude pragmatický a zohlední politickou situaci (IT skepticismus).

### Příklad 2 - Analytický úkol s metodologií

**Prompt:**
```
**Role:**
Jsi senior business analytik certifikovaný v BABOK s expertízou na requirements
engineering. Tvůj přístup je systematický - používáš proven techniky (MoSCoW,
User Story Mapping, INVEST criteria) a vždy validuješ proti best practices.

**Kontext:**
Máš 15 user stories pro nový feature "Advanced Reporting" pro B2B SaaS produkt.
Stories byly napsané různými stakeholdery a pravděpodobně obsahují gaps,
ambiguity, nebo konflikty.

**Úkol:**
Analyzuj user stories a identifikuj quality issues. Navrhni konkrétní improvements.

**Proces:**
1. Zkontroluj každou story proti INVEST criteria (Independent, Negotiable,
   Valuable, Estimable, Small, Testable)
2. Identifikuj missing acceptance criteria
3. Najdi konflikty mezi stories (dependencies, overlaps)
4. Označ ambiguous language (např. "user-friendly", "fast", "intuitive")
5. Prioritizuj issues podle severity (critical/major/minor)

**Formát:**
# User Stories Quality Analysis

## Executive Summary
[Celkový stav: kolik stories je OK, kolik má issues]

## Issues by Story
### Story ID: [ID]
**Original Story:** [text]

**Issues:**
- 🔴 CRITICAL: [popis issue]
- 🟠 MAJOR: [popis issue]
- 🟡 MINOR: [popis issue]

**Recommended fixes:**
[Konkrétní úpravy]

---

## Conflicts & Dependencies
[Cross-story problémy]

## Overall Recommendations
[Top 3-5 systémových doporučení]
```

**Co jsme přidali:**
- ✅ Expertní role s konkrétní certifikací a přístupem
- ✅ Explicitní metodologie (BABOK, INVEST, MoSCoW)
- ✅ 5-krokový proces analýzy
- ✅ Severity klasifikace (critical/major/minor)
- ✅ Velmi detailní struktura výstupu

### Kdy přejít na Level 5?

**Signály:**
- 🔴 Úkol je opravdu komplexní a kritický
- 🔴 Potřebuješ multi-step reasoning (chain-of-thought)
- 🔴 Výstup musí být validovaný proti kritériím
- 🔴 Chceš aby AI ukázal/a svoje uvažování
- 🔴 Potřebuješ few-shot learning (příklady)

---

## Level 5: Pokročilý prompt
**Kdy použít:** Kritické úkoly, komplexní analýzy, kdy kvalita je paramount

### Šablona
```markdown
**Role:**
[Detailní expertní role]

**Kontext:**
[Bohatý kontext situace]

**Úkol:**
[Velmi specifický úkol]

**Proces & Metodologie:**
[Step-by-step proces s reasoning]

**Referenční příklady:**
[1-3 konkrétní příklady očekávaného výstupu]

**Validační kritéria:**
[Checklist pro kontrolu kvality]

**Formát:**
[Detailní template]

**Omezení:**
[Co NEDĚLAT]
```

### Příklad - Komplexní strategická analýza

**Prompt:**
```
**Role:**
Jsi strategic business konzultant s MBA a 20 lety zkušeností v market entry
strategies pro tech firmy. Tvůj přístup kombinuje Porter's Five Forces,
Blue Ocean Strategy, a Jobs-to-be-Done framework. Jsi známý/á tím, že
nenabízíš generic rady - vždycky jdeš do depth a poskytneš unconventional insights.

**Kontext:**
Český B2B SaaS startup (5M Kč ARR, 10 zaměstnanců) zvažuje expanzi do Polska.
Produkt: Project management tool pro kreativní agentury. V ČR mají 45 platících
klientů, churn 8% annual, NPS 67. Competing s Asanou, Monday.com, ale naše
differentiation je "built for creative teams" (features pro kreativní workflow,
asset management integration).

Budget pro expanzi: 500k Kč na 6 měsíců. CEO chce "validovat market fit"
před větší investicí.

**Úkol:**
Navrhni 6-měsíční market entry strategii pro Polsko. Strategie musí být
realistická pro malý startup, data-driven (s metrikami pro go/no-go decision),
a musí validovat 3 klíčové hypotézy:
1. Polský trh kreativních agentur má podobné pain points jako český
2. "Built for creatives" differentiation resonuje i v Polsku
3. Dokážeme získat první 10 platících klientů do 6 měsíců s 500k budget

**Proces & Metodologie:**
1. **Market Research phase (měsíc 1-2):**
   - Identifikuj size of market (kreativní agentury v PL)
   - Analyzuj competitive landscape (kdo dominuje, jak jsou pozicionováni)
   - Identifikuj pain points (interviews, surveys, online research)
   - Validace hypotézy #1

2. **Positioning & Messaging (měsíc 2-3):**
   - Adapti value proposition pro polský trh
   - Vytvoř messaging který testuje "built for creatives" angle
   - Validace hypotézy #2 via landing page + ads

3. **Pilot Campaign (měsíc 3-5):**
   - Lean go-to-market execution (max ROI na 500k)
   - Identifikuj 2-3 acquisition channels
   - Target: 50 qualified leads, 10 trials, 3-5 paying customers
   - Validace hypotézy #3

4. **Evaluation & Decision (měsíc 6):**
   - Analyzuj data
   - Go/no-go decision framework
   - Pokud GO: roadmap pro scale. Pokud NO-GO: lessons learned

**Pro každou fázi ukaž svoje reasoning:**
- Proč tyto aktivity?
- Jaké alternatives jsi zvažoval/a a proč ne?
- Kde jsou biggest risks?

**Referenční příklady:**
### Příklad 1: Dobrá market research fáze
**Špatně:**
"Analyzuj polský trh kreativních agentur"

**Dobře:**
"Market research fáze (měsíc 1-2):
1. Desk research:
   - LinkedIn: identifikuj 100+ kreativních agentur v PL (filters: size 10-50, industries)
   - Competition: zmapuj positioning top 5 PM tools v Polsku (web, G2 reviews)
   - Pricing: benchmark jak Asana/Monday.com pricují v PL vs CZ

2. Primary research:
   - 15 discovery calls s agency owners (script: pain points, current tools, willingness to switch)
   - 2 online surveys (target: 50+ responses, validace pain points z calls)

3. Output:
   - Market size odhad (TAM/SAM/SOM)
   - Pain points ranking (top 5)
   - Validation: Are pain points similar to CZ? (YES/NO + důkazy)

Budget allocated: 80k Kč (researcher freelancer, survey tools, incentives)
Success metric: Min 15 discovery calls completed, min 50 survey responses"

Všimni si:
- Konkrétní aktivity (ne generic "research")
- Čísla (100 agencies, 15 calls, 50 responses)
- Tools a zdroje (LinkedIn, G2)
- Success metriky
- Budget

**Validační kritéria:**
Před finalizací strategie, zkontroluj:
- [ ] Je každá fáze KONKRÉTNÍ? (aktivity, čísla, not generic)
- [ ] Jsou definované SUCCESS METRIKY pro každou fázi?
- [ ] Je BUDGET rozepsaný? (každá fáze má allocated costs)
- [ ] Jsou identifikovaná RIZIKA a mitigation?
- [ ] Je GO/NO-GO framework jasný? (které metriky rozhodují)
- [ ] Je strategie REALISTIC pro 10-person startup?
- [ ] Jsou všechny 3 hypotézy VALIDOVATELNÉ v rámci 6 měsíců?

**Formát:**
# Market Entry Strategy: Polsko
## Executive Summary
[2-3 odstavce: přístup, klíčové fáze, expected outcomes]

## Fáze 1: Market Research (Měsíc 1-2)
### Cíle
[Konkrétní cíle + validace hypotézy #1]

### Aktivity
[Detail aktivity - konkrétní steps]

### Success Metriky
[Měřitelné výsledky pro go/no-go]

### Budget
[Rozpis nákladů]

### Rizika & Mitigation
[Co může selhat + jak tomu předejít]

### Timeline
Week 1-2: [konkrétní aktivity]
Week 3-4: [konkrétní aktivity]
...

[... repeat pro fáze 2, 3, 4]

## Go/No-Go Decision Framework
[Jasná kritéria: IF [metrika X] THEN [decision]]

## Alternative Scenarios
[Co když hypotézy #1 nebo #2 failnou? Pivot options?]

## Reasoning & Trade-offs
[Proč tento přístup? Co jsi zvažoval a proč ne?]

**Omezení & Guardrails:**
**NEDĚLAJ:**
- ❌ Generic rady typu "hire marketing team" (není realistic pro 10-person startup s 500k)
- ❌ Navrhovat aktivity bez konkrétních metrik
- ❌ Ignorovat budget constraint (500k = hard limit)
- ❌ Předpokládat že polský trh je stejný jako český bez validace

**MUSÍŠ:**
- ✅ Být konkrétní (čísla, aktivity, tools)
- ✅ Být realistic (10 lidí, 500k, 6 měsíců)
- ✅ Být data-driven (metriky pro každé rozhodnutí)
- ✅ Ukázat svoje reasoning (proč tento přístup)
```

**Co jsme přidali v Level 5:**
- ✅ Velmi detailní role s přístupem a filozofií
- ✅ Bohatý business kontext včetně čísel (ARR, churn, NPS)
- ✅ Explicitní hypotézy k validaci
- ✅ 4-fázový proces s reasoning requirements
- ✅ Konkrétní příklad (good vs bad)
- ✅ Validační checklist
- ✅ Explicitní omezení (co nedělat)
- ✅ Velmi detailní formát s template

**Proč Level 5:**
Tohle je strategické rozhodnutí které může stát firmu stovky tisíc Kč. Kvalita výstupu je paramount. Extra effort v promptu (5-10 minut) se vrátí ve výrazně lepším, akčním, realistickém výstupu.

---

## 🌳 Rozhodovací strom
### Který level použít pro můj úkol?

```
START: Co je tvůj úkol?
│
├─ Jednoduchý dotaz (info lookup, rychlá rada)
│  └─ ✅ LEVEL 1: Základní prompt
│
├─ Potřebuješ specifický formát/délku/strukturu
│  └─ ✅ LEVEL 2: Strukturovaný prompt
│
├─ Úkol vyžaduje pochopení kontextu/domény
│  └─ Je to kritický business úkol?
│      ├─ Ne → ✅ LEVEL 3: Kontextový prompt
│      └─ Ano → Pokračuj dolů ⬇
│
├─ Potřebuješ expertní perspektivu nebo metodologii
│  └─ Je to strategické rozhodnutí nebo high-stakes situace?
│      ├─ Ne → ✅ LEVEL 4: Expertní prompt
│      └─ Ano → ✅ LEVEL 5: Pokročilý prompt
│
└─ Opakující se úkol (děláš 5x+ měsíčně)
   └─ 💡 Zvažuj Custom GPT / Claude Skill (viz školení o kontextu)
```

### Podle typu úkolu:

| Typ úkolu | Doporučený Level | Příklad |
|-----------|------------------|---------|
| **Info lookup** | Level 1 | "Co je BABOK?" |
| **Brainstorming** | Level 1-2 | "10 nápadů na features" |
| **Formatting/editing** | Level 2 | "Přepiš do business jazyka" |
| **Analýza (jednoduchá)** | Level 2-3 | "Shrň tento feedback" |
| **Analýza (komplexní)** | Level 4-5 | "Analyzuj requirements gaps" |
| **Strategické rozhodnutí** | Level 4-5 | "Market entry strategy" |
| **Kreativní úkol s constraints** | Level 3-4 | "Návrh produktu pro segment X" |
| **Technické spec** | Level 4-5 | "API design pro use case X" |

---

## 💡 Best Practices

### 1. Začni jednoduše, iteruj

**❌ Špatně:**
Strávím 30 minut psaním mega-promptu před prvním pokusem.

**✅ Dobře:**
```
Pokus 1 (Level 1): "Analyzuj tyto user stories"
→ Výstup je moc generic

Pokus 2 (Level 2): + přidám formát a délku
→ Lepší, ale stále chybí domain knowledge

Pokus 3 (Level 3): + přidám kontext (B2B SaaS, kreativní týmy)
→ ✅ Perfektní!

Čas: 3x 2 minuty = 6 minut celkem
```

### 2. Buď konkrétní, ne vague

**❌ Vague:**
"Udělej to dobře"
"Profesionální tón"
"Rozumná délka"

**✅ Konkrétní:**
"Max 500 slov, 3 hlavní sekce, každá s 3-5 bullet points"
"Formální jazyk ale bez corporate žargonu, jako by sis psal/a s respektovaným kolegou"
"1 strana A4 (cca 400-600 slov)"

### 3. Dej příklady, ne jen popisy

**❌ Popis:**
"Chci kreativní ale profesionální headlines"

**✅ Příklad:**
"Chci headlines v tomto stylu:
- ✅ 'Ship Faster, Break Less: CI/CD for Teams That Care'
- ✅ 'Your Design System, Finally Documented'
- ❌ 'Innovative Solutions for Modern Challenges' (moc generic)"

### 4. Používej strukturu (headings, bullets)

**❌ Wall of text:**
"Potřebuju analyzovat requirements a najít konflikty mezi stakeholdery a pak identifikovat gaps a navrhnout řešení a formát by měl být tabulka a každý konflikt musí mít popis a důsledky a doporučení..."

**✅ Strukturováno:**
```
**Úkol:** Analyzuj requirements

**Hledej:**
- Konflikty mezi stakeholdery
- Gaps v requirements
- Rizika

**Formát:**
Tabulka s kolonkami: Konflikt | Dopad | Řešení
```

### 5. Prioritizuj kontext - začátek nebo konec

**Strategie:**
```
[KRITICKÁ INFORMACE]

[hlavní obsah promptu]

[PŘIPOMENUTÍ KRITICKÉ INFORMACE]
```

**Příklad:**
```
⚠️ CRITICAL: Výstup je pro CEO prezentaci - musí být business-focused, ne technický.

[... zbytek promptu ...]

REMINDER: CEO audience - avoid technical jargon, focus on business impact.
```

### 6. Definuj success kritéria

**Místo:**
"Analyzuj user stories"

**Použij:**
"Analyzuj user stories. Success znamená:
- ✓ Identifikuješ min 80% quality issues
- ✓ Každý issue má severity rating
- ✓ Návrhy řešení jsou konkrétní a actionable"

### 7. Iteruj na základě výsledků

**Workflow:**
1. První pokus → dostanu výstup
2. Co je dobře? Co chybí?
3. Uprav prompt → druhý pokus
4. Lepší? Uložím si tento prompt jako template
5. Příště začnu s tímto template, ne od nuly

---

## ⚠️ Časté chyby

### Chyba 1: Předpokládání kontextu

**❌ Špatně:**
"Analyzuj requirements na projektu"

**Problém:** AI neví jaký projekt, jaký typ requirements, pro koho.

**✅ Oprava:**
"Analyzuj functional requirements pro mobilní aplikaci (iOS). Klient je banka, projekt je v discovery fázi. Hledám gaps a ambiguity."

---

### Chyba 2: Vague formát

**❌ Špatně:**
"Dej mi dobrý output"

**Problém:** "Dobrý" je subjektivní. AI neví co očekáváš.

**✅ Oprava:**
"Formát:
\`\`\`
# Nadpis
## Sekce 1
[bullet points]
## Sekce 2
[tabulka]
\`\`\`"

---

### Chyba 3: Moc komplexní hned napoprvé

**❌ Špatně:**
Začnu s Level 5 promptem při jednoduchém úkolu.

**Problém:** Zbytečná komplexita, AI je overwhelmed, výsledek je horší.

**✅ Oprava:**
Začni Level 1 → 2 → 3 podle potřeby.

---

### Chyba 4: Zapomenuté iterace

**❌ Špatně:**
První výstup není dobrý → vzdám to, "AI nerozumí mému use case"

**Problém:** Prompt engineering JE iterativní proces.

**✅ Oprava:**
První výstup je VŽDY draft. Zeptej se: "Co konkrétně chybí?" → uprav prompt → zkus znovu.

---

### Chyba 5: Ignorování délky

**❌ Špatně:**
"Napiš analýzu" (bez specifikace délky)

**Problém:** Dostaneš 10 stránek když potřebuješ půl stránky. Nebo 2 věty když potřebuješ detail.

**✅ Oprava:**
"Max 500 slov" nebo "Min 3 stránky s detailní analýzou"

---

### Chyba 6: Chybějící omezení

**❌ Špatně:**
"Navrhni řešení" (bez constraints)

**Problém:** AI navrhne ideální řešení bez ohledu na budget, čas, resources.

**✅ Oprava:**
"Navrhni řešení. Omezení: budget 100k, timeline 2 měsíce, tým 3 lidé."

---

### Chyba 7: Nedefinovaná cílová skupina

**❌ Špatně:**
"Vytvoř dokumentaci"

**Problém:** Dokumentace pro CTO vypadá jinak než pro junior developera.

**✅ Oprava:**
"Vytvoř dokumentaci pro junior developery (1-2 roky zkušeností). Avoid žargon, explain WHY ne jen HOW."

---

## 📊 Rychlá referenční tabulka

| Pokud výstup... | Přidej do promptu... | Level doporučení |
|-----------------|----------------------|------------------|
| Je moc obecný | + Kontext (tvoje specifická situace) | → Level 3 |
| Nemá správnou strukturu | + Formát (konkrétní template) | → Level 2 |
| Nemá správný tón | + Role & Tone of voice | → Level 3-4 |
| Je moc krátký/dlouhý | + Délkové požadavky | → Level 2 |
| Chybí expertiza | + Role s konkrétní expertízou | → Level 4 |
| Je správný směr ale needs refinement | + Příklady (good vs bad) | → Level 4-5 |
| Není akční (generic rady) | + Success kritéria + Validační checklist | → Level 5 |

---

## 🎯 Quick Start Checklist

Před psaním promptu, zeptej se:

- [ ] **Je můj úkol jasný?** (1 věta: co chci aby AI udělalo)
- [ ] **Vím jaký formát chci?** (struktura, délka)
- [ ] **Potřebuje AI kontext?** (doména, situace, účel)
- [ ] **Potřebuje AI specifickou expertízu?** (role, metodologie)
- [ ] **Mám příklad toho co chci?** (ukázka good output)
- [ ] **Jsou definovaná omezení?** (co NEDĚLAT, constraints)

Odpověz ANO → přidej do promptu
Odpověz NE → pravděpodobně to nepotřebuješ

---

## 📚 Další kroky

### Po přečtení tohoto guide:

1. **Vyzkoušej progresivní přístup** na reálném úkolu:
   - Začni Level 1
   - Iteruj dokud není výstup dobrý
   - Ulož si finální prompt jako template

2. **Vytvoř si knihovnu templates:**
   - Když najdeš prompt který funguje → ulož
   - Příště začni s tímto template, ne od nuly
   - Sdílej s týmem pro konzistenci

3. **Pro opakující se úkoly:**
   - Zvažuj Custom GPT nebo Claude Skill
   - Viz školení "Práce s kontextem při práci s AI"

4. **Studuj model-specific doporučení:**
   - Viz dokument: "Model-Specific Recommendations"
   - Claude vs GPT vs Gemini mají nuance

---

**Máš otázky?**
Všechno je o praxi. První prompt nikdy není perfektní. Iteruj, testuj, učiň se co funguje pro TVŮJ use case.

---

**Verze:** 1.0 | **Datum:** Listopad 2025 | **Pro:** Školení Prompt Engineering
