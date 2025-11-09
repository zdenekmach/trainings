# Specifická doporučení pro jednotlivé AI modely
## Srovnání a best practices (Listopad 2025)

> **Účel:** Tento dokument ti pomůže vybrat správný model pro tvůj use case a optimalizovat prompty pro specifické charakteristiky každého modelu.

> **Aktuální k:** Listopad 2025

---

## 📋 Obsah

1. [Quick Reference - Který model pro který úkol](#quick-reference)
2. [Claude (Anthropic)](#claude-anthropic)
3. [ChatGPT (OpenAI)](#chatgpt-openai)
4. [Gemini (Google)](#gemini-google)
5. [Perplexity](#perplexity)
6. [Microsoft Copilot](#microsoft-copilot)
7. [Srovnávací tabulky](#srovnávací-tabulky)
8. [Decision Tree - Výběr modelu](#decision-tree)

---

## 🎯 Quick Reference

| Use Case | #1 Volba | #2 Alternativa | Proč |
|----------|----------|----------------|------|
| **Dlouhá analytická práce** | Claude Sonnet 4 | Gemini 2.5 Pro | Biggest context, best pro nuance |
| **Rychlé dotazy** | Gemini Flash | Claude Haiku | Rychlost + nízká cena |
| **Komplexní reasoning** | ChatGPT o1 | Claude Sonnet 4 | o1 je optimalizovaný pro reasoning |
| **Kreativní psaní** | Claude Sonnet 4 | GPT-4.1 | Claude má nuancovanější jazyk |
| **Kódování** | Claude Sonnet 4 | GPT-4.1 | Claude je current leader |
| **Aktuální informace** | Perplexity | ChatGPT (search) | Perplexity = search-first |
| **Research s odkazy** | Perplexity | Gemini Pro (search) | Automatické citace |
| **Microsoft ekosystém** | MS Copilot | - | Integrace s M365 |
| **Video/audio analýza** | Gemini 2.5 Pro | - | Jediný s native video support |
| **Multi-modal (obrázky)** | Claude Sonnet 4 | GPT-4.1 | Oba vynikající |

---

## 🤖 Claude (Anthropic)

### Modely (Listopad 2025)

| Model | Context Window | Cena (Input/Output) | Rychlost | Kdy použít |
|-------|----------------|---------------------|----------|------------|
| **Claude Sonnet 4** | 200k tokens | $3/$15 per 1M | Střední | Komplexní úkoly, kódování, analýza |
| **Claude Sonnet 4.5** | 200k tokens | $3/$15 per 1M | Střední | Stejné jako 4, mírně lepší reasoning |
| **Claude Opus 4** | 200k tokens | $15/$75 per 1M | Pomalejší | Nejvyšší kvalita, kritické úkoly |
| **Claude Haiku 4** | 200k tokens | $0.25/$1.25 per 1M | Rychlý | Jednoduché úkoly, batch processing |

**Note:** Ceny nad 200k tokenů jsou 2x vyšší (prompt caching může snížit na ~10%)

### ✅ Silné stránky

1. **Nejlepší pro dlouhý kontext (1M tokens)**
   - Vůbec nezapomíná i při velmi dlouhých konverzacích
   - Exceluje když mu dáš celý projekt/codebase najednou

2. **Nuancovaný jazyk a reasoning**
   - Rozumí subtilním rozdílům
   - Výborný na kreativní psaní s "lidským" tónem
   - Méně "AI-sounding" než konkurence

3. **Kódování**
   - Current leader (listopad 2025) na většině coding benchmarks
   - Vynikající code review a debugging
   - Rozumí komplexním architekturám

4. **Bezpečnost a etika**
   - Nejkonzervativnější z modelů
   - Odmítne problematické požadavky (někdy i false positives)

5. **Strukturovaný output**
   - Exceluje na dodržování formátu když mu dáš template
   - Velmi dobrý na markdown, JSON, tabulky

### ❌ Slabé stránky

1. **Občas příliš "opatrný"**
   - Může odmítnout neškodné požadavky (false positive safety)
   - Někdy přidává zbytečné disclaimery

2. **Nemá native search**
   - Nelze vyhledávat aktuální info (cutoff leden 2025)
   - Musíš dát kontext explicitně

3. **Cena**
   - Dražší než GPT-4.1 pro základní úkoly
   - Nad 200k tokenů 2x cena (ale caching pomáhá)

### 🎯 Kdy použít Claude

- ✅ Dlouhé dokumenty (15+ stránek)
- ✅ Kódování, code review
- ✅ Kreativní psaní s nuancí
- ✅ Eticky citlivé úkoly
- ✅ Strukturovaná analýza

### 💡 Claude-specific prompting tips

#### 1. Využij XML tagy pro strukturu

Claude rozumí XML tagům lépe než markdown v komplexních promptech.

**Příklad:**
```xml
<context>
Projekt: CRM system pro farmaceutickou firmu
Timeline: 6 měsíců
</context>

<task>
Analyzuj requirements a najdi konflikty
</task>

<output_format>
<section name="conflicts">
  <item>
    <description>...</description>
    <impact>...</impact>
    <solution>...</solution>
  </item>
</section>
</output_format>
```

#### 2. Explicitně požaduj "thinking" pro komplexní úkoly

```markdown
Před finální odpovědí, ukaž své uvažování v sekci <thinking>.
Vysvětli kroky, alternativy, trade-offs.
Pak dej finální answer.
```

Claude má interní "thinking" process - pokud ho poprosíš aby ho ukázal, dostaneš lepší reasoning.

#### 3. Buď explicitní o tone

Claude má tendenci být formální. Pokud chceš jiný tón, řekni to explicitně.

```markdown
Tone: Conversational but professional. Jako by sis psal/a email kolegovi
kterého respektuješ, ale nemusíš být super formální.

AVOID: Korpátní žargon, příliš formální fráze typu "I would be happy to assist"
```

#### 4. Pro dlouhé konverzace - summarize periodicky

I když Claude má 1M context, kvalita mírně klesá při opravdu dlouhých konverzacích (100+ zpráv).

```markdown
[Po 50 zprávách]
"Shrň klíčová rozhodnutí a kontext z naší dosavadní konverzace.
Tento summary použiju jako základ pro pokračování."
```

#### 5. Prompt caching pro opakované kontexty

Pokud používáš API a posíláš stejný kontext opakovaně (např. company guidelines):

```markdown
# Strukturuj prompt:
[Static content - bude cached]
Company guidelines...
Templates...
Standards...

---
[Dynamic content - mění se]
Aktuální úkol: ...
```

První request: plná cena
Následující requesty (do 5 min): ~90% cheaper na cached část

---

## 💬 ChatGPT (OpenAI)

### Modely (Listopad 2025)

| Model | Context Window | Cena (Input/Output) | Rychlost | Kdy použít |
|-------|----------------|---------------------|----------|------------|
| **GPT-4.1** | 1M+ tokens | $2.50/$10 per 1M | Střední | Všeobecné úkoly, balanced price/performance |
| **GPT-4o** | 128k tokens | $2.50/$10 per 1M | Rychlejší | Rychlé úkoly, dobrý price/performance |
| **o1-preview** | 128k tokens | $15/$60 per 1M | Pomalejší | Komplexní reasoning, matematika, logika |
| **o1-mini** | 128k tokens | $3/$12 per 1M | Střední | Reasoning pro STEM, levnější než o1-preview |

### ✅ Silné stránky

1. **GPT-4.1: Best balanced model**
   - Velmi dobrý na všechno
   - Nižší cena než Claude Opus
   - Velký context (1M+)

2. **o1 série: Reasoning champion**
   - Nejlepší na komplexní logiku, matematiku
   - "Myslí" před odpovědí (internal chain-of-thought)
   - Výborný na strategy, planning, complex problem-solving

3. **Rychlost (GPT-4o)**
   - Nejrychlejší z "smart" modelů
   - Dobrý pro real-time use cases

4. **Custom GPTs**
   - Snadné vytvoření vlastních GPT s knowledge base
   - Sdílení s týmem nebo public
   - GPT Store pro ready-made nástroje

5. **Multi-modal**
   - DALL-E 3 integrace (generování obrázků)
   - Vision (analýza obrázků)
   - Voice mode (ChatGPT app)

### ❌ Slabé stránky

1. **Občas "hallucinuje" s confidence**
   - Může znít přesvědčivě i když se mýlí
   - Vždycky fact-check kritické info

2. **o1 modely nemají system prompts**
   - Nemůžeš nastavit "role" nebo "tone" pro o1
   - Pouze user messages

3. **GPT-4o má menší kontext (128k)**
   - Pro velké dokumenty musíš použít GPT-4.1

### 🎯 Kdy použít ChatGPT

- ✅ Všeobecné úkoly (GPT-4.1 je best balanced)
- ✅ Komplexní reasoning, matematika (o1)
- ✅ Rychlé odpovědi (GPT-4o)
- ✅ Generování obrázků (DALL-E 3)
- ✅ Vytvoření Custom GPT pro tým

### 💡 ChatGPT-specific prompting tips

#### 1. Pro o1: Méně je víc

o1 modely mají vlastní interní reasoning. **Nepotřebuješ** složité prompty.

**❌ Špatně pro o1:**
```markdown
You are an expert strategist with 20 years of experience.
Follow this process:
1. Analyze
2. Evaluate
3. Recommend
Think step-by-step...
```

**✅ Dobře pro o1:**
```markdown
Analyzuj tuto business situaci a doporuč strategii.

[kontext]
```

o1 už má built-in reasoning - zbytečné instrukce ho můžou zmást.

#### 2. Pro GPT-4.1 / GPT-4o: Buď specifický o formátu

GPT má tendenci být verbose. Omez ho explicitně.

```markdown
IMPORTANT: Odpověz v max 3 bullet points. Každý max 20 slov.
Bez úvodních nebo závěrečných frází.
```

#### 3. Použij "few-shot" pro konzistentní styl

GPT se učí rychle z příkladů.

```markdown
Přepiš tyto requirements do user stories.

Příklad:
Requirement: "System must allow filtering"
User Story: "As a user, I want to filter results by category so that I can find relevant items faster"

Teď přepiš:
Requirement: "Admin can export data"
```

#### 4. Pro faktické úkoly: Request sources

```markdown
Analyzuj tento problém. Pokud používáš fakta nebo statistiky,
CITE zdroj nebo uveď "based on my training data, uncertain about current accuracy"
```

GPT má tendenci znít confident i když si není jistý.

#### 5. Custom GPTs pro opakované úkoly

Pokud děláš úkol 5x+ měsíčně:

1. Create Custom GPT
2. Dej mu instrukce (jak má uvažovat, jaký formát používat)
3. Upload knowledge base (firemní docs, templates)
4. Sdílej s týmem → konzistence

---

## 🔷 Gemini (Google)

### Modely (Listopad 2025)

| Model | Context Window | Cena (Input/Output) | Rychlost | Kdy použít |
|-------|----------------|---------------------|----------|------------|
| **Gemini 2.5 Pro** | 1-2M tokens | $1.25/$5 per 1M | Střední | Dlouhý kontext, video/audio analýza |
| **Gemini 2.5 Flash** | 1M tokens | $0.075/$0.30 per 1M | Velmi rychlý | Vysoký volume, rychlé úkoly |

### ✅ Silné stránky

1. **Největší context window (2M tokens)**
   - Vejde se celá hodina videa
   - 11 hodin audia
   - Ideální pro analýzu obrovských datasetů

2. **Native video & audio understanding**
   - Jediný mainstream model který zpracovává video directly
   - Nemusíš transcript → dá mu přímo video link
   - Analyzuje vizuál + audio současně

3. **Flash = nejlevnější "smart" model**
   - $0.075 per 1M input (10x levnější než GPT-4.1)
   - Stále velmi capable
   - Ideální pro batch processing

4. **Integrovaný search (v některých regionech)**
   - Může vyhledávat online
   - Cituje zdroje

5. **Google ekosystém**
   - Integrace s Google Workspace
   - Google AI Studio (free playground)

### ❌ Slabé stránky

1. **Reasoning slabší než Claude/o1**
   - Dobrý, ale ne top tier pro komplexní logiku

2. **Občas verbose**
   - Má tendenci psát více než je nutné

3. **Safety filtry**
   - Podobně jako Claude, může false-positive odmítat

### 🎯 Kdy použít Gemini

- ✅ Analýza videa/audia (jediný native support)
- ✅ Obrovské dokumenty (využij 2M context)
- ✅ Batch processing velkého množství úkolů (Flash = levný)
- ✅ Research s aktuálními daty (má search)
- ✅ Google Workspace integrace

### 💡 Gemini-specific prompting tips

#### 1. Využij native video/audio

**Místo:**
```markdown
[Upload video]
[Extract transcript]
[Feed transcript to AI]
```

**Použij:**
```markdown
[Upload video přímo do Gemini 2.5 Pro]

Prompt: "Analyzuj toto video z business meetingu.
Identifikuj klíčové body diskuse, rozhodnutí, a action items."
```

Gemini vidí vizuální signály (body language, slides on screen) + slyší audio.

#### 2. Pro Flash: Buď ještě více explicitní

Flash je rychlý ale potřebuje více guidingu než Pro.

```markdown
TASK: Kategorizuj tyto user comments

CATEGORIES:
- Feature request
- Bug report
- Praise
- Question

OUTPUT: JSON array
[
  {"comment": "...", "category": "..."},
  ...
]

DO NOT add explanations, just JSON.
```

#### 3. Specifikuj délku agresivně

Gemini má tendenci být dlouhý. Omez ho.

```markdown
Max 3 věty. Žádné intro/outro. Direct answer only.
```

#### 4. Pro dlouhý kontext: Strukturuj input

I s 2M context, pomůže struktura.

```markdown
# Document 1: Requirements
[...]

# Document 2: User Feedback
[...]

# Document 3: Technical Constraints
[...]

ANALYSIS FOCUS: Find conflicts between Documents 1 and 3
```

#### 5. Využij Google AI Studio pro experimenty

Free playground pro Gemini modely:
- Testuj prompty bez platby
- Porovnávej Flash vs Pro
- Když najdeš fungující prompt → použij v produkci

---

## 🔍 Perplexity

### Modely (Listopad 2025)

| Model | Context | Cena | Kdy použít |
|-------|---------|------|------------|
| **Perplexity Pro** | Varies | $20/měsíc unlimited | Research s aktuálními zdroji |
| **Perplexity Free** | Varies | Free (limited) | Běžný research |

**Note:** Perplexity používá různé backend modely (GPT-4.1, Claude, vlastní), ale hlavní feature je search-first přístup.

### ✅ Silné stránky

1. **Search-first approach**
   - Každá odpověď je backed aktuálními zdroji
   - Automaticky cituje (clickable odkazy)
   - Ideální pro fact-checking

2. **Follow-up questions**
   - AI navrhuje related questions
   - Pomáhá explorovat téma

3. **Collections**
   - Můžeš vytvořit collection pro projekt
   - Všechny searche v jednom místě

4. **Academic mode (Pro)**
   - Focus na peer-reviewed sources
   - Ideální pro research

### ❌ Slabé stránky

1. **Ne pro non-search úkoly**
   - Není optimalizovaný pro kreativní psaní, kódování
   - Best jako "research assistant", ne "work assistant"

2. **Nemá control nad modelem**
   - Nevíš který backend model použije
   - Nemůžeš specifikovat (jako "use Claude for this")

3. **Kratší odpovědi**
   - Optimalizováno pro search results, ne dlouhé analýzy

### 🎯 Kdy použít Perplexity

- ✅ Research aktuálních informací
- ✅ Fact-checking (potřebuješ zdroje)
- ✅ Explorační research (follow-up questions)
- ✅ Academic research (Pro mode)

### 💡 Perplexity-specific prompting tips

#### 1. Explicitně požaduj depth

Perplexity default je brief. Pro detailed analysis:

```markdown
Provide comprehensive analysis (min 500 words) with sources for each claim.
```

#### 2. Specifikuj typy zdrojů

```markdown
Find information about [topic].

Sources preference:
- Academic papers (primary)
- Industry reports (secondary)
- Avoid: Blog posts, opinion pieces
```

#### 3. Použij date range

```markdown
Find developments in [topic] from last 6 months only.
Recent sources critical.
```

#### 4. Pro porovnání: Explicit structure

```markdown
Compare [A] vs [B].

Format:
1. Overview of A (with sources)
2. Overview of B (with sources)
3. Comparison table
4. Expert opinions from both sides
```

#### 5. Využij Collections pro dlouhodobý research

```markdown
Create Collection: "Market Entry Poland Research"

Series of searches:
1. "Polish creative agency market size 2024-2025"
2. "Top project management tools Poland"
3. "B2B SaaS adoption rate Poland"

→ Všechny sources v jednom místě pro finální report
```

---

## 🪟 Microsoft Copilot

### Varianty (Listopad 2025)

| Varianta | Context | Cena | Kdy použít |
|----------|---------|------|------------|
| **Copilot (free)** | Varies | Free | Běžné dotazy, search |
| **Copilot Pro** | Varies | $20/měsíc | M365 integrace, priority access |
| **Copilot for M365** | Varies | $30/user/měsíc | Enterprise, full M365 integration |

**Backend:** Uses GPT-4.1 with Microsoft enhancements + Bing search

### ✅ Silné stránky

1. **Microsoft ekosystém integrace**
   - Word, Excel, PowerPoint, Outlook, Teams
   - "Summarize this email thread"
   - "Create PowerPoint from this Word doc"

2. **Bing search integration**
   - Vždycky má aktuální info
   - Cituje web sources

3. **Enterprise-ready**
   - Commercial data protection
   - Admin controls
   - Compliance (GDPR, etc.)

4. **"Grounded in your data"**
   - Copilot for M365 má přístup k tvým SharePoint, OneDrive files
   - "Find all documents about Project X from last quarter"

### ❌ Slabé stránky

1. **Méně flexibilní než standalone modely**
   - Nemůžeš customizovat systém prompt
   - Designed pro M365 use cases primárně

2. **Občas příliš "safe"**
   - Microsoft je velmi opatrný re: safety
   - Může odmítnout neškodné business scénáře

3. **Quality varies**
   - Někdy brilliantní (díky GPT-4.1)
   - Někdy generic (safety filters, constraints)

### 🎯 Kdy použít Copilot

- ✅ Pracuješ primárně v M365 ekosystému
- ✅ Potřebuješ enterprise compliance
- ✅ Chceš AI integrované do tools (Word, Excel)
- ✅ Search + work combined

### 💡 Copilot-specific prompting tips

#### 1. Leverage M365 context (Copilot for M365)

```markdown
Summarize all emails from last week about "Q1 Planning"
Create action items list with owners.
```

Copilot má přístup k tvému Outlooku → contextual understanding.

#### 2. Pro Word/Excel: Buď specific o struktuře

```markdown
[In Word]
Create executive summary of this document.
Format:
- 3 bullet points (max 15 words each)
- 1 recommendation paragraph
- Table of key metrics
```

#### 3. Iteruj s conversation

Copilot je optimalizovaný pro conversational flow.

```markdown
User: "Summarize Q3 sales data"
Copilot: [summary]
User: "Now create chart showing trend"
Copilot: [chart]
User: "Add forecast for Q4 based on this trend"
```

#### 4. Pro PowerPoint: Template-based requests

```markdown
Create 5-slide presentation about [topic]

Slide 1: Title + key visual
Slide 2-4: Main points (each with image)
Slide 5: Call to action

Style: Professional, blue color scheme
```

#### 5. Combine search + work

```markdown
Find latest industry reports about [topic] (search),
then create summary in Word document with sources.
```

---

## 📊 Srovnávací tabulky

### Hlavní charakteristiky

| Model | Context | Cena (Input) | Rychlost | Reasoning | Kreativita | Kódování |
|-------|---------|--------------|----------|-----------|------------|----------|
| **Claude Sonnet 4** | 200k (1M) | $3/1M | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Claude Opus 4** | 200k (1M) | $15/1M | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Claude Haiku 4** | 200k | $0.25/1M | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| **GPT-4.1** | 1M+ | $2.50/1M | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **GPT-4o** | 128k | $2.50/1M | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **o1-preview** | 128k | $15/1M | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Gemini 2.5 Pro** | 2M | $1.25/1M | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Gemini Flash** | 1M | $0.075/1M | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |

### Speciality Features

| Feature | Claude | ChatGPT | Gemini | Perplexity | Copilot |
|---------|--------|---------|--------|------------|---------|
| **Velký kontext (1M+)** | ✅ (1M) | ✅ (1M+) | ✅ (2M) | ➖ | ➖ |
| **Web search** | ❌ | ✅ (limited) | ✅ | ✅✅✅ | ✅ |
| **Video/audio native** | ❌ | ❌ | ✅✅✅ | ❌ | ❌ |
| **Image generation** | ❌ | ✅ (DALL-E) | ✅ (Imagen) | ❌ | ✅ (Designer) |
| **Custom GPT/Skills** | ✅ (Skills) | ✅ (Custom GPTs) | ❌ | ❌ | ❌ |
| **API access** | ✅ | ✅ | ✅ | ❌ (limited) | ❌ (enterprise only) |
| **M365 integration** | ❌ | ❌ | ➖ (Workspace) | ❌ | ✅✅✅ |
| **Citations/sources** | ❌ | ➖ | ✅ (search) | ✅✅✅ | ✅ (search) |

### Ceny porovnání (na 1M input tokenů)

| Tier | Modely | Cena |
|------|--------|------|
| **Ultra-cheap** | Gemini Flash | $0.075 |
| **Cheap** | Claude Haiku | $0.25 |
| **Mid-range** | GPT-4.1, GPT-4o, Gemini Pro | $1.25-2.50 |
| **Standard** | Claude Sonnet | $3 |
| **Premium** | o1-preview, Claude Opus | $15 |

**Pro kontext:**
- 1,000 slov ≈ 1,300 tokenů
- Typický business document (10 stránek) ≈ 5,000 slov ≈ 6,500 tokenů
- **Gemini Flash:** $0.0005 per document
- **Claude Sonnet:** $0.02 per document
- **Claude Opus:** $0.10 per document

---

## 🌳 Decision Tree - Výběr modelu

```
START: Co je tvůj primární use case?
│
├─ RESEARCH s aktuálními daty
│  └─ Potřebuješ citace a zdroje?
│      ├─ Ano → ✅ PERPLEXITY
│      └─ Ne → Gemini Pro (má search) nebo ChatGPT
│
├─ DLOUHÁ ANALYTICKÁ PRÁCE
│  └─ Jak dlouhý je kontext?
│      ├─ Mega (50+ stránek, hodiny videa) → ✅ GEMINI 2.5 PRO
│      ├─ Velký (15-50 stránek) → ✅ CLAUDE SONNET 4 nebo GPT-4.1
│      └─ Střední → Jakýkoliv top model
│
├─ KÓDOVÁNÍ
│  └─ Komplexita?
│      ├─ Vysoká (architektura, refactoring) → ✅ CLAUDE SONNET 4
│      ├─ Střední → Claude nebo GPT-4.1
│      └─ Jednoduché scripty → Jakýkoliv včetně Haiku/Flash
│
├─ KOMPLEXNÍ REASONING (matematika, logika, strategie)
│  └─ ✅ ChatGPT O1-PREVIEW (best reasoning)
│  └─ Alternative: Claude Sonnet 4
│
├─ KREATIVNÍ PSANÍ
│  └─ ✅ CLAUDE SONNET 4 (nejnuancovanější)
│  └─ Alternative: GPT-4.1
│
├─ VIDEO/AUDIO ANALÝZA
│  └─ ✅ GEMINI 2.5 PRO (jediný native support)
│
├─ MICROSOFT EKOSYSTÉM (Word, Excel, Teams)
│  └─ ✅ MS COPILOT FOR M365
│
├─ VYSOKÝ VOLUME JEDNODUCHÝCH ÚKOLŮ
│  └─ Budget priority?
│      ├─ Ano → ✅ GEMINI FLASH (nejlevnější)
│      └─ Balanced → Claude Haiku nebo GPT-4o
│
└─ VŠEOBECNÉ / BALANCED
   └─ ✅ GPT-4.1 nebo CLAUDE SONNET 4
   └─ (Oba excelují na většině úkolů)
```

---

## 💡 Best Practices - Cross-Model

### 1. Testuj na více modelech pro kritické úkoly

Pro strategic decisions:
1. Zkus stejný prompt na Claude + GPT-4.1 + o1
2. Porovnej odpovědi
3. Syntetizuj best insights

Každý model má mírně jiný "úhel pohledu".

### 2. Optimalizuj cenu vs kvalitu

```
Workflow example:
1. Rapid prototyping → Gemini Flash (cheap, fast)
2. Refinement → Claude Sonnet (quality)
3. Final validation → Claude Opus nebo o1 (highest quality)
```

### 3. Používej správný model pro fázi projektu

```
Discovery phase → Perplexity (research)
Analysis phase → Claude Sonnet (depth)
Coding phase → Claude Sonnet (best coder)
Strategy phase → o1 (best reasoning)
Documentation → GPT-4.1 (balanced)
```

### 4. Model-specific prompts

**Nepoužívej** stejný prompt pro všechny modely. Optimalizuj:

- **Claude:** XML tagy, explicitní structure
- **o1:** Minimal prompting (má vlastní reasoning)
- **Gemini:** Agresivní length limits
- **Perplexity:** Explicit source requirements

### 5. Kombinuj modely v workflow

Není to "který model", ale "která kombinace".

**Příklad workflow:**
```
1. Perplexity: Research konkurence (sources)
2. Claude: Analýza + strategy (depth)
3. GPT-4.1: Create presentation (balanced output)
4. Copilot: Format in PowerPoint (M365 integration)
```

---

## 📈 Tracking vývoje

AI modely se vyvíjejí rychle. Tento dokument je aktuální k **listopadu 2025**.

**Kde sledovat updates:**
- [Anthropic changelog](https://docs.anthropic.com/en/docs/about-claude/changelog) - Claude updates
- [OpenAI blog](https://openai.com/blog) - GPT updates
- [Google AI blog](https://blog.google/technology/ai/) - Gemini updates
- [Simon Willison's blog](https://simonwillison.net/) - Excellent LLM coverage

**Očekávané trendy (2026):**
- Context windows 10M+ tokens
- Multi-modality standard (všechny modely)
- Specialized domain models (legal, medical, finance)
- Další pokles cen

---

## 🎓 Závěr

**Neexistuje "nejlepší model"** - existuje "nejlepší model pro TENTO úkol".

**Univerzální doporučení:**
- **Pro většinu úkolů:** Claude Sonnet 4 nebo GPT-4.1
- **Pro research:** Perplexity
- **Pro budget:** Gemini Flash
- **Pro reasoning:** o1
- **Pro M365:** Copilot

**Golden rule:**
Vyzkoušej několik modelů na tvém specifickém use case. Co funguje pro někoho jiného nemusí být best pro tebe.

---

**Verze:** 1.0 | **Datum:** Listopad 2025 | **Autor:** Expert na AI modely a prompt engineering
