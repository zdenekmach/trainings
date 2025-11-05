# Training Requirements Document: Práce s kontextem při práci s AI

**Vytvořeno:** 2025-11-05
**Status:** Draft
**Typ školení:** Workshop

---

## Executive Summary

Workshop pro business analytiky zaměřený na efektivní práci s kontextovým oknem AI nástrojů. Účastníci se naučí, co je to kontextové okno, jak funguje, jak ho optimalizovat a jak využít pokročilé techniky jako custom GPT, MCP servery a skills. Důraz na praktické dopady pro každodenní práci s Claude, ChatGPT a Gemini.

---

## Cílová skupina

### Primární persona

**Role:** Business Analytik
**Zkušenosti:** Středně pokročilý s AI nástroji
**Background:** Netechnický/smíšený, orientace na byznys procesy a analýzu
**Denní práce:** Analýza požadavků, tvorba dokumentace, komunikace se stakeholdery, práce s daty, modelování procesů
**Motivace:** Chce efektivněji využívat AI nástroje ve své práci, zrychlovat tvorbu dokumentace, zlepšit kvalitu výstupů z AI
**Bolestivé body:**
- AI "zapomíná" předchozí konverzaci
- Nevědí, kolik informací můžou AI poskytnout najednou
- Nejsou si jisti, jestli vkládat dlouhé dokumenty nebo je rozdělit
- Výstupy z AI nejsou konzistentní v delších konverzacích
- Neví, jak nejlépe strukturovat práci s AI pro opakované úkoly

### Velikost skupiny

**Očekávaný počet:** 8-20 účastníků
**Optimální velikost:** 12-15 pro interaktivní cvičení

---

## Cíle školení (SMART)

### Hlavní learning objectives

Po absolvování školení budou účastníci schopni:

1. **Porozumět principům kontextového okna a jeho limitům**
   - Měřitelný výstup: Umí vysvětlit, co je kontextové okno a jaké má rozměry u Claude, ChatGPT a Gemini
   - Časový rámec: Ihned po školení

2. **Optimalizovat využití kontextu pro své úkoly**
   - Měřitelný výstup: Aktivně aplikují techniky context management (např. kdy vložit soubor vs. text, kdy začít novou konverzaci)
   - Časový rámec: Do týdne po školení

3. **Využít pokročilé nástroje pro práci s kontextem**
   - Měřitelný výstup: Vytvoří si vlastní custom GPT nebo skill pro opakovaný úkol ze své praxe
   - Časový rámec: Do 2 týdnů po školení

4. **Aplikovat context engineering techniky**
   - Měřitelný výstup: Strukturují své prompty tak, aby efektivně využívaly kontext a produkovaly konzistentní výstupy
   - Časový rámec: Do týdne po školení

### Sekundární cíle

- Pochopit rozdíly v kontextovém okně mezi různými AI nástroji
- Znát best practices pro dlouhodobou práci s AI projekty
- Umět diagnostikovat problémy související s kontextem

### Out of scope

Co školení NEBUDE pokrývat:
- Technické detaily fungování LLM modelů (tokeny, embeddings, atd.)
- Vývoj vlastních AI modelů
- Programování a coding (kromě základního použití)
- Pokročilé prompt engineering techniky mimo kontext managementu

---

## Osnova školení

### Celková časová dotace

**Délka:** 90-120 minut
**Formát:** Kontinuální blok s krátkou přestávkou
**Distribuce času:**
- Teorie: 30%
- Praktické cvičení: 50%
- Diskuse/Q&A: 20%

### Detailní struktura

#### Modul 1: Co je kontextové okno
**Čas:** 20 minut
**Cíl:** Pochopit základ - co je kontext a proč je to důležité

**Obsah:**
- Co je kontextové okno - jednoduchá analogie
  - Klíčové koncepty: Pracovní paměť AI, limity
  - Praktický příklad: Ukázka, kdy AI "zapomene"
- Velikosti kontextových oken u různých nástrojů
  - Claude: ~200k tokenů
  - ChatGPT: ~128k tokenů (GPT-4), ~8k (GPT-3.5)
  - Gemini: ~1M tokenů (Pro)
  - Co to znamená v praxi (stránky A4, dokumenty)
- Jak se kontext plní a spotřebovává
  - Zprávy, soubory, system prompts
  - Vizualizace postupného zaplňování

**Cvičení:** Účastníci si zkusí odhadnout, kolik obsahu se vejde do kontextu jejich běžného use case

#### Modul 2: Jak kontext efektivně využít
**Čas:** 25 minut
**Cíl:** Naučit se praktické techniky pro optimalizaci kontextu

**Obsah:**
- Kdy vložit soubor vs. kopírovat text
  - Decision tree pro různé scénáře
  - Praktické příklady z práce BA
- Jak strukturovat dlouhé konverzace
  - Kdy začít novou konverzaci
  - Jak přenést důležitý kontext
  - Techniky pro udržení konzistence
- Jak kontext uvolnit
  - Nová konverzace vs. pokračování
  - Export důležitých částí
  - Shrnutí pro přenos do nového kontextu

**Cvičení:** Hands-on práce - účastníci pracují s ukázkovým projektem a aplikují techniky context managementu

#### Modul 3: Pokročilé nástroje pro práci s kontextem
**Čas:** 30 minut
**Cíl:** Poznat a umět použít nástroje, které řeší opakované práce s kontextem

**Obsah:**
- Custom GPT (ChatGPT)
  - Co to je a k čemu slouží
  - Jak si vytvořit vlastní GPT s nastaveným kontextem
  - Praktické příklady pro BA: Template pro user stories, analýzu požadavků
  - Live demo + hands-on tvorba
- MCP servery (Claude)
  - Co jsou MCP servery
  - Jak rozšiřují kontext o externí zdroje
  - Praktické použití - připojení k firemním datům
  - Ukázka populárních MCP serverů
- Skills (Claude)
  - Co jsou skills a jak fungují
  - Jak vytvořit vlastní skill
  - Praktické příklady pro BA úkoly
  - Live demo

**Cvičení:** Účastníci si vytvoří jeden z nástrojů (custom GPT nebo skill) pro svůj vlastní use case

#### Modul 4: Context Engineering
**Čas:** 20 minut
**Cíl:** Naučit se strukturovat práci tak, aby efektivně využívala kontext

**Obsah:**
- Principy context engineeringu
  - Strukturování informací v kontextu
  - Hierarchie důležitosti informací
  - Reference vs. plný obsah
- Praktické techniky
  - Templates a formáty pro opakované úkoly
  - Modularizace velkých dokumentů
  - Inkrementální práce s kontextem
- Best practices
  - Do's and Don'ts
  - Časté chyby a jak se jim vyhnout
  - Checklist pro optimální využití kontextu

**Cvičení:** Refactoring existujícího přístupu - účastníci přepracují svůj typický workflow s AI

#### Závěr a Q&A
**Čas:** 10-15 minut
**Cíl:** Upevnit znalosti, zodpovědět otázky, action items

**Obsah:**
- Rekapitulace klíčových bodů
- Sdílení zkušeností z workshopu
- Action items - co aplikovat hned zítra
- Q&A

### Přestávky
- 1x přestávka 5-10 minut po modulu 2 (po cca 45 minutách)

---

## Předpoklady a prerekvizity

### Co by měli studenti umět/znát předem

**Povinné:**
- Praktická zkušenost s alespoň jedním AI nástrojem (Claude, ChatGPT, nebo Gemini)
- Základní znalost prompt engineeringu (psaní dotazů do AI)
- Zkušenost s prací business analytika (dokumentace, požadavky, procesy)

**Doporučené:**
- Zkušenost s více AI nástroji
- Základní technické povědomí (co je API, účet, nastavení)

### Příprava před školením

**Pro studenty:**
- [ ] Mít aktivní účet na Claude.ai nebo ChatGPT
- [ ] Připravit si 1-2 konkrétní use case ze své práce, které chtějí řešit s AI
- [ ] (Volitelně) Připravit si ukázkový dokument, se kterým obvykle pracují

**Pro lektora:**
- [ ] Připravit demo účty pro všechny platformy
- [ ] Vytvořit ukázkové soubory a scénáře
- [ ] Otestovat všechny nástroje a demo
- [ ] Připravit backup slides pro případ výpadku internetu

---

## Logistika a prostředí

### Delivery formát

**Způsob dodání:** Hybrid (in-person preferováno, možné i online)
**Platforma:** Lokálně/Zoom/Teams podle dostupnosti
**Materiály:** Digital (cheat sheet, cvičení)

### Technické požadavky

**Pro studenty:**
- Hardware: Laptop s webovým prohlížečem
- Software: Moderní browser (Chrome, Firefox, Edge)
- Network: Stabilní internet připojení
- Účty: Aktivní účet na Claude.ai nebo ChatGPT (free tier stačí)

**Pro lektora:**
- Účty na všech třech platformách (Claude, ChatGPT, Gemini)
- Demo prostředí s připravenými příklady
- Sdílená obrazovka pro live demo
- Backup materiály offline

### Prostorové požadavky (pro in-person)

- Konferenční místnost s projekcí
- Wifi pro všechny účastníky
- Stoly pro práci na laptopech
- Možnost skupinové práce

---

## Metriky úspěchu

### Jak poznáme, že školení bylo úspěšné?

**Bezprostřední metriky (den školení):**
- 90%+ studentů úspěšně vytvoří vlastní custom GPT nebo skill
- 100% studentů demonstruje porozumění principům kontextu (exit quiz)
- Průměrné hodnocení workshopu min. 4.5/5
- Každý student odchází s konkrétním action plánem pro své use case

**Krátkodobé metriky (1-2 týdny po):**
- 70%+ účastníků začne aktivně používat techniky context managementu
- 50%+ vytvoří si další custom GPT/skill pro své potřeby
- Měřitelné snížení času stráveného "bojem" s AI

**Dlouhodobé metriky (1-3 měsíce po):**
- Udržitelné používání context management technik v denní práci
- Sdílení best practices s kolegy
- Měřitelné zlepšení produktivity práce s AI (rychlejší tvorba dokumentů, lepší kvalita výstupů)

### Evaluace

**Metody hodnocení:**
- [x] Praktická demonstrace (vytvoření vlastního nástroje)
- [x] Feedback formulář
- [x] Follow-up survey po 2 týdnech
- [ ] Pre/post test (volitelně)

---

## Další materiály a reference

### Doporučené zdroje pro další studium

- Oficiální dokumentace Claude, ChatGPT, Gemini
- Anthropic's prompt engineering guide
- MCP servers repository
- Community fóra a best practices

### Související školení

- Základy práce s AI (prerekvizita)
- Pokročilý prompt engineering (navazující)
- AI pro business analytiky - kompletní kurz (souvislé)

---

## Poznámky a otevřené otázky

### Poznámky z discovery

- Cílová skupina má mírně pokročilé znalosti - nepotřebují základy AI
- Důraz na praktické dopady - každý koncept musí mít jasný benefit pro jejich práci
- Zájem o všechny tři hlavní nástroje (Claude, ChatGPT, Gemini)
- Workshop formát - 1-2 hodiny, takže obsah musí být condensed ale praktický
- Témata rovnoměrně důležitá - kontextové okno, optimalizace, pokročilé nástroje, context engineering

### Otevřené otázky

- [x] Formát a délka - vyřešeno (workshop, 90-120 min)
- [x] Cílová skupina - vyřešeno (BA, mírně pokročilí)
- [ ] Preference pro live demo vs. pre-recorded ukázky

### Change log

- 2025-11-05: Iniciální verze requirements document

---

## Schválení

**Vytvořil:** Claude (Training Builder)
**Schválil:** Čeká na review
**Datum schválení:** Pending

---

*Tento dokument slouží jako základ pro tvorbu všech školících materiálů. Měl by být referenční bod během celého procesu přípravy.*
