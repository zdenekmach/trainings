# Training Requirements Document: Copilot a Databricks pro farmaceutické analýzy

**Vytvořeno:** 2025-11-05
**Status:** Finalized
**Typ školení:** Workshop - celodenní, praktický, prezenční

---

## Executive Summary

Celodenní praktický workshop pro data a business analytiky z farmaceutického průmyslu, kteří chtějí výrazně zefektivnit svou práci s daty pomocí AI nástrojů. Účastníci se naučí kombinovat sílu Databricks datových skladů s pokročilými AI asistenty (GitHub Copilot, Azure OpenAI), psát efektivní prompty pro analytické úlohy a vytvářet komplexní business analýzy pro farmaceutický sektor. Workshop je zaměřený 100% prakticky - každý účastník si odnese hotové skripty, šablony promptů a reálné use cases aplikovatelné hned druhý den v práci.

---

## Cílová skupina

### Primární persona

**Role:** Data analytik / Business analytik ve farmaceutické firmě
**Zkušenosti:** Středně pokročilí (pracují s daty denně, znají SQL, mají základní zkušenosti s AI nástroji)
**Background:** Technický/analytický - SQL, Excel, základy Pythonu, práce s BI nástroji
**Denní práce:**
- Analýza prodejních dat z datového skladu
- Reportování pro obchodní oddělení, marketing, management
- Segmentace zákazníků a produktové analýzy
- Ad-hoc analýzy podle požadavků byznysu
- Příprava dashboardů a prezentací pro stakeholdery

**Motivace:**
- Zrychlit rutinní analytické práce (zpracování dat, psaní SQL dotazů)
- Zvládnout složitější analýzy bez nutnosti být expert na Python/advanced analytics
- Naučit se "mluvit" s AI tak, aby jim skutečně pomohlo
- Využít moderní nástroje, které konkurence už používá

**Bolestivé body:**
- Rutinní SQL dotazy zabírají hodně času, opakující se práce
- Složitější analýzy (cohort analysis, predikce) jsou nad jejich současné možnosti
- Nevědí, jak správně formulovat požadavky na AI, aby dávalo užitečné výsledky
- ChatGPT znají, ale neví jak ho efektivně propojit s jejich datovým skladem
- Tlak na rychlejší reporty a hlubší insights, nedostatek času

### Velikost skupiny

**Očekávaný počet:** 10 účastníků
**Optimální velikost:** 8-12 (dostatek času na individuální konzultace během cvičení)

---

## Cíle školení (SMART)

### Hlavní learning objectives

Po absolvování školení budou účastníci schopni:

1. **Napsat efektivní prompty pro analytické úlohy s datovým kontextem**
   - Měřitelný výstup: Samostatně vytvoří prompt pro generování SQL dotazu a analýzy z vlastních dat
   - Časový rámec: Ihned po školení, ověřitelné během závěrečného cvičení
   - Konkrétně: Znají principy prompt engineeringu, umí specifikovat kontext, požadavky, formát výstupu

2. **Samostatně postavit end-to-end datovou analýzu v Databricks s pomocí AI Copilota**
   - Měřitelný výstup: Vytvoří kompletní notebook s analýzou (import dat, cleaning, analýza, vizualizace) za použití AI asistence
   - Časový rámec: V závěrečném cvičení během workshopu
   - Konkrétně: Propojí Databricks notebook, SQL Warehouse, využije AI assistant pro generování kódu

3. **Vytvořit business analýzu pro farmaceutický use case pomocí dat z DWH**
   - Měřitelný výstup: Postaví minimálně 2 z těchto analýz: geografická analýza prodejů, segmentace zákazníků podle produktů, časové trendy produktů
   - Časový rámec: Během závěrečného projektu v rámci workshopu
   - Konkrétně: Použije připravená demo data z farmaceutického DWH, vytvoří report s grafy a insights

4. **Efektivně používat chatboty a AI agenty pro exploraci a reportování dat**
   - Měřitelný výstup: Nastaví si vlastní workflow pro práci s AI nástroji, vytvoří si knihovnu vlastních prompt šablon
   - Časový rámec: Během workshopu + materiály na pokračování
   - Konkrétně: Rozumí rozdílům mezi různými AI nástroji (ChatGPT, Copilot, Databricks AI), ví kdy použít který

### Sekundární cíle

- Pochopit základy jak fungují Large Language Models (LLM) - aby rozuměli omezením
- Naučit se best practices pro bezpečnou práci s firemními daty a AI (co sdílet, co ne)
- Poznat pokročilé techniky: prompt chaining, few-shot learning, RAG principy
- Vytvořit si osobní knihovnu prompt šablon pro nejčastější analytické úlohy

### Out of scope

Co školení NEBUDE pokrývat:
- Pokročilé machine learning modelování (training vlastních modelů)
- Deep dive do Databricks infrastruktury a administrace
- Vývoj vlastních AI aplikací nebo API integrace
- Fine-tuning LLM modelů
- Komplexní data engineering (ETL pipelines, Delta Lake architektura)
- Python programming od základů (předpokládáme alespoň základní znalost)

---

## Osnova školení

### Celková časová dotace

**Délka:** 1 den (8 hodin čisté školení)
**Formát:** Kontinuální blok s přestávkami (9:00 - 17:30)
**Distribuce času:**
- Teorie/úvod: 20%
- Praktické cvičení: 60%
- Diskuse/Q&A/troubleshooting: 15%
- Závěrečný projekt: 5%

### Detailní struktura

#### Blok 1: Úvod a nastavení prostředí (9:00 - 10:00, 60 min)

**Cíl:** Všichni mají funkční prostředí, rozumí co dnes budeme dělat a proč

**Obsah:**
- **Welcome & Cíle workshopu** (15 min)
  - Co si dnes odnesete
  - Rychlé představení účastníků - co očekávají

- **Rychlý kontext: Jak fungují AI nástroje** (15 min)
  - LLM v kostce - co umí, co neumí
  - Přehled nástrojů: ChatGPT vs. GitHub Copilot vs. Databricks AI Assistant
  - Kdy použít který nástroj

- **Setup check a demo prostředí** (30 min)
  - Přístup do Databricks workspace
  - Demo farmaceutický dataset (prodeje, produkty, zákazníci, regiony)
  - Základní orientace v rozhraní
  - První příkaz s AI asistentem

**Praktické cvičení:** Každý si vyzkoušel základní interakci s AI v Databricks

---

#### Blok 2: Prompt Engineering pro Data Analytiky (10:15 - 11:45, 90 min)

**Cíl:** Umět napsat prompt, který dává konzistentní a užitečné výsledky

**Obsah:**
- **Anatomie dobrého promptu** (20 min)
  - 4 základní komponenty: Role + Kontext + Úkol + Formát
  - Živé příklady - špatný vs. dobrý prompt
  - Praktický příklad: Vygenerovat SQL dotaz na prodeje

- **Pokročilé techniky promptování** (25 min)
  - Few-shot learning (ukázat příklady)
  - Chain-of-thought (krok po kroku reasoning)
  - Prompt chaining (složitější úlohy na menší části)
  - Iterativní vylepšování promptů

- **Hands-on cvičení: Prompt pro farmaceutické analýzy** (45 min)
  - **Cvičení 1:** Napsat prompt pro analýzu TOP 10 produktů podle regionu
  - **Cvičení 2:** Prompt pro segmentaci zákazníků podle nákupního chování
  - **Cvičení 3:** Komplexnější - analýza sezonality prodejů s vizualizací
  - Review a diskuse nad výsledky

**Praktický výstup:** Knihovna 3-5 ověřených prompt šablon pro své use cases

---

#### Oběd (11:45 - 12:45)

---

#### Blok 3: Databricks + AI pro datové analýzy (12:45 - 14:45, 120 min)

**Cíl:** Samostatně postavit kompletní analytický notebook s pomocí AI

**Obsah:**
- **Databricks AI Assistant deep dive** (20 min)
  - Funkce: /ask, /explain, /fix, /doc
  - Integrace s SQL Warehouse
  - Best practices při používání
  - Bezpečnost a práce s citlivými daty

- **Praktický use case 1: Geografická analýza prodejů** (40 min)
  - Problém: "Které čtvrtě v Praze generují nejvyšší prodeje produktu X?"
  - Společně vytvoříme:
    - SQL dotaz s pomocí AI
    - Data cleaning a transformace
    - Vizualizace na mapě
    - Insights a doporučení

- **Praktický use case 2: Segmentace zákazníků** (40 min)
  - Problém: "Jaké skupiny obyvatel nejvíce nakupují produkt Y?"
  - Účastníci samostatně (s podporou):
    - Analýza demografických dat
    - Clustering zákazníků podle chování
    - Profiling segmentů
    - Business doporučení

- **Praktický use case 3: Časové trendy a predikce** (20 min)
  - Problém: "V jakém čase/sezóně je o produkt Z největší zájem v regionu ABC?"
  - Rychlá ukázka:
    - Time series analýza
    - Trend detection
    - Jednoduchá predikce

**Praktický výstup:** 2-3 kompletní notebooks s reálnými analýzami

---

#### Přestávka (14:45 - 15:00)

---

#### Blok 4: Pokročilé techniky a workflow (15:00 - 16:30, 90 min)

**Cíl:** Naučit se efektivní workflow a pokročilé postupy

**Obsah:**
- **Propojení AI nástrojů do workflow** (25 min)
  - ChatGPT/Copilot pro plánování analýzy a brainstorming
  - Databricks AI pro implementaci
  - Exporty a automatizace reportů
  - Ukázka celého workflow od zadání po report

- **Práce s různými datovými zdroji** (20 min)
  - Jak napojit externí data do Databricks
  - Kombinace více tabulek/datasetů
  - AI pomoc při data joining a cleaning

- **Best practices a časté pasti** (15 min)
  - Co dělat když AI "halucinuje" (generuje nesmyslné výsledky)
  - Jak verifikovat AI vygenerovaný kód
  - Bezpečnost: Co NIKDY nesdílet s AI
  - Etické aspekty - bias v datech a analýzách

- **Závěrečný projekt** (30 min)
  - Účastníci si vyberou jeden reálný use case
  - Samostatně postaví end-to-end analýzu
  - Krátká prezentace výsledků (2 min na osobu)

**Praktický výstup:** Finální projekt + osobní workflow setup

---

#### Blok 5: Wrap-up a co dál (16:30 - 17:00, 30 min)

**Cíl:** Shrnutí, Q&A, materiály na další studium

**Obsah:**
- **Recap hlavních takeaways** (10 min)
- **Otevřené Q&A** (15 min)
- **Další kroky a zdroje** (5 min)
  - Cheat sheet s prompt šablonami
  - Odkazy na dokumentaci
  - Komunitní zdroje a Slack/Teams kanály

---

### Přestávky

- **10:00 - 10:15** - Krátká coffee break (15 min)
- **11:45 - 12:45** - Oběd (60 min)
- **14:45 - 15:00** - Odpolední coffee break (15 min)

**Celkový čas:**
- 9:00 - 17:00 (8 hodin včetně přestávek)
- Čistého školení: 6 hodin 30 minut

---

## Předpoklady a prerekvizity

### Co by měli studenti umět/znát předem

**Povinné:**
- **SQL základy:** SELECT, WHERE, JOIN, GROUP BY, ORDER BY - běžné dotazy zvládnou napsat sami
- **Databricks access:** Už s tím pracovali, znají základní koncept notebooks a SQL queries
- **GitHub Copilot nebo ChatGPT základy:** Používali alespoň párkrát, rozumí principu konverzace s AI
- **Základní datová gramotnost:** Rozumí pojmům jako agregace, filtrování, vizualizace dat
- **Business kontext farmacie:** Znají produkty, zákaznické segmenty, základní business metriky

**Doporučené:**
- Python základy (číst kód, rozumět základním strukturám) - není nutné, ale pomůže
- Zkušenost s BI nástroji (Tableau, Power BI) - lépe pochopí vizualizace
- Práce s geolokačními daty - pokud řešili mapy, bude plus

### Příprava před školením

**Pro studenty:**
- [ ] **Ověřit přístup do Databricks workspace** (link pošleme 3 dny předem)
  - Vyzkoušet login
  - Otevřít testovací notebook
- [ ] **Setup GitHub Copilot** nebo alternativně **ChatGPT Plus account**
  - Pokud firma má enterprise licence, ověřit že funguje
  - Alternativa: Free tier ChatGPT bude stačit na základy
- [ ] **Vyplnit pre-workshop survey** (5 min)
  - Jaké jsou jejich hlavní use cases
  - Co je aktuálně nejvíc trápí v práci s daty
  - Jakou mají zkušenost s AI nástroji (1-5)
- [ ] **Připravit si 1-2 reálné use cases z jejich práce**
  - Klidně anonymizované
  - Budeme je používat jako příklady během workshopu

**Pro lektora:**
- [ ] **Připravit demo Databricks workspace**
  - Vytvořit účty pro všechny účastníky
  - Nahrát farmaceutický demo dataset (prodeje, produkty, zákazníci, regiony Praha)
  - Připravit template notebooks
- [ ] **Otestovat všechna cvičení** - projít všechny hands-on části den předem
- [ ] **Připravit backup řešení** - hotové notebooks pro případ technických problémů
- [ ] **Farmaceutický kontext** - seznámit se se základními produkty a business metrikami

---

## Logistika a prostředí

### Delivery formát

**Způsob dodání:** In-person (prezenční workshop)
**Platforma:** Fyzická učebna s projektorem a flipchartem
**Materiály:**
- Digitální materiály (cheat sheet, notebooks, slide deck) - sdílené přes Databricks workspace
- Vytištěný cheat sheet s prompt šablonami pro každého účastníka
- Digitální kopie všech prezentací a kódů k dispozici ihned po workshopu

### Technické požadavky

**Pro studenty:**
- **Hardware:**
  - Vlastní notebook/laptop (Windows, Mac, Linux - cokoliv)
  - Dostatečný výkon pro běh prohlížeče (Databricks je webové rozhraní)
  - Myš (doporučeno, práce bude pohodlnější)

- **Software:**
  - Moderní browser (Chrome, Firefox, Edge - aktuální verze)
  - Přístup na internet (workshop poskytne WiFi)
  - **NENÍ potřeba** instalovat Python, IDE nebo jiné nástroje - vše běží v cloudu

- **Network:**
  - Stabilní internet (poskytne venue)
  - Backup: mobilní data jako fallback

- **Účty:**
  - Databricks workspace účet (vytvoříme a pošleme přístup předem)
  - GitHub Copilot nebo ChatGPT účet (firemní nebo osobní)

**Pro lektora:**
- **Prezentační setup:**
  - HDMI kabel + adaptéry (USB-C, atd.)
  - Backup: vlastní projektor pokud venue selže
  - Wireless presenter s laserem

- **Demo prostředí:**
  - Databricks Community Edition workspace nebo Enterprise workspace s demo daty
  - Připravené notebooks pro každé cvičení
  - SQL Warehouse běžící a připravený

- **Backup plány:**
  - Offline kopie všech materiálů (kdyby internet selhal)
  - Hotové screenshoty a videa z cvičení
  - Alternative: použít local Jupyter notebooks s SQLite jako fallback

### Prostorové požadavky (pro in-person)

**Konfigurace místnosti:**
- **Classroom style** s pracovními stoly
- Kapacita: 10-15 lidí pohodlně
- Každý účastník potřebuje:
  - Pracovní prostor pro notebook + poznámky
  - Elektrická zásuvka (power outlet)
  - Pohodlná židle (budeme 8 hodin sedět)

**Vybavení:**
- Projektor nebo velká obrazovka (min. 65")
- Dobrá viditelnost ze všech míst v místnosti
- Flipchart nebo whiteboard (pro kreslení konceptů, brainstorming)
- Kvalitní WiFi pokrytí v celé místnosti
- Klimatizace (komfort při delším sezení)

**Občerstvení:**
- **Ráno:** Káva, čaj, voda, drobné pečivo
- **Oběd:** Zajištěn (ideálně v blízkosti nebo catering) - 60 min break
- **Odpoledne:** Káva, čaj, ovoce, sladkosti pro energii
- **Celý den:** Dostatek vody na stolech

---

## Metriky úspěchu

### Jak poznáme, že školení bylo úspěšné?

**Bezprostřední metriky (den školení):**
- **90%+ účastníků dokončí všechna hands-on cvičení** (minimálně 2 ze 3 use cases)
- **Průměrné hodnocení workshopu min. 4.3/5** v post-workshop surveyu
- **Každý účastník má funkční notebook** s minimálně jednou kompletní analýzou
- **100% účastníků si vytvoří vlastní knihovnu prompt šablon** (min. 5 šablon)
- **Pozitivní feedback na praktičnost** - min. 80% účastníků označí obsah jako "okamžitě použitelný"

**Krátkodobé metriky (1-2 týdny po školení):**
- **Min. 70% účastníků aktivně používá AI nástroje** v denní práci (follow-up survey)
- **Zvýšení rychlosti** analytických úloh - účastníci reportují úsporu času (subjektivní, ale důležité)
- **Min. 50% účastníků vytvoří novou analýzu** pomocí naučených technik
- **Aktivní sdílení znalostí** - účastníci učí kolegy (ideálně tracking přes interní kanály)

**Dlouhodobé metriky (1-3 měsíce po školení):**
- **Udržitelné používání AI workflow** - min. 60% stále používá naučené postupy
- **Měřitelné zlepšení produktivity** - rychlejší analýzy, více insights, méně rutinní práce
- **Rozšíření do týmu** - další kolegové začnou používat podobné techniky
- **ROI školení** - úspora času/nákladů převýší investici do workshopu

### Evaluace

**Metody hodnocení:**
- [x] **Praktická demonstrace** - závěrečný projekt, každý prezentuje svou analýzu
- [x] **Feedback formulář** - ihned po workshopu (5-10 min)
  - Hodnocení 1-5: obsah, praktičnost, tempo, lektor, prostředí
  - Otevřené otázky: co bylo nejužitečnější, co zlepšit
- [x] **Follow-up survey** (2 týdny po) - používají to? Co funguje? Kde potřebují pomoc?
- [x] **1-on-1 check-in** (měsíc po) - s vybranými účastníky pro detailní feedback
- [ ] Pre/post test - NE, nemáme čas a není potřeba pro praktický workshop
- [ ] Peer review - NE, není relevantní pro tento formát

---

## Další materiály a reference

### Doporučené zdroje pro další studium

**Databricks:**
- [Databricks SQL Documentation](https://docs.databricks.com/sql/index.html)
- [Databricks AI Assistant Guide](https://docs.databricks.com/notebooks/notebook-ai-assistant.html)
- Databricks Community Edition - free tier pro experimentování

**Prompt Engineering:**
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [Learn Prompting - Free Course](https://learnprompting.org/)
- [Awesome ChatGPT Prompts - GitHub](https://github.com/f/awesome-chatgpt-prompts)

**AI pro Analytics:**
- Blog: "Towards Data Science" - sekce AI/ML
- YouTube: "Data with Baraa" - praktické AI use cases
- Podcast: "AI in Business" - business perspektiva

**Komunity:**
- Databricks Community Forum
- Reddit: r/databricks, r/datascience
- LinkedIn groups: "Databricks Users", "AI for Business Analytics"

### Související školení

**Navazující témata (pokud budou chtít pokračovat):**
- **Pokročilý Python pro Data Science** - pro ty, kdo chtějí jít hlouběji
- **Machine Learning v Databricks** - vlastní prediktivní modely
- **Data Engineering 101** - ETL pipelines, Delta Lake
- **Business Intelligence a vizualizace** - propojení s Tableau/Power BI

**Prerekvizitní školení (pro ty, co potřebují doplnit znalosti):**
- **SQL od základů** - pokud mají mezery v SQL
- **Python Basics** - pro lepší pochopení kódu
- **Úvod do Databricks** - pokud jsou úplní začátečníci

---

## Poznámky a otevřené otázky

### Poznámky z discovery

- **Účastníci jsou středně pokročilí** - není potřeba začínat od píky, můžeme jít rychleji
- **Hlavní motivace: zrychlení rutinní práce** - důraz na praktické time-saving techniky
- **Farmaceutický kontext** - budeme potřebovat realistická demo data (prodeje, produkty, regiony)
- **Workshop styl** - preferují hands-on před teorií, maximum času na cvičení
- **Očekávání:** "Chtěli by si odnést něco, co použijí hned zítra v práci"

### Otevřené otázky

- [x] Máme přístup do Databricks workspace? → ANO, budeme používat připravené demo prostředí
- [x] Jaká data použijeme? → Vytvoříme syntetická farmaceutická data (anonymizované)
- [ ] **Jsou citlivá data firmy?** → Potřebujeme vědět co můžeme/nemůžeme sdílet s AI
- [ ] **Jaký je jejich aktuální tech stack?** → Aby návaznost byla seamless
- [ ] **Mají firemní GitHub Copilot licenci?** → Nebo budeme používat ChatGPT?

### Change log

- **2025-11-05:** Initial requirements dokument vytvořen na základě discovery s uživatelem

---

## Schválení

**Vytvořil:** Claude (AI Training Builder)
**Schválil:** [Čeká na schválení uživatele]
**Datum schválení:** [Po potvrzení]

---

## Další kroky

1. ✅ **Requirements schváleny** → Přejít na Phase 1: Research
2. ⏳ **Research** → Najít aktuální best practices, nástroje, case studies
3. ⏳ **Reflection** → Vylepšit osnovu na základě researche
4. ⏳ **Výběr výstupů** → Rozhodnout jaké materiály vytvořit (prezentace, cvičení, cheat sheet)
5. ⏳ **Tvorba materiálů** → Vytvořit všechny dokumenty

---

*Tento dokument slouží jako základ pro tvorbu všech školících materiálů. Měl by být referenční bod během celého procesu přípravy.*
