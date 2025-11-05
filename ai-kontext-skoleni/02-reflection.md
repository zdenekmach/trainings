# Reflection on Training Outline: Práce s kontextem při práci s AI

**Datum:** 2025-11-05
**Status:** Ready for review

---

## Přehled

Tento dokument porovnává původní osnovu školení (z requirements document) s insights z research reportu a navrhuje konkrétní vylepšení.

---

## Confirmed Strengths - Co je v osnově dobře

### ✅ Struktura 4 modulů

Původní struktura 4 modulů (Základy → Optimalizace → Pokročilé nástroje → Context Engineering) **je správná a potvrzená researchem**:

1. **Modul 1: Co je kontextové okno** - Research potvrdil důležitost základů. Mnoho BA nerozumí konceptu kontextového okna, takže start odtud dává smysl.

2. **Modul 2: Efektivní využití** - Research ukázal spoustu praktických technik (caching, distillation, placement), které přesně zapadají do tohoto modulu.

3. **Modul 3: Pokročilé nástroje** - Research potvrdil relevanci Custom GPTs, MCP, Skills. Všechny tři nástroje jsou aktuální a používané.

4. **Modul 4: Context Engineering** - Research dokonce ukázal, že context engineering je nový industry trend, takže dedicated modul je very timely.

### ✅ Praktický focus

Osnova má 50% času na praktická cvičení - **research case studies potvrdily, že hands-on je klíčové**. JPMorgan, Alibaba case studies všechny ukazují practical application.

### ✅ Časový rozsah

90-120 minut pro workshop formát je **realistické** - research ukázal, že basic custom GPT se dá vytvořit za 5-10 min, skill za 10-15 min, takže je čas na hands-on i teorii.

### ✅ Cílová skupina

Business analytici, mírně pokročilí je **správný target** - research case studies (contract review, customer support) jsou všechny relevantní pro BA workflows.

---

## Suggested Additions - Co přidat na základě researche

### 🆕 Addition 1: Aktualizované číslačontextových oken

**Co přidat:** Aktuální čísla pro rok 2025 do Modulu 1

**Důvod:** Research odhalil dramatické změny:
- Claude: ~~200k~~ → **1M tokenů** (5x zvýšení v roce 2025)
- Gemini: ~~1M~~ → **2M tokenů** u Gemini 1.5 Pro
- GPT-4.1: **1,047,576 tokenů** (vs. GPT-4o 128k)

**Praktický dopad:** Tato čísla mění co je možné - např. 1M tokenů = 750k slov = asi 15-20 velkých business requirement dokumentů najednou.

**Kde v osnově:** Modul 1, sekce "Velikosti kontextových oken"

**Jak implementovat:** Update slide s comparison table + praktická ukázka "co se vejde"

---

### 🆕 Addition 2: Cost implications velkých kontextů

**Co přidat:** Nová sub-sekce v Modulu 2 o pricing considerations

**Důvod:** Research ukázal, že:
- Claude: inputs nad 200k tokenů stojí **2x víc** ($6/M vs. $3/M)
- Outputs: **1.5x** ($22.50/M vs. $15/M)
- Long context queries = vyšší computational cost

**Praktický dopad:** BA můžou nechtěně generovat vyšší náklady. Potřebují vědět kdy optimalizovat.

**Kde v osnově:** Modul 2, nová subsekce "Cost vs. Capability"

**Jak implementovat:**
- Quick slide s pricing tiers
- Rule of thumb: "Když potřebuješ nad 200k tokenů, zvaž jestli nemůžeš kontext zredukovat"
- Není to dealbreaker, ale awareness

---

### 🆕 Addition 3: Paradigma shift: Prompt → Context Engineering

**Co přidat:** Opening konceptu v Modulu 4

**Důvod:** Research ukázal industry-wide shift:
> "Context engineering is the new currency in AI. We've moved from finding the right words for prompts to designing the right configuration of context."

**Praktický dopad:** BA potřebují pochopit, že už nejde jen o "jak napsat dobrý dotaz", ale "jak navrhnout celý informační tok".

**Kde v osnově:** Modul 4, intro slide

**Jak implementovat:**
- Timeline slide: 2022-23 = Prompt Engineering era → 2024-25 = Context Engineering era
- Analogie: "Prompt engineering = psát dobré emaily. Context engineering = navrhnout celý email workflow."

---

### 🆕 Addition 4: Real-world case studies s konkrétními čísly

**Co přidat:** 2-3 mini case studies distributed across modulés

**Důvod:** Research našel strong case studies s measurable results:
- JPMorgan: **35% redukce času** na contract review (GPT-4.1)
- Alibaba: **22% faster** ticket resolution (Deepseek v3)
- Stanford: **12 nových korelací** objevených díky large context

**Praktický dopad:** Konkrétní čísla rezonují s BA audience, ukazují ROI.

**Kde v osnově:**
- JPMorgan case → Modul 2 (optimalizace pro dlouhé dokumenty)
- Alibaba case → Modul 2 (context pro customer history)
- Stanford case → Modul 1 (proč velký kontext matters)

**Jak implementovat:** 1 slide per case study, format: Challenge → Solution → Results (s čísly)

---

### 🆕 Addition 5: Conversational Skill Creation

**Co přidat:** Demo conversational vytvoření Claude Skill v Modulu 3

**Důvod:** Research ukázal super easy metodu:
1. Zapnout "skill-creator" skill
2. Říct "I want to create a skill for [use case]"
3. Claude vytvoří skill za tebe

**Praktický dopad:** Eliminuje barrier to entry - BA nemusí rozumět YAML, markdown syntax. Můžou vytvořit skill konverzačně za 5 minut.

**Kde v osnově:** Modul 3, Claude Skills sekce

**Jak implementovat:**
- Live demo: "Vytvořme skill pro analýzu user stories"
- Hands-on: každý si vytvoří vlastní skill konverzačně
- Bonus: ukázat jak pak editovat .md file manuálně (pro advanced)

---

### 🆕 Addition 6: When to start new conversation - decision tree

**Co přidat:** Praktický decision tree do Modulu 2

**Důvod:** Research identifikoval častý pain point a best practices:
- Keep conversations focused na 1 topic
- Start fresh při phase transitions (discovery → implementation)
- Summarize before hitting limit

**Praktický dopad:** BA často neví "kdy už je moc", decision tree poskytne jasná kritéria.

**Kde v osnově:** Modul 2, sekce "Jak strukturovat dlouhé konverzace"

**Jak implementovat:**
```
Decision tree:
1. Změnil se scope projektu? → New conversation
2. Přecházíš do nové fáze? (discovery → design) → New conversation
3. Konverzace >50 zpráv? → Consider summarize + new
4. AI začíná "zapomínat" začátek? → Summarize + new
5. Tangential question mimo current topic? → New conversation
```

---

## Suggested Updates - Změny stávajícího obsahu

### 🔄 Update 1: Modul 3 - Rebalance času mezi nástroji

**Co změnit:**
- **Custom GPTs**: ~~10 min~~ → **15 min** (včetně hands-on)
- **MCP servery**: ~~10 min~~ → **7 min** (demo only, ne hands-on)
- **Claude Skills**: ~~10 min~~ → **13 min** (hands-on s conversational creation)

**Proč:**
- Research ukázal, že Custom GPTs jsou easiest entry point - zaslouží víc času
- MCP je complex, research potvrdil že setup není trivial - lepší demo než hands-on frustration
- Skills s conversational creation jsou fast - ale potřeba času na hands-on

**Dopad na osnovu:** Přerozdělení 30 min v modulu 3, celková doba stejná

---

### 🔄 Update 2: Modul 1 - Praktická vizualizace "co se vejde"

**Co změnit:** Místo abstract "200k tokenů" ukázat konkrétní příklady

**Proč:** Research poskytl great analogie:
- 1M tokenů = 750k slov = 75k řádků kódu = **15-20 velkých business dokumentů**
- 2M tokenů (Gemini) = 11 hodin audia, 1 hodina videa, 30k řádků kódu

**Jak:** Vytvořit vizuální slide:
```
Claude (1M tokenů) =
📄📄📄 x 15-20 velkých business docs
📝 750,000 slov
💻 75,000 řádků kódu

Gemini (2M tokenů) =
🎥 1 hodina videa
🎧 11 hodin audia
📄 x 30-40 dokumentů
```

**Dopad:** Audience okamžitě pochopí scale - "ah, takže celý náš project backlog se vejde"

---

### 🔄 Update 3: Modul 2 - Přidat Context Engineering techniky

**Co změnit:** Rozšířit "best practices" o specific techniky z researche

**Nové techniky:**
1. **Information Distillation** - komprese dlouhého kontextu do shrnutí
2. **Strategic Content Placement** - důležité info na začátek/konec (primacy/recency effect)
3. **Context Caching** - znovupoužití stejného kontextu (náklady, latence)
4. **Modularizace** - breaking dlouhých dokumentů na focused segments

**Proč:** Research ukázal, že toto jsou industry-standard techniky v roce 2025

**Jak implementovat:**
- Každá technika = 1 slide (co to je, proč funguje, příklad)
- Hands-on cvičení: aplikovat 2-3 techniky na sample BA scenario

**Dopad:** +5 min v modulu 2, ale dramaticky zvýší practical value

---

### 🔄 Update 4: Modul 4 - Shift focus od "prompts" k "systems"

**Co změnit:** Reframe modulu z "jak psát dobré prompty" na "jak designovat workflows"

**Proč:** Research clearly ukázal shift v industry:
- Prompt engineering (2022-23): Focus na wording, structure jednoho promptu
- Context engineering (2024-25): Design celých systems pro information flow

**Nový focus:**
- RAG concept (retrieval-augmented generation) - ne implementation, ale awareness
- Summarize-and-continue pattern
- Multi-session workflows (jak udržet konzistenci napříč sessions)
- Information hierarchy (co do kontextu kdy)

**Dopad:** Modul bude více forward-looking, připraví BA na future

---

### 🔄 Update 5: Modul 2 - File upload vs. Copy-paste decision criteria

**Co změnit:** Přidat explicitní decision tree místo vague guidance

**Nový obsah:**
```
Use FILE UPLOAD when:
✅ Whole document je relevantní
✅ Standard format (DOCX, TXT, PDF text)
✅ Chceš minimalizovat human error
✅ Document je < context window limit

Use COPY-PASTE when:
✅ Potřebuješ jen specific section
✅ Format je problematic (PDF s tabulkami/columns)
✅ Chceš explicit control co AI vidí
✅ Combining content z multiple sources
```

**Proč:** Research ukázal, že toto je frequent decision point a confusion source

**Dopad:** Clear criteria eliminují guessing, BA budou confidence v decisions

---

## Optional Enhancements - Nice-to-have pokud čas dovolí

### ⚡ Enhancement 1: Gemini multi-modal demo (video analysis)

**Co:** Quick demo Gemini analyzující business requirements video

**Pros:** Wow factor, ukazuje future direction, relevant pro BA (user interviews, stakeholder meetings)

**Cons:** Niche use case, může vzít 5-10 min setup

**Doporučení:** Bonus slide na konci, "future capabilities", ne hands-on

---

### ⚡ Enhancement 2: Context compression techniques (advanced)

**Co:** Zmínka RAG, embeddings, automated summarization

**Pros:** Forward-thinking, může zajímat advanced účastníky

**Cons:** Většina BA nepracuje na API level, může být moc technical

**Doporučení:** Optional advanced slide, "for those interested"

---

### ⚡ Enhancement 3: Team collaboration patterns

**Co:** Jak sdílet kontext v týmu (shared custom GPTs, skill files v repo)

**Pros:** Praktické pro týmy BA

**Cons:** Vyžaduje org buy-in, možná mimo scope individual workshop

**Doporučení:** Zmínit v závěru jako "next step after workshop"

---

## Doporučené akce - Summary

### Must-have změny (high priority):

1. ✅ **Aktualizovat čísla kontextových oken** (Claude 1M, Gemini 2M, GPT-4.1 1M+)
   - Impact: High - fundamental data
   - Effort: Low - just update slides
   - Where: Modul 1

2. ✅ **Přidat cost implications sekci**
   - Impact: High - business audience cares about $
   - Effort: Low - 1 slide
   - Where: Modul 2

3. ✅ **Přidat case studies s ROI čísly**
   - Impact: High - credibility, motivation
   - Effort: Medium - 3 mini case study slides
   - Where: Moduly 1 & 2

4. ✅ **Rebalance Modul 3** (více Custom GPTs, méně MCP, conversational Skills)
   - Impact: High - user experience, success rate
   - Effort: Medium - restructure timing
   - Where: Modul 3

5. ✅ **Decision tree for new conversations**
   - Impact: High - addresses common pain point
   - Effort: Low - 1 visual slide
   - Where: Modul 2

### Should-have změny (medium priority):

6. ⚡ **Context engineering paradigm shift intro**
   - Impact: Medium - conceptual framing
   - Effort: Low - 1 intro slide
   - Where: Modul 4

7. ⚡ **Practical "co se vejde" vizualizace**
   - Impact: Medium - better understanding
   - Effort: Low - visual slide design
   - Where: Modul 1

8. ⚡ **Context engineering techniky** (distillation, placement, caching)
   - Impact: Medium - concrete techniques
   - Effort: Medium - 4-5 technique slides + mini exercise
   - Where: Modul 2

### Nice-to-have změny (low priority):

9. 💡 **File upload vs copy-paste decision criteria**
   - Impact: Low-Medium - helpful but not critical
   - Effort: Low - 1 slide
   - Where: Modul 2

10. 💡 **Gemini multi-modal demo**
    - Impact: Low - wow factor, but niche
    - Effort: High - demo setup
    - Where: Bonus/end

---

## Time Impact Analysis

**Původní osnova:** 90-120 min

**S must-have změnami:**
- Modul 1: 20 min → **25 min** (+5: aktualizované čísla + vizualizace + case study)
- Modul 2: 25 min → **30 min** (+5: cost, case study, decision trees, techniques)
- Modul 3: 30 min → **30 min** (rebalanced, ale stejný celkový čas)
- Modul 4: 20 min → **22 min** (+2: paradigm shift intro)
- Q&A: 10-15 min → **10-15 min** (same)

**Nový celkový čas:** 105-132 min

**Doporučení:**
- Target **120 min** (2 hodiny) - fits requirement "1-2 hodiny"
- Pokud potřeba zkrátit:
  - Q&A flexibilní (můžeme skončit at 110 min pokud málo dotazů)
  - MCP demo může být ultra-quick (5 min místo 7)
  - Optional enhancements skip

---

## Final Recommendation

**Doporučuji implementovat všech 5 must-have změn:**

1. Aktualizovaná čísla kontextů
2. Cost implications
3. Case studies s ROI
4. Rebalance modulu 3
5. Decision tree pro nové konverzace

**Plus 3 should-have změny pokud lze fit do 120 min:**

6. Context engineering paradigm shift
7. "Co se vejde" vizualizace
8. Context engineering techniky

**Toto dává:**
- ✅ Aktuální, accurate informace (2025 data)
- ✅ Praktický, actionable content (decision trees, techniques)
- ✅ Relevantní pro business audience (costs, ROI, case studies)
- ✅ Balance beginner-friendly a forward-thinking (paradigm shift)
- ✅ Realistic time frame (120 min)

---

## Next Step

Prosím potvrď, jestli souhlasíš s těmito změnami, nebo máš jiné priority. Pak přejdeme k výběru výstupních materiálů (cheat sheet, presentation, exercises, guidelines).

---

**Status:** ✅ Ready for review
