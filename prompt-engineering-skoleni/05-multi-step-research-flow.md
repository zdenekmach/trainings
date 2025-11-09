# Vícekrokové Research & Analytical Flow
## Průvodce složitými analytickými a výzkumnými úkoly s využitím AI

> **Pro koho:** Analytici, výzkumníci, konzultanti, strategové
> **Kdy použít:** Složité výzkumné a analytické projekty vyžadující syntézu z více zdrojů
> **Časová náročnost:** 30-45 min čtení + praktické experimenty

---

## 🎯 O čem je tento průvodce

Tento dokument ti ukáže, jak efektivně řešit složité analytické a výzkumné úkoly pomocí orchestrace různých AI nástrojů. Není to o náhodném skákání mezi nástroji, ale o **strategickém workflow**, kde každý AI nástroj plní svou specifickou roli.

### Co se naučíš:
- ✅ Jak rozložit složitý výzkumný úkol do kroků
- ✅ Který AI nástroj použít v které fázi (a proč)
- ✅ Jak kombinovat nástroje pro maximální efektivitu
- ✅ Jak se vyhnout halucinacím a validovat zjištění
- ✅ Jak efektivně syntetizovat poznatky do výstupů

### Příklady použití:
- 📊 Komplexní market research
- 🔬 Technologické rešerše a competitive analysis
- 📈 Strategic planning založený na datech
- 📝 White papers a research reporty
- 🎤 Prezentace založené na důkladném výzkumu

---

## 🔄 5-fázové Research Flow

```
1. DEFINE         2. RESEARCH       3. VALIDATE       4. SYNTHESIZE     5. CREATE
   (Cíl)            (Sběr)           (Ověření)         (Syntéza)        (Výstup)
     ↓                ↓                  ↓                 ↓               ↓
  ChatGPT o1     Perplexity       Claude Sonnet    NotebookLM      Claude Sonnet
   Claude         Gemini          + Fact-check      + Google       + MS Copilot
                  MS Copilot         Tools           Workspace
```

**Proč 5 fází?**
- Každá fáze má jiné požadavky na AI capabilities
- Prevents "garbage in, garbage out" problém
- Umožňuje iterativní zlepšování
- Snižuje riziko halucinací a nepřesností

---

## 📍 Fáze 1: DEFINE - Doladění cíle výzkumu

**Cíl fáze:** Transformovat vágní zadání na konkrétní, strukturovaný research plán.

### Primární nástroje:
1. **ChatGPT o1** (recommended) - Extended thinking pro strategické plánování
2. **Claude Sonnet 4** (alternative) - Extended thinking mode

### Proč tyto nástroje:
- **o1**: Optimalizovaný pro komplexní reasoning a dekompozici problémů
- **Claude Extended Thinking**: Umožňuje deep reasoning s vizualizací myšlenkového procesu

### Postup:

#### Krok 1.1: Initial scoping
```markdown
**Prompt pro ChatGPT o1:**

Potřebuji ti pomoc s definováním výzkumného projektu.

**Vágní zadání:**
[Tvoje původní zadání, třeba: "Chci pochopit trh s AI nástroji pro marketing"]

**Tvůj úkol:**
1. Identifikuj klíčové research questions (min 5)
2. Navrhni strukturu výzkumu (hlavní oblasti)
3. Definuj success criteria (co bude znamenat "hotovo")
4. Identifikuj potenciální gaps a rizika
5. Navrhni prioritizaci (co první, co později)

**Formát:**
Strukturovaný dokument s jasně oddělenými sekcemi.
```

**Proč to funguje:**
- o1 má extended reasoning - zvládá komplexní dekompozici
- Nutí tě přemýšlet o success criteria PŘED začátkem
- Identifikuje slepé uholky které bys mohl/a přehlédnout

#### Krok 1.2: Refinement
```markdown
**Follow-up prompt:**

Na základě tvé analýzy:

**Vyber top 3 research questions** které mají:
- Nejvyšší business impact
- Jsou answerable v timeframe [X týdnů]
- Mají dostupné zdroje

Pro každou otázku definuj:
1. Sub-questions (rozložení na menší části)
2. Potřebné typy zdrojů (akademické, industry, data)
3. Estimated effort (time to answer)

**Output:**
Prioritizovaný research roadmap, ready to execute.
```

### Output fáze 1:
- ✅ 3-5 konkrétních research questions
- ✅ Strukturovaný plán výzkumu
- ✅ Success criteria
- ✅ Prioritizace (co dělat v jakém pořadí)

**💾 Ulož do:** Notion, Google Docs, nebo Sharepoint jako "Research Brief"

---

## 🔍 Fáze 2: RESEARCH - Rešerše a sběr informací

**Cíl fáze:** Systematicky nasbírat relevantní informace z důvěryhodných zdrojů.

### Primární nástroje:
1. **Perplexity** (Deep Research mode) - Primární research s citacemi
2. **Gemini 2.5 Pro** - Dlouhý kontext, rychlé zpracování velkých dokumentů
3. **MS Copilot** - Pokud potřebuješ info z M365 ekosystému (SharePoint, Teams)

### Tool-specific strategie:

#### 2.1: Perplexity (Deep Research)

**Kdy použít:**
- Potřebuješ široký přehled tématu
- Chceš citace a zdroje
- Topic je aktuální (online zdroje)

**Jak použít:**
```markdown
**Prompt pro Perplexity (Deep Research mode):**

Research question: [Tvoje specific research question z Fáze 1]

**Požadavky:**
- Comprehensive analysis (min 800 slov)
- Academic a industry zdroje preferred
- Citace ke každému tvrzení
- Identifikuj competing viewpoints (pokud existují)

**Zaměř se na:**
1. [Sub-question 1]
2. [Sub-question 2]
3. [Sub-question 3]

**Výstup:**
Strukturovaná analýza s odkazy na zdroje.
```

**Pro tip:**
- Používej Deep Research mode pro komplexní témata (generuje 5-10 min)
- Pro rychlejší průzkum: Standard mode (30s)
- Specifikuj typy zdrojů: "Academic papers only" / "Industry reports preferred"

#### 2.2: Gemini 2.5 Pro (Huge Context)

**Kdy použít:**
- Máš velké množství dokumentů k analýze
- Potřebuješ zpracovat PDF reporty, whitepapers
- Cross-document analysis (najít patterns napříč dokumenty)

**Jak použít:**
```markdown
**Prompt pro Gemini 2.5 Pro:**

Nahrávám ti [X] dokumentů k analýze. Tvůj úkol:

**Research question:** [Konkrétní otázka]

**Dokumenty:**
[Upload PDFs/documents]

**Analýza:**
1. Projdi všechny dokumenty
2. Extrahuj klíčové findings relevant k research question
3. Identifikuj shody a rozdíly mezi zdroji
4. Označ conflicting information

**Formát výstupu:**
- Tabulka findings (zdroj | tvrzení | supporting evidence)
- Summary of consensus vs. debates
- List of gaps (co zdroje nepokrývají)

**Délka:** Comprehensive (min 1000 slov)
```

**Pro tip:**
- Gemini má 2M token context - můžeš nahrát desítky dokumentů najednou
- Flash verze pro rychlé scan, Pro pro deep analysis
- Funguje natively s Google Drive (pokud používáš)

#### 2.3: MS Copilot (M365 Integration)

**Kdy použít:**
- Informace jsou ve vašem SharePointu / Teams
- Potřebuješ historická data z emailů, meetingů
- Internal knowledge base search

**Jak použít:**
```markdown
**Prompt pro MS Copilot:**

Research topic: [Tvoje téma]

**Prohledej:**
- SharePoint site: [site name]
- Teams channels: [channels]
- Email threads obsahující: [keywords]
- OneDrive dokumenty: [folder]

**Najdi:**
- Relevantní dokumenty a presentations
- Discussion threads o [topic]
- Decisions made v posledních [X měsících]

**Výstup:**
Seznam dokumentů/konverzací s:
- Link
- Krátké summary
- Relevance score (high/medium/low)
```

**Pro tip:**
- Copilot je nejlepší pro internal knowledge
- Pro external research radši Perplexity
- Můžeš kombinovat: Internal research (Copilot) + External (Perplexity)

### Research Organization

**Během fáze 2, organizuj findings:**

1. **Vytvoř structured note v Notion/Google Docs:**
```
# Research Notes: [Topic]

## Source 1: [Title] (Perplexity)
- Link: [URL]
- Key findings:
  - Finding 1
  - Finding 2
- Credibility: [High/Medium/Low]
- Notes: [Tvoje poznámky]

## Source 2: [Title] (Gemini)
...
```

2. **Tag each finding:**
- 🟢 High confidence (multiple sources confirm)
- 🟡 Medium confidence (single source, credible)
- 🔴 Low confidence (needs validation)
- ❓ Conflicting information (different sources disagree)

### Output fáze 2:
- ✅ Structured notes s findings
- ✅ Links ke zdrojům
- ✅ Preliminary confidence assessment
- ✅ List of contradictions to resolve

**⚠️ DŮLEŽITÉ:** V této fázi NESYNTETIZUJ. Jen sbírej a organizuj.

---

## ✅ Fáze 3: VALIDATE - Ověření a fact-checking

**Cíl fáze:** Eliminovat halucinace, ověřit tvrzení, zvýšit důvěryhodnost.

### Primární nástroje:
1. **Claude Sonnet 4** - Kritické myšlení, fact-checking
2. **Perplexity** - Cross-reference verification
3. **Manual checks** - Kritická tvrzení ověřit ručně

### Proč je tato fáze kritická:
- AI modely mohou halucinovat (i když méně než dřív)
- Citations mohou být nesprávné
- Misinterpretace zdrojů
- Bias v zdrojích

### Strategie validace:

#### 3.1: AI-powered fact-check (Claude)

```markdown
**Prompt pro Claude Sonnet 4:**

Role: Critical fact-checker a research validator

**Tvůj úkol:**
Analyzuj následující findings z mého researche a identifikuj potential issues.

**Findings k validaci:**
[Paste tvoje findings z Fáze 2]

**Pro každý finding:**
1. Assess source credibility
2. Check for logical consistency
3. Identify potential biases
4. Flag claims that need additional verification
5. Highlight contradictions

**Výstup:**
Tabulka:
| Finding | Confidence | Issues | Recommended Action |
|---------|------------|--------|-------------------|
| ...     | High/Med/Low | ... | Verify/Accept/Reject |

**Buď skeptický.** Raději flag něco zbytečně než přehlédnout problém.
```

**Proč Claude:**
- Vynikající v nuanced reasoning
- Dokáže identifikovat subtle inconsistencies
- Dobrý v critical thinking

#### 3.2: Cross-reference check (Perplexity)

Pro 🔴 Low confidence a ❓ Conflicting findings:

```markdown
**Prompt pro Perplexity:**

Fact-check request:

**Claim:** [Konkrétní tvrzení které chceš ověřit]

**Context:** [Odkud pochází]

**Tvůj úkol:**
1. Find 3-5 independent sources addressing this claim
2. Do sources support, contradict, or provide nuance?
3. What is the current consensus (if any)?

**Requirements:**
- Academic sources preferred
- Recent sources (last 2 years) preferred
- Cite all sources

**Output:** Verification summary (Confirmed / Contradicted / Nuanced / Unclear)
```

#### 3.3: Manual verification checklist

Pro kritická tvrzení (ta co budou v executive summary):

**Ověř ručně:**
- [ ] Link na zdroj funguje a není za paywallem
- [ ] Zdroj skutečně říká co AI tvrdí (ne misinterpretace)
- [ ] Zdroj je credible (academic, reputable publication, known expert)
- [ ] Data jsou aktuální (nejsou zastaralá)
- [ ] Statistiky mají kontext (ne cherry-picked)

### Output fáze 3:
- ✅ Validated findings (high confidence)
- ✅ Flagged items requiring more research
- ✅ Contradictions resolved (nebo acknowledged)
- ✅ Credibility score pro každý finding

**💾 Update:** Notion/Google Docs s validation results

---

## 🧬 Fáze 4: SYNTHESIZE - Syntéza poznatků

**Cíl fáze:** Transformovat raw findings na insights, identifikovat patterns, vytvořit narrative.

### Primární nástroje:
1. **NotebookLM** - Automatická syntéza, podcast generation
2. **Claude Sonnet 4** - Nuanced synthesis, writing
3. **Google Workspace / Notion** - Collaborative synthesis

### Tool-specific strategie:

#### 4.1: NotebookLM (Rychlá syntéza)

**Kdy použít:**
- Máš 10+ zdrojů k syntetizaci
- Chceš rychle pochopit "big picture"
- Potřebuješ audio summary (podcast)

**Jak použít:**

1. **Upload sources do NotebookLM:**
   - Tvoje research notes (Google Doc / PDF export)
   - Key source documents
   - Validation summaries

2. **Generate audio overview:**
   - NotebookLM vytvoří 10-15min "podcast" diskuzi o tématech
   - Poslechni si pro rychlý přehled
   - Identifikuj hlavní themes

3. **Query NotebookLM:**
```markdown
Questions pro NotebookLM:

1. "What are the 5 most important insights across all sources?"
2. "What patterns emerge from the research?"
3. "Where do sources disagree and why?"
4. "What are the implications for [tvůj kontext]?"
5. "What are the gaps in current knowledge?"
```

**Pro tip:**
- Audio overview je skvělý pro "stepping back" a vidět big picture
- Používej Study Guide feature pro strukturovaný přehled
- Citace jsou always linkované ke zdrojům

#### 4.2: Claude Sonnet 4 (Deep Synthesis)

**Kdy použít:**
- Potřebuješ nuanced analysis
- Připravuješ executive summary nebo white paper
- Vyžaduje strategic thinking

**Prompt pro synthesis:**
```markdown
**Role:** Senior research analyst a strategic thinker

**Context:**
Dokončil/a jsem výzkum na téma: [topic]
Mám validated findings z [X] zdrojů.

**Findings:**
[Paste validated findings z Fáze 3]

**Tvůj úkol:**

**1. PATTERN IDENTIFICATION**
- Identifikuj 3-5 hlavních themes napříč findings
- Pro každý theme: supporting evidence z findings
- Highlight emerging trends

**2. INSIGHT GENERATION**
- Co findings znamenají v kontextu [business/industry/research goal]?
- Jaké jsou implications pro [target audience]?
- Co je surprising nebo counterintuitive?

**3. NARRATIVE CREATION**
- Vytvoř coherent story z findings
- Začni s "So what?" (proč je to důležité)
- Builduj argument s evidencí

**4. GAPS & NEXT STEPS**
- Co stále nevíme?
- Kde je potřeba další výzkum?
- What are the limitations?

**Formát:**
Strukturovaný dokument, min 1500 slov, s jasnou narrative arc.

**Tone:** Professional, analytical, ale accessible (ne academic jargon).
```

**Proč Claude:**
- Nejlepší v nuanced, long-form writing
- Umí vytvořit compelling narrative
- Context window (200K) stačí i pro rozsáhlý research

#### 4.3: Collaborative synthesis (Google Workspace / Notion)

**Pro týmové projekty:**

1. **Vytvoř synthesis workspace:**
   - Google Doc: "Research Synthesis - [Topic]"
   - Notion database: Findings + Themes + Insights

2. **Struktura dokumentu:**
```markdown
# Research Synthesis: [Topic]

## Executive Summary (3-5 bullets)
- [Key insight 1]
- [Key insight 2]
...

## Main Themes

### Theme 1: [Name]
**What we found:** [Summary]
**Evidence:** [Links to findings]
**Implications:** [So what?]

### Theme 2: [Name]
...

## Detailed Analysis
[Deep dive do každého theme]

## Gaps & Limitations
[Co nevíme, caveats]

## Recommendations
[Actionable next steps]
```

3. **Iteruj s týmem:**
   - Sdílej draft
   - Collect feedback
   - Zpřesni insights

### Output fáze 4:
- ✅ Synthesis document (hlavní insights)
- ✅ Narrative story (ne jen bullet points)
- ✅ Identifikované patterns a trendy
- ✅ Clear implications a recommendations

**💾 Ulož do:** Google Workspace / Notion / SharePoint (podle firemního standardu)

---

## 🎨 Fáze 5: CREATE - Tvorba finálního výstupu

**Cíl fáze:** Transformovat syntézu do publikovatelného formátu (article, presentation, report).

### Primární nástroje:
1. **Claude Sonnet 4** - Long-form writing (articles, reports)
2. **ChatGPT GPT-4.1** - Polished business writing
3. **MS Copilot** - PowerPoint generation (pokud pracuješ v M365)
4. **Gemini** - Google Slides creation (pokud používáš Google Workspace)

### Output-specific strategie:

#### 5.1: Research Report / White Paper

**Nástroj:** Claude Sonnet 4

```markdown
**Prompt pro Claude:**

**Role:** Professional research writer a content strategist

**Task:** Transformuj research synthesis do polished research report.

**Input:**
[Paste synthesis z Fáze 4]

**Target:**
- Audience: [C-level executives / technical team / general audience]
- Length: [2000-3000 / 5000+ slov]
- Tone: [Professional-academic / Business-accessible]

**Structure:**

1. **Executive Summary** (1 strana)
   - Problem statement
   - Key findings (3-5 bullets)
   - Main recommendations

2. **Introduction** (500 slov)
   - Context a background
   - Research questions
   - Methodology overview

3. **Findings** (hlavní část, 60% délky)
   - Organized by themes
   - Each finding s evidencí
   - Visualizations recommendations (kde dává smysl graf/tabulka)

4. **Analysis** (20% délky)
   - Synthesis a insights
   - Implications
   - Comparison s existing knowledge

5. **Recommendations** (15% délky)
   - Actionable next steps
   - Prioritized
   - S timeframes

6. **Limitations & Future Research** (5% délky)

**Formát:**
- Headings a subheadings (jasná hierarchie)
- Bullet points kde relevantní
- Footnotes / endnotes pro citace
- Call-out boxes pro key insights

**First, vytvoř detailed outline**, pak ask for approval, pak writeuj sekci po sekci.
```

**Iterační proces:**
1. Claude vytvoří outline → review
2. Writeuj Introduction → review
3. Writeuj Findings po themes → review po každém
4. Atd.

**Proč iterovat:** Lepší kontrola, můžeš adjustovat směr, ne 10K slov najednou

#### 5.2: Blog Post / Article

**Nástroj:** ChatGPT GPT-4.1

```markdown
**Prompt pro GPT-4.1:**

Transform research insights into engaging blog post.

**Research insights:**
[Key insights z Fáze 4]

**Target:**
- Audience: [Industry professionals / General tech audience]
- Platform: [LinkedIn / Medium / Company blog]
- Length: 1200-1500 words
- Tone: Professional but conversational

**Structure:**

1. **Hook** (první paragraph)
   - Compelling stat nebo surprising finding
   - Why should reader care?

2. **The Setup** (context)
   - Brief background
   - The problem/question

3. **Main Content** (3-4 sections)
   - Each section = one key insight
   - Use subheadings
   - Include real examples

4. **Implications** (so what?)
   - What this means for readers
   - Actionable takeaways

5. **Conclusion**
   - Recap key points
   - Call to action / next steps

**Style:**
- Short paragraphs (3-4 sentences max)
- Use analogies a examples
- NO jargon unless explained
- Include pullout quotes (zvýraznění key insights)

**SEO keywords:** [pokud relevantní]
```

**Pro tip:**
- GPT-4.1 je často lepší než Claude pro snappy, engaging content
- Claude je lepší pro depth a nuance
- Zkus oba, vyber co ti víc sedí

#### 5.3: Presentation Deck (PowerPoint/Google Slides)

##### Option A: MS Copilot (PowerPoint)

**Pro uživatele M365:**

```markdown
**Prompt pro MS Copilot:**

Create PowerPoint presentation from research synthesis.

**Topic:** [Tvůj topic]

**Source document:** [Link na Google Doc/SharePoint doc s synthesis]

**Presentation requirements:**

**Audience:** [Executives / Team / Conference]
**Length:** [15-20 slides]
**Duration:** [20 min presentation + 10 min Q&A]

**Structure:**

1. Title slide
2. Agenda (1 slide)
3. Executive Summary (2 slides - problem + key findings)
4. Methodology (1 slide - how we researched)
5. Main Findings (8-10 slides, organized by themes)
6. Key Insights (2-3 slides - synthesis)
7. Recommendations (2-3 slides - actionable)
8. Next Steps (1 slide)
9. Q&A slide

**Design preferences:**
- Professional template (suggest: [template name])
- Minimal text (max 5 bullets per slide)
- Suggest where charts/graphs would help
- Include speaker notes

**Create the presentation, then I'll review and iterate.**
```

**Copilot advantage:**
- Direct PowerPoint generation
- Sahá do vašeho company template library
- Může importovat data z Excelu/SharePoint

##### Option B: Claude/GPT (Content) + Manual (Design)

Pokud AI nepodporuje direct slide creation:

**Krok 1: Generate slide content**
```markdown
**Prompt pro Claude/GPT:**

Create slide-by-slide content for presentation.

[Same requirements as above]

**Output format:**

For each slide, provide:

---
**Slide [X]: [Title]**

**Bullet points:**
- Bullet 1
- Bullet 2
...

**Speaker notes:**
[What to say - 100-150 words]

**Visual suggestion:**
[Chart/image/icon suggestion]
---
```

**Krok 2: Manuální design**
- Copy obsah do PowerPoint/Google Slides
- Apply design
- Přidej vizualizace

##### Option C: Gemini (Google Slides)

**Pro Google Workspace users:**

```markdown
**Prompt pro Gemini:**

Create Google Slides presentation from research.

**Research document:** [Link na Google Doc]

[Same structure as MS Copilot prompt above]

Generate slide content and create slides in Google Slides.
```

**Gemini advantage:**
- Native Google Workspace integration
- Může direct access Google Docs
- Automatická tvorba slides

### 5.4: Executive Summary (1-pager)

**Nástroj:** Claude nebo GPT

```markdown
**Critical task:** Create ONE PAGE executive summary.

**Source:** [Link/paste synthesis]

**Constraints:**
- MAX 1 strana A4
- Audience: C-level (assumed zero context)
- Must be self-contained (can stand alone)

**Structure:**

**[Topic]**
Executive Summary

**Context** (2-3 sentences)
[Why this matters]

**Key Findings** (3-5 bullets)
- Finding 1: [Impact]
- Finding 2: [Impact]
...

**Implications** (2-3 sentences)
[What this means for business/org]

**Recommendations** (3 bullets)
- Recommendation 1 [Priority: High/Medium]
- Recommendation 2 [Priority: High/Medium]
- Recommendation 3 [Priority: High/Medium]

**Next Steps** (2 bullets, with owners/timelines)

---

**Formatting:**
- Bold key terms
- White space for readability
- No jargon
- Every sentence adds value (no fluff)

Must fit on ONE page when printed in 11pt font.
```

### Output fáze 5:
- ✅ Polished, publikovatelný dokument/prezentace
- ✅ Adapted pro target audience
- ✅ Professionally formatted
- ✅ Ready to share

---

## 🛠️ Tool Selection Matrix

**Quick reference: Který nástroj v které fázi**

| Fáze | Primární nástroj | Proč | Alternativa |
|------|------------------|------|-------------|
| **1. DEFINE** | ChatGPT o1 | Extended reasoning, dekompozice problémů | Claude Sonnet (extended thinking) |
| **2. RESEARCH** (online) | Perplexity Deep Research | Citace, current info, deep analysis | Gemini Pro (huge context) |
| **2. RESEARCH** (docs) | Gemini 2.5 Pro | 2M token context, multi-doc analysis | Claude Sonnet (200K context) |
| **2. RESEARCH** (internal) | MS Copilot | M365 integration, SharePoint search | Manual search + Claude summary |
| **3. VALIDATE** | Claude Sonnet 4 | Critical thinking, nuance detection | Perplexity (cross-reference) |
| **4. SYNTHESIZE** (quick) | NotebookLM | Auto-synthesis, audio overview | Claude (manual synthesis) |
| **4. SYNTHESIZE** (deep) | Claude Sonnet 4 | Nuanced analysis, narrative creation | GPT-4.1 |
| **5. CREATE** (report) | Claude Sonnet 4 | Long-form writing, depth | GPT-4.1 (more polished) |
| **5. CREATE** (blog) | ChatGPT GPT-4.1 | Engaging, accessible writing | Claude (more formal) |
| **5. CREATE** (slides) | MS Copilot / Gemini | Direct presentation creation | Claude + manual design |

---

## 💡 Best Practices

### Do's ✅

1. **Start with Define**
   - Nekřič do Researche bez jasného plánu
   - 30 min planning ušetří hodiny random browsing

2. **Document as you go**
   - Ne všechno nakonec
   - Real-time notes v Notion/Google Docs

3. **Tag confidence levels**
   - 🟢 High / 🟡 Medium / 🔴 Low
   - Pak víš co validovat v Fáze 3

4. **Use the right tool for each phase**
   - Ne "všechno v Claude" nebo "všechno v GPT"
   - Každý nástroj má strengths

5. **Iterate**
   - První pass nikdy není finální
   - Build, review, refine

6. **Synthesize before creating**
   - Neskákej z raw findings přímo na prezentaci
   - Synthesis = where insights happen

7. **Cross-validate critical claims**
   - Pokud jde do exec summary, double-check
   - Radši paranoid než wrong

### Don'ts ❌

1. **Nepoužívej single AI pro všechno**
   - Suboptimal results
   - Každý model má své sweet spots

2. **Neskipuj Validation phase**
   - "Looks good" ≠ "Is correct"
   - Halucinace se stávají

3. **Nehalucinuj citace**
   - Pokud AI dá citaci, ověř link
   - Dead links = ztráta credibility

4. **Nesyntetizuj příliš brzy**
   - Dej research fázi dostatek času
   - Premature synthesis = missed insights

5. **Nezapomínej na audience**
   - C-level executive ≠ technical team
   - Same research, different outputs

6. **Neztrácej se v perfekcionismu**
   - "Done is better than perfect"
   - Iteruj, ale ship

---

## 🎯 Example Workflow: Market Research

**Scenario:** Analyzovat trh s AI productivity tools pro malé firmy (10-50 zaměstnanců)

### Week 1: Define + Research

**Den 1: DEFINE (2 hodiny)**
- ChatGPT o1: Definovat research questions
- Output: 5 klíčových otázek (market size, key players, pain points, pricing models, adoption barriers)
- Ulož do Notion

**Den 2-3: RESEARCH - Online (4 hodiny)**
- Perplexity Deep Research:
  - Query 1: "Market size and growth AI productivity tools SMB 2024-2025"
  - Query 2: "Top AI productivity tools comparison small business"
  - Query 3: "SMB AI adoption challenges survey data"
- Document findings v Google Doc s citacemi

**Den 4: RESEARCH - Documents (3 hodiny)**
- Gemini 2.5 Pro:
  - Upload 10 industry reports (PDF)
  - Query: "Extract SMB-specific insights from all reports"
  - Cross-reference findings

**Den 5: VALIDATE (2 hodiny)**
- Claude Sonnet: Fact-check top 20 findings
- Perplexity: Cross-verify 3 contradictory claims
- Manual check: Top 5 statistics

### Week 2: Synthesize + Create

**Den 6: SYNTHESIZE (3 hodiny)**
- NotebookLM:
  - Upload all research notes
  - Generate audio overview (listen)
  - Extract key themes
- Claude Sonnet:
  - Deep synthesis prompt
  - Generate insights document

**Den 7-8: CREATE - Report (6 hodin)**
- Claude Sonnet:
  - Outline review
  - Write report po sekcích
  - Iterate based on feedback

**Den 9: CREATE - Presentation (3 hodiny)**
- MS Copilot:
  - Generate PPT z reportu
  - Review slides
  - Add visualizations

**Den 10: CREATE - Executive Summary (1 hodina)**
- Claude: 1-page exec summary
- Final review
- Ship!

**Total time:** ~25 hodin
**Saved vs. manual:** ~60-80 hodin

---

## 🔄 Iterative Refinement

Research není lineární. Často budeš iterovat:

```
DEFINE → RESEARCH → (findings reveal new questions) → back to DEFINE
                                                          ↓
                                              RESEARCH more
                                                          ↓
                                              VALIDATE → SYNTHESIZE → CREATE
                                                          ↑
                                       (synthesis reveals gap) → back to RESEARCH
```

**To je normální a healthy!**

Indicators kdy iterovat back:
- ❓ Synthesis odhalí large gap v coverage
- ❓ Findings jsou contradictory bez explanation
- ❓ Research question se ukáže být wrong question
- ❓ Objevíš critical new source

**Ale pozor:** Infinite research loop. Set boundaries:
- Time box: "Research phase max 2 týdny"
- Good enough threshold: "Need 80% confidence, not 100%"

---

## 📊 Success Metrics

**Jak poznat že flow funguje:**

### Quality indicators:
- ✅ Findings mají reputable sources
- ✅ Contradictions jsou acknowledged nebo resolved
- ✅ Insights jdou beyond "summarizing sources"
- ✅ Recommendations jsou actionable (ne vague)
- ✅ Stakeholders říkají "this is useful"

### Efficiency indicators:
- ✅ Ušetříš 50%+ time vs. pure manual research
- ✅ Méně back-and-forth (dobrá definice na začátku)
- ✅ Minimal rework (validace zachytí issues early)
- ✅ Reusable templates (příště rychlejší)

### Red flags:
- 🚩 Končíš s "I still don't know" (bad Define phase)
- 🚩 Findings jsou generic (bad Research prompts)
- 🚩 Najdeš factual error až post-publish (skipped Validate)
- 🚩 Output je "meh" (weak Synthesis)

---

## 🎓 Practical Exercise

**Try this workflow na vlastní use case:**

**Úkol:** Zvol si research topic relevant pro tvou práci.

**Suggestions:**
- Competitive analysis (kdo jsou hlavní competitors a jak se liší)
- Technology evaluation (který tool/platform použít pro X)
- Market trend analysis (kam směřuje Y industry)

**Cvičení (3-4 hodiny):**

1. **DEFINE (30 min):**
   - ChatGPT o1: Definuj 3 research questions
   - Vytvoř simple research plan

2. **RESEARCH (90 min):**
   - Perplexity: 2-3 deep research queries
   - Document 10-15 findings

3. **VALIDATE (30 min):**
   - Claude: Fact-check top 5 findings
   - Flag any issues

4. **SYNTHESIZE (45 min):**
   - NotebookLM nebo Claude: Create synthesis
   - Identify 3 key insights

5. **CREATE (30 min):**
   - Claude: Write executive summary (1 page)

**Pak:**
- Compare s jak bys to dělal/a manuálně
- Note time saved
- Note quality difference

---

## 📚 Additional Resources

### Notion Templates
- Research Brief template (Fáze 1)
- Research Notes database (Fáze 2)
- Synthesis document template (Fáze 4)

### Google Docs Templates
- Market Research Report outline
- Executive Summary 1-pager
- Presentation slide content template

**[Tyto templates můžeš vytvořit samostatně nebo request od týmu]**

---

## 🆘 Troubleshooting

### Problem: "Research trvá věčně, nikdy nekončí"
**Solution:** Time-box každou fázi. Define jasný "good enough" threshold na začátku.

### Problem: "Findings jsou contradictory, nevím komu věřit"
**Solution:** To je normální! Acknowledge contradiction v reportu. Pokud kritické: manual deep-dive do original sources.

### Problem: "AI halucinuje citace"
**Solution:** VŽDY verify links. Pokud link nefunguje: search pro actual source nebo discard finding.

### Problem: "Synthesis je jen 'summary', ne insights"
**Solution:** Better synthesis prompt. Explicitně žádej "implications", "so what", "what's surprising". Nebo zkus jiný model (Claude vs GPT).

### Problem: "Output je příliš generic/academic"
**Solution:** Specify tone and audience v prompts. Examples of good vs bad writing. Iterate s feedback.

### Problem: "Nevím který tool použít kdy"
**Solution:** Use Tool Selection Matrix výše. When in doubt: start s Claude nebo GPT, jsou most versatile.

---

## 🎯 Quick Start Checklist

Příště když začínáš complex research project:

- [ ] **Define:** 30 min s ChatGPT o1 nebo Claude - research questions + plán
- [ ] **Setup:** Notion/Google Doc pro organizaci notes
- [ ] **Research:** Perplexity (online) + Gemini (docs) + Copilot (internal)
- [ ] **Tag:** Confidence levels 🟢🟡🔴 během researche
- [ ] **Validate:** Claude fact-check critical findings
- [ ] **Synthesize:** NotebookLM (quick) nebo Claude (deep)
- [ ] **Create:** Right tool for output type (Claude report, GPT blog, Copilot slides)
- [ ] **Review:** Před ship, double-check top claims

---

## 💬 Final Thoughts

**Multi-step research flow není o "používání více AI".**

Je to o **orchestraci** - správný nástroj, správná fáze, správný způsob.

Single AI může dát "ok" results.
Orchestrated flow dává **excellent** results v **fraction of time**.

**Investice:**
- První projekt: 30 min extra (learning curve)
- Druhý projekt: 20 min extra (getting comfortable)
- Třetí+ projekt: Ušetříš 50-70% času

**ROI: Massive**

---

**Ready to try?** Pick a research project a run through this flow. Track time and quality. Budeš surprised.

---

**Verze:** 1.0 | **Listopad 2025** | **Pro:** Školení Prompt Engineering
**Next:** [Quick Reference Cheatsheet](./05-multi-step-research-flow-cheatsheet.md) →
