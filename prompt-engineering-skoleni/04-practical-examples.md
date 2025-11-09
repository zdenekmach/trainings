# Praktické příklady použití šablony promptů
## Real-world use cases s komentáři

> **Účel:** Tento dokument obsahuje 5 reálných příkladů použití šablony promptu pro různé typy úkolů. Každý příklad je okomentovaný - vysvětluje PROČ jsou použité specifické sekce.

---

## 📋 Obsah

1. [Příklad 1: Analytický úkol - Requirements Analysis](#příklad-1-requirements-analysis)
2. [Příklad 2: Strategický úkol - Market Entry Strategy](#příklad-2-market-entry-strategy)
3. [Příklad 3: Kreativní úkol - Product Description](#příklad-3-product-description)
4. [Příklad 4: Technický úkol - API Design](#příklad-4-api-design)
5. [Příklad 5: Jednoduchý úkol - Email Template](#příklad-5-email-template)

---

## Příklad 1: Requirements Analysis
### Analytický úkol - střední komplexita

**Use case:** Máš requirements od 3 stakeholderů, potřebuješ najít konflikty a gaps.

**Level použitý:** Level 4 (Expertní prompt)

**Proč tento level?**
- ✅ Vyžaduje domain expertise (BA skills)
- ✅ Potřebuji metodologii (systematický přístup)
- ✅ Business kontext je důležitý
- ❌ Není kritický (není Level 5), ale není ani jednoduchý (není Level 2)

---

### Finální prompt:

```markdown
# Requirements Quality Analysis

## ROLE & EXPERTIZA
Vystupuj jako **senior business analytik** s těmito charakteristikami:
- IIBA CBAP certifikace, 10+ let zkušeností
- Expert na requirements elicitation a validaci
- Používáš BABOK best practices
- Systematický přístup: identifikuješ patterns, ne jen surface issues

**Tone of voice:** Profesionální ale konstruktivní. Kritizuješ issues, ale vždycky nabídneš solution.

---

## KONTEXT & POZADÍ

**Situace:**
Projekt: Nový modul "Advanced Reporting" pro B2B SaaS projekt management tool.
Fáze: Discovery dokončena, nyní validace requirements před přechodem do design.

**Relevantní informace:**
- 3 stakeholdeři poskytli requirements (Product Owner, Head of Engineering, Customer Success Lead)
- Každý stakeholder má jiné priority (features vs. technical feasibility vs. customer demands)
- Timeline: Design musí začít za 2 týdny
- Tým: 5 vývojářů, 1 designer, limitované resources

**Cílová skupina:**
Product team (Product Owner + Engineering Lead) - technicky zdatní, potřebují actionable insights

---

## HLAVNÍ ÚKOL

Analyzuj tyto 3 sady requirements a identifikuj quality issues.
Zaměř se na:
1. **Konflikty** mezi stakeholdery (co si odporuje)
2. **Gaps** (co chybí, nedefinované acceptance criteria)
3. **Ambiguity** (vague language, nejasné požadavky)
4. **Unrealistic expectations** (given timeline a resources)

**Success criteria:**
- ✓ Identifikuješ min 80% významných issues (conflikty, gaps)
- ✓ Každý issue má severity rating (Critical/Major/Minor)
- ✓ Navrhneš konkrétní, akční řešení (ne generic "clarify with stakeholder")
- ✓ Output je prioritizovaný - team ví co řešit první

---

## PROCES & METODOLOGIE

Postupuj systematicky:

**1. Requirement Quality Check (INVEST criteria)**
   - Pro každý requirement: Je Independent, Negotiable, Valuable, Estimable, Small, Testable?
   - Flag requirements které failují INVEST
   - *Očekávaný mezioutput:* Seznam requirements s INVEST pass/fail

**2. Cross-Stakeholder Conflict Analysis**
   - Identifikuj kde stakeholdeři chtějí incompatible věci
   - Např. PO chce feature X, Engineering říká "not feasible in timeline"
   - *Očekávaný mezioutput:* Tabulka konfliktů

**3. Gap Analysis**
   - Co chybí? (acceptance criteria, edge cases, error handling)
   - Který use case není covered?
   - *Očekávaný mezioutput:* Seznam gaps

**4. Ambiguity Detection**
   - Vague terms: "user-friendly", "fast", "intuitive", "seamless"
   - Undefined: "advanced analytics" (co to konkrétně znamená?)
   - *Očekávaný mezioutput:* Seznam ambiguous requirements

**5. Prioritizace & Recommendations**
   - Severity: Critical (blocker pro design) vs Major vs Minor
   - Konkrétní next steps
   - *Očekávaný finální output:* Actionable prioritizovaný plán

**Pro komplexní konflikty: Ukaž svoje reasoning**
Pokud je konflikt netriviální, vysvětli trade-offs a proč navrhuje
š dané řešení.

---

## POŽADAVKY & SPECIFIKACE

### Obsahové požadavky:
- ✓ Každý issue má: popis, severity, dopad na projekt, navržené řešení
- ✓ Konflikty mají identifikované stakeholdery (kdo vs kdo)
- ✓ Gaps jsou specific (ne "chybí detaily", ale "chybí acceptance criteria pro error state when API fails")

### Technické požadavky:
- **Délka:** Max 3 strany A4 (focus na actionable, ne verbose)
- **Jazyk:** Čeština, odborná ale srozumitelná
- **Formát:** Markdown s tabulkami

### Kvalitativní požadavky:
- **Hloubka:** Deep analysis (ne surface-level "tohle je vague")
- **Actionability:** Každý issue má konkrétní next step
- **Prioritizace:** Jasně viditelné co je critical vs nice-to-fix

---

## FORMÁT VÝSTUPU

```markdown
# Requirements Quality Analysis - Advanced Reporting Module

## Executive Summary
[2-3 věty: Celkový stav, počet issues, hlavní doporučení]

**Overall Quality Score:** [X/10]
**Critical Issues:** [počet]
**Timeline Risk:** [High/Medium/Low]

---

## Critical Issues (must fix before design)

### Issue #1: [Název]
**Type:** Conflict / Gap / Ambiguity
**Severity:** 🔴 CRITICAL
**Stakeholders involved:** [kdo]
**Description:** [Co je problém]
**Impact:** [Proč je to critical - co se stane když to neřešíme]
**Recommended Solution:** [Konkrétní akční krok]
**Owner:** [Kdo by měl řešit]

[... další critical issues]

---

## Major Issues (should fix)

### Issue #X: [Název]
**Type:** Conflict / Gap / Ambiguity
**Severity:** 🟠 MAJOR
[... same structure as critical]

---

## Minor Issues (nice to fix)

[Seznam minor issues - bullet points stačí]

---

## Detailed Findings

### Conflicts Between Stakeholders

| Conflict | Stakeholder A | Stakeholder B | Impact | Recommended Resolution |
|----------|---------------|---------------|--------|------------------------|
| Export formats | PO: "Support PDF, Excel, PowerPoint" | Eng: "Only PDF realistic in timeline" | Timeline risk | Phase 1: PDF only. Excel/PPT in Phase 2 |
| ... | ... | ... | ... | ... |

### Gaps in Requirements

| Gap | Missing Element | Impact | Recommended Action |
|-----|-----------------|--------|---------------------|
| Error handling | No spec for API timeout scenarios | Poor UX | Define timeout UX + retry logic |
| ... | ... | ... | ... |

### Ambiguous Language

| Requirement ID | Ambiguous Term | Issue | Suggested Clarification |
|----------------|----------------|-------|------------------------|
| REQ-42 | "Advanced analytics" | Undefined scope | Specify: Which metrics? Visualizations? Filters? |
| ... | ... | ... | ... |

---

## Recommendations & Next Steps

**Immediate Actions (before design starts):**
1. [Action 1 - owner, deadline]
2. [Action 2 - owner, deadline]
3. [Action 3 - owner, deadline]

**Stakeholder Alignment Session Needed:**
- [ ] Resolve conflict: Export formats (PO + Engineering)
- [ ] Define scope: "Advanced analytics" (PO + Customer Success)

**Documentation Updates Required:**
- [ ] Add acceptance criteria for [X]
- [ ] Define error states for [Y]

---

## Appendix: INVEST Check Results

[Tabulka všech requirements s INVEST pass/fail]
```

---

## OMEZENÍ & GUARDRAILS

**NEDĚLEJ:**
- ❌ Generic rady typu "clarify with stakeholder" (buď specific - ČÍM clarify)
- ❌ Listing každý minor issue - focus na impact
- ❌ Blame stakeholdery ("PO clearly didn't think this through") - buď konstruktivní

**MUSÍŠ:**
- ✅ Každý issue má navržené řešení
- ✅ Severity je based on impact, ne jen "tohle je vague"
- ✅ Recommendations jsou actionable (kdo, co, kdy)

---

## VALIDAČNÍ CHECKLIST

Před finalizací, zkontroluj:
- [ ] Jsou všechny critical issues identified? (min 3-5 očekávám)
- [ ] Má každý issue severity + dopad + řešení?
- [ ] Jsou konflikty jasně attributed (stakeholder A vs B)?
- [ ] Jsou gaps konkrétní (ne "chybí detaily")?
- [ ] Je output max 3 strany? (ne verbose)
- [ ] Je prioritizace jasná? (co řešit první)

---

## METADATA
- **Priorita:** Vysoká (blokuje design fázi)
- **Složitost:** Komplexní (vyžaduje BA expertizu)
- **Časový odhad:** Hloubková analýza (15-20 min)
- **Model preference:** Claude Sonnet 4 (best pro analytical depth)

---

## INPUTS

[Zde by následovaly 3 sady requirements od stakeholderů]

**Stakeholder 1 - Product Owner:**
[Requirements...]

**Stakeholder 2 - Head of Engineering:**
[Requirements...]

**Stakeholder 3 - Customer Success Lead:**
[Requirements...]
```

---

### 💬 Komentář k tomuto příkladu:

**Co funguje:**
- ✅ Jasná role s konkrétní expertízou (CBAP, BABOK)
- ✅ Bohatý kontext (projekt, timeline, team size)
- ✅ 5-krokový proces (systematický přístup)
- ✅ Velmi detailní formát (AI ví přesně co vytvořit)
- ✅ Validační checklist (zajistí kvalitu)

**Proč Level 4, ne Level 5:**
- ❌ Není to strategické rozhodnutí za miliony
- ❌ Nepotřebuji few-shot examples (formát je jasný z template)
- ✅ Ale potřebuji expertízu + metodologii → Level 4

**Expected output quality:**
S tímto promptem dostanu professional BA analysis která je directly actionable.

---

## Příklad 2: Market Entry Strategy
### Strategický úkol - vysoká komplexita

**Use case:** Startup zvažuje expanzi do nového trhu. Kritické business rozhodnutí.

**Level použitý:** Level 5 (Pokročilý prompt)

**Proč Level 5?**
- ✅ Strategické rozhodnutí (high stakes)
- ✅ Potřebuji multi-perspective reasoning
- ✅ Musím validovat hypotézy
- ✅ Kvalita výstupu je paramount (špatný strategy = ztráta peněz)

---

### Finální prompt:

```markdown
# 6-Month Market Entry Strategy: Poland

## ROLE & EXPERTIZA

Jsi **strategic business konzultant** specializovaný na market entry strategies pro tech startupy s těmito charakteristikami:

**Expertise:**
- MBA (International Business), 15+ let zkušeností
- Specializace: B2B SaaS expanze do CEE regionu
- Track record: 12 successful market entries, 3 failed (učil ses z chyb)
- Frameworks: Porter's Five Forces, Blue Ocean Strategy, Jobs-to-be-Done, Lean Startup

**Přístup:**
- Data-driven: Každé rozhodnutí backed metr
ikami
- Pragmatický: Realistické strategie pro malé startupy (ne corporate playbooks)
- Risk-aware: Vždycky identifikuješ co může selhat
- Lean mentality: Minimal viable experiments, fast learning

**Filozofie:**
"Better to validate cheaply and pivot than invest heavily and fail."

**Tone:** Profesionální, direct, bez corporate BS. Mluvíš numbers a facts, ne generic buzzwords.

---

## KONTEXT & POZADÍ

**Klient:**
- Český B2B SaaS startup: Project management tool pro kreativní agentury
- Firma: 10 zaměstnanců, bootstrapped (no VC funding)
- Current state: 5M Kč ARR (Annual Recurring Revenue)
- Čeští klienti: 45 platících agentur (size 10-50 people)
- Churn rate: 8% annual (good)
- NPS: 67 (solid)

**Produkt differentiation:**
"Built for creative teams" - features specifické pro kreativní workflow:
- Asset management integration (Figma, Adobe CC)
- Client feedback loops
- Creative briefs templates
- Time tracking for billable hours by project phase

**Konkurence:**
Asana, Monday.com, ClickUp (generické PM tools)
Naše edge: Specificity pro creative agencies

**Expansion target:**
Polsko - geograficky blízko, podobná kultura, větší trh

**Resources pro expanzi:**
- Budget: 500k Kč na 6 měsíců (hard limit)
- People: Founder (50% času), 1 marketing person (100% času)
- Timeline: 6 měsíců na validaci, pak go/no-go decision

**Cílová skupina (tohoto dokumentu):**
Founder + board (3 angel investors) - potřebují see clear plan + metrics pro go/no-go

---

## HLAVNÍ ÚKOL

Navrhni **6-měsíční market entry strategii pro Polsko** která je:
1. **Realistic** pro 10-person bootstrapped startup s 500k Kč budgetem
2. **Data-driven** - každá fáze má clear success metriky
3. **Validační** - zaměřená na testing 3 klíčových hypotéz (viz níže)
4. **Actionable** - founder může execute immediately

**Klíčové hypotézy k validaci:**
1. **Hypotéza #1 (Market fit):** Polský trh kreativních agentur má podobné pain points jako český
2. **Hypotéza #2 (Differentiation):** "Built for creatives" positioning resonuje i v Polsku
3. **Hypotéza #3 (Commercial viability):** Dokážeme získat první 10 platících klientů do 6 měsíců s 500k budget

**Success znamená:**
Na konci 6 měsíců máme data pro confident go/no-go decision pro full market entry.

---

## PROCES & METODOLOGIE

**Postupuj ve 4 fázích:**

### Fáze 1: Market Research & Validation (Měsíc 1-2)
**Cíl:** Validovat hypotézu #1 (market fit)

**Aktivity:**
- Desk research: Size of Polish creative agency market
- Competitive analysis: Jak jsou pozicionováni Asana/Monday v PL
- Primary research: 15 discovery interviews s Polish agency owners
- Pain points mapping: Jaké problémy mají s current PM tools

**Success metriky:**
- Min 15 completed interviews
- Min 3 verified pain points shared s českým trhem
- GO/NO-GO: If <50% pain point overlap → STOP

### Fáze 2: Positioning & Messaging Test (Měsíc 2-3)
**Cíl:** Validovat hypotézu #2 (differentiation resonuje)

**Aktivity:**
- Adapt messaging pro Polish market
- Create landing page (Polish)
- Run small ad campaign (Google/Facebook)
- A/B test: "Creative-specific" vs "Generic PM tool" messaging

**Success metriky:**
- 100 landing page visits
- 20+ email sign-ups
- Survey: "Is creative-specific positioning relevant?" >60% YES
- GO/NO-GO: If <60% relevance → pivot positioning

### Fáze 3: Pilot Sales Campaign (Měsíc 3-5)
**Cíl:** Validovat hypotézu #3 (commercial viability)

**Aktivity:**
- Outbound: 200 targeted agencies (LinkedIn, email)
- Inbound: Content marketing (Polish blog posts, case studies)
- Free trials: 20 agencies
- Sales calls: Convert trials to paid

**Success metriky:**
- 50 qualified leads (agencies 10-50 people, using PM tool)
- 20 trial sign-ups
- 5-10 paying customers (€50/měsíc each)
- CAC (Customer Acquisition Cost) <€500
- GO/NO-GO: If <5 customers OR CAC >€500 → re-evaluate

### Fáze 4: Evaluation & Decision (Měsíc 6)
**Cíl:** Analyzovat data, make go/no-go decision

**Aktivity:**
- Data analysis: All metriky from fáze 1-3
- Financial projection: If we GO, what's required investment?
- Risk assessment: What can go wrong in scale phase?
- Decision framework: Clear GO/NO-GO criteria

**Output:**
- GO → Roadmap pro scaling (hire Polish sales, localization, budget++)
- NO-GO → Lessons learned + alternative markets to consider

---

**Pro každou fázi:**
Ukaż svoje **reasoning**:
- Proč tyto aktivity?
- Jaké alternatives jsi zvažoval/a a proč ne?
- Co je biggest risk v této fázi?

---

## REFERENČNÍ PŘÍKLADY

### Příklad 1: DOBRÁ market research fáze

**✅ Konkrétní a actionable:**

"**Market Research Fáze (Měsíc 1-2)**

**Desk Research (Week 1-2):**
1. LinkedIn search:
   - Filters: "Creative agency" OR "Design studio", Poland, 10-50 employees
   - Target: Identify 200+ agencies, export to spreadsheet
   - Budget: €0 (LinkedIn free)

2. Competitive intel:
   - Visit Asana.com/pl, Monday.com/pl - analyze messaging
   - G2 reviews: Read 50+ Polish reviews of PM tools - identify pain points
   - Pricing: Benchmark how they price in PL vs CZ
   - Budget: €0

3. Market size:
   - Source: Statista, gov data - estimate TAM (Total Addressable Market)
   - Calculation: [# agencies 10-50] × [avg PM tool spend]
   - Budget: €50 (Statista subscription)

**Primary Research (Week 3-6):**
1. Discovery interviews:
   - Recruit: Reach out via LinkedIn to 50 agency owners, target 15 interviews
   - Script: [standard discovery questions]
   - Incentive: €20 gift card per interview
   - Budget: 15 × €20 = €300

2. Survey:
   - Tool: Typeform
   - Target: 100 responses (via LinkedIn, Polish PM groups)
   - Questions: Current tools, pain points, willingness to switch
   - Budget: €30 (Typeform)

**Outputs:**
- Market size estimate (TAM/SAM/SOM)
- Pain points ranking (top 5 with quotes)
- Validation: Are pain points similar to CZ? (YES/NO + evidence)

**Total budget: €380**
**Time: 6 weeks**
**Success metric: Min 15 interviews + 100 survey responses**"

**Proč je tento příklad dobrý:**
- Konkrétní tools (LinkedIn, G2, Typeform)
- Čísla (200 agencies, 15 interviews, €20 per interview)
- Timeline (week-by-week)
- Budget breakdown
- Success metriky

---

### Příklad 2: ŠPATNÁ market research fáze

**❌ Generic a ne-actionable:**

"**Market Research Fáze (Měsíc 1-2)**

**Aktivity:**
- Analyzuj polský trh
- Prozkoumej konkurenci
- Mluv se stakeholdery
- Validuj market fit

**Budget:** Část z 500k

**Očekávaný output:**
- Report o trhu
- Seznam konkurentů
- Insights z interviews"

**Co je špatně:**
- ❌ Žádné konkrétní tools/zdroje
- ❌ Žádná čísla (kolik interviews? kolik stojí?)
- ❌ Není timeline
- ❌ Generic aktivity ("analyzuj trh" - JAK?)
- ❌ Budget není rozepsaný
- ❌ Není success metrika

Founder s tímhle nemůže nic udělat. Potřebuje actionable plan.

---

## FORMÁT VÝSTUPU

```markdown
# Market Entry Strategy: Poland 🇵🇱
## 6-Month Validation Plan

### Executive Summary
[3-4 odstavce: Přístup, klíčové fáze, expected outcomes, required investment]

**Bottom line:**
- Total budget: 500k Kč
- Timeline: 6 months
- Target outcome: 5-10 paying customers + data for go/no-go
- Risk level: [Low/Medium/High] + biggest risk

---

## Strategic Approach

**Lean Startup methodology:**
[Vysvětli proč lean approach pro tento use case]

**Key assumptions we're testing:**
1. [Hypotéza #1 + proč je critical]
2. [Hypotéza #2 + proč je critical]
3. [Hypotéza #3 + proč je critical]

---

## Fáze 1: Market Research & Validation
### Měsíc 1-2

**Objective:**
[Konkrétní cíl + validace které hypotézy]

**Activities:**

#### Desk Research (Week 1-2)
1. **[Aktivita 1]**
   - Co: [konkrétní steps]
   - Tools: [jaké nástroje]
   - Output: [co dostaneme]
   - Budget: [€X]

2. **[Aktivita 2]**
   [... stejná struktura]

#### Primary Research (Week 3-6)
[... detailní breakdown]

**Success Metriky:**
- [ ] Metric 1: [konkrétní číslo]
- [ ] Metric 2: [konkrétní číslo]

**GO/NO-GO Decision:**
IF [podmínka] THEN STOP, ELSE continue

**Budget Breakdown:**
| Item | Cost | Notes |
|------|------|-------|
| [Item 1] | €X | [detail] |
| **Total** | **€X** | **X% of total budget** |

**Risks & Mitigation:**
- Risk: [co může selhat]
  - Mitigation: [jak tomu předejít]

**Timeline:**
```
Week 1: [konkrétní aktivity]
Week 2: [konkrétní aktivity]
...
```

**Reasoning:**
[Proč tento přístup? Co jsi zvažoval jako alternativy? Proč jsi je zavrhl?]

---

[... REPEAT pro Fáze 2, 3, 4 se stejnou strukturou]

---

## Go/No-Go Decision Framework

**GO criteria (all must be TRUE):**
- ✅ [Metrika 1] achieved
- ✅ [Metrika 2] achieved
- ✅ [Metrika 3] achieved
- ✅ CAC < €500
- ✅ Min 5 paying customers

**NO-GO criteria (any is TRUE):**
- ❌ Pain point overlap <50% (market not similar)
- ❌ Positioning relevance <60% (differentiation doesn't resonate)
- ❌ <3 paying customers (commercial viability failed)
- ❌ CAC >€1000 (too expensive to acquire)

**If GO → Next Steps:**
[Roadmap pro scaling: hiring, budget needed, timeline]

**If NO-GO → Pivot Options:**
[Alternative markets, alternative approaches]

---

## Financial Summary

| Fáze | Budget Allocated | % of Total |
|------|------------------|------------|
| Fáze 1 | X Kč | Y% |
| Fáze 2 | X Kč | Y% |
| Fáze 3 | X Kč | Y% |
| Fáze 4 | X Kč | Y% |
| **Contingency** | X Kč | 10% |
| **TOTAL** | **500k Kč** | **100%** |

**ROI Projection (if GO):**
[Optimistic / Realistic / Pessimistic scenarios]

---

## Risk Analysis

### Top 5 Risks

**1. [Risk name]**
- **Probability:** High/Medium/Low
- **Impact:** High/Medium/Low
- **Mitigation:** [konkrétní kroky]
- **Contingency:** [co když se stane]

[... repeat pro risks 2-5]

---

## Alternative Scenarios

**What if Hypotéza #1 fails?**
[Konkrétní pivot plan]

**What if Hypotéza #2 fails but #1 passes?**
[Pivot positioning strategy]

**What if budget runs out at Month 4?**
[Minimal viable plan to get some data]

---

## Reasoning & Trade-offs

**Why Poland?**
[Reasoning pro choice of market]

**Why 6 months?**
[Reasoning pro timeline]

**Why these metrics?**
[Reasoning pro choice of success criteria]

**Alternatives considered:**
1. [Alternative approach 1] - Why not: [reason]
2. [Alternative approach 2] - Why not: [reason]

**Trade-offs accepted:**
- Accepting: [X] to gain: [Y]
- Example: "Accepting smaller sample size (15 interviews vs 50) to stay in budget, but mitigating via survey (100 responses)"
```

---

## OMEZENÍ & GUARDRAILS

**NEDĚLEJ:**
- ❌ Generic rady typu "hire marketing team" (unrealistic pro bootstrapped startup)
- ❌ Aktivity bez konkrétních metrik/čísel
- ❌ Předpokládat že Polish market = Czech market (musí validate)
- ❌ Ignorovat budget constraint (500k = hard limit)
- ❌ Navrhovat "hire agency" (když můžou udělat in-house)

**MUSÍŠ:**
- ✅ Každá aktivita má: konkrétní steps, tools, budget, timeline
- ✅ Každá fáze má: clear success metriky + GO/NO-GO decision
- ✅ Budget je rozepsaný na položky
- ✅ Risks jsou identified s mitigation
- ✅ Reasoning je explained (proč tento přístup)
- ✅ Být realistic (10 lidí, 500k, 6 měsíců)

---

## VALIDAČNÍ CHECKLIST

Před finalizací strategie, zkontroluj:

- [ ] **Konkrétnost:** Je každá aktivita specific? (ne "research market" ale "LinkedIn search: filters X, Y, export 200 agencies")
- [ ] **Čísla:** Jsou všude numbers? (kolik interviews, kolik stojí, timeline week-by-week)
- [ ] **Budget:** Je každá fáze rozepsaná? Celkem = 500k?
- [ ] **Metriky:** Má každá fáze success metriky? (měřitelné, ne vague)
- [ ] **GO/NO-GO:** Je jasný decision framework?
- [ ] **Realism:** Je to realistic pro 10-person startup? (ne corporate playbook)
- [ ] **Rizika:** Jsou top 5 risks identified + mitigation?
- [ ] **Hypotézy:** Jsou všechny 3 hypotézy validovatelné v rámci 6 měsíců?
- [ ] **Reasoning:** Je vysvětleno PROČ tento přístup? (alternatives, trade-offs)
- [ ] **Actionability:** Může founder začít execute zítra?

Pokud něco failuje checklist → FIX before finalizace.

---

## METADATA

- **Priorita:** Kritická (strategic business decision, stovky tisíc Kč at stake)
- **Složitost:** Velmi komplexní (multi-fázový, multi-měsíční project)
- **Časový odhad:** Hloubková analýza (20-30 min pro AI)
- **Model preference:** Claude Opus 4 nebo ChatGPT o1-preview
  - **Důvod:** Strategic complexity + reasoning vyžaduje top-tier model
```

---

### 💬 Komentář k příkladu 2:

**Proč Level 5:**
- ✅ High-stakes strategic decision (failure = stovky tisíc Kč lost)
- ✅ Komplexní multi-fázový plán
- ✅ Potřeba reasoning (explain WHY, not just WHAT)
- ✅ Need for examples (good vs bad research fáze)
- ✅ Validační checklist (10 points) - quality assurance

**Expected output:**
S tímhle promptem dostanu 10-15 stránkový dokument který je:
- Immediately actionable (founder může začít execute)
- Data-driven (metriky pro každé rozhodnutí)
- Realistic (zohledňuje constraints: 10 lidí, 500k, 6 měsíců)
- Risk-aware (top 5 risks + mitigation)

**Effort vs value:**
- Prompt creation: ~20-30 minut
- AI processing: ~5-10 minut (Opus/o1 jsou pomalejší)
- **Value:** Save weeks of founder time + avoid costly mistakes

---

## Příklad 3: Product Description
### Kreativní úkol - nízká až střední komplexita

**Use case:** Potřebuješ catchy product description pro website.

**Level použitý:** Level 3 (Kontextový prompt)

**Proč Level 3, ne víc?**
- ✅ Potřebuji kontext (target audience, product specifics)
- ✅ Potřebuji tone of voice
- ❌ Nepotřebuji expertní metodologii
- ❌ Není to kritický úkol (můžu snadno iterovat)

---

### Finální prompt:

```markdown
# Product Description - FitFlow App

## KONTEXT & POZADÍ

**Produkt:**
FitFlow - Mobilní fitness aplikace pro busy profesionály (age 28-45)

**Unique value proposition:**
"15-minute science-based workouts you can do anywhere, no equipment needed"

**Differentiation:**
- Konkurence (Peloton, Nike Training): vyžadují 45-60 min + často equipment
- My: Ultra-short (15 min), designed pro people s packed schedules
- Science-backed: Vytvořeno s sports physiology PhD

**Target audience:**
- Busy professionals (managers, entrepreneurs)
- Age 28-45
- Chtějí být fit, ale "nemají čas" na gym/dlouhé workouti
- Value efficiency

**Cílová skupina (tohoto textu):**
Landing page visitors - první dojem, musí zaujmout za 3 sekundy

---

## HLAVNÍ ÚKOL

Vytvoř product description pro FitFlow app homepage.

**Success criteria:**
- ✓ Catchy headline (max 10 slov) - grab attention immediately
- ✓ Jasný value proposition (2-3 věty) - proč FitFlow, ne konkurence
- ✓ 3 klíčové benefity (bullet points) - addressing target audience pain points
- ✓ Call-to-action (CTA) - motivující, actionable

---

## FORMÁT VÝSTUPU

```markdown
# [HEADLINE]
[Max 10 slov, catchy, benefit-driven]

## [SUBHEADLINE / Value Proposition]
[2-3 věty: Co je FitFlow, proč je jiný, pro koho je]

## Why FitFlow?

✓ **[Benefit 1 Title]**
[1-2 věty explaining benefit, addressing pain point]

✓ **[Benefit 2 Title]**
[1-2 věty]

✓ **[Benefit 3 Title]**
[1-2 věty]

---

**[Call-to-Action]**
[Motivující CTA, max 5 slov]
```

---

## POŽADAVKY & SPECIFIKACE

### Obsahové požadavky:
- ✓ Headline musí emphasize "15 minutes" (key differentiator)
- ✓ Benefity musí address pain points: "no time", "no equipment", "effectiveness"
- ✓ Mention "science-based" (credibility)

### Tone of voice:
- Motivační but realistic (ne over-the-top "transform your life!")
- Profesionální but friendly
- Empathetic k busy lifestyle

**Examples of tone:**
- ✅ "Get fit on your schedule" (empathetic, realistic)
- ❌ "Become a fitness god in 15 minutes!" (over-the-top, unrealistic)

### Technické požadavky:
- **Délka:** Celkem max 150 slov
- **Jazyk:** Angličtina, conversational but polished
- **Avoid:** Fitness žargon, medical termíny (keep accessible)

---

## OMEZENÍ

**NEDĚLEJ:**
- ❌ Unrealistic claims ("Get six-pack in 2 weeks")
- ❌ Comparison s konkrétními brands (ne "better than Peloton" - legal risk)
- ❌ Příliš formal/corporate tone

---

## METADATA
- **Priorita:** Střední
- **Složitost:** Jednoduchý až střední
- **Model preference:** Claude Sonnet 4 (best pro nuancovaný jazyk) nebo GPT-4.1
```

---

### 💬 Komentář:

**Proč Level 3 stačí:**
- ✅ Jednoduchý úkol (product copy)
- ✅ Kontext + tone of voice vysvětleno
- ✅ Jasný formát
- ❌ Nepotřebuji expertní metodologii
- ❌ Můžu snadno iterovat pokud první pokus není dokonalý

**Expected result:**
Catchy, benefit-driven product description ready for landing page.

---

## Příklad 4: API Design
### Technický úkol - střední až vysoká komplexita

**Use case:** Návrh RESTful API pro nový feature.

**Level použitý:** Level 4 (Expertní prompt)

**Proč Level 4?**
- ✅ Technická expertíza needed
- ✅ Best practices jsou důležité (RESTful standards)
- ✅ Musí být well-designed (změny API jsou costly)
- ❌ Není ultra-critical (Level 5), ale není ani simple

---

### Finální prompt:

```markdown
# RESTful API Design - Advanced Reporting Feature

## ROLE & EXPERTIZA

Vystupuj jako **senior API architect** s těmito charakteristikami:
- 10+ let zkušeností s RESTful API design
- Expert na API best practices (REST maturity, Richardson model, HATEOAS)
- Znáš OpenAPI/Swagger specification
- Focus na developer experience (DX) - API musí být intuitive

**Přístup:**
- Follow RESTful conventions (proper HTTP verbs, status codes)
- Design for extensibility (API verze budou evolve)
- Clear error messaging
- Documentation-first mindset

**Tone:** Technical but clear. Pro senior backend developery.

---

## KONTEXT & POZADÍ

**Projekt:**
B2B SaaS project management tool - přidáváme "Advanced Reporting" feature

**Současný API:**
- RESTful API v1 (stable, dokumentovaný)
- Auth: JWT tokens
- Format: JSON
- Versioning: URL-based (/api/v1/...)

**Nový feature: Advanced Reporting**
Umožní uživatelům:
- Vytvářet custom reporty (choose metrics, filters, date range)
- Ukládat report templates
- Schedulovat automated reports (email delivery)
- Export reports (PDF, Excel, CSV)

**Constraints:**
- Must fit do existing /api/v1 structure
- Backwards compatibility (nesmíme rozbít existing clients)
- Performance: Reports můžou být data-heavy (pagination needed)

---

## HLAVNÍ ÚKOL

Navrhni RESTful API endpoints pro Advanced Reporting feature.

**Success criteria:**
- ✓ Proper RESTful design (HTTP verbs, resource naming)
- ✓ Všechny use cases covered (create, read, update, delete reporty + templates + schedules)
- ✓ Error handling defined (error codes, messages)
- ✓ Pagination strategy for large datasets
- ✓ Clear OpenAPI spec (ready pro implementation)

---

## PROCES & METODOLOGIE

**1. Identifikuj resources**
   - Které entity máme? (Reports, Templates, Schedules)
   - Jaké jsou relationships?

**2. Navrhni endpoints**
   - RESTful naming conventions
   - Proper HTTP verbs (GET, POST, PUT, PATCH, DELETE)
   - URL structure

**3. Define request/response schemas**
   - JSON schemas pro každý endpoint
   - Validation rules

**4. Error handling**
   - HTTP status codes
   - Error response format

**5. Pagination & filtering**
   - Strategy pro large datasets

---

## FORMÁT VÝSTUPU

```markdown
# API Specification: Advanced Reporting

## Resources Overview

**Primary resources:**
1. **Reports** - Generated reports (data + metadata)
2. **Templates** - Saved report configurations
3. **Schedules** - Automated report generation + delivery

**Resource relationships:**
[Diagram or description]

---

## Endpoints

### 1. Reports

#### GET /api/v1/reports
**Description:** List all reports for authenticated user

**Query parameters:**
- `page` (integer, optional): Page number (default: 1)
- `per_page` (integer, optional): Items per page (default: 20, max: 100)
- `filter[status]` (string, optional): Filter by status (pending/completed/failed)
- `filter[date_from]` (ISO 8601, optional): Created after
- `filter[date_to]` (ISO 8601, optional): Created before
- `sort` (string, optional): Sort field (created_at, name), prefix with - for desc

**Response (200 OK):**
```json
{
  "data": [
    {
      "id": "rep_abc123",
      "type": "report",
      "attributes": {
        "name": "Q4 Performance Report",
        "status": "completed",
        "created_at": "2025-11-01T10:30:00Z",
        "generated_at": "2025-11-01T10:35:00Z",
        "metrics": ["tasks_completed", "time_tracked"],
        "filters": {...},
        "data_url": "/api/v1/reports/rep_abc123/data"
      },
      "links": {
        "self": "/api/v1/reports/rep_abc123"
      }
    }
  ],
  "meta": {
    "current_page": 1,
    "total_pages": 5,
    "total_count": 94,
    "per_page": 20
  },
  "links": {
    "self": "/api/v1/reports?page=1",
    "next": "/api/v1/reports?page=2",
    "last": "/api/v1/reports?page=5"
  }
}
```

**Errors:**
- `401 Unauthorized`: Invalid/missing JWT token
- `429 Too Many Requests`: Rate limit exceeded

---

#### POST /api/v1/reports
**Description:** Create new report

**Request body:**
```json
{
  "name": "Q4 Performance Report",
  "template_id": "tpl_xyz789" (optional),
  "metrics": ["tasks_completed", "time_tracked"],
  "filters": {
    "project_ids": ["proj_1", "proj_2"],
    "date_range": {
      "start": "2025-10-01",
      "end": "2025-12-31"
    }
  },
  "format": "json" (or "csv", "pdf")
}
```

**Response (201 Created):**
```json
{
  "data": {
    "id": "rep_new123",
    "type": "report",
    "attributes": {
      "name": "Q4 Performance Report",
      "status": "pending",
      "created_at": "2025-11-09T14:20:00Z",
      ...
    },
    "links": {
      "self": "/api/v1/reports/rep_new123"
    }
  }
}
```

**Errors:**
- `400 Bad Request`: Invalid request body (details in error message)
- `422 Unprocessable Entity`: Validation failed
  ```json
  {
    "errors": [
      {
        "field": "metrics",
        "message": "At least one metric is required"
      }
    ]
  }
  ```

---

[... Continue s dalšími endpoints: GET /reports/:id, DELETE /reports/:id, etc.]
[... Templates endpoints: GET/POST/PUT/DELETE /api/v1/templates/...]
[... Schedules endpoints: GET/POST/PUT/DELETE /api/v1/schedules/...]

---

## Error Handling

**Standard error response format:**
```json
{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "Human-readable error message",
    "details": [
      {
        "field": "email",
        "issue": "Invalid email format"
      }
    ],
    "request_id": "req_abc123"
  }
}
```

**HTTP Status Codes:**
- 200 OK: Successful GET
- 201 Created: Successful POST
- 204 No Content: Successful DELETE
- 400 Bad Request: Invalid request format
- 401 Unauthorized: Missing/invalid auth
- 403 Forbidden: No permission
- 404 Not Found: Resource doesn't exist
- 422 Unprocessable Entity: Validation failed
- 429 Too Many Requests: Rate limit
- 500 Internal Server Error: Server issue

---

## Pagination Strategy

**Approach:** Offset-based pagination (simple, fits existing API style)

**Query params:**
- `page`: Page number (1-indexed)
- `per_page`: Items per page

**Response meta:**
```json
{
  "meta": {
    "current_page": 2,
    "total_pages": 10,
    "total_count": 193,
    "per_page": 20
  },
  "links": {
    "first": "/api/v1/reports?page=1",
    "prev": "/api/v1/reports?page=1",
    "self": "/api/v1/reports?page=2",
    "next": "/api/v1/reports?page=3",
    "last": "/api/v1/reports?page=10"
  }
}
```

**For very large datasets (future):** Consider cursor-based pagination

---

## Versioning Strategy

**Current:** URL-based (/api/v1)

**For breaking changes:** Introduce /api/v2

**Backwards compatibility:**
- Additive changes OK (new optional fields)
- Breaking changes → new version

---

## OpenAPI Spec (partial)

```yaml
openapi: 3.0.0
info:
  title: Advanced Reporting API
  version: 1.0.0

paths:
  /api/v1/reports:
    get:
      summary: List reports
      parameters:
        - name: page
          in: query
          schema:
            type: integer
            default: 1
        - name: per_page
          in: query
          schema:
            type: integer
            default: 20
            maximum: 100
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ReportsListResponse'
        '401':
          $ref: '#/components/responses/Unauthorized'

components:
  schemas:
    ReportsListResponse:
      type: object
      properties:
        data:
          type: array
          items:
            $ref: '#/components/schemas/Report'
        meta:
          $ref: '#/components/schemas/PaginationMeta'
        links:
          $ref: '#/components/schemas/PaginationLinks'

    Report:
      type: object
      properties:
        id:
          type: string
        type:
          type: string
          enum: [report]
        attributes:
          $ref: '#/components/schemas/ReportAttributes'

    [... more schemas]

  responses:
    Unauthorized:
      description: Unauthorized
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/Error'
```

---

## Implementation Notes

**Priority endpoints (MVP):**
1. POST /reports (create report)
2. GET /reports/:id (get report data)
3. GET /reports (list reports)

**Phase 2:**
- Templates (GET/POST /templates)
- Schedules (GET/POST /schedules)

**Performance considerations:**
- Report generation může být slow → async processing
- Use `status: pending` → client poll GET /reports/:id
- Consider webhooks pro completion notification (future)

---

## Testing Recommendations

**Unit tests:**
- Validation logic
- Error handling

**Integration tests:**
- Full request/response cycle
- Edge cases (empty results, large datasets)

**API documentation:**
- Generate from OpenAPI spec (Swagger UI)
- Interactive docs pro developers
```

---

### 💬 Komentář:

**Proč Level 4:**
- ✅ Technická expertíza (RESTful best practices)
- ✅ Systematický proces (5 kroků)
- ✅ Must be well-designed (API changes jsou costly)
- ❌ Není ultra-critical (můžu iterate)

**Expected output:**
Professional API design s OpenAPI spec, ready for implementation.

---

## Příklad 5: Email Template
### Jednoduchý úkol

**Use case:** Potřebuješ email template pro onboarding nových uživatelů.

**Level použitý:** Level 2 (Strukturovaný prompt)

**Proč Level 2?**
- ✅ Jednoduchý úkol (email copy)
- ✅ Potřebuji specifický formát
- ❌ Nepotřebuji bohatý kontext
- ❌ Nepotřebuji expertní metodologii

---

### Finální prompt:

```markdown
# Welcome Email Template - FitFlow App

## ÚKOL

Vytvoř welcome email pro nové uživatele FitFlow fitness app (day 0 po registraci).

**Účel emailu:**
- Přivítat nového usera
- Vysvětlit jak začít (first workout)
- Motivovat k akci (get them to first workout within 24 hours)

---

## FORMÁT

**Subject line:**
[Max 50 znaků, catchy, personal]

**Email body:**

```
Hi [First Name],

[Úvodní odstavec - welcome, validate their decision to join]

[Hlavní část - 3 quick steps jak začít]
1. [Step 1]
2. [Step 2]
3. [Step 3]

[Call-to-action - motivační, clear button/link]

[Závěr - encouraging, podpora]

Cheers,
The FitFlow Team

P.S. [Quick tip nebo motivace]
```

---

## POŽADAVKY

- **Tone:** Warm, friendly, motivační (ne corporate)
- **Length:** Max 150 slov (short = vyšší read rate)
- **CTA:** Jasný - "Start Your First Workout" (button)
- **Focus:** Minimize friction - make it EASY to start

---

## OMEZENÍ

**NEDĚLEJ:**
- ❌ Dlouhé explanace (keep it brief)
- ❌ Multiple CTAs (jen jedna clear akce)
- ❌ Technical žargon

---

## METADATA

- **Priorita:** Střední
- **Model preference:** GPT-4.1 nebo Claude Sonnet (both good pro copy)
```

---

### 💬 Komentář:

**Proč Level 2 stačí:**
- ✅ Jednoduchý úkol
- ✅ Jasný formát + tone
- ❌ Nepotřebuji víc

**Expected result:**
Warm, motivační welcome email ready to use.

---

## 📊 Shrnutí příkladů

| Příklad | Use Case | Level | Proč tento level | Model |
|---------|----------|-------|------------------|-------|
| **#1** | Requirements Analysis | 4 | BA expertise + metodologie | Claude Sonnet |
| **#2** | Market Entry Strategy | 5 | High-stakes strategic | Opus / o1 |
| **#3** | Product Description | 3 | Kontext + tone stačí | Claude / GPT-4.1 |
| **#4** | API Design | 4 | Tech expertise + best practices | Claude / GPT-4.1 |
| **#5** | Email Template | 2 | Jednoduchý + formát | GPT-4.1 / Claude |

---

## 💡 Klíčové takeaways

1. **Začni s nižším levelem** - Nepoužívej Level 5 na Level 2 úkol.

2. **Kontext je král** - I Level 2 prompt potřebuje jasný úkol + formát.

3. **Příklady pomáhají** - Level 5: few-shot examples dramaticky zlepšují kvalitu.

4. **Validační checklist** - Pro kritické úkoly (Level 4-5) přidej checklist.

5. **Iteruj** - První prompt je draft. Based on výsledku, uprav.

---

**Další kroky:**
- Vezmi si reálný úkol ze své práce
- Identifikuj který level potřebuješ (decision tree v guide)
- Použij příslušný příklad jako template
- Customize pro svůj use case
- Testuj a iteruj

---

**Verze:** 1.0 | **Datum:** Listopad 2025 | **Pro:** Školení Prompt Engineering
