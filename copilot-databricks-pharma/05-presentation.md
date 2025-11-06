# Copilot & Databricks pro farmaceutické analýzy - Prezentace

**Celková doba:** 8 hodin (vč. přestávek)
**Počet slidů:** ~40 slides
**Format:** Workshop - 60% hands-on, 40% prezentace

---

## BLOK 1: Úvod a nastavení prostředí (70 min, 9:00-10:10)

### Slide 1: Úvodní slide
**Obsah:**
```
Copilot & Databricks
pro farmaceutické analýzy

Praktický workshop - AI nástroje pro data analytiky

[Datum] | [Místo]
```
**Poznámky:**
- Timing: 2 min
- Přivítání, představení lektora
- "Dnes vám ukážu jak pomocí AI dělat analýzy 5-10x rychleji"

---

### Slide 2: Co si dnes odnesete
**Obsah:**
```
Po dnešku budete umět:

✓ Psát prompty, které dávají přesné výsledky
✓ Používat Databricks AI Assistant pro SQL a Python
✓ Stavět kompletní analýzy s pomocí AI
✓ Validovat AI výstupy aby neobsahovaly chyby
✓ Bezpečně pracovat s citlivými daty

⚡ Bonus: Prompt šablony na odnést domů
```
**Poznámky:**
- Timing: 3 min
- "Konkrétně - konec dne budete mít hotové 2-3 analýzy které použijete v práci"
- Interakce: "Co vy očekáváte? Zdvihněte ruku kdo už používal ChatGPT"

---

### Slide 3: Program dne
**Obsah:**
```
9:00-10:10   Úvod + Setup (✋ hands-on)
10:10-10:25  ☕ Coffee break
10:25-11:55  Prompt Engineering (💪 3 cvičení)
11:55-13:00  🍽️ Oběd
13:00-15:05  Databricks + AI (🔥 3 use cases)
15:05-15:20  ☕ Coffee break
15:20-17:00  Pokročilé techniky + Projekt
17:00-17:30  Wrap-up & Q&A
```
**Poznámky:**
- Timing: 2 min
- "60% času budeme pracovat hands-on, ne poslouchat prezentaci"
- "Materiály dostanete všechny - cheat sheet, notebooky, kódy"

---

### Slide 4: Proč AI + Analytics = 🚀
**Obsah:**
```
Vaše konkurence už to používá:

• Pfizer: Drug discovery 2 roky místo 5-7 let
• Moderna: 60,000+ shipments optimalizováno AI
• Roche: 3-4x lepší detekce nespokojených zákazníků

📊 50-70% úspora nákladů na clinical trials
⏱️ 12+ měsíců zrychlení timelines

Není to sci-fi. Je to realita 2025.
```
**Poznámky:**
- Timing: 3 min
- "Tohle nejsou buzzwordy, to jsou reálná čísla z case studies"
- "AI vás nenahradí. Ale analytik S AI nahradí analytika BEZ AI"

---

### Slide 5: ⚠️ Bezpečnost NEJDŘÍV (kritické!)
**Obsah:**
```
83% farmafir nemá zabezpečení proti úniku dat do AI

❌ NIKDY nesdílet s public AI:
   • Patient data (jména, rodná čísla)
   • Molekulární struktury
   • Clinical trial results
   • API keys, credentials

✅ BEZPEČNÉ:
   • Anonymizovaná data
   • Demo/synthetic data
   • Agregované statistiky

👉 Používejte enterprise nástroje (Databricks AI, GitHub Copilot Enterprise)
```
**Poznámky:**
- Timing: 5 min
- **DŮLEŽITÉ:** Zdůraznit že tohle není optional
- "GDPR: Data v AI modelech nejdou smazat"
- "Dnes budeme používat demo data - žádná reálná patient data!"
- Rozdej printed security checklist

---

### Slide 6: Live Demo - Váš první AI dotaz
**Obsah:**
```
🎯 Live Demo: První krok s Databricks AI

Ukážu vám:
1. Jak otevřít AI Assistant
2. @ mention tabulky
3. První SQL dotaz pomocí AI
4. Validace výsledku
```
**Poznámky:**
- Timing: 10 min
- Screenshare - otevřít Databricks
- Ukázat @ mention @demo_sales_data
- Prompt: "Ukaž mi schéma a prvních 5 řádků"
- Pak: "Najdi TOP 5 produktů podle revenue"
- **Záměrně udělej chybu** - např. zapomeň WHERE clause, pak opravu s AI
- "Vidíte? Není to magie, je to nástroj"

---

### Slide 7: ✋ Hands-On - Setup Check
**Obsah:**
```
Čas si to vyzkoušet!

Úkol (15 min):
1. Přihlásit se do Databricks workspace
2. Otevřít prepared notebook "00-Setup"
3. Spustit @ mention na @demo_sales_data
4. Vygenerovat simple SELECT dotaz s AI
5. Ověřit že výsledek dává smysl

🆘 Problém? Zvedněte ruku!
```
**Poznámky:**
- Timing: 15 min (studenti pracují)
- Během cvičení: choď mezi lidmi, pomáhej
- Všimni si common problems
- Po cvičení: "Jak to šlo? Kdo to má?"
- Rychlé demo řešení pokud někdo zasekl

---

### Slide 8: Jak fungují LLM (bez žargonu)
**Obsah:**
```
Large Language Models v kostce:

🧠 Trénované na obrovských datech
📊 Predikují "co pravděpodobně přijde dál"
🤖 Rozpoznávají patterny, ne rozumí obsahu

Co umí ✅:
• Generovat SQL z popisu
• Vysvětlit složitý kód
• Najít chyby v syntaxi

Co neumí ❌:
• Složité výpočty (arithmetic)
• Business logic bez kontextu
• Vědět co je "správně" (potřebuje validaci)

🎭 Hallucinations = vymýšlí si názvy tabulek/sloupců
```
**Poznámky:**
- Timing: 5 min
- "AI není chytrý človek, je to pattern matcher"
- "Proto musíte VŽDY validovat co vygeneruje"
- Příklad halucinace - ukázat AI response s fake column names

---

### Slide 9: Databricks AI vs ChatGPT vs Copilot
**Obsah:**
```
Který nástroj kdy?

Databricks AI Assistant:
✅ Práce s daty v Databricks
✅ SQL dotazy, Python notebooks
✅ @ mentions - rozumí Unity Catalog

GitHub Copilot:
✅ General programming v IDE
✅ Autocomplete kódu
✅ VS Code, SSMS integration

ChatGPT / Claude:
✅ Brainstorming, plánování
✅ Vysvětlování konceptů
❌ NE pro production kód s citlivými daty

👉 Dnes focus na Databricks AI
```
**Poznámky:**
- Timing: 3 min
- "Databricks AI je váš hlavní nástroj pro analytics"
- "ChatGPT použijte jen s fake data nebo pro learning"

---

## BLOK 2: Prompt Engineering (90 min, 10:25-11:55)

### Slide 10: Proč kvalita promptu = kvalita výsledku
**Obsah:**
```
Stejný AI model, 2 prompty:

❌ Špatný prompt:
   "Ukaž mi prodeje"
   → AI hádá, často špatně

✅ Dobrý prompt:
   "Z @sales_data najdi TOP 10 produktů podle
   revenue v Praze za Q1 2024. SQL + bar chart."
   → AI ví přesně co chceš

📈 Rozdíl v success rate: 20% vs 90%
```
**Poznámky:**
- Timing: 3 min
- "80% úspěchu je v tom JAK se ptáte"
- "Není to o AI modelu, je to o vašem promptu"

---

### Slide 11: Anatomie dobrého promptu
**Obsah:**
```
4 klíčové komponenty:

┌─────────────────────────────┐
│ 1. ROLE                     │
│ "Jsi expert na SQL analýzy" │
└─────────────────────────────┘
         ↓
┌─────────────────────────────┐
│ 2. KONTEXT                  │
│ "@sales: produkt, region..."│
└─────────────────────────────┘
         ↓
┌─────────────────────────────┐
│ 3. ÚKOL                     │
│ "Najdi TOP 10 v Praze Q1"  │
└─────────────────────────────┘
         ↓
┌─────────────────────────────┐
│ 4. FORMÁT                   │
│ "SQL + bar chart + comments"│
└─────────────────────────────┘
```
**Poznámky:**
- Timing: 5 min
- Projít každou komponentu s příkladem
- "Bez kontextu AI hádá. S kontextem AI ví."
- Ukázat side-by-side: vágní vs dobrý prompt

---

### Slide 12: Live Demo - Before & After
**Obsah:**
```
🎯 Živá ukázka: Transformace promptu

PŘED:
"Najdi zákazníky"
→ [ukážu co AI vygeneruje - generické]

PO:
"Z @customers a @orders najdi TOP 20 zákazníků
podle celkového revenue za 2024. Zobraz:
customer_id, total_revenue, order_count.
SQL + seřaď DESC."
→ [ukážu - přesný výsledek]
```
**Poznámky:**
- Timing: 8 min
- Live coding v Databricks
- Zdůraznit rozdíl v kvalitě outputu
- "Vidíte rozdíl? Stejný AI, jiný prompt"

---

### Slide 13: Few-Shot Learning - Superschopnost
**Obsah:**
```
Dej AI 2-3 příklady = 5x lepší výsledky

Princip:
1. Ukázat AI 2-3 příklady co chceš
2. Pak zadat hlavní úkol
3. AI "naučí" z příkladů tvůj styl

Example:
"Tady 2 příklady stylu SQL co chci:
Ex1: TOP produkty → SELECT... LIMIT 10
Ex2: Trend po měsících → DATE_TRUNC...

Teď prosím stejný styl pro: TOP zákazníci"
```
**Poznámky:**
- Timing: 5 min
- "Few-shot = secret weapon pro konzistentní výsledky"
- Kdy použít: specifický format, coding style, repetitivní úlohy

---

### Slide 14: 💪 Cvičení 1 - Přepiš vágní prompt
**Obsah:**
```
Úkol (15 min):

Máte tyto vágní prompty. Přepište je na dobré:

1. "Ukaž mi zajímavé věci o zákaznících"
2. "Najdi problémové produkty"
3. "Analyzuj trendy"

Použijte 4 komponenty:
Role + Kontext + Úkol + Formát

📝 Worksheet: handout-exercise-1
```
**Poznámky:**
- Timing: 15 min
- Rozdat worksheet s template
- Během: choď mezi lidmi, dávej hints
- Po: probereme 1-2 řešení nahlas
- "Není jedno správné řešení, důležitý je proces"

---

### Slide 15: Řešení cvičení 1 (ukázka)
**Obsah:**
```
Prompt 1: "Zajímavé věci o zákaznících"

✅ Dobrý přepis:
"Kontext: @customers (age, region) a @orders (value, date)
Úkol: Segmentuj zákazníky podle avg order value.
Vytvoř 3 segmenty: low/mid/high spenders.
Pro každý urči: count, top region, avg age.
Formát: SQL + tabulka se segmenty"

🔑 Klíč: Specifický úkol místo "zajímavé věci"
```
**Poznámky:**
- Timing: 5 min
- Probrat 1-2 řešení od studentů
- Vyzdvihnout co udělali dobře
- "Vidíte jak je to konkrétní?"

---

### Slide 16: Prompt Chaining - Rozděl a panuj
**Obsah:**
```
Složitý úkol? Rozděl na kroky.

❌ Mega-prompt:
"Udělej kompletní analýzu + trend + predikci..."
→ Příliš komplexní, AI udělá chyby

✅ Chaining:
Krok 1: "Načti a agreguj data"
Krok 2: "Z agregace najdi TOP 3"
Krok 3: "Pro TOP 3 analyzuj trend"
Krok 4: "Vytvoř viz"

Output kroku 1 → Input kroku 2 → ...
```
**Poznámky:**
- Timing: 5 min
- "Každý krok validujete před pokračováním"
- "Snižuje šanci na chybu exponenciálně"
- Analogie: stavění domu - nejdřív základ, pak zdi, pak střecha

---

### Slide 17: 💪 Cvičení 2 - Praktický Prompt Engineering
**Obsah:**
```
Hands-On úkol (25 min):

Scénář: Potřebujete analyzovat prodeje Ibuprofenu
podle městských částí Prahy za Q4 2024.

Úkoly:
1. Napsat prompt pro exploration (schéma, sample)
2. Napsat prompt pro TOP 10 analýzu
3. Napsat prompt pro visualizaci
4. Spustit v Databricks, validovat

📓 Notebook: 01-Prompt-Engineering-Exercise

💡 Tip: Použijte prompt chaining!
```
**Poznámky:**
- Timing: 25 min
- Prepared notebook s demo daty
- Během: intensively pomáhej, tohle je core skill
- Všimni si kdo má problems - wrape up později
- Po: live demo řešení

---

### Slide 18: Common Prompt Mistakes
**Obsah:**
```
Časté chyby:

❌ Vágní: "Najdi hottest tables"
✅ Specifické: "TOP 10 tables by read count, last 24h"

❌ Bez kontextu: AI hádá názvy sloupců
✅ @ mention nebo výpis columns

❌ Mega-prompt: 10 úkolů najednou
✅ Chaining: krok po kroku

❌ Žádná validace: blindly trust
✅ VŽDYCKY zkontroluj výstup
```
**Poznámky:**
- Timing: 3 min
- "Tyto chyby dělá každý začátečník"
- "Já je dělal taky. Teď už ne."

---

### Slide 19: Prompt Templates - Na odnést
**Obsah:**
```
5 ready-to-use šablon v cheat sheetu:

📊 TOP N Analýza
👥 Customer Segmentation
📈 Time Series & Trends
🗺️ Geographic Analysis
🐛 Debugging & Fix

Všechny v: copilot-databricks-cheatsheet.pdf

💾 Vytvořte si prompt library!
```
**Poznámky:**
- Timing: 2 min
- "Každý prompt co funguje → uložte si"
- "Za měsíc budete mít 20-30 prompt šablon"
- "Sdílejte s týmem"

---

## ☕ OBĚD (11:55-13:00)

---

## BLOK 3: Databricks + AI pro datové analýzy (125 min, 13:00-15:05)

### Slide 20: Databricks AI Assistant Deep Dive
**Obsah:**
```
3 režimy použití:

💬 Chat Mode
   • Boční panel, delší konverzace
   • Exploratory questions

✏️ Edit Mode (Cmd+I)
   • Inline editing
   • Rychlé úpravy aktuální buňky

🤖 Agent Mode
   • Autonomous tasks
   • Multi-step operations

🎯 Dnes focus: Chat + Edit
```
**Poznámky:**
- Timing: 5 min
- Live ukázat každý mode
- Zdůraznit Cmd+I jako nejčastější workflow

---

### Slide 21: @ Mentions - Instant Context
**Obsah:**
```
@ mentions = AI vidí tabulky z Unity Catalog

Příklad:
"@sales_data @products @regions"
→ AI ví schéma, relationships, JOINy

Výhoda:
• Nemusíš popisovat celé schéma
• AI navrhne správné JOINy
• Rychlejší, méně chyb

💡 Autocomplete: začni psát @ a objeví se seznam
```
**Poznámky:**
- Timing: 3 min
- Live demo @ mention
- "Unity Catalog = single source of truth pro AI"

---

### Slide 22: / Commands
**Obsah:**
```
Speciální příkazy pro rychlé akce:

/ask     Zeptej se na cokoliv
/explain Vysvětli tento kód
/fix     Oprav chybu
/doc     Generuj dokumentaci

Příklad:
/explain SELECT ... FROM ... WHERE ...
→ AI rozepíše krok po kroku

/fix [error message]
→ AI navrhne opravu
```
**Poznámky:**
- Timing: 3 min
- Ukázat každý command live
- "/explain používám denně na legacy kód"

---

### Slide 23: 🔥 Use Case 1 - Geographic Sales Analysis
**Obsah:**
```
Business otázka:
"Které městské části Prahy mají nejvyšší
prodeje Ibuprofenu 400mg?"

Společně vytvoříme (40 min):
1. Data exploration s @ mentions
2. SQL dotaz pro TOP 10 districts
3. Agregace: revenue, quantity, avg price
4. Horizontal bar chart visualization
5. Business insights

📓 Notebook: 02-Geographic-Analysis
```
**Poznámky:**
- Timing: 40 min
- **SPOLEČNĚ** s účastníky, ne jako demo
- Ptej se: "Co myslíte že by měl být první krok?"
- Nech je psát prompty, ty facilituj
- Validuj každý krok před pokračováním
- Zdůrazni common pitfalls (aggregate wrong, missing filters)

---

### Slide 24: 🔥 Use Case 2 - Customer Segmentation
**Obsah:**
```
Business otázka:
"Jaké skupiny zákazníků nakupují naše
Pain Relief produkty?"

Samostatně s podporou (40 min):
1. JOIN customers + orders
2. Calculate RFM (Recency, Frequency, Monetary)
3. Segment do 3-4 skupin
4. Profile každého segmentu
5. Marketing recommendations

📓 Notebook: 03-Customer-Segmentation

🆘 Hints available pokud zaseknu
```
**Poznámky:**
- Timing: 40 min
- Studenti SAMOSTATNĚ, ty pomáháš
- Prepared notebook s hints v komentářích
- Choď mezi lidmi intenzivně
- Common problem: wrong JOINs, duplicate counts
- Po: quick review řešení, vyzdvihni zajímavé přístupy

---

### Slide 25: 🔥 Use Case 3 - Time Series & Seasonality
**Obsah:**
```
Business otázka:
"Kdy je nejvyšší poptávka po produktech
proti chřipce? Je tam seasonality?"

Quick demo (20 min):
1. Agregace by week za 2 roky
2. Year-over-year comparison
3. Identify seasonal peaks
4. Line chart with trend
5. Insights pro inventory planning

📊 Ukážu vám, vy si zkusíte na vlastním produktu
```
**Poznámky:**
- Timing: 20 min
- Rychlá ukázka, není čas na full hands-on
- Fokus na time series techniky
- "Prophet a forecasting - advanced topic, resources v materiálech"

---

### Slide 26: AI Functions - Bonus Demo
**Obsah:**
```
Built-in AI funkce přímo v SQL!

ai_analyze_sentiment(text)
ai_extract(text, instruction)
ai_query(model, prompt)

Příklad - Sentiment analýzu customer reviews:
SELECT
  review_id,
  review_text,
  ai_analyze_sentiment(review_text) as sentiment
FROM customer_reviews;

→ positive/negative/neutral

🎯 Wow moment: AI přímo v SQL dotazu!
```
**Poznámky:**
- Timing: 7 min
- Quick live demo
- "Nebudeme deep dive, ale chtěl jsem abyste viděli že existuje"
- Resources v materiálech

---

## ☕ PŘESTÁVKA (15:05-15:20)

---

## BLOK 4: Pokročilé techniky + Závěrečný projekt (100 min, 15:20-17:00)

### Slide 27: Validace AI Výstupů - Kritický Skill
**Obsah:**
```
AI NENÍ dokonalé. Časté chyby:

1️⃣ Average-of-averages
   SELECT AVG(avg_revenue) → ŠPATNĚ
   Vážený průměr potřebuje raw data

2️⃣ Duplicate counts
   COUNT(customer_id) → počítá 2x pokud vícekrát v JOIN
   COUNT(DISTINCT customer_id) → SPRÁVNĚ

3️⃣ Ignorování business rules
   AI neví že fiscal year je March-Feb

🛡️ Tvoje práce: VŽDY validovat!
```
**Poznámky:**
- Timing: 5 min
- Ukázat každou chybu s příkladem
- "Dělal jsem tyhle chyby mockrát než jsem se naučil je hledat"

---

### Slide 28: Validační Workflow
**Obsah:**
```
5-step proces:

✅ 1. Code Review
   Přečti kód, dává business logic smysl?

✅ 2. Small Sample Test
   LIMIT 10, zkontroluj manuálně

✅ 3. Edge Cases
   NULL values? Duplicates? Outliers?

✅ 4. Spot Check Calculation
   Jeden řádek, spočítej ručně

✅ 5. Business Sense Check
   "100M revenue" → dává to smysl?

⏱️ 2-3 minuty, ušetří hodiny debugging
```
**Poznámky:**
- Timing: 5 min
- "Tahle rutina se vám stane druhou přirozeností"
- Projít příklad validace live

---

### Slide 29: 💪 Cvičení - Najdi Chybu v AI Kódu
**Obsah:**
```
Úkol (10 min):

AI vygeneroval tento SQL na "průměrná cena
produktu podle regionu":

SELECT region, AVG(price) as avg_price
FROM (
  SELECT region, product, AVG(unit_price) as price
  FROM sales GROUP BY region, product
)
GROUP BY region;

❓ Co je špatně? Jak to opravit?

📝 Worksheet: debugging-exercise
```
**Poznámky:**
- Timing: 10 min
- Nech je přemýšlet sami 5 min
- Pak hints: "Podívejte se na inner query... co počítá?"
- Řešení: average-of-averages problém
- Správně: SELECT region, AVG(unit_price) FROM sales GROUP BY region

---

### Slide 30: Propojení AI do Workflow
**Obsah:**
```
End-to-end workflow s AI:

1️⃣ Plánování (ChatGPT/Claude)
   "Jak nejlépe analyzovat sales data?"
   → Dostaneš high-level plán

2️⃣ Implementace (Databricks AI)
   Krok po kroku podle plánu
   → Generuješ SQL, Python, viz

3️⃣ Validace (tvoje hlava)
   Check každý výstup
   → Ujisti se že je správně

4️⃣ Iterace (zpátky k AI)
   "Přidej totals row na konec"
   → Refinement

5️⃣ Dokumentace (AI)
   "Přidej comments vysvětlující kód"
   → Ready pro kolegy
```
**Poznámky:**
- Timing: 5 min
- "AI v každém kroku, ale TY řídíš proces"
- Ukázat konkrétní příklad workflow

---

### Slide 31: GitHub Copilot + Databricks Integration
**Obsah:**
```
Bonus: Copilot přes VS Code

Setup:
1. VS Code + Databricks extension
2. GitHub Copilot subscription
3. Connect to Databricks cluster

Výhody:
• Offline coding s autocomplete
• Git integration
• Debugging tools

📚 Tutorial v materiálech: setup-guide.md

💡 Pro advanced users - nemusíte nyní
```
**Poznámky:**
- Timing: 5 min
- "Není nutné na tento workshop, ale hodí se vědět"
- Quick screenshare pokud čas dovolí
- "VS Code workflow je pro lidi co preferují IDE"

---

### Slide 32: Security & Compliance - Recap
**Obsah:**
```
Připomínka bezpečnosti:

✅ Enterprise AI nástroje (Databricks, Copilot Enterprise)
✅ Anonymizuj patient data
✅ Audit trails
✅ GDPR/HIPAA compliance

❌ Public ChatGPT s production daty
❌ Raw PII v promptech
❌ Clinical results v modelech

📄 Security checklist v cheat sheetu

🚨 83% firem nemá kontroly - nebuďte mezi nimi!
```
**Poznámky:**
- Timing: 3 min
- "Zopakuju protože je to kritické"
- "Jeden security incident = konec AI adoption ve firmě"

---

### Slide 33: 🚀 Závěrečný Projekt
**Obsah:**
```
Čas na vlastní projekt! (30 min)

Vyberte si 1 z 3 scenářů:

A) Geographic: TOP regions pro váš produkt
B) Segmentation: Zákaznické skupiny pro kategorii
C) Time Series: Seasonal trends pro produkt

Deliverable:
• Kompletní notebook s analýzou
• SQL dotazy + vizualizace
• 2-3 key business insights

💡 Použijte všechny techniky z dneška

📢 Za 30 min: 2min prezentace výsledků
```
**Poznámky:**
- Timing: 30 min (studenti pracují)
- Poskytni 3 prepared scenario notebooks
- Intenzivní podpora - to je jejich final test
- Sleduj kdo má zajímavý přístup
- 5 min warning před koncem

---

### Slide 34: Prezentace Projektů (Lightning Talks)
**Obsah:**
```
Každý 2 minuty:

• Jaký use case jste řešili?
• Jak jste použili AI?
• Co bylo nejtěžší?
• 1-2 key insights

🎤 Dobrovolníci? (nebo losuju)

👏 Applause pro všechny!
```
**Poznámky:**
- Timing: 20 min (10 lidí × 2 min)
- Začni s dobrovolníky, pak pozvi další
- Vyzdvihni co kdo udělal dobře
- Sharing je learning - ostatní vidí různé přístupy
- Poděkuj všem za effort

---

## BLOK 5: Wrap-Up & Kam Dál (30 min, 17:00-17:30)

### Slide 35: Co jsme se naučili - Shrnutí
**Obsah:**
```
Dnes jste zvládli:

✅ Anatomii dobrého promptu (4 komponenty)
✅ Few-shot learning & prompt chaining
✅ Databricks AI Assistant (@ mentions, /commands)
✅ Validaci AI výstupů (5-step workflow)
✅ Security best practices (co sdílet, co ne)
✅ 3 reálné farmaceutické use cases

💪 A postavili jste vlastní analýzu!

🎯 Jste připraveni používat AI v práci od zítřka.
```
**Poznámky:**
- Timing: 3 min
- "Tohle není malý achievement - gratuluju"
- Quick recap hlavních bodů

---

### Slide 36: Materiály Co Dostáváte
**Obsah:**
```
📦 Kompletní balíček:

📄 Cheat Sheet - Prompt šablony & best practices
📚 Student Guide - Detailní vysvětlení všeho
📊 Presentation Slides - Dnešní prezentace
📓 Jupyter Notebooks - Všechny hands-on exercise
🔗 Resources - Links na další zdroje

💾 Ke stažení: [LINK]

📧 Email s materiály dostanete do 24h
```
**Poznámky:**
- Timing: 2 min
- Ukázat kde najdou materiály
- "Všechny notebooks jsou vaše - use them!"

---

### Slide 37: Next Steps - Co Dělat Dál
**Obsah:**
```
Doporučený plán:

📅 Tento týden:
• Aplikuj 1 prompt template na vlastní data
• Vytvoř si prompt library (Notion/OneNote)
• Sdílej s týmem

📅 Příští měsíc:
• Automatizuj týdenní report pomocí AI
• Experimentuj s AI Functions
• Postav dashboard full-stack s AI

📅 Dlouhodobě:
• Učit se pokročilé techniky (RAG)
• Sleduj Databricks blog
• Join community forum
```
**Poznámky:**
- Timing: 3 min
- "Malé kroky, konzistentně"
- "Za měsíc budete 5x rychlejší než dnes"

---

### Slide 38: Resources & Další Studium
**Obsah:**
```
📚 Top resources:

Databricks:
• docs.databricks.com/ai-assistant
• Databricks Community Forum

Prompt Engineering:
• learnprompting.org (free course)
• OpenAI Prompt Engineering Guide

Pharma Analytics:
• IntuitionLabs Blog (case studies)
• IQVIA Reports

Komunity:
• r/databricks
• LinkedIn: "Databricks Users"
```
**Poznámky:**
- Timing: 2 min
- "Všechny linky v materiálech"
- "Community je gold - ptejte se, sdílejte"

---

### Slide 39: Q&A
**Obsah:**
```
Otázky? 🙋

• Cokoliv z dnešního dne
• Implementace ve vaší firmě
• Specifické use cases
• Technické detaily

Klidně se ptejte!
```
**Poznámky:**
- Timing: 15 min
- Pokud ticho: "Často se ptají na... [připrav 2-3 otázky]"
- "Můžete se ptát i na věci mimo scope workshopu"
- Nech prostor pro diskusi
- Zapisuj si zajímavé otázky - feedback pro příští workshop

---

### Slide 40: Děkuji & Stay in Touch
**Obsah:**
```
Děkuji za skvělou účast! 🎉

📧 Email: [tvůj email]
💼 LinkedIn: [tvůj LinkedIn]
📁 Materiály: [link na GitHub/Drive]

💬 Máte otázku i za týden? Napište!
📢 Sdílejte co jste vytvořili

🚀 Hodně úspěchů s AI v práci!

#AIAnalytics #Databricks #PharmaData
```
**Poznámky:**
- Timing: 2 min
- "Byl to intenzivní den, zvládli jste to skvěle"
- "Těším se na vaše úspěchy s AI"
- Poděkuj osobně, případně se můžou ptát i po skončení
- Collect feedback forms pokud máš

---

## Poznámky Pro Lektora - Celkově

### Checklist Před Workshopem
- [ ] Databricks workspace připravený (účty pro všechny)
- [ ] Demo data nahrána (@demo_sales_data, @demo_customers, atd.)
- [ ] Prepared notebooks uploadnuté
- [ ] Printed cheat sheets (1 na osobu)
- [ ] Projektor + HDMI adaptéry testováno
- [ ] WiFi credentials pro účastníky
- [ ] Backup: offline kopie všech materiálů

### Timing Management
- **9:00-10:10** Blok 1 (70 min)
- **10:10-10:25** Coffee (15 min)
- **10:25-11:55** Blok 2 (90 min)
- **11:55-13:00** Oběd (65 min)
- **13:00-15:05** Blok 3 (125 min)
- **15:05-15:20** Coffee (15 min)
- **15:20-17:00** Blok 4 (100 min)
- **17:00-17:30** Blok 5 (30 min)

**Buffer:** 30 min celkem - použij pokud něco trvá déle

### Interakce Tips
- Každých 10-15 min nějaká aktivita (questions, hands-on, discussion)
- Jména: poznej si jména prvních 3-4 lidí, používej je
- Energie: maintainuj nadšení, ale buď autentický
- Ptej se: "Jak vám to jde?" během hands-on

### Common Workshop Problems
| Problém | Řešení |
|---------|--------|
| Tech selhání | Backup screenshots/videos, offline notebooks |
| Někdo ztracený | Během breaks individuální help |
| Běží se napřed | Extra advanced cvičení připravené |
| Běží se pozadu | Skip some slides, focus na hands-on |
| Nikdo neodpovídá | Nedělej z toho problém, pokračuj |

### Energy Management (Pro Sebe)
- Dýchej - nerychlit mluvení
- Pij vodu pravidelně
- Během student exercises odpočívej (ne intensely helping celou dobu)
- Oběd: jez lehce, potřebuješ energii odpoledne

### Follow-Up
- Email s materiály do 24h
- Feedback survey (Google Form)
- 1-2 týdny po: "Jak vám to jde?" check-in email
- LinkedIn connection s účastníky

---

**🎯 Cíl Workshopu: Každý odchází s funkční analýzou a confidence používat AI v práci zítra.**

**Hodně štěstí! 🚀**
