# Copilot & Databricks - Praktická Cvičení

## Jak pracovat s cvičeními

**Pro studenty:**
- Nejdřív zkus sám - učíš se nejvíc z vlastních pokusů a chyb
- Prompty piš v češtině i angličtině - AI rozumí oběma
- Pokud tápeš 10+ minut, koukni na nápovědu
- Srovnej svoje řešení s uvedeným - může být jiné a stejně správné
- VŽDY validuj výsledky - spusť dotaz a zkontroluj jestli dává smysl

**Pro lektory:**
- Nespěchej, dej čas na experimentování
- Ptej se "Co jsi zkoušel?" ne "Nevíš to?"
- Různé přístupy jsou OK pokud fungují
- Choď mezi lidmi během hands-on, pomáhej proaktivně

---

## Cvičení 1: Transformace Vágního Promptu 🟢

### Zadání

Máš tyto vágní prompty. Přepiš je na dobré prompty použitím 4 komponent: **Role + Kontext + Úkol + Formát**.

**Prompt A:** "Ukaž mi zajímavé věci o zákaznících"

**Prompt B:** "Najdi problémové produkty"

**Prompt C:** "Analyzuj trendy"

**Cíl:** Procvičit anatomii dobrého promptu

**Časový odhad:** 15 minut

### Co budeš potřebovat
- Papír a tužka (nebo textový editor)
- Představ si že máš tyto tabulky:
  - `customers` (customer_id, age_group, region, registration_date)
  - `orders` (order_id, customer_id, product_id, order_value, order_date)
  - `products` (product_id, product_name, category, price)

### Očekávaný výstup
Pro každý prompt napiš:
1. ROLE (kdo je AI)
2. KONTEXT (jaká data máš)
3. ÚKOL (co přesně chceš)
4. FORMÁT (jak to chceš dostat)

---

### Nápověda k Cvičení 1

<details>
<summary>Klikni pro nápovědu</summary>

**Hint 1:** Co znamená "zajímavé věci"? Buď konkrétní - segmentace? TOP zákazníci? Churn risk?

**Hint 2:** "Problémové produkty" = nízké prodeje? Záporné reviews? Vrácené zboží? Specifikuj!

**Hint 3:** "Analyzuj trendy" - jaké trendy? Časové? Geografické? Produktové?

**Template:**
```
Kontext: Mám tabulky @[názvy] s columns: [výčet relevantních sloupců]
Úkol: [Specifická akce s měřitelnými parametry]
Formát: SQL dotaz / Python kód / Viz + výstupní columns
```

</details>

---

### Řešení Cvičení 1

**Prompt A - PŘED:**
```
"Ukaž mi zajímavé věci o zákaznících"
```

**Prompt A - PO:**
```
Role: Jsi expert na customer analytics pro e-commerce.

Kontext: Mám tabulky @customers (customer_id, age_group, region, 
registration_date) a @orders (order_id, customer_id, order_value, order_date).

Úkol: Segmentuj zákazníky do 3 skupin podle průměrné order_value:
- Low spenders (0-500 Kč avg)
- Mid spenders (500-2000 Kč avg)
- High spenders (2000+ Kč avg)

Pro každý segment urči:
- Počet zákazníků (absolutní + %)
- TOP region (kde jich je nejvíc)
- Průměrná age_group

Formát: SQL dotaz + tabulka se segmenty + 2-3 key business insights
```

**Proč je to lepší:**
- "Zajímavé věci" → Konkrétní segmentace s čísly
- AI ví přesně jaké sloupce použít
- Jasný output format

---

**Prompt B - PŘED:**
```
"Najdi problémové produkty"
```

**Prompt B - PO:**
```
Kontext: @products (product_id, product_name, category, price) a 
@orders (order_date, product_id, quantity_sold, revenue).

Úkol: Identifikuj "problémové" produkty podle těchto kritérií:
1. Prodeje klesly o 30%+ v posledních 3 měsících vs. předchozí 3 měsíce
2. NEBO celkový revenue < 10,000 Kč za poslední quarter
3. NEBO quantity_sold < 10 kusů za poslední měsíc

Výstup: TOP 20 problémových produktů seřazených podle % poklesu.
Zobraz: product_name, category, revenue_current_quarter, revenue_prev_quarter,
percent_change, quantity_last_month.

Formát: SQL + seřaď DESC podle abs(percent_change)
```

**Proč je to lepší:**
- "Problémové" má 3 jasné definice s čísly
- AI ví jak počítat percent_change
- Konkrétní timeframes

---

**Prompt C - PŘED:**
```
"Analyzuj trendy"
```

**Prompt C - PO:**
```
Kontext: @orders (order_date, product_category, revenue_czk) za posledních 24 měsíců.

Úkol: Time series analýza trendů revenue podle product_category.
1. Agreguj revenue po měsících pro každou kategorii
2. Vypočítej month-over-month % change
3. Identifikuj TOP 3 fastest-growing categories (avg monthly growth)
4. Identifikuj categories s declining trendem (negative growth 3+ měsíce po sobě)

Výstup: 
- SQL dotazy pro aggregaci
- Multi-line chart (1 line per category)
- Tabulka s TOP 3 growing a declining categories + growth rates

Formát: Python (pandas) pro výpočty + matplotlib pro viz
```

**Proč je to lepší:**
- "Trendy" → Časové řady, konkrétní metriky (MoM change)
- Definováno co znamená "growing" a "declining"
- Jasný visualization format

---

**Časté chyby:**
- ❌ Stále vágní: "Najdi zákazníky co hodně nakupují" (kolik je "hodně"?)
- ✅ Konkrétní: "TOP 50 zákazníků podle celkového revenue za 2024"

- ❌ Bez kontextu: AI hádá názvy tabulek a sloupců
- ✅ S kontextem: @ mention nebo explicit výčet sloupců

---

## Cvičení 2: Prompt Engineering v Databricks 🟡

### Zadání

V Databricks notebooku vytvoř analýzu prodejů Ibuprofenu podle městských částí Prahy za Q4 2024.

**Použij prompt chaining - rozděl na 3 kroky:**

**Krok 1:** Exploration - zjisti schéma a sample data

**Krok 2:** Analýza - TOP 10 městských částí podle revenue

**Krok 3:** Vizualizace - horizontal bar chart

**Cíl:** Procvičit prompt chaining a @ mentions

**Časový odhad:** 25 minut

### Co budeš potřebovat
- Databricks notebook
- Demo tabulka: `@demo_sales_data`
  - Columns: product_name, city_district, sale_date, revenue_czk, quantity_sold

### Očekávaný výstup
- 3 buňky v notebooku (1 prompt per step)
- SQL dotazy s výsledky
- Bar chart vizualizace

### Testovací data
```
Předpokládej že demo_sales_data obsahuje:
- Products: "Ibuprofen 400mg", "Aspirin 500mg", "Paracetamol 500mg", ...
- Districts: "Praha 1", "Praha 2", ... "Praha 10", "Vinohrady", "Žižkov", ...
- Dates: 2024-01-01 až 2024-12-31
```

---

### Nápověda k Cvičení 2

<details>
<summary>Klikni pro nápovědu</summary>

**Hint 1 - Krok 1 (Exploration):**
```
Prompt: "Z @demo_sales_data ukaž mi:
1. Schéma tabulky (column names a datatypes)
2. Prvních 5 řádků kde product_name LIKE '%Ibuprofen%'
3. Count total rows"
```

**Hint 2 - Krok 2 (Analýza):**
```
Prompt: "Z @demo_sales_data pro produkt 'Ibuprofen 400mg':
- Filtruj sale_date mezi 2024-10-01 a 2024-12-31 (Q4)
- Filtruj city_district kde začíná 'Praha' (jen Praha, ne okolí)
- Agreguj podle city_district: SUM(revenue_czk), SUM(quantity_sold)
- TOP 10 podle revenue DESC
SQL dotaz s columns: city_district, total_revenue, total_quantity"
```

**Hint 3 - Krok 3 (Viz):**
```
Prompt: "Z předchozích výsledků vytvoř horizontal bar chart:
- X-axis: total_revenue (v mil. Kč)
- Y-axis: city_district (seřaď od nejvyššího revenue)
- Color: single color (modrá)
- Title: 'TOP 10 městských částí - Ibuprofen 400mg Q4 2024'
- Zobraz hodnoty na konci barů"
```

</details>

---

### Řešení Cvičení 2

**Krok 1: Exploration**

Prompt v Databricks:
```
Z @demo_sales_data ukaž mi:
1. Schéma tabulky (DESCRIBE TABLE)
2. Sample 5 řádků pro produkt obsahující "Ibuprofen"
3. Celkový počet řádků

Výstup: SQL dotazy pro každý bod
```

AI vygeneruje:
```sql
-- 1. Schéma
DESCRIBE TABLE demo_sales_data;

-- 2. Sample
SELECT * FROM demo_sales_data
WHERE product_name LIKE '%Ibuprofen%'
LIMIT 5;

-- 3. Count
SELECT COUNT(*) as total_rows FROM demo_sales_data;
```

**Validace:** Zkontroluj že vidíš správné sloupce a data vypadají reálně.

---

**Krok 2: TOP 10 Analýza**

Prompt:
```
Z @demo_sales_data najdi TOP 10 městských částí Prahy podle revenue 
pro produkt "Ibuprofen 400mg" v Q4 2024 (říjen-prosinec).

Filtr:
- product_name = 'Ibuprofen 400mg'
- sale_date >= '2024-10-01' AND sale_date < '2025-01-01'
- city_district LIKE 'Praha%'

Agregace podle city_district:
- total_revenue = SUM(revenue_czk)
- total_quantity = SUM(quantity_sold)
- avg_price_per_unit = total_revenue / total_quantity

Seřaď DESC podle total_revenue, TOP 10.

Výstup: SQL dotaz s komentáři
```

AI vygeneruje:
```sql
-- TOP 10 městských částí Prahy - Ibuprofen 400mg Q4 2024
SELECT
    city_district,
    SUM(revenue_czk) as total_revenue,
    SUM(quantity_sold) as total_quantity,
    SUM(revenue_czk) / NULLIF(SUM(quantity_sold), 0) as avg_price_per_unit
FROM demo_sales_data
WHERE
    product_name = 'Ibuprofen 400mg'
    AND sale_date >= '2024-10-01'
    AND sale_date < '2025-01-01'
    AND city_district LIKE 'Praha%'
GROUP BY city_district
ORDER BY total_revenue DESC
LIMIT 10;
```

**Validace:**
- Spusť LIMIT 10 a check číselné hodnoty
- Dává smysl že Praha 1 má vyšší revenue než Praha 10? (depends on demographics)
- Zkontroluj že avg_price_per_unit je rozumné (např. 50-150 Kč)

---

**Krok 3: Vizualizace**

Prompt:
```
Z výsledků předchozího dotazu vytvoř horizontal bar chart:

Config:
- Chart type: horizontal bar
- X-axis: total_revenue (label: "Revenue (Kč)")
- Y-axis: city_district (seřazený od nejvyššího revenue)
- Color: modrá (#1f77b4)
- Title: "TOP 10 městských částí - Ibuprofen 400mg Q4 2024"
- Zobraz hodnoty na konci každého baru (formatted s tisíci: "1,234,567 Kč")

Python matplotlib nebo Databricks viz.
```

AI vygeneruje Python:
```python
import matplotlib.pyplot as plt
import pandas as pd

# Data z předchozího SQL dotazu
df = spark.sql("""
    SELECT city_district, total_revenue
    FROM (...previous query...)
""").toPandas()

# Sort DESC
df = df.sort_values('total_revenue', ascending=True)  # True pro horizontal

# Plot
fig, ax = plt.subplots(figsize=(10, 6))
bars = ax.barh(df['city_district'], df['total_revenue'], color='#1f77b4')

# Labels on bars
for bar in bars:
    width = bar.get_width()
    ax.text(width, bar.get_y() + bar.get_height()/2,
            f'{width:,.0f} Kč',
            ha='left', va='center', fontsize=9)

ax.set_xlabel('Revenue (Kč)', fontsize=12)
ax.set_title('TOP 10 městských částí - Ibuprofen 400mg Q4 2024', fontsize=14)
plt.tight_layout()
plt.show()
```

**Validace:**
- Chart se zobrazil?
- Pořadí je správně (highest nahoře nebo dole, depends on sort)
- Labels jsou readable?

---

**Alternativní přístup - Databricks native viz:**
```python
# Jednodušší - použij Databricks display()
display(df)
# Pak v UI: switch to "Visualization" → "Bar chart" → configure
```

**Časté chyby:**
- ❌ Zapomenutý WHERE filter na Q4 → vrací celý rok
- ❌ LIKE '%Praha' místo 'Praha%' → nehledá správně
- ❌ Neošetřené NULL values v quantity → division by zero

---

## Cvičení 3: Customer Segmentation (RFM) 🟡

### Zadání

Vytvoř customer segmentation pomocí RFM analýzy (Recency, Frequency, Monetary) pro produktovou kategorii "Pain Relief".

**RFM definice:**
- **Recency:** Kolik dní od poslední objednávky
- **Frequency:** Počet objednávek za posledních 12 měsíců
- **Monetary:** Celková hodnota objednávek za 12 měsíců

**Segmenty:**
1. Champions: R=high, F=high, M=high
2. Loyal Customers: F=high, M=high
3. At Risk: R=low (dlouho nenakupovali)
4. Lost: R=very low

**Cíl:** Procvičit JOINy, agregace, segmentaci

**Časový odhad:** 40 minut

### Co budeš potřebovat
- `@demo_customers` (customer_id, age_group, region)
- `@demo_orders` (order_id, customer_id, product_category, order_value, order_date)

### Očekávaný výstup
1. SQL dotaz pro RFM výpočet
2. Segmentační logika (CASE WHEN)
3. Tabulka: segment_name, customer_count, avg_monetary, top_region
4. Business recommendations pro každý segment

---

### Nápověda k Cvičení 3

<details>
<summary>Nápověda - strategický přístup</summary>

**Rozlož na kroky:**

1. **Filtruj data:** Jen Pain Relief, posledních 12 měsíců
2. **Vypočítej RFM metriky pro každého zákazníka:**
   - Recency = DATEDIFF(CURRENT_DATE, MAX(order_date))
   - Frequency = COUNT(DISTINCT order_id)
   - Monetary = SUM(order_value)
3. **Segmentuj:** CASE WHEN logic na základě RFM
4. **Agreguj podle segmentu:** count, averages, top region

**Na co si dát pozor:**
- CURRENT_DATE vs. fixed date (pro reproducible results použij např. '2024-12-31')
- LEFT JOIN vs. INNER JOIN (chceš jen customers co mají orders)
- DISTINCT order_id aby duplicates nepočítal 2x

</details>

---

### Řešení Cvičení 3

**Krok 1: RFM Calculation**

```sql
-- RFM Analýza pro Pain Relief kategorii
WITH customer_rfm AS (
    SELECT
        c.customer_id,
        c.age_group,
        c.region,
        -- Recency (dny od poslední objednávky)
        DATEDIFF('2024-12-31', MAX(o.order_date)) as recency_days,
        -- Frequency (počet objednávek za 12 měsíců)
        COUNT(DISTINCT o.order_id) as frequency,
        -- Monetary (celková hodnota)
        SUM(o.order_value) as monetary_value
    FROM demo_customers c
    INNER JOIN demo_orders o ON c.customer_id = o.customer_id
    WHERE
        o.product_category = 'Pain Relief'
        AND o.order_date >= DATE_SUB('2024-12-31', 365)  -- Posledních 12 měsíců
        AND o.order_date <= '2024-12-31'
    GROUP BY c.customer_id, c.age_group, c.region
)
SELECT * FROM customer_rfm LIMIT 10;
```

**Krok 2: Segmentace**

```sql
WITH customer_rfm AS (...previous CTE...),

customer_segments AS (
    SELECT
        *,
        CASE
            -- Champions: recently bought, often, high value
            WHEN recency_days <= 30 AND frequency >= 5 AND monetary_value >= 5000
                THEN 'Champions'
            
            -- Loyal Customers: frequent + high value (ale možná ne recent)
            WHEN frequency >= 4 AND monetary_value >= 3000
                THEN 'Loyal Customers'
            
            -- Potential Loyalists: recent, decent frequency
            WHEN recency_days <= 60 AND frequency >= 2 AND monetary_value >= 1000
                THEN 'Potential Loyalists'
            
            -- At Risk: dlouho nenakoupili, ale historically good
            WHEN recency_days > 90 AND recency_days <= 180 AND frequency >= 3
                THEN 'At Risk'
            
            -- Lost: velmi dlouho nenakoupili
            WHEN recency_days > 180
                THEN 'Lost'
            
            -- New Customers: nízká frequency
            WHEN frequency <= 1
                THEN 'New Customers'
            
            ELSE 'Regular'
        END as segment
    FROM customer_rfm
)
SELECT * FROM customer_segments LIMIT 10;
```

**Krok 3: Segment Profiling**

```sql
WITH (...previous CTEs...),

segment_summary AS (
    SELECT
        segment,
        COUNT(*) as customer_count,
        ROUND(AVG(recency_days), 1) as avg_recency,
        ROUND(AVG(frequency), 1) as avg_frequency,
        ROUND(AVG(monetary_value), 0) as avg_monetary,
        -- TOP region per segment
        FIRST_VALUE(region) OVER (
            PARTITION BY segment
            ORDER BY COUNT(*) OVER (PARTITION BY segment, region) DESC
        ) as top_region
    FROM customer_segments
    GROUP BY segment, region
)
SELECT
    segment,
    customer_count,
    ROUND(100.0 * customer_count / SUM(customer_count) OVER (), 1) as pct_of_total,
    avg_recency,
    avg_frequency,
    avg_monetary,
    top_region
FROM segment_summary
GROUP BY segment, customer_count, avg_recency, avg_frequency, avg_monetary, top_region
ORDER BY customer_count DESC;
```

**Výstup:**
| segment | customer_count | pct_of_total | avg_recency | avg_frequency | avg_monetary | top_region |
|---------|----------------|--------------|-------------|---------------|--------------|------------|
| Regular | 450 | 35.2 | 65.3 | 2.8 | 2,150 | Praha |
| Loyal Customers | 280 | 21.9 | 45.1 | 6.2 | 4,800 | Brno |
| Champions | 120 | 9.4 | 15.2 | 8.5 | 7,200 | Praha |
| At Risk | 95 | 7.4 | 125.7 | 4.1 | 3,500 | Ostrava |
| Lost | 180 | 14.1 | 245.3 | 3.2 | 2,900 | Praha |
| ... | ... | ... | ... | ... | ... | ... |

**Krok 4: Business Recommendations**

```
Champions (9.4%):
💎 Nejvhodnější pro: VIP program, early access k novým produktům, referral rewards
📊 Průměrná hodnota: 7,200 Kč - udržuj je happy

Loyal Customers (21.9%):
🎯 Strategie: Upsell/cross-sell, membership programy
💡 Opportunity: Převést na Champions (zvýšit frequency)

At Risk (7.4%):
⚠️ Akce: Win-back kampaň, speciální nabídky, survey proč nenak upovali
⏰ Urgence: Jednaj RYCHLE, jinak přejdou do Lost

Lost (14.1%):
😔 Realita: Nákladné získat zpátky, možná již u konkurence
🤔 Rozhodnutí: Aggressive win-back vs. let go

New Customers (X%):
🎉 Focus: Onboarding, education o produktech, early loyalty incentives
🚀 Goal: Převést na Regular → Loyal

Regular (35.2%):
📈 Opportunity: Largest segment - zvýšit frequency a monetary
💡 Tactics: Personalizované recommendations, bundle deals
```

---

**Časté chyby:**
- ❌ Počítání všech orders místo DISTINCT → inflated frequency
- ❌ Zapomenutý filter na category → RFM pro všechny produkty
- ❌ Hardcoded thresholdy bez znalosti dat → nesmyslné segmenty (všichni v jednom)

**Alternativní přístup - Percentily:**
```sql
-- Místo hardcoded thresholds použij percentily
WITH rfm_scores AS (
    SELECT *,
        NTILE(5) OVER (ORDER BY recency_days DESC) as R_score,  -- DESC: lower recency = higher score
        NTILE(5) OVER (ORDER BY frequency ASC) as F_score,
        NTILE(5) OVER (ORDER BY monetary_value ASC) as M_score
    FROM customer_rfm
)
SELECT *,
    CASE
        WHEN R_score >= 4 AND F_score >= 4 AND M_score >= 4 THEN 'Champions'
        WHEN F_score >= 4 AND M_score >= 4 THEN 'Loyal'
        ...
    END as segment
FROM rfm_scores;
```
→ Adaptabilní, funguje i když data scale změní

---

## Cvičení 4: Debugging - Najdi Chybu v AI Kódu 🟢

### Zadání

AI ti vygeneroval tento SQL pro "průměrná cena produktu podle regionu". Najdi chybu a opravo ji.

```sql
-- Prompt byl: "průměrná cena produktu podle regionu"
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
) AS subquery
GROUP BY region
ORDER BY avg_price DESC;
```

**Otázky:**
1. Co je špatně?
2. Jak to opravit?
3. Proč AI udělal tuto chybu?

**Cíl:** Procvičit validaci AI výstupů

**Časový odhad:** 10 minut

---

### Nápověda k Cvičení 4

<details>
<summary>Hint</summary>

**Hint 1:** Podívej se na inner query. Co počítá? Průměrnou cenu pro každý produkt v regionu.

**Hint 2:** Outer query pak počítá průměr těchto průměrů. Je to správně?

**Hint 3:** Příklad proč je to špatně:
- Region A: Product 1 (10 sales, avg 100 Kč), Product 2 (1000 sales, avg 50 Kč)
- Špatně: (100 + 50) / 2 = 75 Kč
- Správně: Vážený průměr = ~52 Kč (protože Product 2 má 100x víc sales)

</details>

---

### Řešení Cvičení 4

**Co je špatně:**

Toto je **average-of-averages problém**!

Inner query počítá průměrnou cenu pro KAŽDÝ produkt v regionu. Outer query pak počítá průměr těchto průměrů, což NErespektuje počet transakcí.

**Proč je to problém:**

Představ si Region A:
- Product 1: 10 prodejů po 100 Kč (avg = 100 Kč)
- Product 2: 1000 prodejů po 50 Kč (avg = 50 Kč)

**Špatný výpočet** (average-of-averages):
```
avg_price = (100 + 50) / 2 = 75 Kč
```
→ Dává Product 1 a Product 2 stejnou váhu, i když Product 2 má 100x více transakcí!

**Správný výpočet** (vážený průměr):
```
Total revenue = (10 × 100) + (1000 × 50) = 1,000 + 50,000 = 51,000 Kč
Total quantity = 10 + 1000 = 1010
avg_price = 51,000 / 1010 = ~50.5 Kč
```

---

**Správné řešení - Varianta 1 (jednoduchá):**

```sql
-- Jednoduchý průměr přímo z raw data
SELECT
    region,
    AVG(unit_price) as avg_price
FROM sales
GROUP BY region
ORDER BY avg_price DESC;
```

**Proč funguje:** Počítá průměr ze všech transakcí, ne z agregovaných průměrů.

---

**Správné řešení - Varianta 2 (vážený průměr):**

Pokud chceš weighted average podle quantity:

```sql
SELECT
    region,
    SUM(unit_price * quantity) / SUM(quantity) as weighted_avg_price,
    SUM(quantity) as total_quantity,
    COUNT(*) as total_transactions
FROM sales
GROUP BY region
ORDER BY weighted_avg_price DESC;
```

**Proč funguje:** Váží každou cenu podle quantity - vysoké sales mají větší vliv.

---

**Proč AI udělal tuto chybu:**

1. **Literal interpretation:** Prompt řekl "průměrná cena podle regionu" a AI udělal to co prompt doslova říká, ale ignoroval business logic
2. **Pattern matching:** AI viděl pattern "aggregate → aggregate again" v training datech a aplikoval ho
3. **Chybějící kontext:** Prompt nespecifikoval "vážený průměr" nebo "z raw transactions"

**Jak předejít příště:**

```
Špatný prompt:
"průměrná cena produktu podle regionu"

Dobrý prompt:
"Z tabulky @sales (region, unit_price, quantity) vypočítej průměrnou 
unit_price podle regionu. POZOR: Počítej z raw transakcí, ne average-of-averages.
Pokud relevantní, váž podle quantity.

Výstup: SQL dotaz s: region, avg_price, total_transactions"
```

---

**Časté podobné chyby AI:**

| Chyba | Příklad | Fix |
|-------|---------|-----|
| Average-of-averages | `AVG(AVG(x))` | Počítej z raw data |
| Duplicate counts | `COUNT(id)` v JOINu | `COUNT(DISTINCT id)` |
| Neošetřené NULLs | `SUM(revenue) / COUNT(*)` | `NULLIF`, `COALESCE` |
| Špatné JOINy | INNER kde měl být LEFT | Specifikuj v promptu |

---

## Cvičení 5: Závěrečný Projekt 🔴

### Zadání

Vytvoř kompletní end-to-end analýzu podle jednoho z těchto scénářů. Použij VŠECHNY techniky z workshopu.

**Scénář A: Geographic Analysis**
Najdi TOP 10 regionů podle revenue pro produktovou kategorii "Cardiovascular" za posledních 6 měsíců. Include year-over-year comparison a identifikuj fastest-growing regions.

**Scénář B: Product Performance**
Analyzuj performance všech produktů v kategorii "Diabetes Care". Segmentuj do 4 skupin: Stars, Cash Cows, Question Marks, Dogs (podle revenue a growth rate). Recommendations pro každou skupinu.

**Scénář C: Seasonal Patterns**
Pro kategorii "Cold & Flu" identifikuj seasonal patterns za posledních 2 roky. Kdy jsou peaks? Jaká je week-over-week volatilita? Predikuj peak pro příští rok.

**Cíl:** Demonstrovat všechny skills z workshopu

**Časový odhad:** 30 minut

### Deliverables

1. **Databricks Notebook** s:
   - Data exploration (@ mentions, schéma check)
   - SQL dotazy s komentáři
   - Vizualizace (min. 1 chart)
   - Validace výsledků

2. **Business Insights** (2-3 bullet points):
   - Co jsi zjistil/a?
   - Jaké recommendations?

3. **Prompty** které jsi použil/a:
   - Ukaž jak jsi používal/a prompt chaining
   - Highlight 1-2 good prompts

### Požadavky

✅ Must have:
- Použij @ mentions
- Min. 2 prompty (exploration + analysis)
- SQL dotaz s aggregací
- 1 visualization
- Validace (check že výsledky dávají smysl)

⚡ Nice to have:
- Few-shot learning
- Prompt chaining (3+ kroky)
- Multiple viz
- Statistical insights (YoY growth, volatility, atd.)

---

### Nápověda k Projektu

<details>
<summary>Strategický přístup</summary>

**Workflow:**

1. **Planning (5 min):**
   - Jaké otázky chceš zodpovědět?
   - Jaká data potřebuješ?
   - Jaký je expected output?

2. **Exploration (5 min):**
   - @ mention tabulky
   - Check schéma, sample data
   - Validuj že data obsahují co potřebuješ

3. **Analysis (15 min):**
   - Prompt chaining - rozděl na kroky
   - SQL dotazy s validací každého kroku
   - Aggregace, JOINy, filtry

4. **Visualization (3 min):**
   - Chart type podle dat (bar, line, scatter)
   - Labels, title, formatting

5. **Insights (2 min):**
   - 2-3 key takeaways
   - Business recommendations

**Tip:** Nemusíš být perfektní. Better done than perfect!

</details>

---

### Příklad Řešení - Scénář A

(Pro inspiraci - tvoje řešení může vypadat jinak!)

**Krok 1: Exploration**

```python
# Prompt: "Z @demo_sales_data a @demo_products zjisti:
# 1. Jaké produkty patří do category 'Cardiovascular'
# 2. Sample 5 řádků pro tuto kategorii
# 3. Date range dat (MIN a MAX date)"

# AI vygeneruje:
%sql
SELECT p.product_name, COUNT(*) as sales_count
FROM demo_sales_data s
JOIN demo_products p ON s.product_id = p.product_id
WHERE p.category = 'Cardiovascular'
GROUP BY p.product_name
ORDER BY sales_count DESC
LIMIT 10;
```

**Krok 2: Current Period Analysis**

```python
# Prompt: "Pro kategorii 'Cardiovascular' za posledních 6 měsíců
# (2024-07-01 až 2024-12-31):
# Agreguj podle region: total_revenue, total_quantity
# TOP 10 regionů podle revenue DESC
# SQL s komentáři"

# AI vygeneruje SQL... (similar to previous exercises)
```

**Krok 3: YoY Comparison**

```python
# Prompt: "Přidej year-over-year srovnání:
# Stejná analýza pro same 6 months v roce 2023
# Calculate YoY growth %
# Identifikuj fastest-growing TOP 3 regions"
```

**Krok 4: Visualization**

```python
# Prompt: "Bar chart s YoY comparison:
# Grouped bars (2023 vs 2024) pro TOP 10 regions"
```

**Krok 5: Insights**

```
Key Findings:
• Region "Praha" dominates with 15.2M Kč revenue (+25% YoY)
• Fastest growth: "Liberec" (+89% YoY) - emerging market opportunity
• "Ostrava" declined -12% YoY - investigate why (competition? demographics?)

Recommendations:
• Invest marketing in Liberec (high growth potential)
• Analyze Ostrava decline - retention campaign?
• Praha - maintain leadership, upsell opportunities
```

---

## Reflexe a Self-Check

Po dokončení cvičení si polož tyto otázky:

- [ ] **Chápu proč moje prompty fungovaly/nefungovaly?**
  - Co bych příště udělal jinak?
  - Které komponenty (role, kontext, úkol, formát) mi pomohly nejvíc?

- [ ] **Dokážu validovat AI výstupy?**
  - Zkontroloval/a jsem business logic?
  - Testoval/a jsem edge cases (NULLs, duplicates)?
  - Spustil/a jsem LIMIT 10 pro quick check?

- [ ] **Umím aplikovat na jiný use case?**
  - Dokážu vzít template z cvičení a použít na svá data?
  - Vím kdy použít few-shot learning vs. simple prompt?
  - Rozumím prompt chaining?

- [ ] **Znám common pitfalls?**
  - Average-of-averages
  - Duplicate counts
  - Ignorování business rules

**Pokud na některou otázku odpovídáš NE:**
- Projdi si znovu student guide
- Zkus cvičení s jinými daty
- Diskutuj s lektorem nebo kolegy

---

## Bonusové Výzvy (Pro Rychlejší Studenty)

### Výzva A: Cohort Analysis

Vytvoř cohort analýzu zákazníků:
- Cohorts podle měsíce registrace
- Retention rate po 1, 3, 6, 12 měsících
- Heatmap vizualizace

### Výzva B: Sentiment Analysis s AI Functions

Použij `ai_analyze_sentiment()` na customer reviews:
```sql
SELECT
  product_id,
  AVG(CASE WHEN sentiment = 'positive' THEN 1 ELSE 0 END) as positive_rate,
  COUNT(*) as review_count
FROM (
  SELECT
    product_id,
    ai_analyze_sentiment(review_text) as sentiment
  FROM customer_reviews
)
GROUP BY product_id;
```

### Výzva C: Predictive Segmentation

Vytvoř scoring model:
- Features: RFM + demographics + product preferences
- Score 0-100 (likelihood of churn)
- Segment: High risk, Medium risk, Low risk

---

## Další Procvičování

**Chceš víc?**
- [Databricks SQL Exercises](https://docs.databricks.com/sql/index.html)
- [Kaggle Datasets](https://www.kaggle.com/datasets) - pharmacy/healthcare data
- [Mode Analytics SQL Tutorial](https://mode.com/sql-tutorial/) - intermediate/advanced

**Našel/a jsi lepší řešení?**
- Sdílej v týmu!
- Přidej do team prompt library
- Diskutuj na Databricks Community Forum

**Potřebuješ pomoc?**
- Databricks Community: community.databricks.com
- Stack Overflow: tag [databricks]
- Email lektor: [email]

---

**🎉 Gratuluju že jsi dokončil/a všechna cvičení! Teď jsi ready používat AI v práci. 🚀**

*Cvičení vytvořena pro workshop "Copilot & Databricks pro farmaceutické analýzy" | 2025*
