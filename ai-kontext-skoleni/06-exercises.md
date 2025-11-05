# Práce s kontextem AI - Cvičení

## Jak pracovat s cvičeními

**Pro studenty:**
- Nejdřív zkus sám, řešení nehled hned
- Dělej si vlastní poznámky - co fungovalo, co ne
- Pokud tápneš víc než 10 minut, koukni na nápovědu
- Tvoje řešení nemusí být stejné jako uvedené - hlavně ať funguje

**Pro lektory:**
- Dej studentům čas, nespěchej s řešením
- Ptej se "Co jsi zkoušel?" místo "Nevíš to?"
- Vyzdvihni různé přístupy, ne jen jedno správné řešení
- Během hands-on chodíš mezi lidmi a pomáháš

---

## Cvičení 1: Optimalizace kontextu - Začátečník 🟢

### Zadání

Máš dlouhou konverzaci s AI (45+ zpráv) o analýze requirements pro e-commerce project. Pracovali jste na discovery fázi. Teď chceš přejít do design fáze, ale nechceš začínat úplně od nuly.

**Cíl:** Naučit se techniku summarize-and-continue

**Časový odhad:** 10 minut

### Scénář

```
Current situation:
- Konverzace s 45 zprávami v Claude/ChatGPT
- Discovery fáze je hotová
- Identifikovány key requirements, stakeholder preferences, constraints
- Teď chceš začít design fáze
```

### Úkol

1. Vytvoř prompt, kterým požádáš AI o shrnutí discovery fáze
2. AI ti vrátí summary
3. Start novou konverzaci
4. Použij summary jako kontext pro design fázi

### Očekávaný výstup

- Summary optimalizované pro use v nové konverzaci
- Nová konverzace má relevantní kontext, ale fresh start
- Design discussion může začít bez ztráty důležitých infos

---

### Nápověda k Cvičení 1

<details>
<summary>Klikni pro nápovědu (ale nejdřív zkus sám!)</summary>

**Hint 1:** Prompt by měl být specifický - ne jen "shrň konverzaci", ale "shrň pro use case X"

**Hint 2:** Specifikuj co má summary obsahovat: key requirements, decisions, constraints, stakeholder preferences

**Hint 3:** Řekni explicitně "optimalizuj pro použití jako vstup do nové konverzace" - AI pak vytvoří vhodnější format

**Příklad struktury promptu:**
```
"Shrň naši discovery fázi. Zahrnout:
- Klíčové requirements
- Stakeholder preferences a constrains
- Finální rozhodnutí

Optimalizuj pro použití jako kontext v nové konverzaci o design fázi."
```

</details>

---

### Řešení Cvičení 1

**Krok 1: Prompt pro shrnutí**

```
Shrň klíčové poznatky z naší discovery fáze pro e-commerce projekt.

Zahrnout:
• Hlavní business requirements
• Stakeholder preferences (koho, co chtějí)
• Technical constraints (budget, timeline, tech stack)
• Key decisions které jsme udělali
• Open questions nebo risks

Formát: Strukturovaný summary optimalizovaný pro použití jako vstup
do nové konverzace zaměřené na design fázi.

Vynechej: Detaily z brainstormingu, zamítnuté nápady, tangential diskuse.
```

**Proč to funguje:**
- ✅ Specifické co zahrnout (requirements, preferences, constraints, decisions)
- ✅ Jasný use case (design fáze)
- ✅ Explicitní optimalizace pro novou konverzaci
- ✅ Říká co vynechat (noise reduction)

**Krok 2: AI vrátí summary (příklad)**

```
# E-commerce Project - Discovery Summary

## Business Requirements
- Multi-vendor marketplace for handmade goods
- Target: Small artisan sellers (100-500 sellers in year 1)
- Key features: Product listings, shopping cart, payment processing, seller dashboard

## Stakeholder Preferences
- CEO (Alice): Fast time-to-market (6 months), MVP approach
- CTO (Bob): Scalable architecture, cloud-native
- Head of Sales (Carol): Easy onboarding for sellers, intuitive UI

## Constraints
- Budget: $150k for development
- Timeline: Launch in 6 months
- Tech stack: React frontend, Node.js backend (team expertise)
- Compliance: GDPR, PCI-DSS for payments

## Key Decisions
- Phase 1: MVP with core features only (no reviews/ratings yet)
- Payment: Integrate Stripe (fastest, PCI compliant)
- Hosting: AWS (team familiarity)

## Open Questions
- Multi-currency support: Nice-to-have or must-have?
- Seller verification process: Manual or automated?

## Risks
- Tight timeline with small team (3 devs)
- Payment integration complexity
```

**Krok 3: Start novou konverzaci**

Nová konverzace v Claude/ChatGPT:

```
Kontext: Pracuji na e-commerce project. Discovery fáze je hotová,
tady je shrnutí:

[Paste celý summary z kroku 2]

---

Teď chci začít design fázi. Zaměříme se na high-level architekturu.

První otázka: Jaká je doporučená architektura pro multi-vendor marketplace
s našimi constraints (Node.js, AWS, 6-month timeline)?
```

**Výsledek:**
- ✅ Nová konverzace má clean context
- ✅ AI rozumí projektu bez 45 předchozích zpráv
- ✅ Můžeš pokračovat v design fázi s full context ale fresh start

---

**Alternativní přístup:**

Můžeš použít i kratší prompt:

```
"Udělej mi executive summary naší discovery fáze - klíčové body
které potřebuji znát pro design fázi. Budu to používat v nové konverzaci."
```

Kratší = rychlejší, ale méně kontroly nad tím co bude zahrnuto.

---

**Časté chyby:**

- ❌ **Chyba:** "Shrň naši konverzaci" (příliš vague)
  - ✅ **Správně:** "Shrň discovery fázi pro use v design phase - zahrnout requirements, constraints, decisions"

- ❌ **Chyba:** Copy-paste celé summary do nové konverzace bez kontextu
  - ✅ **Správně:** "Kontext: [summary]. Teď chci [co chceš dělat dál]"

- ❌ **Chyba:** Nezačít novou konverzaci, jen pokračovat
  - ✅ **Správně:** Vždy start fresh conversation při phase transition

---

## Cvičení 2: Custom GPT creation - Mírně pokročilý 🟡

### Zadání

Vytvoř Custom GPT (pokud máš ChatGPT Plus) nebo Claude Skill, který ti pomůže s analýzou user stories. Nástroj by měl automaticky kontrolovat kvalitu user stories podle best practices.

**Cíl:** Hands-on vytvoření reusable nástroje

**Časový odhad:** 15 minut

### Co budeš potřebovat

- ChatGPT Plus account NEBO Claude account
- Základní znalost user story formátu

### Specifikace nástroje

Tvůj GPT/Skill by měl kontrolovat:

1. **Format check:** Má story formát "As a [role] I want [feature] So that [benefit]"?
2. **Acceptance criteria:** Jsou jasná, testovatelná, kompletní?
3. **Ambiguous language:** Obsahuje vague terms (např. "user-friendly", "fast", "intuitive")?
4. **Size check:** Je story dostatečně malá (completable in 1 sprint)?

### Očekávaný výstup

GPT/Skill, který když dostane user story, vrátí:
- ✅ nebo ❌ status pro každý check
- List konkrétních issues (pokud nějaké jsou)
- Suggestions jak story vylepšit

### Příklad vstupu (pro testování)

```
User Story:
As a customer I want to search products so I can find what I need quickly.

Acceptance Criteria:
- Search works
- Results are relevant
```

---

### Nápověda k Cvičení 2

<details>
<summary>Klikni pro nápovědu</summary>

**Hint 1: Conversational creation (easiest)**

Pro Custom GPT:
- Jdi na chatgpt.com/create
- Řekni GPT Builderu: "Chci GPT který analyzuje user stories a kontroluje [list checks]"

Pro Claude Skill:
- Settings → Capabilities → zapni "skill-creator"
- Nová konverzace: "Chci vytvořit skill pro analýzu user stories..."

**Hint 2: Co říct při vytváření**

```
"Chci nástroj pro analýzu user stories. Měl by kontrolovat:
1. Format (As a / I want / So that)
2. Acceptance criteria (jasná, testovatelná)
3. Ambiguous language
4. Size (achievable in one sprint)

Output by měl být:
- Checklist co funguje/nefunguje
- Konkrétní issues
- Suggestions for improvement

Tone: Professional ale helpful, ne overly critical."
```

**Hint 3: Testování**

Po vytvoření hned otestuj na příkladu vstupu (viz zadání). Pokud output není dobrý, uprav instrukce.

</details>

---

### Řešení Cvičení 2

**Varianta A: Custom GPT (ChatGPT Plus)**

**Krok 1: Jdi na chatgpt.com/create**

**Krok 2: Řekni GPT Builderu:**

```
Chci vytvořit GPT který pomáhá business analytikům analyzovat kvalitu user stories.

GPT by měl kontrolovat:

1. Format check: Má story strukturu "As a [role] I want [feature] So that [benefit]"?

2. Acceptance criteria check:
   - Jsou tam acceptance criteria?
   - Jsou jasná a testovatelná?
   - Není jich moc málo (min 2-3)?

3. Ambiguous language check:
   - Hledej vague terms: "user-friendly", "fast", "intuitive", "easy", "simple", "good"
   - Tyto terms by měly být specifikované

4. Size check:
   - Je story achievable in one sprint (1-2 týdny)?
   - Není moc broad?

Output format:
- Pro každý check: ✅ Pass nebo ❌ Fail
- List of specific issues
- Concrete suggestions how to improve

Tone: Professional, helpful, constructive (ne overly critical)
```

**Krok 3: GPT Builder se ptá upřesňujících otázek**

Typicky:
- "Chceš aby GPT byl formální nebo casual?"
  → *Odpověz: "Professional ale přístupný"*

- "Máš nějaké příklady dobrých user stories?"
  → *Můžeš dát příklad, nebo říct "Ne, použij standard best practices"*

**Krok 4: Preview a test**

V pravém panelu (Preview) zkus na příkladu:

```
Analyze this user story:

As a customer I want to search products so I can find what I need quickly.

Acceptance Criteria:
- Search works
- Results are relevant
```

**Očekávaný output (příklad):**

```
## User Story Analysis

### ✅ Format Check
PASS - Story follows "As a / I want / So that" format correctly.

### ❌ Acceptance Criteria Check
FAIL - Acceptance criteria are too vague:
- "Search works" - What defines "works"? Speed? Accuracy?
- "Results are relevant" - How is relevance measured?

Issues:
- Criteria are not testable
- Missing specific metrics or behaviors

### ❌ Ambiguous Language Check
FAIL - Found vague terms:
- "quickly" - How fast is quick? 1 second? 3 seconds?

### ✅ Size Check
PASS - Story appears achievable in one sprint (assuming basic search functionality).

## Suggestions for Improvement

**Rewritten Acceptance Criteria:**
- Search returns results within 2 seconds for 95% of queries
- Results include products matching ≥80% of search keywords
- Search supports filters by category, price range
- Empty state shows helpful message when no results found

**Rewritten Story:**
As a customer I want to search products by keyword and filters so I can find relevant items in under 2 seconds.
```

**Krok 5: Save**

Pokud jsi spokojený s outputem → **Save**

Pojmenuj: "User Story Analyzer"
Sharing: "Only me" nebo "Anyone with link" (pokud chceš sdílet s týmem)

---

**Varianta B: Claude Skill**

**Krok 1: Settings → Capabilities → skill-creator ON**

**Krok 2: Nová konverzace, řekni Claude:**

```
Chci vytvořit skill pro analýzu user stories.

Skill by měl kontrolovat:
1. Format (As a / I want / So that)
2. Acceptance criteria (jasná, testovatelná, dostatečně detailní)
3. Ambiguous language (vague terms jako "fast", "user-friendly")
4. Size (achievable in sprint)

Output:
- Checklist ✅/❌ pro každý check
- Specific issues
- Improvement suggestions

Use when: User asks to analyze nebo review user stories.
```

**Krok 3: Claude vytvoří skill**

Claude ti vrátí něco jako:

```
Created skill: user-story-analyzer

The skill will activate when you ask me to analyze or review user stories.
It will check format, acceptance criteria, ambiguous language, and size,
then provide a detailed analysis with improvement suggestions.
```

**Krok 4: Test**

V té samé nebo nové konverzaci:

```
Analyze this user story:

As a customer I want to search products so I can find what I need quickly.

Acceptance Criteria:
- Search works
- Results are relevant
```

Claude by měl automaticky aktivovat skill a vr

átit podobnou analýzu jako Custom GPT example výše.

---

**Alternativní přístup - Manuální vytvoření (pokročilé):**

Můžeš také vytvořit skill manuálně jako markdown soubor:

`~/.claude/skills/user-story-analyzer.md`:

```markdown
---
name: user-story-analyzer
description: Analyzes user stories for quality and completeness. Use when user asks to review or analyze user stories.
---

# User Story Analyzer

When I receive a user story, I will analyze it across 4 dimensions:

## 1. Format Check
- Does it follow "As a [role] I want [feature] So that [benefit]" structure?

## 2. Acceptance Criteria Check
- Are acceptance criteria present?
- Are they specific and testable?
- Are there at least 2-3 criteria?

## 3. Ambiguous Language Check
Look for vague terms that need specification:
- "user-friendly", "intuitive", "easy"
- "fast", "quickly", "slow"
- "good", "bad", "better"

## 4. Size Check
- Is the story achievable in one sprint (1-2 weeks)?
- Is it too broad?

## Output Format

For each dimension:
- ✅ PASS or ❌ FAIL
- List of specific issues
- Concrete suggestions for improvement

Tone: Professional, helpful, constructive.
```

Save → Claude automaticky načte.

---

**Časté chyby:**

- ❌ **Chyba:** Příliš vague instrukce - "GPT by měl analyzovat user stories"
  - ✅ **Správně:** Specifické checks, expected output format

- ❌ **Chyba:** Zapomenout otestovat po vytvoření
  - ✅ **Správně:** Vždy test na real example, uprav pokud potřeba

- ❌ **Chyba:** Nerealistická očekávání - AI není perfektní
  - ✅ **Správně:** Iteration - vytvoř, test, uprav, test again

---

## Cvičení 3: Multi-stakeholder requirements analysis - Výzva 🔴

### Zadání

Reálný complex scenario: Máš requirements dokumenty od 3 stakeholderů pro nový feature. Každý má jiné priority. Tvůj úkol je identifikovat konflikty, gaps, a navrhnout prioritizaci.

**Cíl:** Praktická aplikace large context + context engineering

**Časový odhad:** 20-25 minut

**Obtížnost:** Toto cvičení kombinuje více konceptů. Je OK pokud bude trvat déle.

### Scénář

Vyvíjíte nový "Reporting Dashboard" feature pro interní analytics tool.

**Stakeholder A (VP Sales)** chce:
- Real-time sales metrics
- Drill-down by region, salesperson, product
- Export to Excel
- Mobile-friendly view

**Stakeholder B (Data Team Lead)** chce:
- Historical data analysis (3+ years)
- Custom date ranges
- SQL query builder for power users
- Data quality indicators

**Stakeholder C (IT Security)** chce:
- Role-based access control
- Audit logs for all data access
- Data anonymization options
- Compliance with GDPR

**Constraints:**
- Budget: Development time for 2 devs, 3 months
- Tech stack: React + Python backend
- Must integrate with existing MySQL database

### Úkol

Použij AI (Claude/ChatGPT) s large context approach:

1. Vytvoř strukturovaný prompt s všemi stakeholder requirements
2. Požádej AI o analýzu konfliktů a gaps
3. Získej prioritization recommendation
4. Vytvoř finální requirements document

### Očekávaný výstup

1. **Conflicts analysis:**
   - Stakeholder A vs B: Real-time vs Historical (technical conflict)
   - Technical feasibility vs desires

2. **Gaps identification:**
   - Chybějící requirements (např. performance SLAs, user training)
   - Uncovered use cases

3. **Prioritization:**
   - Must-have vs Nice-to-have
   - Phase 1 vs Phase 2 features
   - Reasoning pro každé rozhodnutí

4. **Revised requirements doc:**
   - Consolidated, prioritized requirements
   - Clear acceptance criteria
   - Implementation phases

---

### Nápověda k Cvičení 3

<details>
<summary>Nápověda - strategický přístup</summary>

**Strategický breakdown:**

1. **Strukturuj input** - ne volný text, ale organized sections
2. **Strategic placement** - constraints na začátek (critical)
3. **Explicit asks** - jasně řekni co chceš jako output
4. **Follow-up** - první response může být broad, zeptej se na detaily

**Doporučená struktura promptu:**

```
CONTEXT & CONSTRAINTS:
[Budget, timeline, tech stack]

STAKEHOLDER REQUIREMENTS:
Stakeholder A (VP Sales):
[list]

Stakeholder B (Data Lead):
[list]

Stakeholder C (IT Security):
[list]

ANALYSIS REQUEST:
1. Identify conflicts between stakeholder requirements
2. Identify gaps in requirements
3. Recommend prioritization (must-have vs nice-to-have)
4. Suggest phasing (Phase 1 vs Phase 2)

OUTPUT FORMAT:
[Specify tabulka nebo structured list]
```

**Pro follow-up:**
Po první analýze se zeptej na specifics:
- "Elaborate on conflict #2 - jak to technicky vyřešit?"
- "Který gap je nejvíc critical?"

</details>

---

### Řešení Cvičení 3

**Krok 1: Strukturovaný prompt**

```
# Reporting Dashboard Feature - Multi-Stakeholder Requirements Analysis

## CONSTRAINTS (Critical)
- **Budget:** 2 developers, 3 months development time
- **Tech Stack:** React frontend, Python backend
- **Integration:** Must work with existing MySQL database
- **Timeline:** Launch in 3 months

## STAKEHOLDER REQUIREMENTS

### Stakeholder A: VP Sales
**Priority:** Customer-facing reporting, speed
Requirements:
1. Real-time sales metrics (revenue, deals closed, pipeline)
2. Drill-down capabilities (region, salesperson, product)
3. Export to Excel functionality
4. Mobile-friendly responsive view

### Stakeholder B: Data Team Lead
**Priority:** Deep analysis capabilities
Requirements:
1. Historical data analysis (3+ years of data)
2. Custom date range selection
3. SQL query builder for power users
4. Data quality indicators (freshness, completeness)

### Stakeholder C: IT Security Officer
**Priority:** Security and compliance
Requirements:
1. Role-based access control (RBAC)
2. Audit logs for all data access
3. Data anonymization options for sensitive fields
4. GDPR compliance (data retention, right to deletion)

## ANALYSIS REQUEST

Please analyze these requirements and provide:

### 1. Conflicts Analysis
Identify conflicts between stakeholder requirements:
- Technical conflicts (incompatible features)
- Priority conflicts (competing for same resources)
- Timeline conflicts (cannot all fit in 3 months)

For each conflict:
- Who vs Who
- What's the conflict specifically
- Business impact of not resolving it
- Suggested resolution approach

### 2. Gaps Identification
What's missing from requirements:
- Performance SLAs (response time, concurrent users)
- Error handling and edge cases
- User onboarding/training needs
- Maintenance and support plan
- Testing strategy

### 3. Prioritization Recommendation
Categorize requirements:
- **Must-have (P0):** Critical for launch, non-negotiable
- **Should-have (P1):** Important, include if time permits
- **Nice-to-have (P2):** Defer to Phase 2

Reasoning for each prioritization decision.

### 4. Phasing Proposal
- **Phase 1 (MVP - 3 months):** Minimum viable features for launch
- **Phase 2 (Post-launch):** Enhancements and advanced features

## OUTPUT FORMAT

Use structured format with tables and clear sections. Be specific with reasoning.
```

---

**Krok 2: AI analyzuje (příklad očekávaného outputu)**

```
# Multi-Stakeholder Requirements Analysis

## 1. CONFLICTS ANALYSIS

| Conflict | Stakeholders | Issue | Impact | Resolution |
|----------|-------------|--------|---------|------------|
| **Real-time vs Historical** | A (Sales) vs B (Data) | Real-time requires different architecture than 3-year historical analysis | High - architectural decision affects entire system | **Resolution:** Implement both with hybrid approach: Real-time for last 30 days (in-memory), historical via batch queries |
| **Simple UI vs Power User Tools** | A (Sales) vs B (Data) | Sales wants simple mobile-friendly UI, Data wants complex SQL builder | Medium - UI complexity | **Resolution:** Two interface modes: Simple (default) and Advanced (toggle for power users) |
| **Speed vs Security Logging** | A (Sales) vs C (Security) | Audit logging adds latency, conflicts with "real-time" requirement | Medium - performance trade-off | **Resolution:** Async audit logging (don't block queries), cache user permissions |
| **3-month timeline vs Full Feature Set** | All stakeholders | Cannot deliver all requirements in 3 months with 2 devs | High - scope vs timeline | **Resolution:** Phased approach (see section 4) |

## 2. GAPS IDENTIFICATION

**Missing Critical Requirements:**

1. **Performance SLAs** ❌
   - No definition of "real-time" (1 sec? 5 sec?)
   - No concurrent user limits specified
   - **Suggestion:** Define: <2 sec for simple queries, <10 sec for complex, support 50 concurrent users

2. **Error Handling** ❌
   - What happens when MySQL is down?
   - How to handle malformed custom queries?
   - **Suggestion:** Graceful degradation, cached data fallback, query validation

3. **Data Refresh Strategy** ❌
   - How often is data updated?
   - What's acceptable data staleness?
   - **Suggestion:** Every 5 minutes for real-time, daily batch for historical

4. **User Onboarding** ❌
   - No training plan for Sales team
   - No documentation requirements
   - **Suggestion:** Interactive tutorial, video walkthrough, FAQs

5. **Export Limits** ❌
   - Excel export for how much data? (Excel has row limits)
   - **Suggestion:** Max 100k rows per export, pagination for larger datasets

6. **Mobile Experience Details** ❌
   - Which mobile features? (all or subset?)
   - Native app or responsive web?
   - **Suggestion:** Responsive web, core metrics only on mobile (not SQL builder)

## 3. PRIORITIZATION RECOMMENDATION

### Must-Have (P0) - Phase 1

| Feature | Stakeholder | Reasoning |
|---------|-------------|-----------|
| **Basic real-time metrics** | A (Sales) | Core value prop, sales team is primary user |
| **Drill-down (region, product)** | A (Sales) | Essential for sales analysis |
| **RBAC (basic)** | C (Security) | Non-negotiable for production launch, compliance requirement |
| **Audit logging** | C (Security) | Compliance requirement (GDPR) |
| **Custom date ranges** | B (Data) | Needed for historical comparison |
| **Excel export (basic)** | A (Sales) | Frequently requested by exec team |

**Time estimate:** ~2.5 months with 2 devs

### Should-Have (P1) - Include if time permits

| Feature | Stakeholder | Reasoning |
|---------|-------------|-----------|
| **Mobile-responsive view** | A (Sales) | Nice-to-have, sales team primarily desktop |
| **Data quality indicators** | B (Data) | Helpful but not blocking |
| **3-year historical data** | B (Data) | Can start with 1 year, expand later |

**Time estimate:** +2-4 weeks

### Nice-to-Have (P2) - Defer to Phase 2

| Feature | Stakeholder | Reasoning |
|---------|-------------|-----------|
| **SQL query builder** | B (Data) | Advanced feature, small user base (power users only) |
| **Data anonymization** | C (Security) | Not required for initial internal use, add when needed |
| **Drill-down by salesperson** | A (Sales) | Sensitive data, defer until RBAC is mature |

**Time estimate:** Phase 2 (post-launch)

## 4. PHASING PROPOSAL

### Phase 1: MVP (3 months, 2 devs)

**Goal:** Launch functional dashboard for Sales team with basic security

**Features:**
- ✅ Real-time sales metrics (last 30 days)
- ✅ Drill-down by region and product (not salesperson)
- ✅ Custom date ranges (up to 1 year historical)
- ✅ Basic RBAC (roles: Admin, Sales Manager, Sales Rep)
- ✅ Audit logging (async, non-blocking)
- ✅ Excel export (up to 10k rows)
- ✅ Desktop-optimized UI

**Out of scope:**
- Mobile responsiveness
- SQL query builder
- 3-year historical data
- Data anonymization
- Salesperson drill-down

**Success criteria:**
- Sales team can view real-time metrics
- Export reports to Excel
- Meets GDPR basic requirements (audit logs, RBAC)
- Page load <2 seconds for simple queries

### Phase 2: Enhancements (Post-launch, 2-3 months)

**Features:**
- Mobile-responsive view
- SQL query builder for power users (Data team)
- Extended historical data (3 years)
- Advanced RBAC (granular permissions)
- Data anonymization options
- Salesperson drill-down (with privacy controls)
- Performance optimizations

**Dependencies:**
- Phase 1 feedback from Sales team
- Load testing results
- User adoption metrics

## 5. RISKS & MITIGATION

| Risk | Likelihood | Impact | Mitigation |
|------|------------|---------|------------|
| **Timeline slippage** | High | High | Cut nice-to-haves, strict scope control |
| **Performance issues with large data** | Medium | High | Load testing early (week 4), caching strategy |
| **Stakeholder expectations mismatch** | Medium | Medium | Weekly demos, clear communication on what's in/out of Phase 1 |
| **GDPR compliance gaps** | Low | High | Security review before launch, legal sign-off |

## 6. RECOMMENDED NEXT STEPS

1. **Week 1:** Stakeholder alignment meeting - present this analysis, get buy-in on Phase 1 scope
2. **Week 2:** Finalize technical architecture (real-time + historical hybrid approach)
3. **Week 3:** Start development (basic RBAC + real-time metrics)
4. **Week 6:** Mid-point demo to Sales team, gather feedback
5. **Week 10:** Security review and GDPR compliance check
6. **Week 12:** Launch Phase 1

## 7. OPEN QUESTIONS FOR STAKEHOLDERS

1. **VP Sales:** Can you accept desktop-only for Phase 1, mobile in Phase 2?
2. **Data Lead:** Is 1-year historical sufficient for Phase 1, or must-have 3 years?
3. **Security:** Is basic RBAC (3 roles) sufficient, or need more granular permissions?
4. **All:** Who is the final decision-maker for scope tradeoffs if timeline slips?
```

---

**Krok 3: Follow-up pro detaily**

Po první analýze můžeš deep-dive:

```
"Focus na Conflict #1 (Real-time vs Historical).

Elaborate na hybrid approach:
- Jak exactly implementovat? (architecture)
- Jaké jsou performance implications?
- Co je effort estimate pro tento approach vs. simple approach?"
```

AI vrátí detailnější technical breakdown.

---

**Krok 4: Vytvoř finální requirements doc**

```
"Na základě této analýzy vytvoř finální requirements document pro Phase 1.

Format:
- Executive summary
- In-scope features (detailed)
- Out-of-scope (explicitly stated)
- Acceptance criteria per feature
- Non-functional requirements (performance, security)
- Success metrics

Optimalizuj pro handoff development týmu."
```

---

**Alternativní approach:**

Pokud AI vrátilo moc dlouhý output, můžeš použít information distillation:

```
"Shrň tuto analýzu do 1-page executive summary pro steering committee meeting.

Focus:
- Top 3 konflikty a jak je řešíme
- Phase 1 scope (bullet points)
- Key risks
- Timeline

Target audience: Non-technical executives, need decision in 10 min meeting."
```

---

**Proč tohle funguje:**

✅ **Large context:** Všechny stakeholder requirements najednou → AI vidí celý obraz, zachytí konflikty
✅ **Structure:** Clear sections, tables → AI rozumí co kde patří
✅ **Strategic placement:** Constraints na začátku → AI je prioritizuje
✅ **Explicit output format:** Specifikovaný format → consistent, usable output
✅ **Follow-up capability:** Můžeš deep-dive do specifics podle potřeby

---

**Časté chyby:**

- ❌ **Chyba:** Posílat requirements jako 3 separate prompty
  - ✅ **Správně:** Všechno najednou v jednom structured promptu - AI musí vidět celý obraz

- ❌ **Chyba:** Vague request "analyze these requirements"
  - ✅ **Správně:** Specific asks - conflicts, gaps, prioritization, phasing

- ❌ **Chyba:** Přijmout první output bez validation
  - ✅ **Správně:** Review output, follow-up na specifics, iterate

- ❌ **Chyba:** Zapomenout na constraints
  - ✅ **Správně:** Constraints (timeline, budget) na začátek - AI je bude respektovat v recommendations

---

## Bonusové výzvy (pro rychlejší studenty)

### Výzva A: Context Cost Optimization

Máš konverzaci která spotřebovala 400k tokenů (input + output). Většina je opakovaný context (company guidelines, templates).

**Úkol:** Navrhni optimalizaci která sníží cost o 50%+ při zachování funkčnosti.

**Hint:** Custom GPT/Skill, context caching, information distillation

### Výzva B: Multi-modal Context

Máš 1-hodinové video ze stakeholder meetingu + written notes. Chceš to analyzovat s AI.

**Úkol:** Navrhni approach - Gemini s video upload? Transcript + text analysis? Hybrid?

**Considerations:** Cost, accuracy, time, tool availability

---

## Reflexe a self-check

Po dokončení cvičení si polož tyto otázky:

- [ ] **Chápu kdy začít novou konverzaci?** Umím identifikovat signály (>50 zpráv, phase transition, AI zapomíná)?
- [ ] **Umím vytvořit reusable nástroj?** Custom GPT nebo Skill pro opakovaný úkol?
- [ ] **Rozumím strukturování kontextu?** Umím použít strategic placement, headers, explicit format requests?
- [ ] **Dokážu analyzovat complex scénář?** Multi-stakeholder requirements, large context approach?

**Pokud na některou otázku odpovídáš ne:**
- Projdi si znovu teorii (student guidelines)
- Zkus cvičení s jinými vstupy
- Diskutuj s lektorem nebo kolegy

---

## Další procvičování

**Chceš víc?**

**Projekt 1:** Vytvoř kompletní Custom GPT/Skill pro svůj real work use case
- Investuj 30 min do detailního setupu
- Používej 1 týden, track kolik času ušetříš
- Iteruj basedna experience

**Projekt 2:** Aplikuj summarize-and-continue na real long-term projekt
- Zkus rozdíl vs. tvůj běžný přístup
- Porovnej kvalitu outputs a čas strávený

**Projekt 3:** Context engineering pro celý tým
- Navrhni workflow jak váš tým může používat AI systematicky
- Vytvoř shared Custom GPTs nebo Skills
- Měř team productivity impact

**Komunity pro diskusi:**
- r/ClaudeAI - sdílení use cases, troubleshooting
- r/ChatGPTPro - pokročilé techniky, GPT marketplace
- LinkedIn groups - business analytics + AI

---

**Našel jsi lepší řešení než uvedené?**
Super! AI tools jsou flexibilní, často existuje více správných přístupů. Sdílej svoje řešení:
- S lektorem (email)
- V komunitě (Reddit, LinkedIn)
- S týmem (internal wiki)

---

*Cvičení vytvořena 2025-11-05 | Pro business analytiky workshop | Časová dotace: 45-60 min celkem*
