# Research Report: Copilot a Databricks pro farmaceutické analýzy

**Vytvořeno:** 2025-11-06
**Research depth:** Quick (zrychlený)
**Počet zdrojů:** 13 klíčových zdrojů
**Doba researche:** 15 minut

---

## Executive Summary

Research potvrdil, že kombinace GitHub Copilot a Databricks AI Assistant je v roce 2025 osvědčená cesta pro zrychlení datových analýz. Klíčové zjištění: prompt engineering je kritický skill - vágní prompty dávají vágní výsledky, zatímco specifické prompty s kontextem (schémata tabulek, business pravidla) výrazně zvyšují přesnost. Ve farmaceutickém průmyslu jsou AI nástroje aktivně využívány pro customer segmentaci, clinical trials optimalizaci a predikce prodejů, s prokázanými úsporami 50-70% v nákladech a čase.

**Klíčové insights:**
- **Bezpečnost je kritická:** 83% farmaceutických firem nemá automatické kontroly proti úniku citlivých dat do AI nástrojů - musíme to důrazně pokrýt
- **Databricks AI Assistant 2025:** Context-aware, používá Unity Catalog metadata, má funkce /ask, /explain, /fix - zdarma pro všechny zákazníky
- **Praktické use cases ve farma:** Geographic sales analysis, customer segmentation, time series forecasting - všechny jsou běžně řešeny v Databricks s Pythonem

---

## Aktuální trendy

### Trend 1: Context-Aware AI Assistants
**Popis:** Databricks AI Assistant v roce 2025 automaticky rozumí kontextu workspace - zná tabulky, schémata, populární dotazy z Unity Catalog.
**Relevance:** Studenti nemusí poskytovat celé schéma manuálně, stačí @mention tabulky a AI rozumí.
**Zdroje:**
- [Databricks Assistant Tips and Tricks](https://www.databricks.com/blog/databricks-assistant-tips-and-tricks-data-analysts) - Používejte @ mentions pro reference tabulek, Cmd+I pro rychlou iteraci
- [Use Databricks Assistant](https://learn.microsoft.com/en-us/azure/databricks/notebooks/use-databricks-assistant) - Chat, Edit a Agent mody pro různé use cases

### Trend 2: Prompt Engineering jako Core Skill
**Popis:** Kvalita AI výstupů závisí 80% na kvalitě promptu - ne na modelu. Clear instructions + context + examples = konzistentní výsledky.
**Relevance:** Hlavní část školení musí být o psaní dobrých promptů, ne jen o klikání na tlačítka.
**Zdroje:**
- [Best Practices for Prompt Engineering with Meta Llama 3 for Text-to-SQL](https://aws.amazon.com/blogs/machine-learning/best-practices-for-prompt-engineering-with-meta-llama-3-for-text-to-sql-use-cases/) - Few-shot learning, clear instructions, schema context
- [Prompt Engineering for Better SQL Code Generation](https://medium.com/datamindedbe/prompt-engineering-for-a-better-sql-code-generation-with-llms-263562c0c35d) - Specifické guidelines: LIMIT 5, query jen potřebné columns

### Trend 3: AI v Farmaceutice = Mainstream
**Popis:** Pfizer, GSK, Moderna, AstraZeneca - všichni používají AI pro analytics, clinical trials, manufacturing, market intelligence.
**Relevance:** Účastníci nejsou early adopters - konkurence už to používá. Musíme zdůraznit urgenci.
**Zdroje:**
- [AI in Pharmaceutical Industry: 2025 Guide](https://sranalytics.io/blog/ai-in-pharmaceutical-industry/) - 50-70% úspora nákladů na clinical trials, 12+ měsíců zrychlení
- [Big Data in Pharma: Case Studies](https://intuitionlabs.ai/articles/big-data-case-studies) - Pfizer, GSK, Moderna konkrétní příklady

---

## Best Practices & Přístupy

### Co funguje dobře

**Practice 1: Poskytovat explicitní kontext**
- **Co to je:** V promptu vždy specifikovat schéma tabulek, business pravidla, požadovaný formát výstupu
- **Proč to funguje:** LLM nemůže hádat co chcete - clear context = clear results
- **Jak to aplikovat:**
  1. Začít prompt popisem dat (názvy tabulek, klíčové sloupce)
  2. Definovat business kontext (co znamenají metriky)
  3. Specifikovat formát (SQL query, Python viz, dashboard)
- **Příklad:** "Using sales_data table (columns: product_id, region, date, revenue), write SQL to find top 10 products by revenue in Prague region for 2024"
- **Zdroje:** Microsoft Learn SSMS Copilot Best Practices

**Practice 2: Few-Shot Learning (ukázat příklady)**
- **Co to je:** Dát AI 2-3 příklady natural language → SQL před tím, než zadáte skutečný dotaz
- **Proč to funguje:** AI se "učí" z příkladů jaký styl a formát chcete
- **Jak to aplikovat:**
  ```
  Example 1: "Show top customers" → SELECT customer_id, SUM(revenue) FROM orders GROUP BY customer_id ORDER BY revenue DESC LIMIT 10
  Example 2: "Sales by month" → SELECT DATE_TRUNC('month', date) as month, SUM(revenue) FROM sales GROUP BY month
  Now: "Show top products by region"
  ```
- **Zdroje:** AWS Best Practices for Text2SQL

**Practice 3: Iterativní validace (nikdy neslepě důvěřovat AI)**
- **Co to je:** Každý AI-generated kód zkontrolovat, otestovat na malém samplu dat, verifikovat business logiku
- **Proč to funguje:** AI často dělá subtilní chyby (average-of-averages, nesprávné JOINy, ignorování edge cases)
- **Jak to aplikovat:**
  1. Spusť AI dotaz na LIMIT 10 rows
  2. Manuálně zkontroluj výsledky
  3. Zkus edge cases (co když NULL hodnoty?)
  4. Porovnej s očekáváním
- **Zdroje:** KDnuggets Optimizing Data Analytics

### Častí chyby a anti-patterns

**Anti-pattern 1: Vágní prompty ("Find the hottest tables")**
- **Co to je:** Nespecifické požadavky bez kontextu nebo definice "hottest"
- **Proč je to problém:** AI hádá co myslíte, často špatně
- **Jak se vyhnout:** Buď specifický - "List top 10 tables by read count in last 24 hours"
- **Zdroje:** GitHub Copilot Best Practices

**Anti-pattern 2: Blindly trusting AI kód (zejména u business users)**
- **Co to je:** Copy-paste AI kódu bez pochopení nebo testování
- **Proč je to problém:** Subtilní chyby v business logice (počítá lidi 2x pokud jsou v multiple rows, nesprávné agregace)
- **Jak se vyhnout:** Vždy validovat output, ideálně mít někoho s SQL znalostmi zkontrolovat
- **Zdroje:** AnswerRocket Guide

**Anti-pattern 3: Sdílení citlivých dat s public AI tools**
- **Co to je:** Copy-paste pacientských dat, molekulárních struktur, clinical results do ChatGPT
- **Proč je to problém:** GDPR/HIPAA violation, data nelze smazat z AI modelu, konkurence může získat insights
- **Jak se vyhnout:** Používat enterprise AI nástroje (GitHub Copilot Enterprise, Databricks AI Assistant), anonymizovat data, implementovat DLP (Data Loss Prevention) controls
- **Zdroje:** Contract Pharma - AI Data Security

---

## Nástroje & Technologie

### Nástroj 1: Databricks AI Assistant
**Co to dělá:** Context-aware AI asistent integrovaný do Databricks notebooks a SQL editor - generuje kód, debuguje, vysvětluje, fixuje errors
**Use cases:** SQL query generation, PySpark code, data transformations, vizualizace
**Pros:**
- Zdarma pro všechny Databricks zákazníky
- Rozumí Unity Catalog metadata (tabulky, schemas)
- 3 mody: Chat (konverzace), Edit (úpravy kódu), Agent (autonomous tasks)
- @ mention tabulek pro kontext

**Cons:**
- Vyžaduje Databricks workspace (ne standalone)
- Limitováno na Databricks ekosystém

**Pro naše školení:** MUST HAVE - hlavní nástroj celého workshopu
**Learning curve:** Beginner-friendly, 15 minut na pochopení základů
**Dokumentace:** https://docs.databricks.com/notebooks/databricks-assistant-examples.html

### Nástroj 2: GitHub Copilot pro SQL/Python
**Co to dělá:** AI pair programmer - autocomplete kódu, generuje funkce z komentářů, vysvětluje code
**Use cases:** Psaní SQL dotazů, Python skriptů, dokumentace kódu
**Pros:**
- Funguje v multiple IDE (VS Code, SSMS, atd.)
- Inteligentní autocomplete - dokončuje celé bloky kódu
- Review code suggestions (cyklování přes varianty)
- Integruje se s Databricks přes VS Code

**Cons:**
- Platený (GitHub Copilot subscription)
- Méně context-aware než Databricks AI (nevidí tabulky automaticky)

**Pro naše školení:** Nice to have - ukázat pro comparison, ale fokus na Databricks AI
**Learning curve:** Beginner-friendly
**Dokumentace:** https://learn.microsoft.com/en-us/ssms/github-copilot/best-practices

### Nástroj 3: Databricks AI Functions (ai_query, ai_analyze_sentiment)
**Co to dělá:** Built-in SQL funkce pro AI tasks přímo v dotazech - sentiment analysis, text extraction, classification
**Use cases:** Analýza customer reviews, spam detection, forecasting
**Pros:**
- Žádné extra setup - funguje out of box
- Škáluje na velkých datech (běží v Spark)
- SQL syntax (no Python knowledge needed)

**Cons:**
- Limitovaná sada funkcí
- Méně flexible než custom modely

**Pro naše školení:** Bonus topic - ukázat jako "wow moment"
**Learning curve:** Easy (jen SQL syntax)
**Dokumentace:** https://docs.databricks.com/aws/en/large-language-models/ai-functions

---

## Real-World Případové studie

### Case Study 1: Moderna - Clinical Operations & Logistics
**Context:** Moderna používá Google Cloud Looker + AI pro analýzu clinical operations a logistiky (60,000+ shipments ročně)
**Challenge:** Najít cost-saving opportunities v komplexní supply chain, analyzovat sentiment stakeholderů
**Solution:** Looker pro data access + AI analytics pro sentiment analysis a predictive insights
**Results:** Identifikovali savings opportunities, sentiment analysis pomohl zlepšit stakeholder relationships
**Lessons learned:** AI nemusí být jen o drug discovery - operační analytics má velký ROI
**Relevance pro školení:** Ukázat že AI analytics má value i mimo R&D - logistics, operations, commercial jsou low-hanging fruit
**Zdroj:** IntuitionLabs Big Data Case Studies

### Case Study 2: Roche - Customer Analytics & Predictive NPS
**Context:** Roche partnered s Gemseek pro prediktivní analytics zákaznické spokojenosti
**Challenge:** Surveys zachytí jen část nespokojených zákazníků - většina "silent detractors"
**Solution:** Predictive NPS using AI/ML na behavioral data (ne jen survey responses)
**Results:** 3-4x zvýšení identifikace detractors, retention accounts worth millions annually
**Lessons learned:** AI může predikovat customer sentiment z dat, které už máte - nemusíte čekat na surveys
**Relevance pro školení:** Customer segmentation use case - ukázat jak behavioral data + AI = better insights než tradiční metody
**Zdroj:** DigitalDefynd Use of Data Analytics in Pharma

### Case Study 3: Pfizer - Predictive Model pro wtATTR-CM
**Context:** Pfizer vytvořil prediction model pro rare disease identification
**Challenge:** wtATTR-CM je rare, life-threatening condition - těžké identifikovat pacienty early
**Solution:** Predictive model na patient data
**Results:** Faster patient identification → treatments get to patients sooner
**Lessons learned:** Data analytics v pharma může mít direct impact na patient outcomes
**Relevance pro školení:** Motivace - ukázat že jejich práce není "jen čísla", ale real-world impact
**Zdroj:** IntuitionLabs Case Studies

---

## Statistiky & Data Points

- **83% farmaceutických firem nemá automated controls** proti úniku citlivých dat do AI nástrojů - Contract Pharma
  - Využití: Otevřít workshop s tímto alarmujícím číslem - urgence bezpečnosti

- **50-70% úspora nákladů na clinical trials** pomocí AI-enabled processes - SR Analytics
  - Využití: Business case pro AI adoption - nejen rychlost, ale i ROI

- **12+ měsíců zrychlení trial timelines** s AI optimalizací - SR Analytics
  - Využití: Prokázat business value AI v pharma

- **98% firem má zaměstnance používající unsanctioned AI apps** (průměr 1,200 apps) - Contract Pharma
  - Využití: "Shadow AI" problém - důvod proč potřebují enterprise solutions

- **60%+ enterprise AI deployments v 2025 budou používat RAG** nebo podobné grounding techniques - Gartner (via TowardsDataScience)
  - Využití: RAG jako emerging trend - zmínit jako pokročilou techniku

---

## Best Practices pro Bezpečnost (kritické pro pharma)

**Practice 1: Nikdy nesdílet raw data s public AI**
- Anonymizovat data před AI použitím
- Používat synthetic data pro experimenty
- Enterprise AI nástroje s data residency controls (Databricks, GitHub Copilot Enterprise)

**Practice 2: Implementovat Data Loss Prevention (DLP)**
- Automated classification of sensitive data
- Blocking mechanisms pro unauthorized AI platforms
- Audit trails for all data access

**Practice 3: GDPR/HIPAA Compliance**
- Data embedded v AI modelech nelze smazat (GDPR Right to Delete problém)
- Používat differential privacy pro anonymizaci
- Role-based access controls

**Zdroje:** Contract Pharma AI Data Security, GDPR Local Clinical Trials

---

## Doporučení pro osnovu

Na základě researche doporučuji:

### ✅ Určitě zahrnout:
- [x] **Prompt Engineering deep dive** - Důvod: Nejdůležitější skill, rozdíl mezi 20% a 90% success rate
- [x] **Bezpečnost a compliance** - Důvod: 83% firem to nemá v pořádku, kritické pro pharma
- [x] **Databricks AI Assistant hands-on** - Důvod: Hlavní nástroj, který budou používat
- [x] **Few-shot learning a prompt chaining** - Důvod: Pokročilé techniky s immediate value
- [x] **Validace AI výstupů** - Důvod: Business logic errors jsou common, musí umět detekovat

### ⚡ Zvážit přidání:
- [x] **Databricks AI Functions** - Pros: Wow factor, easy to learn, Cons: Limited use cases - **Přidat jako bonus/demo**
- [x] **Time series forecasting s Prophet** - Pros: Relevantní pro pharma sales, Cons: Může být too advanced - **Zmínit, poskytnout resources**
- [x] **Geospatial viz (Folium, Mosaic)** - Pros: Geographic analysis use case, Cons: Setup overhead - **Ukázat jako příklad, ne full cvičení**

### ❌ Nedoporučuji zahrnovat:
- Fine-tuning LLMs - Důvod: Too advanced, out of scope, není potřeba pro basic analytics
- Custom model deployment - Důvod: Data engineering focus, ne analytics focus
- Deep RAG implementation - Důvod: Emerging, complex, není nutné pro začátečníky

### 🔄 Aktualizovat stávající osnovu:
- **Blok 1** → Přidat: 10-minute "Security & Compliance" mini-section (83% stat, co sdílet/nesdílet)
- **Blok 2** → Zdůraznit: Few-shot learning prakticky (ne jen teoreticky)
- **Blok 4** → Přidat: "Common AI Mistakes" checklist (business logic errors, validation)

---

## Rizika & Výzvy

### Riziko 1: Studenti budou copy-paste bez pochopení
**Impact:** Naučí se špatné návyky, nebudou schopni debugovat když AI selže
**Likelihood:** Vysoká (AI dělá práci tak easy, že se vypne critical thinking)
**Mitigation:**
- Vynucovat code review u každého cvičení
- Záměrně dát broken AI output k fixování
- "Explain what this code does" pop quizzes

### Riziko 2: Bezpečnostní incident během workshopu
**Impact:** Někdo sdílí citlivá data s public AI, GDPR/compliance problém
**Likelihood:** Střední (lidé jsou zvyklí používat ChatGPT)
**Mitigation:**
- Security brief na začátku workshopu (5 min)
- Používat pouze demo/synthetic data
- Clear guidelines co je OK/not OK

### Riziko 3: AI hallucinations demotivují studenty
**Impact:** Zkušenost "AI vygeneroval nesmysl, tohle nefunguje"
**Likelihood:** Střední (zejména u složitějších dotazů)
**Mitigation:**
- Set expectations - "AI je asistent, ne expert"
- Naučit jak rozpoznat hallucinations
- Mít prepared fallback examples když live demo selže

---

## Kompletní seznam zdrojů

### Primární zdroje (nejvíc využité)
1. [Databricks Assistant Tips and Tricks for Data Analysts](https://www.databricks.com/blog/databricks-assistant-tips-and-tricks-data-analysts) - 2025 - @ mentions, Cmd+I shortcuts, best practices
2. [Best Practices for Prompt Engineering with Meta Llama 3 for Text-to-SQL](https://aws.amazon.com/blogs/machine-learning/best-practices-for-prompt-engineering-with-meta-llama-3-for-text-to-sql-use-cases/) - 2025 - Few-shot learning, schema context, clear instructions
3. [AI Data Security: The 83% Compliance Gap Facing Pharmaceutical Companies](https://www.contractpharma.com/exclusives/ai-data-security-the-83-compliance-gap-facing-pharmaceutical-companies/) - 2025 - Critical security stats
4. [AI in Pharmaceutical Industry: 2025 Guide & Use Cases](https://sranalytics.io/blog/ai-in-pharmaceutical-industry/) - 2025 - ROI metrics, case studies
5. [Big Data in Pharma: Case Studies](https://intuitionlabs.ai/articles/big-data-case-studies) - 2024 - Pfizer, GSK, Moderna examples

### Sekundární zdroje
6. [Use Databricks Assistant - Microsoft Learn](https://learn.microsoft.com/en-us/azure/databricks/notebooks/use-databricks-assistant) - Official docs
7. [GitHub Copilot Best Practices - SSMS](https://learn.microsoft.com/en-us/ssms/github-copilot/best-practices) - SQL-specific tips
8. [Optimizing Data Analytics: Integrating GitHub Copilot in Databricks - KDnuggets](https://www.kdnuggets.com/optimizing-data-analytics-integrating-github-copilot-in-databricks) - Integration workflow
9. [Time Series Forecasting With Prophet And Spark - Databricks](https://www.databricks.com/blog/2020/01/27/time-series-forecasting-prophet-spark.html) - Forecasting use case
10. [Market Segmentation with Novel Machine Learning - Pharma Exec](https://www.pharmexec.com/view/market-segmentation-with-novel-machine-learning) - Customer segmentation techniques

### Další užitečné zdroje
11. [Databricks AI Functions](https://docs.databricks.com/aws/en/large-language-models/ai-functions) - Built-in AI capabilities
12. [Common Mistakes Using AI Code Generation](https://medium.com/learning-sql/generative-ai-with-sql-first-impressions-3d26c5f17ae3) - Pitfalls to avoid
13. [Data Analytics Training Workshop Best Practices](https://www.datacamp.com/blog/corporate-data-analytics-training) - Training methodology

---

## Next Steps

**Akce na základě researche:**
1. [x] Aktualizovat requirements doc s bezpečnostními considerations
2. [x] Připravit security guidelines handout (1 page)
3. [ ] Vytvořit "Common AI Mistakes" checklist
4. [ ] Najít nebo vytvořit synthetic pharma dataset (sales, products, regions Praha)

**Follow-up research needed:**
- [ ] Specific Databricks AI Assistant examples for pharmaceutical data (pokud existují)
- [ ] GDPR-compliant AI usage guidelines pro EU pharma

---

*Tento research report slouží jako podklad pro reflexi osnovy a tvorbu obsahu školení.*
