# Copilot & Databricks pro farmaceutické analýzy - Cheat Sheet

## Hlavní myšlenky (co si odnést)

- **Kvalita promptu = kvalita výsledku:** 80% úspěchu je v tom, jak zadáš požadavek AI. Vágní prompt ("ukaž mi data") = vágní odpověď. Specifický prompt s kontextem = přesný výsledek.

- **AI je asistent, ne expert:** Vždycky validuj co AI vygeneruje. Business logic chyby jsou časté (počítá lidi 2x, dělá average-of-averages). Tvoje hlava + AI hands = nejrychlejší combo.

- **Bezpečnost není optional:** NIKDY nesdílej raw patient data, molekulární struktury nebo clinical results s public AI. Používej enterprise nástroje (Databricks AI, GitHub Copilot Enterprise) a anonymizuj data.

- **Few-shot learning je твoje superschopnost:** Dej AI 2-3 příklady co chceš a výsledky budou 5x lepší než bez příkladů.

- **@ mention = instant kontext:** V Databricks stačí napsat `@tabulka_prodeje` a AI hned ví o čem mluvíš. Nemusíš popisovat celé schéma.

## Rychlý přehled

### Databricks AI Assistant - Základní ovládání

**Co to je:** AI asistent integrovaný v Databricks notebooks a SQL editoru - generuje kód, opravuje chyby, vysvětluje dotazy

**Kdy to použít:**
- Když potřebuješ napsat SQL dotaz ale nevíš přesnou syntax
- Debugging - když kód hlásí chybu a nevíš proč
- Rychlá vizualizace dat
- Vysvětlení komplexního kódu od kolegy

**Jak na to:**
- **Cmd/Ctrl + I** - otevřít AI asistent inline (rychlá úprava kódu)
- **Chat panel** - otevřít boční panel pro delší konverzaci
- **@mention tabulky** - např. `@sales_data` pro automatický kontext
- **Příkazy:** `/ask`, `/explain`, `/fix`, `/doc`

### Anatomie dobrého promptu

**Co to je:** Struktura promptu, která konzistentně funguje

**Kdy to použít:** Vždycky když chceš od AI něco konkrétního

**Jak na to - 4 komponenty:**

```
1. ROLE: "Jsi expert na SQL analýzy pro farmaceutický průmysl"

2. KONTEXT: "Mám tabulku sales_data s: product_id, region, date, revenue, quantity"

3. ÚKOL: "Najdi TOP 10 produktů podle celkového revenue v Praze za Q1 2024"

4. FORMÁT: "Výstup: SQL dotaz s vysvětlením jednotlivých kroků"
```

**Příklad kompletního promptu:**
```
Jsi expert na SQL analýzy. Mám tabulku @sales_data (columns: product_id,
region_name, sale_date, revenue_czk). Najdi TOP 10 produktů podle celkového
revenue v regionu 'Praha' za Q1 2024. Výstup: SQL dotaz s komentáři.
```

### Few-Shot Learning (učení z příkladů)

**Co to je:** Dáš AI 2-3 příklady před tím, než zadáš hlavní úkol

**Kdy to použít:** Když potřebuješ specifický formát nebo styl kódu

**Jak na to:**

```
Tady jsou 2 příklady jak chci dotazy:

Example 1:
Input: "TOP zákazníci podle revenue"
Output: SELECT customer_id, SUM(revenue) as total
        FROM orders
        GROUP BY customer_id
        ORDER BY total DESC
        LIMIT 10;

Example 2:
Input: "Prodeje po měsících"
Output: SELECT DATE_TRUNC('month', date) as month, SUM(revenue)
        FROM sales
        GROUP BY month
        ORDER BY month;

Teď udělej podobný dotaz pro: "TOP produkty podle počtu objednávek"
```

### Security Checklist - Co sdílet s AI?

| ✅ BEZPEČNÉ | ❌ NIKDY |
|------------|----------|
| Anonymizovaná demo data | Patient data (jména, rodná čísla) |
| Agregované statistiky | Molekulární struktury léků |
| SQL query struktury | Clinical trial results (raw) |
| Mock/synthetic data | Interní business strategie |
| Názvy tabulek/sloupců | API keys, credentials |
| Chybové hlášky (bez PII) | Competitive intelligence |

**Pravidlo:** Pokud by data na billboardu poškodila firmu nebo pacienty → NESDÍLEJ s AI.

## Užitečné tipy a triky

- **Tip 1: Začni s LIMIT 10** - Vždycky nejdřív otestuj dotaz na malém samplu. Ušetříš čas když je chyba a zjistíš jestli výsledky dávají smysl.

- **Tip 2: @ mention více tabulek najednou** - `@sales_data @products @regions` a AI pochopí joins mezi nimi automaticky.

- **Tip 3: Požádej AI o vysvětlení PŘED generováním kódu** - "Nejdřív mi napiš kroky jak bys to vyřešil, pak teprve kód." Často objevíš chybu v logice dřív než AI začne psát.

- **Tip 4: Iteruj, neopravuj ručně** - Když AI kód není dobře, neupravuj ho sám. Řekni AI co je špatně: "Tento dotaz počítá každého zákazníka 2x, oprav to pomocí DISTINCT."

- **Tip 5: Cmd+I na konci buňky** - Když dáš Cmd+I na konci kódu, AI modifikuje jen kód pod kurzorem. Super pro targeted úpravy.

- **Tip 6: Ulož si fungující prompty** - Když najdeš prompt co skvěle funguje, ulož si ho do Notion/OneNote jako šablonu. Příště jen zkopíruješ a upravíš detaily.

## Prompt šablony - Copy & Paste Ready

### Šablona 1: TOP N Analýza

```
Analyza TOP produktů/zákazníků/regionů podle metriky X.

Kontext: Mám tabulku @[TABULKA] s columns: [SEZNAM_SLOUPCŮ]

Úkol: Najdi TOP [N] [CO - produkty/zákazníci/regiony] podle [METRIKA - revenue/quantity/count]
v [FILTR - region/časové období/segment] za [OBDOBÍ].

Výstup: SQL dotaz + vizualizace (bar chart)
```

**Příklad použití:**
```
Kontext: Mám tabulku @sales_data s columns: product_id, product_name, region,
sale_date, revenue_czk, quantity

Úkol: Najdi TOP 10 produktů podle celkového revenue v regionu Praha za Q1 2024.

Výstup: SQL dotaz + bar chart
```

### Šablona 2: Segmentace zákazníků

```
Segmentace zákazníků/produktů podle chování nebo charakteristik.

Kontext: Mám tabulky @[HLAVNÍ_TABULKA] a @[DIMENZE_TABULKY]

Úkol: Segmentuj [CO] podle [KRITÉRIA - nákupní frekvence/průměrná hodnota/kategorie].
Vytvoř [POČET] segmentů a pro každý urči:
- Velikost segmentu (počet + %)
- Charakteristiky (průměry, top hodnoty)
- Klíčové insights

Výstup: SQL dotazy + tabulka se segmenty + vizualizace distribuce
```

**Příklad použití:**
```
Kontext: Mám @customers (customer_id, age_group, region) a
@orders (customer_id, product_category, order_value, order_date)

Úkol: Segmentuj zákazníky podle nákupního chování. Vytvoř 3-4 segmenty
(např. high-value frequent, low-value frequent, occasional, at-risk).

Výstup: SQL + segment profily + pie chart
```

### Šablona 3: Time Series analýza

```
Analýza trendu v čase - prodeje, poptávka, seasonality.

Kontext: Mám tabulku @[TABULKA] s časovou řadou: [DATE_COLUMN], [VALUE_COLUMN]

Úkol: Analyzuj trend [METRIKY] v čase pro [SCOPE - produkt/region/kategorie].
Zahrň:
- Agregace po [PERIOD - den/týden/měsíc/čtvrtletí]
- Identifikace peaků a dips
- Seasonality (pokud relevantní)
- Year-over-year comparison (pokud mám 2+ roky dat)

Výstup: SQL + line chart s trendem
```

**Příklad použití:**
```
Kontext: Mám @sales_data (sale_date, product_id, revenue_czk, region)

Úkol: Analyzuj trend revenue pro produkt "Aspirin 500mg" v regionu Morava
za posledních 12 měsíců. Agregace po měsících. Zahrň srovnání s předchozím rokem.

Výstup: SQL + line chart
```

### Šablona 4: Geographic Analysis

```
Geografická analýza - heatmapy, top regiony, distribuce.

Kontext: Mám @[TABULKA] s geo daty: [GEO_COLUMN - region/city/district]

Úkol: Analyzuj [METRIKA] podle geografické lokace [LEVEL - kraj/okres/městská část].
Najdi:
- TOP a BOTTOM regiony
- Distribuce metriky (kde je concentration)
- Anomálie (regiony s výrazně jiným chováním)

Výstup: SQL + vizualizace (map pokud možné, jinak bar chart)
```

**Příklad použití:**
```
Kontext: Mám @sales_data (city_district, product_category, revenue_czk)

Úkol: Analyzuj prodeje kategorie "Pain Relief" podle městských částí Prahy.
Najdi TOP 5 a BOTTOM 5 částí, urči kde je nejvyšší concentration revenue.

Výstup: SQL + horizontal bar chart (seřazený)
```

### Šablona 5: Debugging & Fix

```
Když máš chybu v kódu a nevíš jak opravit.

Tento kód mi vrací chybu:
```[ТВŮJ KÓD]```

Chyba: [ERROR MESSAGE]

Kontext: Snažím se [CO CHCEŠ UDĚLAT]. Tabulky: [SEZNAM TABULEK A RELEVANTNÍCH SLOUPCŮ]

Úkol: Identifikuj problém a oprav kód. Vysvětli co bylo špatně.
```

## Praktický příklad - End-to-End

**Situace:** Potřebuješ analyzovat které městské části Prahy mají nejvyšší prodeje produktu "Ibuprofen 400mg" v Q4 2024 a vytvořit vizualizaci pro management meeting.

**Krok 1: Prompt pro data exploration**
```
Kontext: Mám tabulku @sales_data. Ukaž mi schéma (columns + datové typy)
a prvních 5 řádků pro produkt obsahující "Ibuprofen".
```

**Krok 2: Prompt pro analýzu**
```
Kontext: Tabulka @sales_data má: product_name, city_district, sale_date,
revenue_czk, quantity_sold.

Úkol: Pro produkt "Ibuprofen 400mg" najdi TOP 10 městských částí Prahy
podle celkového revenue v Q4 2024 (říjen-prosinec).

Výstup: SQL dotaz s těmito sloupci:
- city_district
- total_revenue (v Kč, formát s tisíci)
- total_quantity
- avg_price_per_unit
Seřaď od nejvyššího revenue.
```

**Krok 3: Prompt pro vizualizaci**
```
Z předchozího výsledku vytvoř horizontal bar chart:
- X-axis: total_revenue
- Y-axis: city_district (seřazený od nejvyššího)
- Barvy: gradient (highest = tmavě modrá, lowest = světle modrá)
- Title: "TOP 10 městských částí - Ibuprofen 400mg prodeje Q4 2024"
- Zobraz hodnoty na barech (v mil. Kč)
```

**Vysvětlení:** Rozdělili jsme komplexní úkol na 3 menší kroky. AI dělá jednu věc po druhé, snižuje se šance na chybu. Každý krok validuješ před pokračováním.

## Nejčastější chyby a jak je řešit

| Problém | Řešení |
|---------|--------|
| **AI vrací generický kód, ne co potřebuješ** | Přidej víc kontextu - názvy tabulek, sloupce, business pravidla. Ukaž 1-2 příklady (few-shot). |
| **SQL dotaz vrací duplicity** | Prompt: "Tento dotaz počítá záznamy vícekrát, přidej DISTINCT nebo uprav JOIN aby každý záznam byl jen jednou." |
| **Average-of-averages problém** | AI počítá průměr průměrů místo vážený průměr. Řekni: "Počítej agregaci na raw data, ne průměr z už agregovaných hodnot." |
| **AI "halucinuje" - vymýšlí si názvy sloupců** | @ mention tabulku aby AI viděl skutečné schéma. Nebo explicitně vypiš sloupce v promptu. |
| **Výsledky vypadají divně ale nevíš proč** | Spusť dotaz s LIMIT 10, manuálně zkontroluj. Pak požádej AI: "Vysvětli tento dotaz krok po kroku, co dělá každá část." |
| **Kód funguje ale je strašně pomalý** | "Tento dotaz běží 5 minut, optimalizuj ho - přidej indexy, zlepši JOINy nebo omez data časovým filtrem dřív." |
| **AI ignoruje část mého promptu** | Rozděl prompt na kroky: "Nejdřív udělej X, pak Y, nakonec Z." Nebo čísla kroky: "1. ... 2. ... 3. ..." |
| **Nejsem si jistý jestli AI výsledek je správně** | Požádej o vysvětlení: "Vysvětli business logiku tohoto dotazu. Co přesně počítá a jakými kroky?" Pak porovnej s očekáváním. |

## Databricks AI Assistant - Klávesové zkratky

| Zkratka | Co to dělá |
|---------|------------|
| **Cmd/Ctrl + I** | Otevřít inline AI asistent (rychlé úpravy kódu) |
| **Tab** | Přijmout AI suggestion |
| **Esc** | Zavřít AI suggestion/panel |
| **/** v chatu | Zobrazit dostupné příkazy (/ask, /explain, /fix, /doc) |
| **@** v chatu | Začít mention tabulky (autocomplete se objeví) |
| **Shift + Enter** | Nový řádek v chat promptu (bez odeslání) |

## Workflow - Jak pracovat s AI efektivně

**1. Plánování (v ChatGPT nebo Copilot Chat):**
```
"Potřebuji analyzovat prodeje Aspirinu podle regionů za Q4.
Jaký je nejlepší postup? Jaké kroky bych měl udělat?"
```
→ AI ti dá high-level plán

**2. Implementace (v Databricks AI Assistant):**
```
"Krok 1: Načti data z @sales_data pro produkt Aspirin, Q4 2024,
agreguj podle regionu."
```
→ AI generuje SQL

**3. Validace (tvoje hlava):**
- Spusť LIMIT 10, zkontroluj výsledky
- Dávají čísla smysl?
- Zkus edge case (co když NULL hodnoty?)

**4. Iterace (zpátky k AI):**
```
"Výsledky vypadají dobře, ale chybí mi celkový součet.
Přidej řádek TOTAL na konec výsledků."
```

**5. Dokumentace (AI tě ušetří času):**
```
"Přidej komentáře k tomuto kódu aby kolega pochopil co dělá."
```

## Kam dál

**Databricks dokumentace:**
- [Databricks AI Assistant Examples](https://docs.databricks.com/notebooks/databricks-assistant-examples.html)
- [AI Functions - Built-in AI capabilities](https://docs.databricks.com/sql/language-manual/functions/ai_query.html)

**Prompt Engineering:**
- [Learn Prompting (Free Course)](https://learnprompting.org/)
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)

**Komunity:**
- Databricks Community Forum
- Reddit: r/databricks
- LinkedIn: "Databricks Users" group

**Praktické cvičení:**
- Vezmi svoje reálné use case z práce (anonymizuj data)
- Zkus ho vyřešit pomocí AI - sleduj kolik času to ušetří
- Sdílej fungující prompty s týmem

---

**💡 Hlavní takeaway:** AI je tvůj pair programmer. Ty znáš byznys a data, AI zná syntax a patterny. Společně jste 10x rychlejší než sami.

**Úspěšného analytika s AI:**
1. Konkrétní prompty s kontextem
2. Vždy validovat výsledky
3. Bezpečnost na prvním místě
4. Iterovat až je to perfektní

---

*Vytvořeno během workshopu "Copilot & Databricks pro farmaceutické analýzy" | 2025*
