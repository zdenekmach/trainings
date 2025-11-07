# Copilot & Databricks pro farmaceutické analýzy - Studijní průvodce

## Úvod

**Co se naučíš:**
- Psát efektivní prompty pro AI nástroje, které ti dávají přesné výsledky
- Používat Databricks AI Assistant pro SQL dotazy, Python analýzy a vizualizace
- Stavět kompletní analytické notebooky s pomocí AI
- Aplikovat AI na reálné farmaceutické use cases (geographic analysis, segmentace, trendy)
- Validovat AI výstupy aby neobsahovaly chyby
- Bezpečně pracovat s citlivými daty

**Proč je to užitečné:**
- Rutinní analýzy uděláš 5-10x rychleji
- Zvládneš složitější úlohy, které by ti předtím zabraly hodiny nebo dny
- Konkurence to už používá - Pfizer, GSK, Moderna šetří 50-70% času pomocí AI
- Budeš produktivnější a budeš mít čas na hlubší insights místo rutiny

**Předpoklady:**
- Základy SQL (SELECT, WHERE, JOIN, GROUP BY)
- Znáš Databricks notebook interface
- Už jsi někdy použil ChatGPT nebo GitHub Copilot

**Časová náročnost:** 3-4 hodiny self-study (nebo 1 den na workshopu)

---

## Jak s tímto materiálem pracovat

1. **Projdi to popořadě** - materiál je strukturovaný od základů k pokročilým technikám
2. **Zkoušej průběžně** - každý příklad si zkus v Databricks, ne jen čti
3. **Validuj výsledky** - vždy zkontroluj co AI vygeneruje, ne slepě důvěřuj
4. **Vytvoř si knihovnu promptů** - funkční prompty si ulož pro opakované použití
5. **Aplikuj na vlastní data** - vezmi svoje reálné use cases a řeš je pomocí AI

---

## Část 1: Základy AI Assistentů pro Analytics

### Co se dozvíš
Jak fungují AI nástroje, jaké jsou jejich možnosti a limity, a jak je správně používat.

### Přehled nástrojů

**Databricks AI Assistant:**
- Integrovaný v notebooks a SQL editoru
- Rozumí kontextu workspace (Unity Catalog metadata)
- Modes: Chat, Edit, Agent
- Funkce: Generuje kód, debuguje, vysvětluje, opravuje
- @ mentions pro reference tabulek
- **Kdy použít:** Primární nástroj pro práci s daty v Databricks

**GitHub Copilot:**
- AI pair programmer v IDE (VS Code, SSMS)
- Autocomplete celých bloků kódu
- Funguje offline po initial setupu
- **Kdy použít:** Psaní kódu mimo Databricks, general programming

**ChatGPT / Claude:**
- Brainstorming a plánování
- Vysvětlování konceptů
- Generating text, dokumentace
- **Kdy použít:** High-level plánování, ne pro production kód s citlivými daty

### Jak fungují Large Language Models (LLM)

**V kostce:**
- Trénované na obrovských množstvích textu a kódu
- Predikují "co pravděpodobně přijde dál"
- Nerozumí obsahu - rozpoznávají patterny
- Nemají přístup k tvým datům (pokud jim je nepošleš v promptu)

**Co umí dobře:**
✅ Generovat SQL dotazy z popisu
✅ Vysvětlit složitý kód
✅ Najít chyby v syntaxi
✅ Navrhovat patterny a best practices
✅ Psát dokumentaci a komentáře

**Co neumí / dělá špatně:**
❌ Složité výpočty (arithmetic)
❌ Business logic bez kontextu
❌ Aktuální data (knowledge cutoff)
❌ Rozpoznat co je "správně" bez validace
❌ Pamatovat si předchozí konverzace (nový chat = nový kontext)

**Hallucinations (halucinace):**
- AI si vymýšlí názvy sloupců, tabulek nebo funkcí co neexistují
- Generuje kód co vypadá správně ale má subtilní chyby
- **Jak předejít:** @ mention tabulky, explicitní kontext, validuj výstupy

---

## Část 2: Prompt Engineering - Základ úspěchu

### Co se dozvíš
Jak psát prompty, které dávají konzistentní a přesné výsledky.

### Anatomie dobrého promptu

**4 klíčové komponenty:**

```
┌─────────────────────────────────────────────┐
│ 1. ROLE (kdo je AI)                        │
│ "Jsi expert na SQL analýzy pro pharma"     │
└─────────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────────┐
│ 2. KONTEXT (jaká máš data)                 │
│ "Tabulka @sales: product, region, revenue" │
└─────────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────────┐
│ 3. ÚKOL (co chceš)                         │
│ "Najdi TOP 10 produktů v Praze za Q1"     │
└─────────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────────┐
│ 4. FORMÁT (jak to chceš)                   │
│ "SQL dotaz + bar chart + komentáře"       │
└─────────────────────────────────────────────┘
```

**Příklad ŠPATNÉHO promptu:**
```
Ukaž mi prodeje
```
→ Vágní, AI neví co přesně chceš, bude hádat

**Příklad DOBRÉHO promptu:**
```
Kontext: Mám tabulku @sales_data s columns: product_id, product_name,
region_name, sale_date, revenue_czk.

Úkol: Pro produkt "Ibuprofen 400mg" najdi TOP 10 regionů podle celkového
revenue v roce 2024.

Výstup: SQL dotaz + horizontal bar chart seřazený od nejvyššího.
Zobraz revenue v milionech Kč.
```
→ Specifické, AI má všechno co potřebuje

### Few-Shot Learning (učení z příkladů)

**Princip:** Dej AI 2-3 příklady PŘED hlavním úkolem.

**Bez few-shot:**
```
Prompt: "Najdi TOP zákazníky"
AI response: [generuje různé formáty, někdy správně, někdy ne]
```

**S few-shot:**
```
Tady jsou 2 příklady stylu dotazů co chci:

Example 1:
Request: "TOP produkty podle revenue"
SQL: SELECT product_name, SUM(revenue) as total
     FROM sales
     GROUP BY product_name
     ORDER BY total DESC
     LIMIT 10;

Example 2:
Request: "Prodeje po měsících"
SQL: SELECT DATE_TRUNC('month', sale_date) as month, SUM(revenue)
     FROM sales
     GROUP BY month
     ORDER BY month;

---
Teď prosím stejný styl pro: "TOP zákazníci podle počtu objednávek"
```
→ AI rozumí přesně jaký formát chceš

**Kdy použít few-shot:**
- Chceš specifický coding style (naming, formatting)
- Potřebuješ konzistentní výstupy pro sérii dotazů
- AI ti generuje špatný formát

### Prompt Chaining (řetězení)

**Princip:** Rozděl složitý úkol na menší kroky, kde output kroku 1 → input kroku 2.

**Místo jednoho mega-promptu:**
```
"Udělej kompletní analýzu prodejů včetně trendu, segmentace a predikce."
→ Příliš komplexní, AI udělá chyby
```

**Rozděl na kroky:**
```
Krok 1: "Načti sales data za Q4 2024, agreguj podle produktů a regionů."
→ Získáš agregovaná data

Krok 2: "Z těchto agregovaných dat identifikuj TOP 3 produkty podle revenue."
→ Filtrovaný subset

Krok 3: "Pro tyto 3 produkty analyzuj trend po týdnech."
→ Time series pro top produkty

Krok 4: "Vytvoř multi-line chart s trendy."
→ Vizualizace
```
→ Každý krok je jednoduchý, snižuješ šanci na chybu

### Praktické cvičení

**Úkol 1:** Přepiš tento vágní prompt na dobrý prompt:
```
Vágní: "Ukaž mi zajímavé věci o zákaznících"
```

**Řešení:**
```
Kontext: Mám tabulku @customers (customer_id, age_group, region,
registration_date) a @orders (customer_id, order_value, order_date,
product_category).

Úkol: Analyzuj chování zákazníků:
1. Segmentuj podle průměrné order_value (low/medium/high spenders)
2. Pro každý segment urči: count, průměrná age_group, top region,
   průměrná frekvence objednávek
3. Identifikuj zajímavé patterny (např. high spenders preferují určité
   product_category)

Výstup: SQL dotazy + tabulka se segmenty + 2-3 key insights
```

---

## Část 3: Databricks AI Assistant - Praktický průvodce

### Co se dozvíš
Jak efektivně používat Databricks AI Assistant v notebookech.

### Základní ovládání

**Spuštění AI Assistenta:**
- **Cmd/Ctrl + I** - Inline assistant (rychlé úpravy aktuální buňky)
- **Chat panel** - Klik na AI ikonu vpravo nahoře (delší konverzace)
- **/ commands** - /ask, /explain, /fix, /doc

**@ Mentions:**
```
@sales_data → AI načte schéma tabulky z Unity Catalog
@customers @orders → Mentions více tabulek, AI pochopí relationships
```

**Workflow:**
```
1. Otevři notebook
2. Nová buňka → Cmd+I
3. Napiš prompt (s @ mentions)
4. Tab pro přijetí / Esc pro zamítnutí
5. Spusť kód → validuj výstup
6. Iteruj pokud potřeba
```

### Praktické use cases

**Use Case 1: Generování SQL z popisu**

```
Prompt v Databricks:
"Kontext: @sales_data table.
Úkol: Najdi TOP 10 produktů podle revenue v regionu Praha za Q1 2024.
Výstup: SQL s komentáři."
```

**AI vygeneruje:**
```sql
-- TOP 10 produktů v Praze za Q1 2024
SELECT
    product_name,
    SUM(revenue_czk) as total_revenue,
    COUNT(*) as transaction_count,
    AVG(revenue_czk) as avg_transaction
FROM sales_data
WHERE region_name = 'Praha'
  AND sale_date >= '2024-01-01'
  AND sale_date < '2024-04-01'
GROUP BY product_name
ORDER BY total_revenue DESC
LIMIT 10;
```

**Use Case 2: Debugging chyby**

```
Máš kód:
SELECT product, SUM(revenue)
FROM sales
WHERE region = Prague
GROUP BY product;

Chyba: column "prague" does not exist

Prompt: "/fix tento dotaz, chyba je že Prague není quoted"
```

**AI opraví:**
```sql
SELECT product, SUM(revenue)
FROM sales
WHERE region = 'Prague'  -- Přidán quotes
GROUP BY product;
```

**Use Case 3: Vysvětlení složitého kódu**

```
Kolega ti poslal složitý SQL:
SELECT ... [200 řádků nested subqueries] ...

Prompt: "/explain co tento dotaz dělá krok po kroku"
```

**AI rozepíše:**
```
Tento dotaz dělá:
1. Innermost subquery: Filtruje sales za Q4
2. Second level: Agreguje podle produktů
3. Outer query: Počítá percentile ranks
4. Final: Filtruje jen top 20%
...
```

### Vyzkoušej si to

**Cvičení:** Otevři Databricks notebook a zkus:
1. @ mention jakoukoliv tabulku v tvém workspace
2. Požádej AI o schéma tabulky a prvních 5 řádků
3. Vygeneruj simple SELECT dotaz
4. Spusť ho a zkontroluj výsledek

---

## Část 4: Bezpečnost a Compliance

### Co se dozvíš
Jak bezpečně pracovat s AI nástroji a neporušit GDPR/HIPAA/company policies.

### Kritická statistika

**83% farmaceutických firem nemá automated controls** proti úniku citlivých dat do AI nástrojů. To znamená:
- Zaměstnanci paste patient data do ChatGPT
- Molekulární struktury končí v public AI modelech
- Clinical trial results leakují bez audit trail

**GDPR problém:** Data embedovaná v AI modelech **nelze smazat** → Right to be Forgotten violation.

### Security Checklist

**✅ BEZPEČNÉ sdílet s AI:**
- Anonymizovaná data (patient_id místo jmen)
- Aggregované statistiky (průměry, součty bez PII)
- Demo/synthetic data
- SQL query struktury (bez actual values)
- Chybové hlášky (odstraň PII)
- Názvy tabulek a sloupců (pokud neobsahují sensitive info)

**❌ NIKDY nesdílet:**
- Patient identifiable data (jména, rodná čísla, adresy)
- Molekulární struktury léků (competitive advantage)
- Clinical trial raw results
- API keys, credentials, connection strings
- Interní business strategie
- Pricing data, margins

**Pravidlo palce:** Pokud by data na billboardu:
- Porušila GDPR → NESDÍLEJ
- Poškodila pacienty → NESDÍLEJ
- Dala konkurenci advantage → NESDÍLEJ

### Enterprise vs. Public AI

**Public AI (ChatGPT Free, Claude Free):**
- ❌ Data se používají pro training
- ❌ Žádný audit trail
- ❌ Nelze smazat data z modelu
- ❌ Není GDPR/HIPAA compliant

**Enterprise AI (Databricks AI, GitHub Copilot Enterprise):**
- ✅ Data se nepoužívají pro training
- ✅ Audit logs
- ✅ Data residency controls
- ✅ Compliance certifications

**Doporučení:**
- Používej **enterprise nástroje** pro production work
- Public AI jen pro learning, brainstorming (s fake data)

### Anonymizace dat

**Před sdílením s AI:**
```python
# ŠPATNĚ
df_original = spark.sql("SELECT customer_name, birthdate, revenue FROM customers")
# → paste do ChatGPT

# DOBŘE
df_anonymized = spark.sql("""
    SELECT
        MD5(customer_name) as customer_id,  -- Hash místo jména
        YEAR(birthdate) as birth_year,       -- Rok místo přesného data
        revenue
    FROM customers
""")
# → můžeš použít s AI
```

---

## Část 5: Validace AI výstupů

### Co se dozvíš
Jak rozpoznat a opravit chyby v AI generovaném kódu.

### Časté chyby AI

**1. Average-of-Averages problém**

```sql
-- AI vygeneruje ŠPATNĚ:
SELECT region, AVG(avg_revenue) as final_avg
FROM (
    SELECT product, region, AVG(revenue) as avg_revenue
    FROM sales GROUP BY product, region
)
GROUP BY region;
```
→ Počítá průměr z průměrů, ne vážený průměr

**SPRÁVNĚ:**
```sql
SELECT region, AVG(revenue) as avg_revenue
FROM sales
GROUP BY region;
```

**2. Duplicate counts problém**

```sql
-- AI vygeneruje:
SELECT COUNT(customer_id) FROM orders JOIN customers ...
```
→ Pokud customer má více orders, počítá ho vícekrát

**SPRÁVNĚ:**
```sql
SELECT COUNT(DISTINCT customer_id) FROM orders JOIN customers ...
```

**3. Ignorování business rules**

```
Prompt: "Prodeje za fiscal year 2024"
AI: WHERE YEAR(date) = 2024
```
→ AI neví že vaše fiscal year je March-February

**SPRÁVNĚ (v promptu specifikuj):**
```
"Fiscal year 2024 je od 2024-03-01 do 2025-02-28"
```

### Validační workflow

**Krok 1: Code review**
- Přečti si kód, dává smysl business logic?
- Jsou tam DISTINCT, WHERE filters, správné JOINy?

**Krok 2: Small sample test**
```sql
-- Přidej LIMIT 10
SELECT ... FROM ... LIMIT 10;
```
- Zkontroluj několik řádků manuálně
- Dávají čísla smysl?

**Krok 3: Edge cases**
```sql
-- Co když NULL values?
SELECT ... WHERE column IS NOT NULL

-- Co když duplicates?
SELECT ... , COUNT(*) as dup_check
GROUP BY ...
HAVING COUNT(*) > 1
```

**Krok 4: Spot check calculation**
- Vezmi jeden řádek, spočítej ručně (kalkulačka)
- Shoduje se s AI výsledkem?

**Krok 5: Business sense check**
- "TOP produkt má 100M revenue" → dává to smysl nebo je to chyba o 3 řády?

### Vyzkoušej si to

**Cvičení: Najdi chybu v AI kódu**

```sql
-- AI vygeneroval tento dotaz na "průměrná cena produktu podle regionu":
SELECT
    region,
    AVG(price) as avg_price
FROM (
    SELECT
        region,
        product,
        AVG(unit_price) as price
    FROM sales
    GROUP BY region, product
)
GROUP BY region;
```

**Co je špatně?** (řešení na konci)

---

## Část 6: Reálné Use Cases - Farmaceutická analytika

### Geographic Sales Analysis

**Business otázka:** "Které městské části Prahy mají nejvyšší prodeje Ibuprofenu?"

**Postup s AI:**

```
Krok 1: Exploration
Prompt: "Zobraz mi schéma @sales_data a sample 5 řádků pro product LIKE '%Ibuprofen%'"

Krok 2: Aggregation
Prompt: "Pro produkt 'Ibuprofen 400mg' agreguj total revenue a quantity
podle city_district v Praze za posledních 12 měsíců. Seřaď od nejvyššího."

Krok 3: Visualization
Prompt: "Z předchozích výsledků vytvoř horizontal bar chart, TOP 10 districts,
color gradient (highest = dark blue)"
```

**Výstup:** Map nebo bar chart s insights.

### Customer Segmentation

**Business otázka:** "Jaké skupiny zákazníků (podle demografie a chování) nakupují naše Pain Relief produkty?"

**Postup s AI:**

```
Krok 1: Data preparation
Prompt: "JOIN @customers a @orders, filtruj category = 'Pain Relief',
vytvoř features: avg_order_value, order_frequency, recency_days"

Krok 2: Segmentation
Prompt: "Segmentuj zákazníky do 4 skupin podle RFM (Recency, Frequency,
Monetary value). Pro každý segment urči size, charakteristiky, top age_group."

Krok 3: Profiling
Prompt: "Pro každý segment vytvoř profil: demographics, behavior patterns,
product preferences. Navrhni marketing recommendations."
```

**Výstup:** Segment profily + business recommendations.

### Time Series & Seasonality

**Business otázka:** "Kdy je nejvyšší poptávka po produktech proti chřipce? Je tam seasonality?"

**Postup s AI:**

```
Krok 1: Time aggregation
Prompt: "Pro category 'Cold & Flu' agreguj sales by week za posledních 2 roky.
Include year-over-year comparison."

Krok 2: Trend analysis
Prompt: "Identifikuj seasonal patterns - ve kterých měsících/týdnech jsou peaks?
Vypočítej průměrný růst/pokles week-over-week."

Krok 3: Visualization
Prompt: "Line chart s 2 lines (2023 vs 2024), highlight peak periods."
```

**Výstup:** Seasonal insights pro inventory planning.

---

## Shrnutí a Next Steps

### Co teď umíš

✅ Psát efektivní prompty (4 komponenty: role, kontext, úkol, formát)
✅ Používat few-shot learning pro lepší výsledky
✅ Pracovat s Databricks AI Assistant (@ mentions, /commands)
✅ Bezpečně zacházet s citlivými daty (co sdílet, co ne)
✅ Validovat AI výstupy (common errors, validační workflow)
✅ Aplikovat AI na farmaceutické use cases

### Doporučené next steps

**1. Praktické procvičení (tento týden):**
- Vezmi 3 svoje reálné analýzy z minulého měsíce
- Zkus je zopakovat s pomocí AI - měř čas
- Porovnej: kolik času jsi ušetřil/a?

**2. Vytvoř si knihovnu promptů (do 2 týdnů):**
- Každý prompt co funguje → ulož do Notion/OneNote
- Organizuj podle typu (SQL generation, debugging, visualization)
- Sdílej s týmem

**3. Učit se pokročilé techniky (příští měsíc):**
- RAG (Retrieval Augmented Generation) pro práci s dokumentací
- AI Functions v Databricks (ai_query, sentiment analysis)
- Prompt optimization (A/B testing promptů)

**4. Experimentuj s reálnými projekty:**
- Postav dashboard kompletně s AI
- Automatizuj týdenní report pomocí AI + Databricks Jobs
- Vytvoř chatbot pro business users (AI + SQL warehouse)

### Užitečné zdroje

**Databricks:**
- [Databricks AI Assistant Documentation](https://docs.databricks.com/notebooks/databricks-assistant-examples.html)
- [AI Functions Guide](https://docs.databricks.com/sql/language-manual/functions/ai_query.html)
- Databricks Community Forum

**Prompt Engineering:**
- [Learn Prompting (Free Course)](https://learnprompting.org/) - Kompletní guide
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering) - Best practices
- [Awesome ChatGPT Prompts (GitHub)](https://github.com/f/awesome-chatgpt-prompts) - Inspiration

**Pharma Analytics:**
- IntuitionLabs Blog - AI in Pharma case studies
- IQVIA Reports - Market analytics trends

**Komunity:**
- Reddit: r/databricks, r/datascience
- LinkedIn: "Databricks Users" group
- Stack Overflow: databricks tag

---

## Řešení cvičení

### Část 2 - Úkol: Přepis vágního promptu

**Původní:**
```
"Ukaž mi zajímavé věci o zákaznících"
```

**Přepsané:**
```
Kontext: Mám tabulku @customers (customer_id, age_group, region,
registration_date) a @orders (customer_id, order_value, order_date,
product_category).

Úkol: Analyzuj chování zákazníků:
1. Segmentuj podle průměrné order_value (low/medium/high spenders)
2. Pro každý segment urči: count, průměrná age_group, top region,
   průměrná frekvence objednávek
3. Identifikuj zajímavé patterny (např. high spenders preferují určité
   product_category)

Výstup: SQL dotazy + tabulka se segmenty + 2-3 key insights
```

### Část 5 - Úkol: Najdi chybu v kódu

**Kód:**
```sql
SELECT
    region,
    AVG(price) as avg_price
FROM (
    SELECT
        region,
        product,
        AVG(unit_price) as price
    FROM sales
    GROUP BY region, product
)
GROUP BY region;
```

**Chyba:** Average-of-averages problém!

Inner query počítá průměrnou cenu pro každý produkt v regionu. Outer query pak počítá průměr těchto průměrů, což není vážený průměr.

Příklad proč je to špatně:
- Region A: Product 1 (10 sales, avg price 100 Kč), Product 2 (1000 sales, avg price 50 Kč)
- Špatný výpočet: (100 + 50) / 2 = 75 Kč
- Správný výpočet by měl vážit podle počtu sales → ~52 Kč

**Správné řešení:**
```sql
SELECT
    region,
    AVG(unit_price) as avg_price
FROM sales
GROUP BY region;
```

Nebo pokud chceš vážený průměr s quantity:
```sql
SELECT
    region,
    SUM(unit_price * quantity) / SUM(quantity) as weighted_avg_price
FROM sales
GROUP BY region;
```

---

## Máš otázku? Nevíš si rady?

**Databricks Community Forum:**
- https://community.databricks.com/
- Hledej podobné problémy, často už někdo řešil

**Stack Overflow:**
- Tag: [databricks] [sql] [ai]
- Při dotazu zahrň: code snippet, error message, co jsi už zkusil/a

**Jak správně položit otázku:**
1. Popis co se snažíš udělat (business goal)
2. Co jsi už zkusil/a
3. Co je konkrétní problém (error message, neočekávaný výsledek)
4. Minimální reproducible example
5. Verze Databricks/software

**Časté problémy:**

| Problém | Řešení |
|---------|--------|
| AI nereaguje v Databricks | Zkontroluj workspace permissions, zkus restart kernelu |
| @ mention nefunguje | Tabulka musí být v Unity Catalog, zkus plný název: catalog.schema.table |
| SQL dotaz je strašně pomalý | Přidej WHERE filtr na datu dřív, zkontroluj indexy, použij LIMIT pro test |
| AI generuje nesmyslné názvy sloupců | Explicit @ mention tabulky, nebo vypiš sloupce v promptu |

---

**Úspěšného učení! 🚀**

*Materiál vytvořen pro workshop "Copilot & Databricks pro farmaceutické analýzy" | 2025*
