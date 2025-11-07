# Práce s kontextem AI - Cheat Sheet

## Hlavní myšlenky (co si odnést)

- **Kontextové okno = pracovní paměť AI.** Všechno, co AI "vidí" a pamatuje si během konverzace. Když se naplní, AI začíná zapomínat.

- **Velikosti se dramaticky zvýšily (2025).** Claude 1M tokenů (~750k slov), Gemini 2M tokenů, GPT-4.1 1M+ tokenů. Vejde se ti tam celý projekt najednou.

- **Větší kontext = vyšší náklady.** Claude účtuje 2x za inputs nad 200k tokenů. Optimalizace není jen o výkonu, ale i penězích.

- **Context engineering nahradil prompt engineering.** Nejde už jen o "jak napsat dobrý dotaz", ale "jak navrhnout celý informační tok" pro práci s AI.

- **Specializované nástroje šetří čas.** Custom GPT, Claude Skills, MCP servery - naučíš AI svůj kontext jednou, používáš opakovaně.

## Rychlý přehled

### Co je kontextové okno
**Co to je:** Počet tokenů (slov/znaků), které AI zpracuje najednou. Představ si to jako "paměť RAM" pro AI - má limit.

**Proč je to důležité:** Když překročíš limit, AI zapomíná začátek konverzace. Výstupy jsou horší, ztrácíš konzistenci.

**Kolik se vejde:**
- Claude (1M tokenů) = ~15-20 velkých business dokumentů
- Gemini (2M tokenů) = ~30-40 dokumentů NEBO 1 hodina videa
- GPT-4.1 (1M+ tokenů) = podobně jako Claude

### Kdy začít novou konverzaci

✅ **Start fresh když:**
- Změnil se scope projektu
- Přecházíš do nové fáze (discovery → design → implementace)
- Konverzace má >50 zpráv a AI začíná "zapomínat"
- Tangential question mimo current topic

❌ **NEPOKRAČUJ donekonečna:**
- Nečekej na "maximum length reached"
- Kvalita klesá dávno před hard limitem

**Pro tip:** Před novou konverzací požádej o shrnutí: *"Shrň klíčové body naší diskuse optimalizované pro start nové konverzace"*

### File upload vs. Copy-paste

**Použij FILE UPLOAD když:**
- ✅ Celý dokument je relevantní
- ✅ Standard format (DOCX, TXT, clean PDF)
- ✅ Chceš minimalizovat chyby z copy-paste
- ✅ Dokument < context window limit

**Použij COPY-PASTE když:**
- ✅ Potřebuješ jen specific sekci
- ✅ Format je problematický (PDF s tabulkami)
- ✅ Chceš explicit kontrolu co AI vidí
- ✅ Kombinuješ obsah z více zdrojů

### Velikosti podle nástrojů

| Nástroj | Context Window | Co se vejde |
|---------|----------------|-------------|
| **Claude Sonnet 4** | 1M tokenů | 750k slov / 75k řádků kódu |
| **Gemini 2.5 Pro** | 1-2M tokenů | 1 hod videa / 11 hod audia |
| **GPT-4.1** | 1M+ tokenů | ~750k slov |
| **GPT-4o** | 128k tokenů | ~96k slov |

💡 **Prakticky:** 1 velký business requirements dokument = ~20-50k tokenů. S 1M kontextem máš prostor pro 15-20 takových dokumentů najednou.

## Užitečné tipy a triky

- **Strategic content placement:** Nejdůležitější info dej na začátek NEBO konec promptu. AI má lepší "paměť" pro primacy/recency effect.

- **Information distillation:** Po dlouhé analýze: *"Vytvoř kompaktní shrnutí, které zachová všechny klíčové požadavky a rozhodnutí"* - pak to použij v novém chatu.

- **Context caching (pro API):** Pokud používáš stejný dokument opakovaně (např. company guidelines), využij caching - ušetříš peníze i latenci.

- **Modularizace:** Místo jednoho 100-stránkového dokumentu pošli strukturované sekce s jasnými headingy. AI se lépe orientuje.

- **Práce s týmem:** Custom GPT nebo Skill můžeš sdílet s kolegy - každý má stejný kontext, nikdo nemusí znovu vysvětlovat.

## Praktický příklad - BA use case

**Situace:** Analyzuješ requirements pro nový feature z 5 stakeholderů. Každý poslal vlastní dokument (celkem 80 stránek). Potřebuješ identifikovat conflicts a gaps.

**Postup:**
1. Nahraj všech 5 dokumentů do Claude/Gemini (vejde se do 1M kontextu)
2. Prompt:
   ```
   Analyzuj tyto requirements dokumenty:

   HLAVNÍ CÍL: Identifikuj konflikty mezi stakeholdery a chybějící requirements.

   Pro každý conflict uveď:
   - Kdo vs. kdo (stakeholder names)
   - Co se liší (specifics)
   - Business impact

   Pro každý gap:
   - Co chybí
   - Proč to může být problém

   Formát: strukturovaná tabulka
   ```

3. Po analýze požádej o shrnutí a start novou konverzaci pro design phase

**Proč to funguje:** Large context vidí všechny dokumenty najednou → zachytí vztahy a konflikty, které bys při fragmentovaném přístupu minul.

## Nejčastější chyby a jak je řešit

| Problém | Řešení |
|---------|--------|
| **Waiting for hard limit** - Pokračuješ v konverzaci až AI řekne "maximum length reached" | Proaktivně začni novou konverzaci při phase transitions. Kvalita klesá dávno před hard limitem. |
| **Dumping všeho najednou** - Nahrál jsi 50 dokumentů s myšlenkou "víc = líp" | Větší kontext ≠ lepší výsledek. Vyber jen relevantní obsah. Irelevantní info ruší + zbytečně platíš. |
| **Nestructured chaos** - Posíláš nestrukturovaný text bez sekcí/headerů | Používej headings, bullet points, clear sections. AI (i lidé) se v tom lépe orientují. |
| **Zapomenuté summarize** - Začal jsi nový chat bez přenosu kontextu | Před novou konverzací: "Shrň klíčové body pro start nové konverzace" → copy do nového chatu. |
| **Cost ignorance** - Nesleduješ kolik stojí large contexts | Check pricing: Claude 2x cena nad 200k tokenů. Optimalizuj když můžeš, ale ne na úkor kvality. |

## Cost implications (důležité vědět!)

**Claude pricing (ilustrativní):**
- Do 200k tokenů: $3 per million (input), $15 per million (output)
- Nad 200k tokenů: $6 per million (input - 2x), $22.50 per million (output - 1.5x)

**Prakticky:**
- Běžná práce (5-10k tokenů): zanedbatelné náklady
- Large context (500k+ tokenů): sleduj usage, optimalizuj kde má smysl
- Context caching může ušetřit 90% costs pro opakované dokumenty

💡 **Rule of thumb:** Pokud pravidelně posíláš stejný kontext (guidelines, templates), zvaž Custom GPT nebo Skill - stojí to fixně, ne per-token.

## Specializované nástroje

### Custom GPT (ChatGPT)
**Co to je:** Tvoje vlastní verze ChatGPT s přednastavenými instrukcemi a knowledge base.

**Kdy použít:** Opakované úkoly (generování user stories v konkrétním formátu, analýza podle firemních standardů).

**Jak začít:** ChatGPT → Explore GPTs → Create. Řekni co chceš, GPT builder to vytvoří za tebe. 5-10 minut.

**Requires:** ChatGPT Plus ($20/měsíc)

### Claude Skills
**Co to je:** Reusable workflows - markdown soubor s instrukcemi, které se aktivují když je relevantní.

**Kdy použít:** Standardizované BA úkoly (quarterly reviews, feedback analysis, requirements template).

**Jak začít:** Claude → Settings → Capabilities → skill-creator ON. Pak řekni: *"Chci vytvořit skill pro analýzu user stories"*.

**Requires:** Claude account (free tier OK)

### MCP Servery (pokročilé)
**Co to je:** "USB-C port for AI" - připojíš Claude k externím nástrojům/databázím (Jira, Notion, your database).

**Kdy použít:** Potřebuješ real-time data z externích systémů, ne jen static dokumenty.

**Jak začít:** [7 Claude MCP servers](https://zapier.com/blog/claude-mcp-servers/) - ready-made servery, můžeš nastavit za 15-30 min.

**Requires:** Claude Desktop, basic tech skills (JSON config)

## Decision Trees

### Kdy použít který nástroj?

```
Opakuješ stejný typ úkolu často?
├─ Ano → Custom GPT nebo Skill
│   ├─ Používáš ChatGPT? → Custom GPT
│   └─ Používáš Claude? → Skill
│
└─ Ne → Běžná konverzace s file upload
    ├─ Potřebuješ external data? → MCP server
    └─ Stačí dokumenty? → Upload files
```

### Jak strukturovat velký projekt?

```
Projekt je dlouhodobý (týdny/měsíce)?
├─ Ano → Rozdel na fáze, každá = nová konverzace
│   ├─ Discovery konverzace → Summarize
│   ├─ Design konverzace (start se summary)
│   └─ Implementation (start se summary)
│
└─ Ne → Jedna konverzace stačí
    ├─ Sleduj délku (>50 messages? consider new)
    └─ Watch for "zapomínání" (AI ztrácí začátek)
```

## Kam dál

**Oficiální dokumentace:**
- [Claude Context Windows Docs](https://docs.claude.com/en/docs/build-with-claude/context-windows)
- [ChatGPT Custom GPTs Guide](https://help.openai.com/en/articles/8554397-creating-a-gpt)
- [Gemini Long Context](https://ai.google.dev/gemini-api/docs/long-context)

**Praktické guides:**
- [Context Engineering Guide](https://www.promptingguide.ai/guides/context-engineering-guide)
- [Effective Context Engineering - Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

**Case studies:**
- JPMorgan: 35% redukce času na contract review s GPT-4.1
- Alibaba: 22% rychlejší ticket resolution s large context
- Stanford: 12 nových korelací objevených díky large context analysis

**Komunity:**
- r/ClaudeAI - praktické tipy a use cases
- r/ChatGPTPro - pokročilé techniky, custom GPT sharing

---

💡 **Quick wins pro zítra:**
1. Start nové konverzace při phase transition (místo pokračování v nekonečně dlouhém chatu)
2. Před novou konverzací: "Shrň klíčové body pro start nové konverzace"
3. Zkus si vytvořit Custom GPT nebo Skill pro jeden opakující se úkol (10 minut investice)
4. Strukturuj své prompty (headings, clear sections)

---

*Cheat sheet vytvořen 2025-11-05 | Aktuální pro Claude Sonnet 4, ChatGPT GPT-4.1, Gemini 2.5*
