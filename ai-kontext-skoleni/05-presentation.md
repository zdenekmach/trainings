# Práce s kontextem při práci s AI - Prezentace

## Struktura prezentace

**Celková doba:** 120 minut (2 hodiny)
**Počet slidů:** ~35 slidů
**Formát:** Workshop s hands-on cvičeními
**Audience:** Business analytici, mírně pokročilí s AI

---

## Slide 1: Úvodní slide

### Obsah slidu
```
Práce s kontextem při práci s AI
Jak na kontextové okno, optimalizaci, a pokročilé nástroje

Workshop pro business analytiky
[Tvoje jméno]
[Datum]
```

### Poznámky pro lektora
- **Timing:** 3 min
- **Tone:** Přátelský, nadšený, energický
- **Co říct:**
  - "Ahoj! Jsem [jméno] a dalších 2 hodiny strávíme společně s tématem, které dramaticky změní jak pracujete s AI."
  - "Kolik z vás používá Claude, ChatGPT, nebo Gemini pravidelně v práci? Dejte ruce nahoru."
  - "Skvělé. A kolik z vás někdy zažilo, že AI 'zapomene' co jste říkali na začátku dlouhé konverzace? *[typicky všichni]*"
  - "Přesně o tom je dnešní workshop - jak tomu rozumět a jak to vyřešit."

- **Pro interakci:** Zjisti kdo používá jaký nástroj (Claude/ChatGPT/Gemini) - pomůže ti tailorovat příklady

---

## Slide 2: Co tě dnes čeká

### Obsah slidu
```
Dnes se naučíš:

✓ Co je kontextové okno a jak funguje
✓ Optimalizovat využití kontextu (kdy file vs. text, kdy nová konverzace)
✓ Používat pokročilé nástroje (Custom GPT, Skills, MCP servery)
✓ Context engineering pro long-term projekty

Bonus: Real-world case studies s konkrétními ROI čísly
```

### Poznámky pro lektora
- **Timing:** 2 min
- **Klíčový message:** Konkrétní skills, ne teoretické kecy
- **Co říct:**
  - "Konec dnešního workshopu budete umět pracovat s AI systematicky, ne jen ad-hoc."
  - "Uvidíte case studies - třeba JPMorgan ušetřil 35% času na contract review. Podobné výsledky můžete mít vy."
  - "A hlavně - všechno si vyzkoušíte. Půlka času je hands-on cvičení."

- **Pro interakci:** "Máte nějaké konkrétní očekávání? Co byste rádi uměli na konci?"

- **Varování:** Nepoužívat slova jako "revolutionize", "game-changing" - držet se faktů

---

## MODUL 1: Co je kontextové okno (25 min)

## Slide 3: Co je kontextové okno - analogie

### Obsah slidu
```
Kontextové okno = "poznámkový blok" AI

[Vizuál: Notebook s omezeným počtem stránek]

AI si pamatuje všechno... co se vejde do bloku.
Když se naplní → začátek vypadává.
```

### Poznámky pro lektora
- **Timing:** 4 min
- **Struktura:**
  1. Analogie (1 min)
  2. Co to prakticky znamená (2 min)
  3. Ukázka problému (1 min)

- **Co říct:**
  - "Představte si AI jako člověka, se kterým mluvíte přes telefon. Má skvělou paměť - pamatuje si každé slovo."
  - "Ale jeho poznámkový blok má limit. Když se zaplní, vypadává začátek konverzace."
  - "Kontextové okno = ten poznámkový blok. Má konkrétní velikost v 'tokenech'."

- **Live demo:** Ukázat dlouhou konverzaci kde AI začne zapomínat začátek (připravit předem)

- **Pro interakci:**
  - "Kdo z vás zažil, že AI začne ignorovat něco, co jste řekli na začátku? *[většina]*"
  - "Přesně. To je naplněný kontext."

---

## Slide 4: Co je token (quickly)

### Obsah slidu
```
Token ≈ 3/4 slova (anglicky), ~1/2 slova (česky)

Nemusíš to přesně počítat!

Stačí vědět:
📝 Tvoje zprávy = tokeny
🤖 AI odpovědi = tokeny
📄 Soubory = tokeny

Všechno dohromady < limit kontextu
```

### Poznámky pro lektora
- **Timing:** 2 min
- **Key message:** Don't overthink it, jen obecné povědomí

- **Co říct:**
  - "Token je technická jednotka. Nemusíte to řešit do detailu."
  - "Zhruba: 1 stránka A4 = ~650 tokenů. To vám bude stačit pro odhady."
  - "Důležité je pochopit princip: všechno co posíláš, zabírá místo."

- **Pozor na:** Nelezť do technických detailů (tokenization, BPE encoding) - audience je netřeba

---

## Slide 5: Velikosti v roce 2025 - comparison table

### Obsah slidu
```
| Nástroj           | Context Window | Co se vejde                  |
|-------------------|----------------|------------------------------|
| Claude Sonnet 4   | 1M tokenů      | ~15-20 velkých dokumentů     |
| Gemini 2.5 Pro    | 1-2M tokenů    | ~30-40 dokumentů / 1 hod video |
| GPT-4.1           | 1M+ tokenů     | ~15-20 dokumentů             |
| GPT-4o (běžný)    | 128k tokenů    | ~2-3 dokumenty               |

💡 2023: Standard byl 8k-32k tokenů
💡 2025: Standard je 1M-2M tokenů = 30x+ nárůst!
```

### Poznámky pro lektora
- **Timing:** 5 min
- **Klíčový bod:** Dramatický nárůst = fundamentální změna co je možné

- **Co říct:**
  - "Podívejte se na ten rozdíl. Před 2 lety jste mohli vložit max 1-2 dokumenty."
  - "Dnes můžete vložit celý projekt najednou. To není inkrementální improvement - to je změna paradigmatu."
  - "Claude nebo Gemini: vejde se vám tam kompletní backlog, všechny user stories, celá projektová dokumentace."

- **Praktický příklad:**
  - "Typický requirements dokument: 20-30 stránek = ~20k tokenů."
  - "S GPT-4o (128k): vejde se vám 5-6 takových dokumentů."
  - "S Claude (1M): vejde se vám 40-50 takových dokumentů."
  - "S Gemini (2M): ještě 2x víc. Plus můžete nahrát hodinu videa ze stakeholder meetingu."

- **Pro interakci:**
  - "Kolik dokumentů typicky analyzujete najednou? *[zjisti od audience]*"
  - "Vejde se vám to? *[pomůž jim spočítat]*"

- **Stanford case study mini-mention:**
  - "Stanford research: analyzovali 850k tokenů klimatických dat najednou → našli 12 korelací, které by při fragmentovaném přístupu minuli."

---

## Slide 6: Živá ukázka - co se vejde

### Obsah slidu
```
Live Demo: Kolik se vejde do 1M tokenů?

[Připravit ukázkový projekt s dokumenty]
```

### Poznámky pro lektora
- **Timing:** 5 min
- **Příprava:** Mít připravený složku s 10-15 dokumenty (requirements, user stories, meeting notes)

- **Scénář:**
  1. "Ukážu vám reálný projekt. Mám tady:" *[ukaž složku]*
  2. Upload dokumentů do Claude/ChatGPT jeden po druhém
  3. Po každém: "Kolik tokenů máme teď?"
  4. Ukaž jak se postupně plní kontext
  5. Nakonec: *"Máme použitých X z 1M tokenů = Ytemplate% kapacity. Ještě je místo na..."*

- **Pro interakci:**
  - "Co myslíte, vejde se ještě další dokument?" *[nechej hádat]*
  - "Zkuste odhadnout kolik % kontextu jsme použili" *[interaktivní]*

- **Záložní plán:** Pokud demo selže (internet issue), mít screenshot sequence připravený

- **Pozor:** Watch timing - pokud jde demo dlouho, shrň rychle

---

## Slide 7: Kdy začíná být kontext problém

### Obsah slidu
```
Kontext se plní... co se stane?

✅ Do ~70% kapacity: Všechno funguje skvěle
⚠️ 70-90%: AI začíná být pomalejší, občas "zapomíná"
❌ 90%+: AI výrazně ztrácí začátek, kvalita klesá
🚫 100%: "Maximum length reached" - konec konverzace

💡 Neč

ekej na 100%! Zahaj novou konverzaci okolo 70-80%.
```

### Poznámky pro lektora
- **Timing:** 4 min
- **Key message:** Proaktivita, ne reakce

- **Co říct:**
  - "Největší chyba: čekat až AI řekne 'maximum length'. Tehdy už je pozdě."
  - "Kvalita klesá dávno předtím - okolo 70-80% kontext už začíná být problém."
  - "Prakticky: Máte konverzaci s 50+ zprávami? Začněte přemýšlet o nové."

- **Přístup:** Sdílej vlastní zkušenost - "Já osobně když vidím 40-50 zpráv, automaticky..."

- **Pro interakci:**
  - "Jak poznáte, že kontext je moc plný? Jaké signály vidíte?" *[nechat audience sdílet - typicky: AI opakuje, zapomíná, je inconsistent]*

---

## MODUL 2: Efektivní využití kontextu (30 min)

## Slide 8: File upload vs. Copy-paste - decision tree

### Obsah slidu
```
Kdy nahrát soubor vs. copy-paste text?

File Upload ✅
• Celý dokument je relevantní
• Standard formát (DOCX, TXT, PDF)
• Minimalizovat chyby

Copy-Paste ✅
• Jen specific sekce
• Problematický formát (PDF tabulky)
• Explicit kontrola co AI vidí
• Kombinace z více zdrojů

[Vizuální decision tree]
```

### Poznámky pro lektora
- **Timing:** 5 min
- **Praktický focus:** Real scenarios z BA práce

- **Co říct:**
  - "Tohle je častý dilema. Mám to uploadnout nebo copy-paste?"
  - "Jednoduchá pravidlo: Celý dokument relevantní? Upload. Jen kousek? Copy-paste."

- **Reálný příklad:**
  - "Máte master requirements 80 stránek. Ptáte se na feature ze stran 45-48."
  - "Špatně: Upload celých 80 stránek → AI musí hledat relevantní část."
  - "Dobře: Copy-paste stran 45-48 + krátký kontext."
  - "Proč: Menší, focused kontext = lepší odpověď, levnější, rychlejší."

- **Pro interakci:**
  - "Co děláte vy? Uploadujete nebo copy-paste?" *[quick poll]*
  - "Narazili jste na problém kdy upload nefungoval dobře?" *[získej stories]*

---

## Slide 9: Kdy začít novou konverzaci - checklist

### Obsah slidu
```
Zahaj novou konverzaci když:

✓ Změnil se scope projektu
✓ Přecházíš do nové fáze (discovery → design)
✓ Konverzace má >50 zpráv
✓ AI začíná "zapomínat" začátek
✓ Tangential question mimo current topic

💡 Pro tip: Před novou konverzací požádej o shrnutí!
"Shrň klíčové body naší diskuse pro start nové konverzace"
```

### Poznámky pro lektora
- **Timing:** 6 min
- **Key technique:** Summarize-and-continue pattern

- **Co říct:**
  - "Tohle je jedna z nejužitečnějších technik: vědět KDY začít novou konverzaci."
  - "Nečekejte až vás AI vyhodí. Buďte proaktivní."

- **Praktická ukázka:**
  1. Ukaž dlouhou konverzaci (připravenou)
  2. Live: "Shrň klíčové body pro novou konverzaci"
  3. AI vrátí summary
  4. Start novou konverzaci, paste summary
  5. "Vidíte? Máme fresh context, ale nic důležitého se neztratilo."

- **Alibaba case study:**
  - "Alibaba: 22% rychlejší ticket resolution když začali používat tuhle techniku."
  - "Místo 1 nekonečné konverzace → series focused konverzací s transferem kontextu."

- **Pro interakci:**
  - "Jak často začínáte novou konverzaci vy?" *[zjisti current behavior]*
  - "Někdo zkusil summarize pattern?" *[pokud ano, nech sdílet]*

---

## Slide 10: Strategic content placement

### Obsah slidu
```
Kde v promptu dát důležité info?

🥇 ZAČÁTEK: AI má nejlepší "paměť" (primacy effect)
🥉 STŘED: Často se "ztratí" v šumu
🥈 KONEC: Druhá nejlepší "paměť" (recency effect)

✅ Dobře:
PRIORITA: Security + GDPR
[dlouhý kontext]
PŘIPOMENUTÍ: Focus na security

❌ Špatně:
[dlouhý kontext]
btw hlavní je security...
```

### Poznámky pro lektora
- **Timing:** 5 min
- **Research-backed:** Zmínit že to je research finding, ne jen tips

- **Co říct:**
  - "Research ukázal zajímavou věc: AI má 'primacy and recency effect' - stejně jako lidi."
  - "Pamatuje si nejlíp začátek a konec. Střed se často ztratí."
  - "Prakticky: nejdůležitější info dej na začátek NEBO na konec."

- **Live příklad:**
  - Ukaž 2 prompty side-by-side: špatný (priorita buried in middle) vs. dobrý (priorita na začátku a konci)
  - "Který myslíte že dostane lepší odpověď?" *[audience guess]*

- **Pro interakci:**
  - "Kdy jste si všimli, že AI ignorovalo něco důležitého z vašeho promptu?" *[typicky middle]*

---

## Slide 11: Information Distillation technique

### Obsah slidu
```
Information Distillation = Udělat ze

 dlouhého kontextu krátké shrnutí

Kdy použít:
• Po dlouhé analýze (transfer do nové konverzace)
• Máš hodně info, jen část je relevantní
• Chceš snížit náklady (méně tokenů)

Jak na to:
"Vytvoř kompaktní shrnutí. Zachovej všechny klíčové požadavky
a rozhodnutí. Vynechej detaily, které nejsou kritické."
```

### Poznámky pro lektora
- **Timing:** 4 min
- **Practical example:** Ukaž před/po

- **Co říct:**
  - "Distillation zní fancy, ale je to prostě: dlouhý → krátký, bez ztráty podstaty."
  - "Po 2 hodinách brainstormingu máte konverzaci plnou dead-endů a tangents."
  - "Distillation: vytáhnete jen finální rozhodnutí."

- **Před/Po ukázka:**
  - "Před: 50 zpráv, 30k tokenů, hodně šumu"
  - "Po: Shrnutí 2k tokenů, jen final decisions"
  - "Tohle pak použijete v design fázi."

- **Pro interakci:**
  - "Zkusí to teď někdo?" *[pokud čas, nech audience zkusit na vlastní konverzaci]*

---

## Slide 12: Cost implications - důležité vědět

### Obsah slidu
```
Velký kontext = vyšší náklady

Claude pricing (ilustrativní):
• Do 200k tokenů: $3/M input, $15/M output
• Nad 200k: $6/M input (2x), $22.50/M output (1.5x)

Prakticky:
• Běžná práce (5-10k): ~2-3 Kč per request
• Large context (500k): ~100 Kč per request

💡 20x denně = 2,000 Kč/den = 40k+ Kč/měsíc
```

### Poznámky pro lektora
- **Timing:** 5 min
- **Business audience:** Tento slide je key - BA rozumí cost/benefit

- **Co říct:**
  - "Tohle není strašení, jen awareness. AI není zadarmo - potřebujete rozumět nákladům."
  - "Malý kontext: zanedbatelné náklady, neřešte to."
  - "Velký kontext opakovaně: začíná to být číslo, optimalizujte."

- **Kdy optimalizovat, kdy ne:**
  - "Jednorázová analýza velkého projektu? 100 Kč vs. ušetřené hodiny = no brainer, neoptimalizuj."
  - "Opakuješ stejný úkol 20x denně? = 40k měsíčně → optimalizuj (Custom GPT/Skill)."

- **JPMorgan case:**
  - "JPMorgan: 35% redukce času na contract review."
  - "I kdyby je to stálo 10x víc, ROI je masivní. Time savings > AI cost."

- **Pro interakci:**
  - "Trackujete AI costs ve firmě?" *[většinou ne - highlight importance]*
  - "Zkuste odhadnout váš měsíční usage" *[pomůž jim spočítat]*

---

## MODUL 3: Pokročilé nástroje (30 min)

## Slide 13: Přehled specializovaných nástrojů

### Obsah slidu
```
Naučit AI svůj kontext jednou, používat stokrát

🔧 Custom GPT (ChatGPT)
  • Easiest, conversational tvorba
  • Requires ChatGPT Plus ($20/měsíc)

🔧 Claude Skills
  • File-based, sharable
  • Free s Claude accountem

🔧 MCP Servery (pokročilé)
  • Připojení k external data/tools
  • Requires tech skills
```

### Poznámky pro lektora
- **Timing:** 3 min
- **Overview slide:** Rychlý přehled, detaily budou následovat

- **Co říct:**
  - "Teď se dostáváme k tomu, co vám reálně ušetří hodiny práce."
  - "Představte si: máte opakující se úkol. Místo vysvětlovat AI pokaždé od začátku..."
  - "...nastavíte to jednou. AI si 'pamatuje' jak to dělat. Used opakovaně."

- **Decision guide:**
  - "ChatGPT user? → Custom GPT"
  - "Claude user? → Skills"
  - "Need external data? → MCP (pokročilé)"

---

## Slide 14: Custom GPT - demo a hands-on (15 min celkem)

### Obsah slidu
```
Custom GPT: Tvoje vlastní AI pro specifický úkol

Live Demo: Vytvoříme GPT za 5 minut

Pak: Každý si vytvoří vlastní (10 min hands-on)
```

### Poznámky pro lektora
- **Timing:** 15 min total (5 demo + 10 hands-on)
- **Klíčové:** Tohle je hands-on část, ne jen prezentace

**Demo (5 min):**

- **Příprava:** Mít chatgpt.com/create otevřený, screenshare ready

- **Live vytvoření:**
  1. "Jdeme na chatgpt.com/create"
  2. Screen share, všichni vidí
  3. "Řeknu GPT Builderu co chci:"
     ```
     "Chci GPT který pomáhá BA psát user stories podle našeho templatu.
     Template je: As a [role] I want [feature] So that [benefit].

     GPT by měl:
     - Ptát se na detaily když něco chybí
     - Být friendly ale professional
     - Navrhovat dobré acceptance criteria"
     ```
  4. GPT Builder pokládá otázky → odpovídáš live
  5. Preview → testuj
  6. Save
  7. "Hotovo! 5 minut. Teď to můžu používat pořád."

**Hands-on (10 min):**

- **Zadání:**
  "Teď vy. Vytvořte si Custom GPT pro jeden opakující se úkol z vaší práce.

   Nápady:
   - Requirements analyzer
   - Meeting notes summarizer
   - User story writer
   - SWOT analysis helper

   Máte 10 minut. Kdo potřebuje pomoc, volejte."

- **Během cvičení:**
  - Chodíš mezi lidmi
  - Pomáháš s technickými problémy
  - Všímej si zajímavých use cases

- **Po cvičení (2 min):**
  - "Kdo má hotovo? Co jste vytvořili?" *[nechej 2-3 lidi sdílet]*
  - "Kdo narazil na problém?" *[troubleshooting common issues]*

- **Záložní plán:** Pokud někdo nemá ChatGPT Plus, může použít něčí shared link nebo jen sledovat

---

## Slide 15: Claude Skills - conversational creation (13 min celkem)

### Obsah slidu
```
Claude Skills: Reusable workflows pro Claude

Nejjednodušší způsob: Conversational creation

Live Demo + Hands-on
```

### Poznámky pro lektora
- **Timing:** 13 min total (3 demo + 10 hands-on)

**Demo (3 min):**

- **Příprava:** Claude open, skill-creator zapnutý

- **Live vytvoření:**
  1. "Settings → Capabilities → skill-creator ON"
  2. Nová konverzace
  3. "Řeknu Claude:"
     ```
     "Chci vytvořit skill pro analýzu user stories. Skill by měl:
     - Zkontrolovat format (As a / I want / So that)
     - Najít chybějící acceptance criteria
     - Identifikovat ambiguous language
     - Output: checklist co opravit"
     ```
  4. Claude vytvoří skill za 30 sekund
  5. "Vidíte? Ještě jednodušší než Custom GPT."

**Hands-on (10 min):**

- **Zadání:**
  "Teď vy - vytvořte Claude Skill pro váš use case.
   Pokud nemáte Claude, můžete pokračovat s Custom GPT z minula."

- **Během/po:** Stejný approach jako u Custom GPT hands-on

---

## Slide 16: MCP Servery - overview (ne hands-on)

### Obsah slidu
```
MCP Servery: "USB-C port for AI"

Připojení Claude k externím zdrojům:
• Jira, Notion, Linear
• Your database
• Filesystem, GitHub

⚠️ Pokročilé - requires tech skills

[Screenshot: Claude Desktop s MCP servery]

Náplady use cases pro BA:
• Real-time Jira data
• Auto-read project files
• Query databáze
```

### Poznámky pro lektora
- **Timing:** 4 min
- **Approach:** Demo-only, ne hands-on (moc complex pro workshop)

- **Co říct:**
  - "MCP je silný nástroj, ale technicky náročnější. Nepůjdeme do hands-on."
  - "Ukážu vám co to umí, abyste věděli že to existuje."
  - "Pokud vás to zajímá: po workshopu vám dám odkazy na setup guides."

- **Quick demo nebo screenshot walkthrough:**
  - Ukaž Claude Desktop s připojenými MCP servery
  - Demonstruj query: "Kolik open issues máme v Jira?" → Claude odpovídá z real-time data
  - "Vidíte? Nemusíte export CSV a upload. Claude čte přímo z Jira."

- **When to consider:**
  - "MCP dává smysl když: pravidelně potřebujete data z externích systémů."
  - "Většinou ale stačí Custom GPT nebo Skill. MCP je pro specific advanced cases."

---

## MODUL 4: Context Engineering (22 min)

## Slide 17: Paradigma shift - Prompt → Context Engineering

### Obsah slidu
```
2022-2023: Prompt Engineering Era
"Jak napsat jeden dobrý dotaz?"

2024-2025: Context Engineering Era
"Jak navrhnout celý informační workflow?"

[Vizuál: Timeline ukazující shift]

Analogie:
• Prompt eng = Psát dobré emaily
• Context eng = Designovat komunikační systém firmy
```

### Poznámky pro lektora
- **Timing:** 4 min
- **Conceptual framing:** Tohle je intro do nového mindset

- **Co říct:**
  - "Poslední modul je trochu jiný - přejdeme od technik k systémovému myšlení."
  - "Industry prošlo shiftem. Dřív: 'jak napsat perfektní prompt'. Teď: 'jak navrhnout celý workflow'."
  - "Analogicky: dřív jste se učili psát dobré emaily. Teď navrhujete celý komunikační systém."

- **Research quote:**
  > "Context engineering is the new currency in AI. We've moved from finding right words to designing right configuration of context."

- **Pro interakci:**
  - "Kolik z vás přemýšlí o AI jako o tool pro jednoí dotaz vs. long-term asistent?" *[discover current mindset]*

---

## Slide 18: Principy context engineeringu

### Obsah slidu
```
1. Treat context as finite resource
   → Prioritizuj co tam patří

2. Design for reuse
   → Systém, ne ad-hoc dotazy

3. Multi-session thinking
   → Projekty = series konverzací, ne jedna mega-konverzace

4. Information hierarchy
   → Ne všechny info jsou stejně důležité
```

### Poznámky pro lektora
- **Timing:** 5 min
- **Vysvětli každý princip s příkladem:**

- **Princip 1: Finite resource**
  - "Stejně jako máš 24 hodin denně, máš X tokenů v kontextu."
  - "Ptej se: Je tahle info critical? Nebo nice-to-have?"

- **Princip 2: Design for reuse**
  - "Místo 'jak napsat ten dotaz' → 'jak navrhnout systém pro TEN TYP dotazů'"
  - Příklad: Custom GPT je reuse. Každotýdenní psaní 500-word promptu není.

- **Princip 3: Multi-session**
  - "Projekt trvá týdny. Nebudeš mít jednu konverzaci."
  - "Budeš mít: Discovery session → Design session → Implementation session"
  - "Každá = fresh context + summary z předchozí"

- **Princip 4: Hierarchy**
  - "Critical info (goal, constraints) → vždy na začátek"
  - "Nice-to-have (historical context) → separate doc nebo end"

---

## Slide 19: Pattern: Summarize-and-Continue

### Obsah slidu
```
Nejužitečnější pattern pro dlouhodobé projekty

Week 1: Discovery
  → Na konci: "Shrň findings"

Week 2: Design (nová konverzace)
  → Start: Paste summary z Week 1
  → Na konci: "Shrň design decisions"

Week 3: Implementation (nová konverzace)
  → Start: Paste summaries z Week 1+2

Fresh context každou fázi, ale nic důležitého se neztratí
```

### Poznámky pro lektora
- **Timing:** 5 min
- **Practical walkthrough:** Ukaž real example (připravený)

- **Co říct:**
  - "Tohle je pattern, který používám na každém dlouhodobém projektu."
  - "Místo 1 nekonečné konverzace → series focused sessions s transfer kontextu."

- **Live demo nebo prepared example:**
  - Ukaž 3 konverzace side-by-side:
    1. Discovery (dlouhá) → ends with summary
    2. Design starts with that summary
    3. Implementation starts with both summaries

  - "Vidíte rozdíl? Každá fáze má clean, optimized context."

- **Pro interakci:**
  - "Kdo dělá dlouhodobé projekty (měsíce)? Jak to řešíte?" *[compare approaches]*

---

## Slide 20: Pattern: Modular Context

### Obsah slidu
```
Rozděl kontext na moduly (reusable pieces)

Module 1: Project Context (static)
  • Project goal, stakeholders, constraints

Module 2: Current Phase (changes per phase)
  • Phase name, focus, deliverable

Module 3: Today's Task (changes per conversation)
  • Specific question/task

Každou konverzaci: Mix jen relevant modules
```

### Poznámky pro lektora
- **Timing:** 4 min
- **Template approach:** Dej lidem praktický template

- **Co říct:**
  - "Místo copy-paste 50 stránek pokaždé, copy-paste jen relevantní moduly."
  - "Module 1 je stejný celý projekt. Module 2 se mění per fáze. Module 3 per conversation."

- **Praktický příklad:**
  ```
  Úterý: Module 1 + Module 2 (Discovery) + "Task: Stakeholder interview summary"
  Středa: Module 1 + Module 2 (Discovery) + "Task: Requirements gaps analysis"
  Příští týden: Module 1 + Module 2 (Design) + "Task: High-level architecture"
  ```

- **Pro interakci:**
  - "Kdo by použil tohle na svém current projektu?" *[nechej přemýšlet]*

---

## Slide 21: Mini hands-on - návrh workflow (4 min)

### Obsah slidu
```
Rychlé cvičení: Navrhni context engineering pro tvůj projekt

1. Rozdel na fáze
2. Pro každou fázi: Co jsou critical infos?
3. Kde budeš dělat summarize?
4. Který nástroj použiješ?

Partner work - 4 minuty
```

### Poznámky pro lektora
- **Timing:** 4 min
- **Quick exercise:** Ne plné hands-on, jen brainstorm

- **Zadání:**
  - "Vezmi si projekt, na kterém teď pracuješ."
  - "4 minuty: Navrhni context engineering approach. Nemusíš implementovat, jen návrh."
  - "Pracuj s někým vedle, diskutujte."

- **Po cvičení (1 min):**
  - "Kdo chce sdílet co navrhl?" *[1-2 dobrovolníci]*
  - *[Dej quick feedback na jejich návrh]*

---

## ZÁVĚR A Q&A (13 min)

## Slide 22: Shrnutí - co jsi se naučil

### Obsah slidu
```
Dnes jsi se naučil:

✓ Kontextové okno a jeho velikosti (1M-2M tokenů!)
✓ Optimalizační techniky (file vs. paste, nová konverzace, placement)
✓ Cost implications a kdy optimalizovat
✓ Custom GPT a Skills pro opakované úkoly
✓ Context engineering pro long-term projekty

Bonus: Case studies (JPMorgan 35%, Alibaba 22%)
```

### Poznámky pro lektora
- **Timing:** 3 min
- **Recap:** Rychle projdi key takeaways

- **Co říct:**
  - "Tak, co si z toho odnášíte?"
  - *[Rychle projdi slides]*
  - "Největší takeaway: Kontext není jen technical detail. Je to fundamental change jak pracujete s AI."

---

## Slide 23: Quick wins pro zítra

### Obsah slidu
```
Co aplikovat hned zítra:

1️⃣ Start novou konverzaci při phase transition
   (ne pokračovat v nekonečném chatu)

2️⃣ Před novou konverzací: "Shrň pro nový chat"

3️⃣ Strukturuj prompty (headings, clear sections)

4️⃣ Zkus vytvořit Custom GPT/Skill pro 1 úkol (10 min)
```

### Poznámky pro lektora
- **Timing:** 2 min
- **Actionable:** Konkrétní, malé kroky

- **Co říct:**
  - "Nechci abyste odešli a nic neudělali. Tady jsou 4 věci které můžete zkusit zítra."
  - "Číslo 1 je nejjednodušší a nejvíc impactful: začněte nové konverzace častěji."
  - "Číslo 4: investice 10 minut, long-term benefit."

---

## Slide 24: Kam dál - resources

### Obsah slidu
```
Dokumentace:
• Claude Context Docs
• ChatGPT Custom GPTs Guide
• Gemini Long Context

Komunity:
• r/ClaudeAI, r/ChatGPTPro

Case studies:
• JPMorgan contract review (35%)
• Alibaba support tickets (22%)

Materiály z workshopu:
[Link na materiály]
```

### Poznámky pro lektora
- **Timing:** 2 min
- **Dej konkrétní odkazy:** Účastníci by měli odejít s clear next steps

---

## Slide 25: Q&A

### Obsah slidu
```
Otázky?

[Tvůj kontakt]
```

### Poznámky pro lektora
- **Timing:** 6+ min (zbytek času)

- **Approach:**
  - "Otázky? Klidně se ptejte na cokoliv."
  - *[Pokud ticho, prepared questions:]*
    - "Často se ptají: Co když Custom GPT nefunguje dobře?"
    - "Další častá: Jak trackovat AI costs ve firmě?"

- **Odpovídání:**
  - Nejdřív se ujisti že rozumíš otázce
  - Odpověz stručně, prakticky
  - Pokud nevíš: "To nevím přesně, zjistím a pošlu email"

- **Zakončení:**
  - "Díky za účast! Doufám, že to bylo užitečné."
  - "Materiály najdete na [link]. Můžete psát kdykoliv."
  - "A hlavně - zkoušejte to! Theory is nice, but practice je kde se učíte."

---

## Poznámky k celé prezentaci

### Obecné tipy

- **Tempo:** Raději pomaleji. Nech čas na otázky a hands-on.
- **Energie:** Udržuj nadšení, ale natural - ne fake hype.
- **Interakce:** Každých 10 min nějaká aktivita (otázka, poll, mini hands-on).
- **Čas:** Sleduj timing, ale 5-10 min tam nebo tam není problém.

### Checklist před začátkem

- [ ] Tested tech (projektor, internet, screenshare)
- [ ] Mít vodu
- [ ] Link na materiály sdílený (Slide, chat, email)
- [ ] Demo prepared (dlouhá konverzace, documents ready)
- [ ] Accounts ready (ChatGPT, Claude) pro live demo
- [ ] Backup slides/screenshots pokud demo selže

### Co dělat když...

- **Nikdo neodpovídá:** Nedělej drama, pokračuj. Nebo "OK, pojďme dál..."
- **Někdo moc mluví:** "Super otázka! Pojďme ji rozvést po workshopu - nechci vyhodit časování."
- **Tech selže:** Klid. "OK, technical hiccup. Mám backup..." *[switch to screenshots]*
- **Dojde čas:** "Vidím že nám dochází čas. Rychlé shrnutí..." *[hit key points, skip details]*
- **Hands-on trvá dlouho:** "Vidím že hodně z vás ještě pracuje. Dám ještě 2 minuty navíc."

### Time tracking during workshop

**Checkpoint times:**
- 25 min: Měl bys být na konci Modulu 1
- 55 min: Měl bys být na konci Modulu 2
- 85 min: Měl bys být na konci Modulu 3
- 107 min: Měl bys být na konci Modulu 4
- 120 min: Done

Pokud jsi pozadu 5-10 min: no problem, zkrať Q&A
Pokud jsi pozadu 15+ min: skip MCP demo nebo zkrať hands-on o 5 min

---

**Status:** ✅ Ready to deliver
**Last updated:** 2025-11-05
**Version:** 1.0
