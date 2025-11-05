# Práce s kontextem při práci s AI - Průvodce pro studenty

## Úvod

**Co se naučíš:** Po projití tohoto materiálu budeš rozumět tomu, jak funguje kontextové okno AI nástrojů, jak ho efektivně využít, a jak používat pokročilé nástroje (Custom GPT, Skills, MCP servery) pro opakované úkoly. Prakticky: budeš schopný/á lépe strukturovat práci s AI, vyhnout se častým problémům, a ušetřit čas.

**Proč je to užitečné:** Většina lidí používá AI jako "chytřejší Google" - ptají se, dostávají odpověď, a jdou dál. Když rozumíš kontextu, můžeš AI používat jako skutečného asistenta - poskytnout mu celý projekt najednou, udržet konzistenci napříč týdny, a naučit ho tvůj specifický způsob práce. To znamená rychlejší analýzu, kvalitnější výstupy, méně opakování.

**Předpoklady:** Základní zkušenost s alespoň jedním AI nástrojem (Claude, ChatGPT, nebo Gemini). Umíš napsat prompt, víš co je to konverzace. Není potřeba žádné programování.

**Časová náročnost:** Přečtení ~45 minut, procvičení 30-60 minut.

---

## Jak s tímto materiálem pracovat

1. **Nejdřív přečti:** Projdi celý materiál jednou rychle. Získej celkový přehled, nezastavuj se u detailů.
2. **Pak si zkus:** U každé části je praktický příklad - vyzkoušej ho ve svém AI nástroji.
3. **Nakonec procvič:** Na konci jsou cvičení - udělej aspoň 2 ze 3.
4. **A hlavně:** Netrap se teorií. Neptej se "proč přesně to funguje", ale "jak tohle můžu použít zítra v práci".

---

## Část 1: Co je kontextové okno a proč ti na tom záleží

### Co se dozvíš
Pochopíš základní koncept kontextového okna, jaké má velikosti u různých AI nástrojů, a co to prakticky znamená pro tvoji práci.

### Analogie z běžného života

Představ si AI jako člověka, se kterým mluvíš přes telefon. Má skvělou paměť - pamatuje si každé slovo, co řekneš. Ale jeho poznámkový blok má limit - vejde se tam jen určitý počet stránek.

Když mluvíš a mluvíš, postupně zaplňuješ jeho blok. Když se naplní úplně, začne vypadávat začátek konverzace. Už si nepamatuje, o čem jste mluvili na začátku.

**Kontextové okno = ten poznámkový blok.** Má konkrétní velikost (počet tokenů), a když se naplní, AI začne "zapomínat".

### Co to prakticky znamená

**Token** = zhruba 3/4 slova v angličtině, ~1/2 slova v češtině. Není důležité to přesně počítat - stačí vědět, že:

- Tvoje zprávy zabírají místo v kontextu
- AI odpovědi zabírají místo v kontextu
- Soubory, které nahraje

š, zabírají místo v kontextu
- Všechno dohromady musí být menší než limit

### Velikosti v roce 2025

Tady jsou aktuální čísla pro hlavní nástroje:

| Nástroj | Context Window | Prakticky |
|---------|----------------|-----------|
| **Claude Sonnet 4** | 1 milion tokenů | ~750,000 slov = 15-20 velkých business dokumentů |
| **Gemini 2.5 Pro** | 1-2 miliony tokenů | 1 hodina videa NEBO ~30-40 dokumentů |
| **GPT-4.1** (API) | 1,047,576 tokenů | ~750,000 slov podobně jako Claude |
| **GPT-4o** (běžný) | 128,000 tokenů | ~96,000 slov = 2-3 dokumenty |

**Důležité:** Čísla se rychle mění. V roce 2023 byl standard 8k-32k tokenů. V roce 2025 je to 1M-2M tokenů. Tady je několikanásobný nárůst - to fundamentálně mění co můžeš s AI dělat.

### Jednoduchý příklad

Řekněme, že analyzuješ requirements od 5 stakeholderů. Každý poslal dokument ~15 stránek (cca 7,500 slov = ~10,000 tokenů).

**Celkem:** 5 × 10,000 = 50,000 tokenů

**S GPT-4o (128k):** Vejde se + prostor na konverzaci ✅
**S GPT-3.5 (8k):** Nevejde se, musel bys dělit ❌

**S Claude/Gemini (1M+):** Vezme si to jako svačinku, vejde se ti tam ještě 10x tolik ✅✅✅

### Co se tu děje

Tahle čísla znamenají, že moderní AI nástroje můžou pracovat s **celým tvým projektem najednou**, ne jen s fragmenty. To je game changer pro business analytiky:

- Můžeš uploadnout celou projektovou dokumentaci
- Můžeš nahrát všechny user stories najednou
- Můžeš dát AI kompletní meeting notes z celého kvartálu

A AI to "vidí" všechno současně - zachytí vztahy, konflikty, patterns, které bys při fragmentovaném přístupu minul.

### Vyzkoušej si to

**Úkol:** Vezmi si dokument, se kterým běžně pracuješ (requirements doc, user stories, analýza). Podívej se kolik má stránek.

**Odhad:**
- 1 stránka A4 = ~500 slov = ~650 tokenů
- Tvůj dokument × 650 = kolik tokenů zabere

Vejde se do kontextu tvého AI nástroje? (Zkontroluj v tabulce výše)

**Bonus:** Zkus ten dokument uploadnout do Claude nebo ChatGPT a zeptej se: *"Kolik tokenů má tento dokument?"* Většinou ti to řeknou.

---

## Část 2: Jak kontext efektivně využívat

### Co se dozvíš
Praktické techniky, které ti pomůžou vytěžit maximum z kontextového okna - kdy vkládat soubory, kdy začít novou konverzaci, jak udržet konzistenci.

### Technika 1: File upload vs. Copy-paste

Často nevíš - mám ten dokument nahrát jako soubor, nebo zkopírovat text? Tady je jednoduchý decision tree.

**Použij FILE UPLOAD když:**
- Celý dokument je relevantní pro tvou otázku
- Je to standardní formát (DOCX, TXT, clean PDF)
- Nechceš risknout chyby při copy-paste (chybějící části, rozbité formátování)

**Použij COPY-PASTE když:**
- Potřebuješ jen určitou sekci (např. jen kapitola 3 z 50-stránkové knihy)
- Formát je problematický (PDF s tabulkami často neparsuje dobře)
- Chceš explicitně kontrolovat, co AI vidí
- Kombinuješ kousky z více dokumentů

**Příklad situace:**

Máš master requirements dokument (80 stránek). Potřebuješ se zeptat na specific feature, která je na stranách 45-48.

❌ **Špatně:** Nahrát celých 80 stránek, AI má najít relevantní část.
✅ **Dobře:** Copy-paste stran 45-48 + krátký kontext co to je.

**Proč:** Menší, focused kontext = lepší výkon, nižší náklady, rychlejší odpověď.

### Technika 2: Kdy začít novou konverzaci

Tohle je jedna z nejčastějších chyb - lidé pokračují v jedné konverzaci donekonečna, až AI začne produkovat nesmysly.

**Start novou konverzaci když:**

1. **Změnil se scope projektu** - přešel jsi z Feature A na Feature B, nejsou přímo spojené
2. **Přecházíš do nové fáze** - discovery → design → implementation
3. **Konverzace má >50 zpráv** a začíná být těžkopádná
4. **AI začíná "zapomínat"** - vrací se k věcem, které jste už vyřešili
5. **Tangential question** - potřebuješ se zeptat na něco úplně jiného

**Určitě NEDĚL:**
- Čekat až AI řekne "maximum length reached"
- Ignorovat signály, že kvalita klesá

**Pro tip - Transfer kontextu:**

Před začátkem nové konverzace:
```
"Shrň klíčové body naší diskuse, rozhodnutí, a requirements.
Optimalizuj to pro použití jako vstup do nové konverzace."
```

AI ti vytvoří kompaktní summary. Copy-paste to do nové konverzace jako kontext.

**Reálný příklad:**

Analyzuješ projekt 2 týdny. Máš konverzaci s 80+ zprávami. Discovery je hotová, jdeš do design fáze.

**Co udělat:**
1. Požádej AI o summary: klíčové requirements, stakeholder preferences, constrains
2. Start novou konverzaci
3. První zpráva: *"Kontxt: [paste summary]. Teď se chci zaměřit na high-level design pro tento feature..."*

**Výsledek:** Nový, čistý kontext s jen relevantními infos. AI má "fresh start" ale neztratilo se nic důležitého.

### Technika 3: Strategic Content Placement

Research ukázal zajímavou věc: AI má lepší "paměť" na **začátek** a **konec** kontextu (primacy & recency effect - stejně jako lidi).

**Prakticky to znamená:**

Nejdůležitější informace dej **na začátek promptu** nebo **na konec**.

**Příklad špatně:**
```
Mám tady 5 dokumentů s requirements.
[paste document 1 - 10 stránek]
[paste document 2 - 10 stránek]
[paste document 3 - 10 stránek]
[paste document 4 - 10 stránek]
[paste document 5 - 10 stránek]

Btw, nejdůležitější jsou security requirements a musí být compliant s GDPR.

Udělej mi analýzu.
```

**Příklad dobře:**
```
HLAVNÍ PRIORITA: Security a GDPR compliance. Tohle je kritické.

Kontxt: Analyzuješ requirements pro nový feature od 5 stakeholderů.
Focus: Security requirements a GDPR compliance gaps.

[paste document 1]
[paste document 2]
[paste document 3]
[paste document 4]
[paste document 5]

PŘIPOMENUTÍ: Hlavní focus je security a GDPR. Identifikuj gaps a rizika.
```

**Proč to funguje:** AI vidí prioritu hned na začátku (primacy) a je mu připomenuta na konci (recency). Středové dokumenty zpracuje, ale s jasným kontextem co je důležité.

### Technika 4: Information Distillation

"Distillation" zní fancy, ale je to jen: **vezmi dlouhý kontext, udělej z něj krátké shrnutí co zachová podstatu**.

**Kdy použít:**
- Po dlouhé analýze/diskusi potřebuješ kontext pro novou konverzaci
- Máš hodně informací, ale jen část je relevantní pro další krok
- Chceš snížit token consumption (= náklady)

**Jak na to:**
```
"Vytvoř kompaktní shrnutí [této analýzy/této diskuse/těchto dokumentů].
Zachovej všechny klíčové požadavky, rozhodnutí, a constrains.
Vynechej detaily, které nejsou kritické pro pokračování."
```

**Příklad:**

Po 2 hodinách brainstormingu s AI máš konverzaci plnou různých nápadů, dead-endů, a nakonec finální rozhodnutí.

**Před distillation:** 50 zpráv, 30,000 tokenů
**Po distillation:** Shrnutí 2,000 tokenů s jen finálními rozhodnutími

Tenhle summary pak použiješ v další fázi - nepřenášíš celou cestu, jen výsledek.

### Technika 5: Strukturuj své prompty

AI (stejně jako lidé) se líp orientuje ve strukturovaném obsahu.

**Místo:**
```
Tak mám tady projekt kde potřebujeme udělat analýzu requirements a je tam stakeholder A který chce X ale stakeholder B chce Y a ještě máme GDPR requirements a deadline je za měsíc a potřebuju vědět co je priorita...
```

**Udělej:**
```
# Projekt: [Název]

## Kontext
- Stakeholder A požaduje: X
- Stakeholder B požaduje: Y
- Constraints: GDPR compliance, deadline 1 měsíc

## Má otázka
Jaká je doporučená prioritizace těchto requirements?

## Očekávaný output
Seřazený seznam s reasoningem pro každou prioritu.
```

**Proč to funguje:**
- AI vidí jasnou strukturu (# headings)
- Informace jsou chunked do logických skupin
- Tvoje otázka je explicitní
- Víš co očekáváš → AI ví co deliver

### Vyzkoušej si to

**Úkol:** Vezmi si reálný use case ze své práce. Napiš prompt, který používá aspoň 3 z těchto technik:

1. Strategic placement (priorita na začátek a konec)
2. Struktura (headings, sekce)
3. Jasný expected output

Vyzkoušej to v AI nástroji a porovnej s tím, jak by sis zeptal "normálně".

---

## Část 3: Cost implications - co stojí velký kontext

### Co se dozvíš
AI služby nejsou zadarmo (nebo free tier má limity). Pochopíš kolik stojí práce s velkým kontextem a jak optimalizovat náklady.

### Jak funguje pricing

Většina AI služeb účtuje **per token** - platíš za input (co pošleš) i output (co AI vrátí).

**Claude pricing (ilustrativní, 2025):**
- **Do 200k tokenů:** $3 per million tokenů (input), $15 per million (output)
- **Nad 200k tokenů:** $6 per million (input) = **2x**, $22.50 per million (output) = **1.5x**

**Prakticky:**

Normální konverzace (5-10k tokenů celkem):
- Input: 5k tokenů × $3/1M = $0.015 = ~0.4 Kč
- Output: 5k tokenů × $15/1M = $0.075 = ~2 Kč
- **Celkem: ~2.5 Kč** - zanedbatelné

Large context (500k tokenů):
- Input: 500k tokenů × $6/1M = $3 = ~75 Kč (je to nad 200k, tak 2x cena)
- Output: 50k tokenů × $22.50/1M = $1.13 = ~28 Kč
- **Celkem: ~103 Kč per request**

Když to děláš 20x denně = 2,060 Kč denně = 40k+ Kč měsíčně.

### Kdy optimalizovat, kdy ne

**Neoptimalizuj zbytečně když:**
- Jednorázová analýza velkého projektu - zaplatíš pár set korun, ušetříš hodiny práce
- Business value je vyšší než cost - pokud ti to ušetří 2 hodiny (= tisíce Kč tvého času), 100 Kč za AI je steal

**Optimalizuj když:**
- Opakuješ stejný úkol často (10x+ denně)
- Posíláš stejné dokumenty dokola (používej caching nebo custom GPT)
- Většina kontextu není relevantní (pošli jen potřebnou část)

### Techniky pro snížení nákladů

1. **Context caching** - pokud používáš API, claude/openai mají caching. Stejný kontext poslaný podruhé stojí ~10% ceny.

2. **Custom GPT nebo Skill** - místo posílání 50k tokenů instrukcí při každém requestu, nastavíš to jednou. Fixní "cost" vs. per-token cost.

3. **Information distillation** - zmenši kontext na essentials před posláním.

4. **Batch processing** - místo 10 separate requestů s velkým kontextem, udělej 1 request s 10 otázkami.

### Vyzkoušej si to

**Úkol:** Odhadni cost tvého typického use case:

1. Kolik tokenů posíláš? (dokumenty + tvůj prompt)
2. Kolik tokenů dostáváš zpátky? (AI odpověď)
3. Jak často to děláš? (per den/týden)

Spočítej měsíční cost. Je to significant? Nebo je to "rounding error" v tvém tech budgetu?

**Kalkulačka:**
- Small use (<10k tokens): ~$0.10 = ~2.5 Kč per request
- Medium use (50k tokens): ~$0.50 = ~12 Kč per request
- Large use (500k tokens): ~$4 = ~100 Kč per request

---

## Část 4: Specializované nástroje pro opakované kontexty

### Co se dozvíš
Jak používat Custom GPT (ChatGPT), Claude Skills, a MCP servery pro opakované úkoly - nastavíš jednou, používáš stokrát.

### Nástroj 1: Custom GPT (ChatGPT)

**Co to je:** Tvoje vlastní verze ChatGPT s přednastavenými instrukcemi, knowledge base (dokumenty), a chováním.

**Kdy použít:**
- Opakuješ stejný typ úkolu často (generování user stories, analýza feedbacku)
- Máš firemní guidelines/template, které chceš aby AI vždycky používalo
- Chceš sdílet nástroj s kolegy

**Jak vytvořit (5-10 minut):**

1. Jdi na chat.openai.com → **Explore GPTs** → **Create**
2. Řekni GPT Builderu co chceš:
   ```
   "Chci vytvořit GPT který pomáhá business analytikům psát user stories
   podle našeho firemního templatu. Template je:

   As a [role]
   I want [feature]
   So that [benefit]

   Acceptance criteria:
   - [criterion 1]
   - [criterion 2]

   GPT by měl být friendly ale professional, ptát se na detaily když něco chybí."
   ```
3. GPT Builder ti položí pár upřesňujících otázek
4. Můžeš uploadnout knowledge files (firemní dokumenty, guidelines)
5. Otestuj Preview → **Save**

**Možnosti sdílení:**
- **Only me** - jen ty
- **Anyone with the link** - sdílíš link s týmem
- **Public** - publikuješ do GPT store

**Requires:** ChatGPT Plus ($20/měsíc) nebo Enterprise

**Praktický příklad - BA helper:**

Vytvoř si GPT:
- **Jméno:** "BA Requirements Analyzer"
- **Instrukce:** "Analyzuješ business requirements dokumenty. Hledáš gaps, konflikty mezi stakeholdery, a missing acceptance criteria. Vždy strukturuješ output jako tabulku."
- **Knowledge:** Nahraj svůj template pro requirements doc
- **Tone:** Professional ale přístupný

Teď každý týden uploadneš nové requirements → GPT je analyzuje podle stejného standardu.

### Nástroj 2: Claude Skills

**Co to je:** Reusable workflow - markdown soubor s YAML frontmatter. Když je situace relevantní, Claude automaticky aktivuje ten skill.

**Kdy použít:**
- Standardizované BA úkoly (quarterly reviews, retrospectives, feedback analysis)
- Chceš aby Claude "věděl" jak děláš specifickou věc
- Chceš sdílet workflow s týmem (skill = soubor, můžeš dát do repo)

**Jak vytvořit - conversational způsob (easiest):**

1. Claude → **Settings** → **Capabilities** → zapni **"skill-creator"**
2. Start novou konverzaci:
   ```
   "Chci vytvořit skill pro analýzu user stories. Skill by měl:
   - Zkontrolovat že každá story má role, feature, benefit
   - Najít chybějící acceptance criteria
   - Identifikovat ambiguous language
   - Output by měl být checklist co opravit"
   ```
3. Claude ti vytvoří skill markdown za 30 sekund
4. Save → skill je aktivní

**Jak vytvořit - manuální způsob:**

Vytvoř soubor `user-story-analyzer.md`:

```markdown
---
name: user-story-analyzer
description: Analyzuje user stories a identifikuje gaps a quality issues. Use when user asks to review user stories.
---

# User Story Analyzer

Když dostanu user stories, udělám:

1. **Format check:** Má každá story As a / I want / So that?
2. **Acceptance criteria:** Jsou jasná, testovatelná, kompletní?
3. **Ambiguous language:** Najdu vague terms (např. "user-friendly", "fast", "intuitive")
4. **Dependencies:** Identifikuji cross-story dependencies

## Output format

Pro každou story vrátím:
- ✅ nebo ❌ status
- List of issues (pokud nějaké jsou)
- Suggestions for improvement
```

Uložíš do `~/.claude/skills/` → Claude ho automaticky načte.

**Rozdíl Custom GPT vs. Skill:**

| Custom GPT | Claude Skill |
|------------|--------------|
| Pro ChatGPT | Pro Claude |
| Vyžaduje Plus ($20) | Free (s Claude accountem) |
| Má vlastní chat interface | Aktivuje se v běžné konverzaci |
| Můžeš publikovat do store | File-based, sharable přes git |

### Nástroj 3: MCP Servery (pokročilé)

**Co to je:** "USB-C port for AI" - standardizované rozhraní pro připojení Claude k externím nástrojům a datům.

**Kdy použít:**
- Potřebuješ real-time data z databáze nebo API
- Chceš aby Claude mohl číst/psát do firemních systémů (Jira, Notion, Linear)
- Statické dokumenty nestačí, potřebuješ live info

**Příklady ready-made MCP serverů:**
- **Filesystem** - Claude může číst/psát soubory na disku
- **GitHub** - Claude může číst issues, PRs, code
- **Postgres** - Claude může query databázi
- **Slack** - Claude může číst channels, posílat messages

**Jak začít (basic setup):**

1. Nainstaluj Claude Desktop
2. Nainstaluj MCP server (např. filesystem):
   ```bash
   npm install -g @modelcontextprotocol/server-filesystem
   ```
3. Konfigurace v `~/.claude/claude_desktop_config.json`:
   ```json
   {
     "mcpServers": {
       "filesystem": {
         "command": "npx",
         "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/your/projects"]
       }
     }
   }
   ```
4. Restart Claude Desktop

Teď můžeš říct: *"Přečti všechny .md soubory v mém projektu a vytvoř summary"* a Claude to udělá přímo přes MCP.

**Requires:**
- Claude Desktop (free)
- Basic tech skills (terminal, JSON config)
- Node.js pro většinu MCP serverů

**Je to pro tebe?**

MCP je skvělý když:
- ✅ Pravidelně pracuješ se stejnými zdroji dat
- ✅ Máš tech background nebo IT support
- ✅ Potřebuješ automatizaci beyond static documents

MCP NENÍ nutný když:
- ❌ Upload dokumentů ti stačí
- ❌ Není tech savvy a nechceš se učit terminal/JSON
- ❌ Používáš AI jen občas

### Vyzkoušej si to

**Úkol:** Vyber si jeden nástroj a zkus ho vytvořit:

**Varianta A - Custom GPT (pokud máš ChatGPT Plus):**
- Jdi na chatgpt.com/create
- Vytvoř GPT pro jeden opakující se úkol ze své práce
- Otestuj na reálném use case

**Varianta B - Claude Skill (pokud máš Claude):**
- Zapni skill-creator
- Řekni: "Chci vytvořit skill pro [tvůj use case]"
- Nech Claude ho vytvořit
- Zkus ho použít

**Varianta C - Průzkum (pokud žádné nemáš):**
- Najdi Custom GPT v GPT store relevantní pro BA práci
- Vyzkoušej ho (můžeš použít bez Plus accountu, jen nemůžeš tvořit vlastní)

---

## Část 5: Context Engineering - systémový přístup

### Co se dozvíš
Jak přemýšlet o kontextu systematicky, ne jen ad-hoc. Posun od "psát dobré dotazy" k "designovat informační workflow".

### Paradigma shift: Prompt → Context Engineering

**2022-2023: Éra Prompt Engineeringu**
- Focus: Jak napsat jeden dobrý dotaz
- Skillset: Wordsmithing, structure, examples
- Approach: Trial and error každý dotaz

**2024-2025: Éra Context Engineeringu**
- Focus: Jak navrhnout celý systém pro práci s AI
- Skillset: Information architecture, workflow design, tool selection
- Approach: Systematický design pro opakované použití

**Analogie:**
- **Prompt engineering** = Psát dobré emaily
- **Context engineering** = Navrhnout celý komunikační systém firmy

### Principy Context Engineeringu

**1. Treat context as finite resource**

Stejně jako máš jen 24 hodin denně, máš jen X tokenů v kontextu. Prioritizuj co tam patří.

**Ptej se:**
- Je tahle info critical pro úkol?
- Nebo jen "nice to have"?
- Můžu to poskytnout později když bude potřeba?

**2. Design for reuse**

Místo "how do I ask this specific question" → "how do I design system for this TYPE of questions"

**Příklad:**
- Špatně: Každý týden píšeš nový 500-word prompt pro týmový status report
- Dobře: Vytvoř Custom GPT/Skill jednou, každý týden jen uploadneš data

**3. Multi-session thinking**

Projekty trvají týdny/měsíce. Nebudeš mít jednu megakonverzaci - budeš mít series konverzací.

**Design workflow:**
- Discovery session → Summary
- Design session (s summary z discovery)
- Implementation session (s summary z design)
- Review session (s summary celého projektu)

Každá session = fresh context, ale se zděděným shrnutím.

**4. Information hierarchy**

Ne všechny informace jsou stejně důležité. Strukturuj accordingly:

```
CRITICAL (vždy na začátek):
- Main goal
- Hard constraints (budget, deadline, compliance)
- Key stakeholders

IMPORTANT (middle):
- Requirements details
- Background context
- Previous decisions

NICE-TO-HAVE (end nebo separate doc):
- Historical info
- Tangential research
- Future possibilities
```

### Pattern: Summarize-and-Continue

Tohle je jeden z nejužitečnějších patterns pro dlouhodobou práci.

**Scénář:** Pracuješ na projektu 3 týdny. Potřebuješ udržet konzistenci, ale konverzace jsou už moc dlouhé.

**Pattern:**

1. **Week 1:** Discovery - volná konverzace, explorace, brainstorming
   *Na konci:* "Shrň klíčové findings a decisions z této discovery fáze"

2. **Week 2:** Design - nová konverzace
   *Na začátku:* Paste summary z Week 1
   *Na konci:* "Shrň design decisions a rationale"

3. **Week 3:** Implementation - nová konverzace
   *Na začátku:* Paste summary z Week 1 + Week 2
   *Průběžně:* Pracuješ na implementation

**Výhoda:** Každá fáze má fresh, optimalizovaný kontext. AI "pamatuje" podstatné z předchozích fází bez drag nekonečně dlouhé konverzace.

### Pattern: Modular Context

Místo jednoho monolitického kontextu, rozděl na moduly.

**Příklad - Analýza velkého projektu:**

**Module 1: Project Context** (static, reusable)
```
Project: [Name]
Goal: [High-level goal]
Stakeholders: [List]
Constraints: [Budget, timeline, compliance]
```

**Module 2: Current Phase** (changes per phase)
```
Phase: Design
Focus: High-level architecture
Deliverable: Design document
```

**Module 3: Specific Task** (changes per conversation)
```
Today's task: Design database schema
Questions:
1. [Q1]
2. [Q2]
```

**Použití:**

Každou konverzaci začneš: Module 1 + Module 2 + Module 3 (relevant pieces)

Místo copy-paste 50 stránek pokaždé, copy-paste jen relevantní moduly.

### Vyzkoušej si to

**Úkol:** Vezmi si projekt, na kterém aktuálně pracuješ. Navrhni context engineering approach:

1. **Rozdel na fáze** - discovery, design, implementation, review?
2. **Pro každou fázi:** Co jsou critical infos? Co můžeš vypustit?
3. **Navrhni summarize points** - kde budeš dělat shrnutí pro další fázi?
4. **Zvol nástroj** - bude stačit běžná konverzace? Nebo chceš Custom GPT/Skill?

Nemusíš to implementovat hned - jen design workflow na papíře.

---

## Shrnutí a next steps

### Co teď umíš

✅ **Rozumíš kontextovému oknu** - co to je, jak funguje, jaké má velikosti
✅ **Umíš optimalizovat kontext** - kdy file upload, kdy copy-paste, kdy nová konverzace
✅ **Znáš cost implications** - kolik stojí velký kontext, kdy optimalizovat
✅ **Umíš použít specialized nástroje** - Custom GPT, Skills, MCP servery
✅ **Přemýšlíš systematicky** - context engineering, ne jen ad-hoc prompting

### Doporučené next steps

**1. Immediate (zítra):**
- Start novou konverzaci při phase transition (místo pokračování v dlouhém chatu)
- Před novou konverzací: požádej o shrnutí
- Strukturuj svoje prompty (headings, clear sections)

**2. Tento týden:**
- Vytvoř Custom GPT NEBO Skill pro jeden opakující se úkol
- Vyzkoušej information distillation na reálném projektu
- Experimentuj s strategic content placement

**3. Tento měsíc:**
- Navrhni context engineering workflow pro long-term projekt
- Sdílej Custom GPT/Skill s týmem, získej feedback
- Trackuj kolik času/peněz ti to ušetří

### Užitečné zdroje

**Oficiální dokumentace:**
- [Claude Context Windows Docs](https://docs.claude.com/en/docs/build-with-claude/context-windows)
- [ChatGPT Custom GPTs Guide](https://help.openai.com/en/articles/8554397-creating-a-gpt)
- [Claude Skills Documentation](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills)

**Practical guides:**
- [Context Engineering Guide](https://www.promptingguide.ai/guides/context-engineering-guide)
- [Effective Context Engineering - Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

**Komunity:**
- r/ClaudeAI - praktické tipy, use case sharing
- r/ChatGPTPro - pokročilé techniky pro ChatGPT
- OpenAI Developer Community - technical discussions

**Case studies:**
- JPMorgan: 35% redukce času na contract review s GPT-4.1 large context
- Alibaba: 22% rychlejší ticket resolution s kontextovou historií
- Stanford: 12 nových korelací díky analýze velkého datasetu najednou

---

## Máš otázku? Nevíš si rady?

**Časté problémy a řešení:**

**Q: AI "zapomíná" co jsme řešili na začátku konverzace**
A: Začni novou konverzaci, před tím požádej o shrnutí důležitých bodů.

**Q: Custom GPT mi nefunguje dobře, odpovídá jinak než chci**
A: Edit GPT → upřesni instrukce, přidej examples jak má odpovídat, otestuj v Preview.

**Q: Skill se neaktivuje automaticky**
A: Check že description jasně říká "use when...", zkus explicitně říct "použij skill X".

**Q: Nějako velké náklady, jak snížit?**
A: 1) Použij context caching, 2) Vytvoř Custom GPT/Skill místo opakovaného posílání instrukcí, 3) Information distillation - shrň místo posílání všeho.

**Q: Nevím jestli se mi to vejde do kontextu**
A: Jednoduše se zeptej AI: "Kolik tokenů má tento dokument?" nebo použij online estimator.

**Kde hledat pomoc:**
- Dokumentace každého nástroje (links výše)
- Reddit komunity (r/ClaudeAI, r/ChatGPTPro)
- Tvůj IT tým (obzvlášť pro MCP setup)

---

*Studijní materiály vytvořeny 2025-11-05 | Pro business analytiky, mírně pokročilé s AI*
