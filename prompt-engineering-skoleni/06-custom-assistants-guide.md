# Od promptů k AI asistentům
## Custom GPT, Projects, Gems a další specializované nástroje

> **Účel:** Tento guide ti ukáže kdy a jak přejít z jednorázových promptů na reusable AI asistenty (Custom GPT, Claude Projects, Gemini Gems, atd.)

> **Předpoklad:** Rozumíš základům prompt engineeringu (viz předchozí soubory v tomto modulu)

---

## 📋 Obsah

1. [Kdy přejít z promptu na asistenta](#kdy-přejít-z-promptu-na-asistenta)
2. [Decision Framework](#decision-framework)
3. [Knowledge Base Deep Dive](#knowledge-base-deep-dive)
4. [Instrukce vs běžné prompty](#instrukce-vs-běžné-prompty)
5. [Model-Specific Implementace](#model-specific-implementace)
6. [Best Practices pro asistenty](#best-practices-pro-asistenty)
7. [Praktické příklady migrace](#praktické-příklady-migrace)
8. [Troubleshooting](#troubleshooting)

---

## 🎯 Kdy přejít z promptu na asistenta

### Prompt vs Asistent - Klíčové rozdíly

| Aspekt | Běžný prompt | Custom asistent (GPT/Project/Gem) |
|--------|--------------|-----------------------------------|
| **Použití** | Jednorázové | Opakované (3x+ měsíčně) |
| **Kontext** | Musíš posílat pokaždé | Nastavíš jednou, trvalý |
| **Náklady** | Per-token každý request | Fixní setup, pak nižší per-use |
| **Sdílení** | Copy-paste prompt | Sdílíš link/přístup |
| **Konzistence** | Varies (záleží na promptu) | Konzistentní (fixed instructions) |
| **Učení** | No memory mezi sessions | Může mít persistent context |

### Kdy vytvořit asistenta - Clear signals

**✅ VYTVOŘ ASISTENTA když:**

1. **Opakovaný úkol (3x+ měsíčně)**
   - Příklad: Týdenní status reports, měsíční analýzy, code reviews

2. **Standardizovaný proces**
   - Příklad: User story quality check podle firemního templatu

3. **Velký fixní kontext**
   - Příklad: Company guidelines (50 stran) které potřebuješ pro každý úkol

4. **Tým používá stejný workflow**
   - Příklad: Celý BA tým analyzuje requirements stejným způsobem

5. **Potřebuješ konzistentní kvalitu**
   - Příklad: Customer support responses musí být aligned s brand voice

**❌ NETVOŘIT ASISTENTA když:**

1. **Jednorázový úkol**
   - Použij běžný prompt

2. **Experimentuješ**
   - Není jasný proces → začni s prompty, iteruj, pak vytvoř asistenta

3. **Kontext se často mění**
   - Pokud guidelines či requirements se mění týdně → prompt flexibilnější

4. **Nemáš ještě clear workflow**
   - Nejdřív definuj proces, pak automatizuj

---

## 🌳 Decision Framework

```
START: Mám úkol, který možná potřebuje asistenta

├─ Jak často tento úkol dělám?
│  ├─ Jednou/občas → ✅ PROMPT (běžná konverzace)
│  └─ 3x+ měsíčně → ⬇ pokračuj

├─ Potřebuji stejný kontext opakovaně?
│  ├─ Ne (vždy jiný kontext) → ✅ PROMPT
│  └─ Ano (např. company guidelines, templates) → ⬇ pokračuj

├─ Je proces standardizovaný?
│  ├─ Ne (pokaždé jiný přístup) → ✅ PROMPT
│  └─ Ano (vždy stejné kroky) → ⬇ pokračuj

├─ Budou to používat i jiní lidé?
│  ├─ Ne (jen já) → Zvažuj asistenta (time-saving)
│  └─ Ano (tým) → ✅ ASISTENT (konzistence + sdílení)

└─ Kolik stojí fixní kontext v tokenech?
   ├─ <10k tokenů → Možná PROMPT (nižší overhead)
   └─ >10k tokenů → ✅ ASISTENT (ušetříš na context caching)
```

### ROI Calculation

**Prompt approach:**
- Setup time: 0 min (žádný)
- Per-use time: 2-5 min (copy-paste kontext + instrukce)
- Per-use cost: plná cena tokenů

**Asistent approach:**
- Setup time: 30-60 min (jednou)
- Per-use time: <1 min (rovnou začneš pracovat)
- Per-use cost: nižší (context cached nebo fixed)

**Break-even point:**
Pokud úkol děláš 10x+ měsíčně → asistent se vyplatí již v prvním měsíci.

---

## 📚 Knowledge Base Deep Dive

### Co je Knowledge Base?

**Knowledge Base (KB)** = soubory, které nahraje do asistenta jako persistent kontext.
- Custom GPT: "Knowledge" (files)
- Claude Projects: "Project Knowledge"
- Gemini: zatím limitované
- Copilot: SharePoint/OneDrive integration

### KB vs Příloha v promptu - Klíčové rozdíly

| Aspekt | Knowledge Base | Příloha v promptu |
|--------|----------------|-------------------|
| **Persistence** | Trvalá (všechny konverzace) | Jednorázová (jen tento chat) |
| **Context window** | **Vždy v kontextu** (retrieval) | Zabírá aktivní context |
| **Náklady** | **Cached** (nižší cena) | Plná cena každý request |
| **Retrieval** | **Automatický** (AI vyhledává) | Celý dokument v kontextu |
| **Velikost** | Limit per file (např. 20 MB) | Limit celkového contextu |
| **Update** | Musíš manually re-upload | Pokaždé pošleš aktuální verzi |

### ⚠️ KRITICKÉ POCHOPENÍ: Context Window Rozdíly

#### Scénář: Máš company guidelines (50 stran, ~30k tokenů)

**Option A: Příloha v běžném promptu**
```
Kontext dostupný: 200k tokens (např. Claude)
Guidelines: 30k tokens (příloha)
Tvůj prompt: 2k tokens
Zbývá pro konverzaci: 168k tokens

Náklady (Claude Sonnet 4):
- Input: 32k tokens × $3/1M = $0.096 PER REQUEST
- Pokud děláš 50 requestů/měsíc = $4.80/měsíc jen na guidelines
```

**Option B: Knowledge Base v Custom GPT/Project**
```
Guidelines v KB: cached nebo retrieval-based
Aktivní context pro konverzaci: ~celých 200k tokens

Náklady:
- KB: $0 (nebo minimální retrieval cost)
- Pouze tvůj prompt + response
- 50 requestů/měsíc ≈ $0.50/měsíc

Úspora: ~90%
```

#### Jak funguje retrieval z KB

**GPT a Claude používají RAG (Retrieval-Augmented Generation):**

1. **Uživatel pošle dotaz:** "Jaké jsou naše GDPR requirements pro data export?"

2. **AI vyhledá v KB:**
   - Semantic search v nahraných dokumentech
   - Najde relevantní sekce (ne celý dokument)
   - Příklad: Vytáhne pouze GDPR sekci z guidelines (2k tokens místo celých 30k)

3. **AI odpovídá:**
   - Používá pouze relevantní kontext
   - Zbylých 28k tokenů guidelines NENÍ v aktivním kontextu
   - **Ušetříš context window pro konverzaci**

**Výhoda:**
- ✅ Můžeš mít 100 MB dokumentů v KB
- ✅ Aktivní context obsahuje jen relevantní části
- ✅ Více prostoru pro hlubokou konverzaci

### Co dávat do Knowledge Base

#### ✅ IDEÁLNÍ pro KB:

1. **Reference dokumenty (neměnné/pomalu se měnící):**
   - Company guidelines, policies
   - Product documentation
   - Brand voice guide
   - Templates a standards
   - Historical data (pro comparison)

2. **Velké dokumenty (>10k tokenů):**
   - Pokud potřebuješ často, ale ne vždy celé
   - RAG retrieval ušetří context

3. **Strukturované znalosti:**
   - FAQs
   - Process documentation
   - Code snippets library
   - Best practices guides

#### ❌ NEHODÍ SE do KB:

1. **Často se měnící data:**
   - Denní/týdenní reporty
   - Real-time data
   - → Radšij jako příloha v konkrétní konverzaci

2. **Příliš malé soubory (<1k tokenů):**
   - Dej to rovnou do Instructions (system prompt)
   - KB overhead není worth it

3. **Kontext specifický pro jeden úkol:**
   - Pokud jen 10% konverzací potřebuje tento kontext
   - → Příloha v konkrétní konverzaci lepší

### KB Best Practices

#### 1. Strukturuj soubory logicky

**❌ Špatně:**
```
knowledge.txt (100 stran všeho dohromady)
```

**✅ Dobře:**
```
company_guidelines/
  ├── brand_voice.md (10 stran)
  ├── gdpr_compliance.md (15 stran)
  ├── user_story_template.md (5 stran)
  └── qa_standards.md (8 stran)
```

**Proč:** RAG retrieval je přesnější když jsou dokumenty tematicky oddělené.

#### 2. Používej jasné názvy a struktura

**V dokumentu:**
```markdown
# GDPR Compliance Guidelines

## 1. Data Export Requirements
[konkrétní requirements]

## 2. User Consent Management
[konkrétní requirements]

## 3. Right to be Forgotten
[konkrétní requirements]
```

**Proč:** Jasné headingy pomáhají semantic search najít správnou sekci.

#### 3. Metadata v top každého souboru

```markdown
---
Document: Brand Voice Guidelines
Last Updated: 2025-11-01
Version: 2.3
Applies to: Marketing, Customer Support, Product Copy
---

# Brand Voice Guidelines
...
```

**Proč:** AI ví kontext dokumentu (kdy aktualizován, na co se vztahuje).

#### 4. Linkuj mezi dokumenty (cross-references)

```markdown
# User Story Template

For GDPR considerations, see: [GDPR Compliance Guidelines]
For QA checklist, see: [QA Standards]
```

**Proč:** Pomůže AI najít related context když je potřeba.

#### 5. Aktualizuj pravidelně

- **Quarterly review:** Jsou dokumenty v KB aktuální?
- **Version control:** Poznamenej verzi v metadata
- **Deprecated content:** Odstraň zastaralé dokumenty

---

## 📝 Instrukce vs Běžné Prompty

### System Prompt (Instructions) - Co je jinak

**Běžný prompt:**
- Posíláš per-request
- Můžeš měnit každou konverzaci
- Součást user message

**System Prompt (Instructions):**
- Nastavíš jednou, platí pro všechny konverzace
- "Osobnost" asistenta
- Vyšší priorita než user messages

### Struktura Instructions

```markdown
# [NÁZEV ASISTENTA]

## CO DĚLÁM (Core Purpose)
[1-2 věty: Hlavní účel tohoto asistenta]

## JAK PRACUJI (Approach)
[Metodologie, frameworks které používáš]

## PROCES (Workflow)
[Step-by-step jak zpracováváš requesty]

## FORMÁT VÝSTUPU (Default Output)
[Jak defaultně strukturuješ odpovědi]

## TONE & STYLE
[Jak komunikuješ]

## OMEZENÍ (Guardrails)
[Co NEDĚLÁM, kdy odmítnu request]

## KNOWLEDGE BASE USAGE
[Jak používám nahrané dokumenty]
```

### Příklad: BA Assistant Instructions

```markdown
# BA Requirements Analyzer

## CO DĚLÁM
Analyzuji business requirements dokumenty podle BABOK best practices.
Identifikuji gaps, konflikty, ambiguity a navrhuji řešení.

## JAK PRACUJI
- Používám INVEST criteria (Independent, Negotiable, Valuable, Estimable, Small, Testable)
- Systematický přístup: nejdřív quality check, pak cross-stakeholder analysis, pak gaps
- Data-driven: každé tvrzení musí být podložené konkrétním findings z requirements

## PROCES
Když dostanu requirements:

1. **Quick scan** - Kolik stakeholderů, jak velký scope
2. **INVEST check** - Pro každý requirement
3. **Conflict analysis** - Kde si stakeholdeři odporují
4. **Gap analysis** - Co chybí (acceptance criteria, edge cases)
5. **Prioritizace** - Critical vs Major vs Minor issues
6. **Recommendations** - Konkrétní akční kroky

## FORMÁT VÝSTUPU
Default output:
```
# Analysis Summary
- Overall quality score: X/10
- Critical issues: N
- Major issues: M

## Critical Issues
[Seznam s severity, impact, solution]

## Recommendations
[Top 3-5 actionable items]
```

Pokud uživatel požaduje jiný formát, přizpůsobím.

## TONE & STYLE
- Profesionální ale konstruktivní
- Kritizuji issues, ne lidi
- Vždycky navrhuji řešení, ne jen problémy
- Konkrétní (ne vague "tohle je unclear" - říkám ČÍM je unclear)

## OMEZENÍ
NEDĚLÁM:
- Generic rady bez konkrétního reasoning
- Blame stakeholderů
- Analysis bez access k actual requirements

Pokud nemám dostatečný kontext, zeptám se místo guessingu.

## KNOWLEDGE BASE USAGE
Mám přístup k:
- BABOK Guide v3.0 (reference)
- Company's requirements template
- Historical examples (good vs bad requirements)

Když analyzuji, automaticky cross-reference s company template a BABOK best practices.
```

### Workflow Možnosti v Instructions

Můžeš definovat **conditional workflows** - jak se asistent chová v různých scénářích:

```markdown
## WORKFLOW

### Scénář A: Uživatel pošle requirements dokumenty
1. Automaticky začni INVEST check
2. Identifikuj stakeholders z dokumentů
3. Analyzuj konflikty
4. Poskytni structured output (default format)

### Scénář B: Uživatel se ptá na BABOK concept
1. Reference BABOK Guide z KB
2. Vysvětli concept s praktickým příkladem
3. Nabídni: "Chceš aplikovat toto na konkrétní requirements?"

### Scénář C: Uživatel požaduje quick check (ne full analysis)
1. Pouze INVEST check
2. Top 3 critical issues
3. Brief recommendations (max 5 bullet points)

### Scénář D: Neví si rady / ambiguous request
1. Zeptej se clarifying questions
2. Nabídni options: "Chceš A, B, nebo C?"
```

### Interaktivní prompty v Instructions

```markdown
## FIRST MESSAGE (při startu konverzace)
Když uživatel otevře nový chat, automaticky řekni:

"Ahoj! Jsem BA Requirements Analyzer. Můžu ti pomoct s:
- 📊 Full requirements analysis (INVEST + gaps + conflicts)
- ⚡ Quick quality check (top issues only)
- 📚 BABOK concepts vysvětlení
- 💡 Best practices konzultace

Co dneska potřebuješ?"

## FOLLOW-UP PROMPTS
Po dokončení analýzy, nabídni:
"Chceš:
1. Deep dive do konkrétního issue?
2. Export do formátu pro presentation?
3. Analyzovat další requirements?
4. Něco jiného?"
```

---

## 🤖 Model-Specific Implementace

### Custom GPT (ChatGPT)

**URL:** https://chat.openai.com/gpts/editor

**Capabilities:**
- ✅ Knowledge Base: Ano (files upload, max 20MB per file)
- ✅ Web browsing: Ano (can enable)
- ✅ DALL-E: Ano (image generation)
- ✅ Code Interpreter: Ano (run Python)
- ✅ Actions (API calls): Ano (pokročilé)
- ✅ Sdílení: Public, Private, Anyone with link

#### Vytvoření Custom GPT

**Způsob A: Conversational (easiest)**

1. **Chat GPT → Explore GPTs → Create**
2. GPT Builder se zeptá: "What would you like to make?"
3. Popisy co chceš:
   ```
   "I want to create a business analyst assistant that analyzes
   requirements documents. It should use BABOK best practices,
   identify gaps and conflicts, and provide structured analysis.

   Tone: Professional but constructive
   Output: Always structured with clear sections
   Knowledge: I'll upload our company requirements template"
   ```
4. GPT Builder položí follow-up questions
5. Testuj v Preview → Iterate
6. Upload knowledge files
7. Configure → Save

**Způsob B: Manual (více kontroly)**

1. **Configure** tab:
   - **Name:** "BA Requirements Analyzer"
   - **Description:** "Analyzes business requirements using BABOK..."
   - **Instructions:** [Paste strukturované instructions]
   - **Conversation starters:**
     - "Analyze these requirements"
     - "Quick quality check"
     - "Explain BABOK concept"
   - **Knowledge:** Upload files
   - **Capabilities:** Enable/disable (web, DALL-E, code)

2. **Create** tab (optional):
   - Chat s GPT Builder pro refinement

#### Custom GPT Instructions Template

```markdown
# Role
You are a senior business analyst with CBAP certification and 10+ years experience.

# Capabilities
You help analyze requirements documents using BABOK v3.0 best practices.

# Approach
- Systematic: Always follow INVEST criteria check → conflict analysis → gap analysis
- Data-driven: Base findings on actual content, not assumptions
- Constructive: Criticize issues but always provide solutions

# Process
When user uploads requirements:
1. Scan for stakeholders and scope
2. Apply INVEST criteria to each requirement
3. Identify conflicts between stakeholders
4. Find gaps (missing acceptance criteria, edge cases)
5. Prioritize issues (Critical/Major/Minor)
6. Provide actionable recommendations

# Output Format
Always structure as:
- Executive summary (quality score, issue count)
- Critical issues (with severity, impact, solution)
- Recommendations (top 3-5 actionable items)

Unless user requests different format.

# Tone
Professional, constructive, specific (not vague).

# Knowledge Base
You have access to:
- BABOK Guide v3.0
- Company requirements template
- Historical examples

Reference these when analyzing.

# Guardrails
- Don't make assumptions without data
- Don't blame stakeholders
- Don't provide generic advice
- If insufficient context → ask clarifying questions
```

#### Custom GPT Best Practices

1. **Conversation Starters:**
   ```
   - "Analyze these requirements" (upload prompt)
   - "Quick quality check (top issues only)"
   - "Explain [BABOK concept]"
   - "Best practices for [topic]"
   ```
   → Pomůže uživatelům rychle začít

2. **Test před publikováním:**
   - Zkus 5-10 různých use cases v Preview
   - Edge cases (co když uživatel pošle špatný input?)

3. **Knowledge file naming:**
   ```
   ✅ babok_guide_v3.pdf
   ✅ company_requirements_template.md
   ❌ document.pdf
   ❌ untitled.txt
   ```

4. **Versioning:**
   - V description uveď verzi: "BA Analyzer v2.1"
   - Update log in Knowledge: "changelog.md"

5. **Permissions:**
   - **Only me:** Testing phase
   - **Anyone with link:** Team sharing
   - **Public:** Když chceš publikovat do GPT Store

---

### Claude Projects

**URL:** claude.ai → Projects

**Capabilities:**
- ✅ Project Knowledge: Ano (docs upload)
- ✅ Custom Instructions: Ano
- ✅ Web search: Ne (zatím)
- ✅ Artifacts: Ano (code, documents)
- ✅ Sdílení: Ano (team members)

#### Vytvoření Claude Project

1. **Claude.ai → Projects → Create Project**

2. **Set Project Name & Color:**
   - Name: "BA Requirements Analysis"
   - Color: Pick (pro vizuální organization)

3. **Add Custom Instructions:**
   ```markdown
   # BA Requirements Analyzer

   [Same structure jako u Custom GPT - viz výše]
   ```

4. **Add Project Knowledge:**
   - Upload docs (BABOK guide, templates, examples)
   - Podporované formáty: PDF, TXT, MD, CSV, DOCX

5. **Start chatting:**
   - Každý chat v projektu má access k Instructions + Knowledge

#### Claude Projects vs Custom GPT - Rozdíly

| Feature | Custom GPT | Claude Project |
|---------|-----------|----------------|
| **Instructions** | System prompt | Custom Instructions |
| **Knowledge** | Files (RAG) | Project Knowledge (RAG) |
| **Code execution** | Code Interpreter | Artifacts (no execution) |
| **Web search** | Ano (optional) | Ne |
| **Image gen** | DALL-E | Ne |
| **Sharing** | Public/Link/Private | Team only |
| **Chats** | Separate per GPT | Multiple chats per project |
| **Artifacts** | Ne | Ano (code, docs, diagrams) |

#### Claude-Specific Tips

1. **Používej XML tagy v Instructions:**
   ```xml
   <role>
   You are a senior business analyst...
   </role>

   <process>
   When analyzing requirements:
   1. <step>INVEST check</step>
   2. <step>Conflict analysis</step>
   </process>
   ```

2. **Artifacts jsou powerful:**
   - Pro code generation
   - Pro dlouhé dokumenty (exports)
   - Pro diagrams (Mermaid)

3. **Multiple chats v projektu:**
   - Všechny sdílí stejné Instructions + Knowledge
   - Skvělé pro iteraci (chat 1: draft, chat 2: refinement)

---

### Gemini Gems (experimentální)

**Status (listopad 2025):** Limited availability

**Capabilities:**
- ✅ Custom instructions: Ano
- ✅ Knowledge: Limited (zatím ne full KB)
- ✅ Sharing: Ano
- ❌ Advanced features: Zatím omezené

**Poznámka:** Gemini je zatím pozadu za Custom GPT a Projects v oblasti custom assistants. Sleduj updates.

---

### Microsoft Copilot

**Varianty:**
- **Copilot (free/Pro):** Limited customization
- **Copilot Studio:** Full custom agents (enterprise)

#### Copilot Studio (Enterprise)

**Capabilities:**
- ✅ Custom instructions: Ano (Topics)
- ✅ Knowledge: SharePoint, OneDrive integration
- ✅ Actions: Power Automate flows
- ✅ Channels: Teams, Web, Email

**Vytvoření:**
1. Copilot Studio → Create → Custom copilot
2. Define Topics (conversation flows)
3. Connect to knowledge sources (SharePoint)
4. Add Actions (API calls, Power Automate)
5. Test → Publish to Teams/Web

**Best for:**
- Enterprise s M365
- Integrace s internal systems (SharePoint, Dynamics)
- Compliance requirements

---

### Perplexity

**Customization:** Velmi limitovaná (listopad 2025)

**Možnosti:**
- ✅ Collections: Skupina searches na téma
- ❌ Custom instructions: Ne
- ❌ Knowledge base: Ne (hledá online)

**Use case:** Research-focused use cases, ne custom assistants.

---

## ✅ Best Practices pro Asistenty

### 1. Clear Scope Definition

**❌ Špatně:**
```
"This assistant helps with business tasks"
```

**✅ Dobře:**
```
"This assistant analyzes business requirements documents.
Specifically:
- INVEST criteria validation
- Stakeholder conflict identification
- Gap analysis
- Recommendations based on BABOK v3.0

Out of scope:
- Project management
- Technical implementation
- Unrelated business consulting"
```

### 2. Progressive Disclosure v Instructions

Místo mega-promptu, strukturuj hierarchicky:

```markdown
# Core Identity (always active)
[Who you are, main purpose]

# Default Workflow (most common use case)
[Standard process for 80% use cases]

# Alternative Workflows (for specific scenarios)
## If user requests quick check
[simplified process]

## If user asks for explanation
[educational mode]

# Advanced Features (user can discover)
## Export capabilities
[formats you can export to]

## Integration options
[if applicable]
```

### 3. Fail Gracefully

```markdown
## ERROR HANDLING

If user uploads wrong file type:
"I can analyze requirements documents (PDF, DOCX, TXT, MD).
This file is [type]. Can you upload requirements in supported format?"

If context is insufficient:
"To provide quality analysis, I need:
- Actual requirements document (not summary)
- OR specific question about BABOK concept
- OR scenario you want to discuss

What would you like to do?"

If request is out of scope:
"This request is outside my expertise (requirements analysis).
For [topic], I recommend [alternative].
Can I help with requirements-related task instead?"
```

### 4. Version Control pro Knowledge Base

```
knowledge_base/
  ├── v1.0/ (archived)
  │   ├── babok_guide_v2.pdf
  │   └── template_old.md
  │
  ├── v2.0/ (current)
  │   ├── babok_guide_v3.pdf
  │   ├── requirements_template.md
  │   └── changelog.md
  │
  └── README.md (which version is active)
```

### 5. Instructions Template v Knowledge Base

**Místo** psát celý template do Instructions:

**Instructions:**
```markdown
## OUTPUT FORMAT

Default: Use "Analysis Report Template" from Knowledge Base

For quick checks: Use "Quick Check Template"

User can request custom format.
```

**Knowledge Base:**
```markdown
# analysis_report_template.md

# Requirements Analysis Report

## Executive Summary
- Quality Score: [X/10]
- Critical Issues: [count]
- Recommendations: [top 3]

## Detailed Findings
[struktura...]
```

**Proč:** Instructions jsou limited v délce. KB neomezené.

### 6. Testing Matrix

Před deploym asistenta, testuj:

| Scenario | Expected Behavior | Status |
|----------|-------------------|--------|
| Upload valid requirements | Full analysis with all sections | ✅ |
| Upload wrong file type | Error message + guidance | ✅ |
| Ask BABOK question | Reference KB + explanation | ✅ |
| Request custom format | Adapt output accordingly | ✅ |
| Insufficient context | Ask clarifying questions | ✅ |
| Out-of-scope request | Politely decline + suggest alternative | ✅ |

### 7. Feedback Loop

```markdown
## CONTINUOUS IMPROVEMENT

At end of each analysis, ask:
"Was this analysis helpful?
- If YES: Great! Need anything else?
- If NO: What could be improved? (I learn from feedback)"

[Collect feedback → update Instructions/KB periodically]
```

### 8. Multi-Language Support (pokud potřeba)

```markdown
## LANGUAGE

Default: Respond in user's language
- If user writes in Czech → respond in Czech
- If user writes in English → respond in English

For BABOK terms: Use English term + Czech explanation
Example: "INVEST criteria (Nezávislý, Vyjednatelný, Hodnotný...)"
```

---

## 💼 Praktické Příklady Migrace

### Příklad 1: Z promptu na Custom GPT

**Original Prompt (používáš 10x měsíčně):**

```markdown
# Weekly Status Report Generator

Jsi expert na project management reporting.

CONTEXT:
- Projekt: [jméno]
- Tým: [size]
- Timeline: [dates]

TASK:
Vygeneruj weekly status report z těchto updates:
[paste team updates]

FORMAT:
# Week [N] Status Report

## Highlights
[top 3 achievements]

## Blockers
[issues + mitigation]

## Next Week
[planned activities]

## Metrics
[progress %]
```

**Migration → Custom GPT:**

**1. Identifikuj co je fixní vs co se mění:**
- ✅ Fixní: Role, proces, formát
- 🔄 Mění se: Projekt details, team updates

**2. Vytvoř Custom GPT Instructions:**

```markdown
# Weekly Status Report Generator

## ROLE
You are a project management assistant specialized in creating
executive-friendly weekly status reports.

## PROCESS
When user provides team updates:
1. Extract key achievements (top 3)
2. Identify blockers and risks
3. Summarize next week's plan
4. Calculate progress metrics (if data provided)

## OUTPUT FORMAT
# Week [N] Status Report

## Highlights 🎯
[Top 3 achievements this week]

## Blockers & Risks ⚠️
[Current blockers]
[Mitigation plan for each]

## Next Week 📅
[Planned activities]

## Metrics 📊
[Progress %, velocity, etc.]

## TONE
- Executive-friendly (high-level, concise)
- Positive but honest about blockers
- Action-oriented recommendations

## KNOWLEDGE BASE
You have access to:
- Project timeline and milestones
- Team structure
- Previous status reports (for trend analysis)
```

**3. Knowledge Base:**
```
project_context.md:
  - Project name, goals, timeline
  - Team members and roles
  - Milestones

historical_reports/:
  - week_45_report.md
  - week_46_report.md
  [for trend analysis]
```

**4. Conversation Starter:**
```
"Paste this week's team updates and I'll generate the status report"
```

**Výsledek:**
- Setup: 30 min (jednou)
- Per-use: <2 min (paste updates → done)
- **Saved time:** 3 min × 10 uses/month × 12 months = 6 hours/rok

---

### Příklad 2: Z ad-hoc analýzy na Claude Project

**Original workflow:**
1. Dostaneš user feedback (email, CSV, comments)
2. Napíšeš prompt: "Analyzuj tento feedback..."
3. Copy-paste company guidelines pro analýzu
4. Copy-paste feedback data
5. Iteruješ dokud není output dobrý

**Problém:**
- Guidelines (20 stran) posíláš pokaždé
- Proces není konzistentní
- Každý v týmu dělá jinak

**Migration → Claude Project:**

**1. Vytvoř "User Feedback Analysis" project**

**2. Custom Instructions:**
```markdown
# User Feedback Analyzer

## PURPOSE
Analyze user feedback (surveys, comments, support tickets) and
identify actionable insights for product team.

## METHODOLOGY
1. Categorization (using taxonomy from KB)
2. Sentiment analysis (per category)
3. Priority ranking (based on frequency + impact)
4. Actionable recommendations

## PROCESS
When user provides feedback data:

**Step 1: Categorize**
Use taxonomy from "feedback_taxonomy.md" (in KB)
Each piece of feedback → 1+ categories

**Step 2: Sentiment**
Per category: % Positive / Neutral / Negative

**Step 3: Frequency Analysis**
Which categories have most mentions?

**Step 4: Impact Assessment**
High/Medium/Low impact (based on criteria in KB)

**Step 5: Recommendations**
Top 5 actionable items for product team

## OUTPUT
# Feedback Analysis - [Period]

## Overview
- Total feedback items: [N]
- Top 3 categories: [...]
- Overall sentiment: [...]

## Category Breakdown
| Category | Count | Sentiment | Priority |
|----------|-------|-----------|----------|
[table]

## Top Insights
1. [Insight with supporting quotes]
2. [Insight]
...

## Recommended Actions
1. [Action - owner - timeline]
...

## TONE
Data-driven, objective, actionable
```

**3. Project Knowledge:**
```
feedback_taxonomy.md:
  - Feature requests
  - Bugs
  - UX issues
  - Performance
  - Documentation
  - Integrations
  [with subcategories]

analysis_criteria.md:
  - Impact assessment framework
  - Priority scoring
  - When to escalate

historical_analysis/:
  - Q3_feedback_analysis.md
  - Q4_feedback_analysis.md
  [for trend comparison]
```

**4. Workflow:**
```
Team member:
1. Opens "User Feedback Analysis" project
2. New chat: "Q1 2026 Feedback Analysis"
3. Uploads: feedback_q1_2026.csv
4. Says: "Analyze"
5. Gets consistent, structured analysis
```

**Výsledek:**
- ✅ Konzistence napříč týmem
- ✅ Historical trend analysis (references previous quarters)
- ✅ Time saved: 90 min → 15 min per analysis

---

### Příklad 3: Dokumentace → Knowledge Base Strategy

**Scénář:**
Máš 100 stran product documentation. Potřebuješ často odpovídat na otázky týkající se features, API, workflows.

**Špatný přístup:**
- Nahrát celou documentation jako jeden 100-page PDF do KB

**Proč špatně:**
- RAG retrieval je horší (příliš velký dokument)
- Těžké updateovat (musíš re-upload celý PDF)

**✅ Dobrý přístup: Modularizace**

```
knowledge_base/
  ├── product_overview.md (5 stran)
  │   [High-level product description]
  │
  ├── features/
  │   ├── feature_authentication.md (10 stran)
  │   ├── feature_reporting.md (15 stran)
  │   ├── feature_integrations.md (12 stran)
  │   └── ... (each feature separate)
  │
  ├── api/
  │   ├── api_overview.md (5 stran)
  │   ├── api_authentication.md (8 stran)
  │   ├── api_endpoints.md (20 stran)
  │   └── api_examples.md (10 stran)
  │
  ├── workflows/
  │   ├── workflow_onboarding.md (7 stran)
  │   ├── workflow_data_export.md (6 stran)
  │   └── ...
  │
  └── faq.md (15 stran)
      [Common questions with answers]
```

**Proč lepší:**
- ✅ Semantic search je přesnější (najde relevantní modul)
- ✅ Easy updates (změnil se API → update jen api_endpoints.md)
- ✅ Cross-references fungují ("See feature_integrations.md for details")

**Instructions:**
```markdown
## KNOWLEDGE BASE STRUCTURE

I have access to modular product documentation:
- Product overview
- Features (each feature separate doc)
- API documentation (overview, auth, endpoints, examples)
- Workflows (common user journeys)
- FAQ

When answering questions:
1. Identify relevant module(s)
2. Reference specific section
3. Provide context + example
4. Link to related modules if applicable

Example response:
"For API authentication, we use JWT tokens (see api_authentication.md).

Here's the process:
1. [steps from docs]

Example:
[code example from api_examples.md]

Related: If you're implementing SSO, see feature_authentication.md"
```

---

## 🔧 Troubleshooting

### Problém 1: "Asistent ignoruje Knowledge Base"

**Symptom:** Odpovídá bez reference k nahraným dokumentům.

**Možné příčiny:**
1. **Retrieval nefunguje:**
   - Dokumenty nemají jasnou strukturu (headings)
   - File format není optimální (např. scanned PDF)

2. **Instructions neříkají použít KB:**
   - Přidej: "Always reference Knowledge Base when answering"

3. **Query není specific:**
   - Vague otázka → těžké najít relevantní část KB

**Řešení:**
```markdown
## KNOWLEDGE BASE USAGE

ALWAYS check Knowledge Base before answering.

Process:
1. Identify which KB document(s) are relevant
2. Search for specific info in those docs
3. Base answer on KB content (cite sections)
4. If KB doesn't have info → say "This isn't covered in KB, but based on general knowledge..."

When citing:
"According to [document name], section [X]: [quote/paraphrase]"
```

### Problém 2: "Responses jsou inconsistent"

**Symptom:** Stejný input → různé outputs.

**Možné příčiny:**
1. Instructions příliš vague
2. Chybějící examples v KB
3. Není definovaný default workflow

**Řešení:**
- Přidej konkrétní examples do KB
- Zpřesni Instructions (step-by-step process)
- Přidej "default output template" do KB

### Problém 3: "Asistent dělá out-of-scope úkoly"

**Symptom:** Uživatelé požadují věci mimo scope, asistent se snaží pomoct (ale špatně).

**Řešení:**
```markdown
## SCOPE BOUNDARIES

IN SCOPE:
- [list konkrétních úkolů]

OUT OF SCOPE:
- [list co NEDĚLÁM]

If user requests out-of-scope task:
"This is outside my expertise. I specialize in [X].
For [user's request], I recommend [alternative: different assistant, tool, person].

Can I help with [in-scope alternative]?"
```

### Problém 4: "Context window přeplněn i s KB"

**Symptom:** Dlouhé konverzace → AI začíná zapomínat začátek.

**Řešení:**
1. **Summarize periodically:**
   ```markdown
   After every 20 messages, automatically offer:
   "This conversation is getting long. Want me to summarize
   key points before we continue?"
   ```

2. **New chat per task:**
   - Instructions: "For new task/topic, start new chat in this project"

3. **Reference previous chats:**
   - V projektu: "See chat [name] from [date] for details"

### Problém 5: "Updates KB jsou pain"

**Symptom:** Často musíš updateovat dokumenty, re-upload je tedious.

**Řešení:**
1. **Version control outside:**
   - Git repo s KB dokumenty
   - Update tam → pak re-upload

2. **Changelog v KB:**
   ```markdown
   # changelog.md

   ## 2025-11-09
   - Updated: api_endpoints.md (added new /reports endpoint)
   - Removed: deprecated_features.md

   ## 2025-11-01
   - Added: workflow_data_export.md
   ```

3. **Modularizace:**
   - Místo 1 velkého souboru → mnoho malých
   - Update jen co se změnilo

---

## 🎓 Závěr

### Kdy použít co - Final Decision Matrix

| Situace | Řešení |
|---------|--------|
| **Jednorázový úkol** | Běžný prompt |
| **2-5x měsíčně, malý kontext** | Uložený prompt template |
| **5x+ měsíčně, velký kontext** | Custom GPT / Project |
| **Tým potřebuje konzistenci** | Custom GPT / Project (sdílený) |
| **Enterprise, M365 integrace** | Copilot Studio |
| **Experimentuješ** | Prompt → iteruj → pak asistent |

### Checklist pro vytvoření asistenta

- [ ] Mám jasně definovaný scope (co dělá, co nedělá)
- [ ] Proces je standardizovaný (ne ad-hoc)
- [ ] Identifikoval/a jsem fixní kontext (→ KB)
- [ ] Napsal/a jsem strukturované Instructions
- [ ] Nahrál/a jsem Knowledge Base (modular structure)
- [ ] Testoval/a jsem 5+ různých scenarios
- [ ] Edge cases jsou handled (error messages)
- [ ] Conversation starters jsou clear
- [ ] Dokumentace existuje (jak asistenta používat)

### Resources

**Oficiální dokumentace:**
- [OpenAI Custom GPTs](https://help.openai.com/en/articles/8554397-creating-a-gpt)
- [Claude Projects](https://support.anthropic.com/en/articles/projects)
- [Microsoft Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)

**Best practices:**
- [RAG Best Practices](https://www.anthropic.com/research/retrieval-augmented-generation)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)

---

**Next Steps:**
1. Identifikuj 1 úkol který děláš 5x+ měsíčně
2. Začni s promptem (iteruj dokud není dobrý)
3. Migruj na asistenta (Custom GPT / Project)
4. Sdílej s týmem
5. Collect feedback → improve

---

**Verze:** 1.0 | **Listopad 2025** | **Pro:** Školení Prompt Engineering - Advanced
