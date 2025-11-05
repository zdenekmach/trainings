# Research Report: Práce s kontextem při práci s AI

**Vytvořeno:** 2025-11-05
**Research depth:** Deep
**Počet zdrojů:** 12 web searches, 60+ articles
**Doba researche:** ~15 minut

---

## Executive Summary

Research odhalil dramatickou expanzi kontextových oken v roce 2025 - z původních 8-32k tokenů na 1-2 miliony tokenů u moderních modelů. To fundamentálně mění způsob, jak s AI pracujeme. Zároveň se posunul focus z "prompt engineering" na "context engineering" - od psaní dobrých dotazů k designu celých systémů pro management kontextu.

Pro business analytiky to znamená možnost pracovat s celými projekty najednou (např. všechny user stories, kompletní analýza, sada dokumentů), ale také potřebu nových skills pro efektivní využití této kapacity.

**Klíčové insights:**
- **Masivní nárůst kapacity**: Claude Sonnet 4 má 1M tokenů (750k slov), Gemini 2.5 Pro až 2M tokenů, GPT-4.1 přes 1M tokenů
- **Paradigma shift**: Z prompt engineering na context engineering - strukturování a optimalizace celého informačního toku
- **Praktické nástroje**: Custom GPTs, MCP servery a Claude Skills umožňují opakovaně používat nastavený kontext bez nutnosti znovu vše vysvětlovat
- **Cost vs. capability**: Delší kontexty znamenají vyšší náklady a latenci - optimalizace je klíčová pro business use cases

---

## Aktuální trendy

### Trend 1: Explosion kontextových oken
**Popis:** Všichny hlavní AI platformy dramaticky zvýšily velikost kontextového okna v roce 2024-2025. Claude z 100k na 1M tokenů, Gemini na 2M tokenů, GPT-4.1 přes 1M tokenů.

**Relevance:** Business analytici teď můžou vložit kompletní projektovou dokumentaci, celou backlog, nebo všechny user stories najednou. To mění způsob práce - místo fragmentovaných dotazů můžeme pracovat holisticky.

**Zdroje:**
- [Claude Sonnet 4 Expands to 1 Million Token Context Window](https://www.infoq.com/news/2025/08/claude-sonnet-4/) - Claude Sonnet 4 nyní podporuje 1M tokenů (750k slov, 75k řádků kódu)
- [Gemini 2.5 Pro with 2M context](https://blog.google/technology/google-deepmind/gemini-model-thinking-updates-march-2025/) - Gemini 2.5 Pro má 1M tokenů s plánovanými 2M, Gemini 1.5 Pro již má 2M tokenů dostupných
- [GPT-4.1 context window](https://www.datastudios.org/post/chatgpt-context-window-token-limits-memory-policy-and-2025-rules) - GPT-4.1 má největší context window ze všech OpenAI modelů - až 1,047,576 tokenů
- [Context windows - Claude Docs](https://docs.claude.com/en/docs/build-with-claude/context-windows) - Oficiální dokumentace o velikostech kontextu

### Trend 2: Posun od Prompt Engineering k Context Engineering
**Popis:** Komunita přešla z focus na "dokonalé prompty" k designu celých systémů pro management kontextu. Context engineering se stává samostatnou disciplínou.

**Relevance:** Pro BA to znamená naučit se nejen psát dotazy, ale strukturovat celou práci s AI - jak organizovat informace, kdy začít novou konverzaci, jak udržet konzistenci napříč sessions.

**Zdroje:**
- [Context Engineering Guide](https://www.promptingguide.ai/guides/context-engineering-guide) - Comprehensive guide k context engineeringu
- [The New Skill in AI is Not Prompting, It's Context Engineering](https://www.philschmid.de/context-engineering) - Context engineering jako iterativní proces optimalizace instrukcí a kontextu
- [Effective context engineering for AI agents - Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) - Oficiální Anthropic guide k efektivnímu context engineeringu
- [Context Engineering - DataCamp](https://www.datacamp.com/blog/context-engineering) - Definice: "discipline of designing and building dynamic systems that provides the right information and tools, in the right format, at the right time"

### Trend 3: Specializované nástroje pro opakované kontexty
**Popis:** Custom GPTs (ChatGPT), MCP servery (Claude), Skills (Claude) - všechny platformy nabízejí způsob, jak "naučit" AI váš specifický kontext a používat ho opakovaně.

**Relevance:** BA můžou vytvořit vlastní "šablony" pro opakované úkoly - analýza user stories, psaní dokumentace, review requirements - bez nutnosti pokaždé znovu vysvětlovat kontext a formát.

**Zdroje:**
- [How to create custom GPT - Zapier](https://zapier.com/blog/custom-chatgpt/) - Step-by-step guide na tvorbu custom GPTs
- [Ultimate Guide to Claude MCP Servers](https://generect.com/blog/claude-mcp/) - Komplexní průvodce MCP servery
- [How to Create Claude Skills](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills) - Oficiální dokumentace k vytváření skills

---

## Best Practices & Přístupy

### Co funguje dobře

**Practice 1: Context Caching**
- **Co to je:** Znovu použití stejného kontextu bez opakovaného zpracování
- **Proč to funguje:** Snižuje latenci i náklady, obzvlášť při opakovaném použití stejných dokumentů nebo instrukcí
- **Jak to aplikovat:** Při práci s dlouhými dokumenty nebo standardními procedurami využít caching funkce (dostupné v Claude API)
- **Příklad:** Firma pracující s dlouhými smlouvami - nahraje template jednou, pak posílá jen specifické dotazy
- **Zdroje:** [Optimizing Context Windows](https://medium.com/@catalanogabriele15/optimizing-context-windows-for-effective-ai-agents-1778e8edbbfc)

**Practice 2: Information Distillation (Destilace informací)**
- **Co to je:** Transformace dlouhého kontextu do kompaktního shrnutí, které zachovává podstatné
- **Proč to funguje:** Redukuje token consumption při zachování klíčových informací
- **Jak to aplikovat:** Před zahájením nové konverzace požádat AI o shrnutí předchozí, použít jako vstup do nového contextu
- **Příklad:** Po dlouhé analýze projektu: "Shrň klíčové požadavky a rozhodnutí z této konverzace pro použití v novém chatu"
- **Zdroje:** [Context Window Optimization](https://empathyfirstmedia.com/context-window-optimization/)

**Practice 3: Strategic Content Placement**
- **Co to je:** Umístění nejdůležitějších informací na začátek nebo konec kontextu
- **Proč to funguje:** Research ukazuje, že modely mají lepší výkon s informacemi na začátku a konci kontextu (recency & primacy effect)
- **Jak to aplikovat:** Klíčové požadavky, constrains a priority dát na začátek promptu
- **Příklad:** "HLAVNÍ CÍL: vytvoř analýzu zaměřenou na UX... [dlouhý kontext]... PŘIPOMÍNKA: důraz na UX perspektivu"
- **Zdroje:** [Context Window Management](https://blog.qolaba.ai/ai-tools-by-qolaba/context-window-management-maximizing-ai-memory-for-complex-tasks/)

**Practice 4: Modularizace velkých dokumentů**
- **Co to je:** Rozdělení velkých dokumentů na logické části s jasnou strukturou
- **Proč to funguje:** Pomáhá modelům udržet pozornost na relevantních detailech, redukuje "memory overload"
- **Jak to aplikovat:** Místo jednoho 100-stránkového dokumentu použít strukturu s jasně označenými sekcemi
- **Příklad:** User stories organizované po epic/feature, ne jeden velký seznam
- **Zdroje:** [AI Context Window Optimization Tips](https://promptsty.com/context-window-optimization-tips/)

**Practice 5: Summarize before starting fresh**
- **Co to je:** Před dosažením limitu konverzace požádat o summary a použít ji jako start nové konverzace
- **Proč to funguje:** Zachová kontinuitu bez ztráty důležitého kontextu, "resetuje" context window
- **Jak to aplikovat:** Když konverzace je dlouhá: "Shrň klíčové body naší diskuse optimalizované pro start nové konverzace"
- **Příklad:** Po 2 hodinách analýzy požadavků získat summary a pokračovat v novém chatu s implementací
- **Zdroje:** [When to start new conversation](https://nolongerset.com/understanding-context-length/)

### Častí chyby a anti-patterns

**Anti-pattern 1: Waiting for hard limit**
- **Co to je:** Pokračovat v konverzaci až do chvíle, kdy AI odmítne ("maximum length reached")
- **Proč je to problém:** Kvalita odpovědí klesá dávno před hard limitem, ztráta kontextu na začátku konverzace
- **Jak se vyhnout:** Proaktivně začínat novou konverzaci při přechodu mezi fázemi projektu, ne až když to AI vynutí
- **Zdroje:** [Understanding Context Length](https://nolongerset.com/understanding-context-length/)

**Anti-pattern 2: Dumping všeho najednou**
- **Co to je:** Vložení maximálního množství informací s myšlenkou "víc je líp"
- **Proč je to problém:** Větší kontext ≠ lepší odpovědi. Irelevantní informace ruší a zvyšují náklady
- **Jak se vyhnout:** Selektivní výběr relevantního obsahu, ne automatic dump všeho
- **Zdroje:** [Quality over Quantity: Context Window Management](https://tilburg.ai/2025/03/context-window-management/)

**Anti-pattern 3: Nepromisl file vs. copy-paste**
- **Co to je:** Random rozhodnutí mezi uploadem souboru vs. copy-paste textu bez strategie
- **Proč je to problém:** Některé formáty (PDF tabulky) se špatně parsují, někdy potřebujeme jen část dokumentu
- **Jak se vyhnout:** File upload pro celé dokumenty ve supported formátech, copy-paste pro specifické sekce nebo problematické formáty
- **Zdroje:** [File upload vs copy paste best practices](https://support.box.com/hc/en-us/articles/22158484213267-Box-AI-for-Documents)

**Anti-pattern 4: Ignorování structured formatting**
- **Co to je:** Posílání nestrukturovaného textu bez jasných sekcí a headerů
- **Proč je to problém:** AI má problém navigovat chaos, horší výsledky
- **Jak se vyhnout:** Používat headings, bullet points, clear sections - pomáhá AI i lidem
- **Zdroje:** [Context Engineering Best Practices](https://www.kubiya.ai/blog/context-engineering-best-practices)

---

## Nástroje & Technologie

### Nástroj 1: Custom GPTs (ChatGPT)
**Co to dělá:** Umožňuje vytvořit vlastní verzi ChatGPT s přednastavenými instrukcemi, knowledge base, a chováním

**Use cases:**
- Opakované úkoly (generování user stories v konkrétním formátu)
- Specifická expertiza (BA helper pro konkrétní domén
u)
- Firemní templates a standardy

**Pros:**
- No-code tvorba pomocí konverzace s GPT builderem
- Možnost upload knowledge files (dokumenty, guidelines)
- Sharing s týmem (anyone with link nebo GPT store)
- API integrace pro externí data

**Cons:**
- Vyžaduje ChatGPT Plus ($20/měsíc)
- Omezení free tier má menší context window
- Privacy concerns při uploadu firemních dat

**Pro naše školení:** ✅ Určitě zahrnout - jedna z nejjednodušších cest jak "naučit" AI firemní kontext. Live demo + hands-on cvičení.

**Learning curve:** Beginner-friendly - vytvoření základního GPT za 5-10 minut

**Dokumentace:** [Creating a GPT - OpenAI](https://help.openai.com/en/articles/8554397-creating-a-gpt)

**Zdroje:**
- [How to create custom GPT - Zapier](https://zapier.com/blog/custom-chatgpt/)
- [DataCamp tutorial](https://www.datacamp.com/tutorial/how-to-make-custom-gpts)

### Nástroj 2: MCP Servery (Model Context Protocol - Claude)
**Co to dělá:** Standardizované rozhraní ("USB-C port for AI") pro připojení Claude k externím nástrojům, databázím a API. MCP server = bridge mezi AI a specifickým nástrojem.

**Use cases:**
- Připojení k firemním databázím a datům
- Integrace s issue trackery (Jira, Linear)
- Přístup k monitoring datům, design systémům
- Automatizace desktop workflows

**Pros:**
- Open-source standard, roste ekosystém
- Rozšíření kontextu o real-time externí data
- Možnost custom integrace s firemními systémy
- Funguje v Claude Desktop i Claude Code

**Cons:**
- Technicky náročnější setup (JSON konfigurace, případně Docker)
- Vyžaduje pochopení konceptů jako stdio transport, SSE
- Ne všechny nástroje mají ready-made MCP server
- Pro non-technical BA může být challenging

**Pro naše školení:** ⚡ Zmínit s ukázkou, ale ne hands-on - zajímavé pro pokročilejší, ale může být moc technické pro workshop formát. Ukázat populární servery a use cases.

**Learning curve:** Intermediate - basic setup 15-30 min, vlastní server requires development

**Dokumentace:** [Connect Claude Code to tools via MCP](https://docs.claude.com/en/docs/claude-code/mcp)

**Zdroje:**
- [7 Claude MCP servers you can set up right now](https://zapier.com/blog/claude-mcp-servers/)
- [Getting Started with MCP](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop)
- [Claude MCP directory](https://www.claudemcp.com/servers)

### Nástroj 3: Claude Skills
**Co to dělá:** Reusable workflows a specialized knowledge base pro Claude. Skill = markdown file s YAML frontmatter definující name, description a instructions.

**Use cases:**
- Standardizované workflows (quarterly business reviews, customer feedback analysis)
- Firemní best practices a guidelines
- Opakované analytické úkoly
- Domain-specific expertise

**Pros:**
- Jednoduchá tvorba - buď manuálně (markdown) nebo konverzačně
- File-based = lehký version control, sharing
- Aktivuje se automaticky když je relevantní
- Dostupné v Claude.ai i Claude Code
- Free (pro Claude uživatele)

**Cons:**
- Specifické pro Claude (ne přenosné na jiné platformy)
- Zatím relativně nový feature (od Q4 2024)
- Méně viditelné než custom GPTs (není marketplace)

**Pro naše školení:** ✅ Určitě zahrnout - perfektní balance mezi simple a powerful. Hands-on vytvoření vlastního skillu.

**Learning curve:** Beginner to Intermediate - konverzační tvorba 5-10 min, manuální 15-30 min

**Dokumentace:** [How to create custom Skills](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills)

**Zdroje:**
- [Create skill through conversation](https://support.claude.com/en/articles/12599426-how-to-create-a-skill-with-claude-through-conversation)
- [Introducing Agent Skills](https://www.anthropic.com/news/skills)
- [Claude Skills explained](https://www.lennysnewsletter.com/p/claude-skills-explained)

---

## Real-World Případové studie

### Case Study 1: JPMorgan - Contract Review
**Context:** JPMorgan Chase využívá GPT-4.1 Turbo pro review právních dokumentů a kontraktů

**Challenge:** Manuální review kontraktů je časově náročný, chybový, drahý. Potřeba analyzovat stovky dlouhých dokumentů rychle a konzistentně.

**Solution:** Využití GPT-4.1 s velkým context window (1M+ tokenů) pro analýzu celých kontraktů najednou, identifikace rizik, nekonzistencí a klíčových podmínek.

**Results:**
- **35% redukce času** na document review
- Konzistentnější identifikace rizik
- Uvolnění legal týmu pro komplexnější práci

**Lessons learned:** Velké context window umožňuje holistickou analýzu bez nutnosti chunking - zachytí kontext a vztahy napříč celým dokumentem.

**Relevance pro školení:** Ukázat BA, že podobný přístup funguje pro requirements documents, business case analysis, vendor contracts.

**Zdroj:** [AI context window practical examples use cases 2025](https://www.qodo.ai/blog/context-windows/)

### Case Study 2: Stanford Research - Climate Data Analysis
**Context:** Stanford výzkumníci analyzují rozsáhlá climate data s pomocí LLM s velkým context window

**Challenge:** Potřeba analyzovat 850,000 tokenů klimatických dat, najít korelace a patterns napříč datasety

**Solution:** Využití large context window model pro současnou analýzu všech dat v jednom session

**Results:**
- Objeveno **12 nových korelací**, které by při fragmentovaném přístupu nebyly viditelné
- Dramaticky rychlejší než tradiční chunking approach
- Zachování kontextu vztahů mezi různými datapointy

**Lessons learned:** Large context umožňuje cross-referencing a pattern recognition, které není možné při práci s fragmenty.

**Relevance pro školení:** BA můžou analogicky analyzovat user feedback z mnoha zdrojů, market research, customer interview notes najednou.

**Zdroj:** [AI context window practical examples](https://raoinformationtechnology.com/ai-context-window-comparison-2025/)

### Case Study 3: Alibaba Cloud - Customer Support Tickets
**Context:** Alibaba Cloud optimalizuje customer support s pomocí Deepseek v3 model

**Challenge:** Tisíce support tickets, potřeba rychlého a kvalitního resolution s plným kontextem customer history

**Solution:** Využití large context window pro načtení kompletní customer history, předchozích tickets, product info najednou

**Results:**
- **22% redukce času** na ticket resolution
- Vyšší customer satisfaction (méně opakování informací)
- Lepší first-contact resolution rate

**Lessons learned:** Kontext zákazníka (historie, předchozí issues, preferences) dramaticky zlepšuje kvalitu podpory.

**Relevance pro školení:** BA working se stakeholdery můžou použít podobný approach - nahrát všechny předchozí meeting notes, emails, requirements do jednoho kontextu.

**Zdroj:** [AI context window use cases](https://www.qodo.ai/blog/context-windows/)

### Case Study 4: Legal Firm - Multi-Contract Analysis
**Context:** Law firm analyzuje enterprise deals s pomocí velkého context window

**Challenge:** Potřeba cross-compare multiple contracts a case histories bez chunking

**Solution:** Nahrání všech relevantních kontraktů a case law do jednoho large context window

**Results:**
- Identifikace inconsistencies mezi kontrakty
- Rychlejší due diligence
- Snížení rizika missed clauses

**Lessons learned:** Holistic view beats piecemeal analysis pro complex document work.

**Relevance pro školení:** BA analyzující business requirements z různých stakeholderů můžou použít totéž - nahrát všechny dokumenty a hledat conflicts, gaps, overlaps.

**Zdroj:** [Long Context Windows in Generative AI](https://www.emerge.haus/blog/long-context-windows-in-generative-ai)

---

## Statistiky & Data Points

- **750,000 slov = 1 million tokenů** - [Zdroj: Claude Docs](https://www.datastudios.org/post/claude-context-window-token-limits-memory-policy-and-2025-rules)
  - Context: Claude Sonnet 4 s 1M tokenů zvládne asi 750k slov nebo 75k řádků kódu
  - Využití: Demonstrovat co se vejde do kontextu - asi 15-20 velkých business requirements dokumentů

- **Zdvojnásobení ceny za extended context** - [Zdroj: Claude Pricing](https://docs.claude.com/en/docs/build-with-claude/context-windows)
  - Context: Inputs nad 200k tokenů stojí $6/million místo $3/million (2x), outputs $22.50 místo $15 (1.5x)
  - Využití: Vysvětlit cost implications velkých kontextů - optimalizace není jen o performance, ale i o penězích

- **40% faster response times, 25% higher visibility** - [Zdroj: Empathy First Media](https://empathyfirstmedia.com/context-window-optimization/)
  - Context: Firmy používající context optimization reporting these benefits
  - Využití: ROI slide - ukázat business value optimalizace kontextu

- **Gemini 2M tokens = 11 hours audio, 1 hour video, 30,000 lines code** - [Zdroj: Google Blog](https://developers.googleblog.com/en/new-features-for-the-gemini-api-and-google-ai-studio/)
  - Context: Co se vejde do Gemini 1.5 Pro s 2M token context
  - Využití: Praktická představa objemu - BA můžou uploadnout záznam celého discovery workshopu

- **GPT-4o: 128,000 tokens, GPT-4.1: 1,047,576 tokens** - [Zdroj: DataStudios](https://www.datastudios.org/post/chatgpt-context-window-token-limits-memory-policy-and-2025-rules)
  - Context: Rozdíl mezi běžně používaným GPT-4o a top-tier GPT-4.1
  - Využití: Ukázat kdy upgrade dává smysl (ChatGPT Pro vs Plus)

---

## Quotes & Citace

> "Context engineering is the new currency in AI. We've moved from finding the right words for prompts to designing the right configuration of context for desired behavior."
> — Context Engineering Guide, [Prompt Engineering Guide](https://www.promptingguide.ai/guides/context-engineering-guide)

Využití: Opening slide o paradigma shiftu od prompt k context engineering

---

> "Think of MCP as a 'USB-C port for AI' — a standardized interface that lets Claude communicate with a wide range of services and applications."
> — [Ultimate Guide to Claude MCP](https://generect.com/blog/claude-mcp/)

Využití: Vysvětlení MCP serverů - dobrá analogie pro non-technical audience

---

> "Quantity does not equal quality: larger context windows do not automatically lead to better answers. Effective context management is crucial for optimal performance."
> — [Quality over Quantity: Context Window Management](https://tilburg.ai/2025/03/context-window-management/)

Využití: Warning slide - bigger není always better, potřeba strategie

---

> "Long-context queries typically increase data processing times and demand more computational resources, which can potentially result in higher costs."
> — [What is long context - Google Cloud](https://cloud.google.com/transform/the-prompt-what-are-long-context-windows-and-why-do-they-matter)

Využití: Cost considerations section - balance capability vs. cost

---

## Emergenční témata

### Emerging Topic 1: Context Compression Techniques
**Co to je:** Automatické techniky pro kompresi kontextu při zachování meaning (embeddings, summarization, retrieval)

**Proč sledovat:** Může dramaticky zlepšit cost/performance ratio, ale zatím není mainstream v business tools

**Maturity:** Growing - dostupné v API, ale ne v consumer interfaces (Claude.ai, ChatGPT web)

**Doporučení:** Zmínit jako bonus/future trend, ne hands-on. Většina BA nebude používat API directly.

**Zdroje:** [Context Engineering - LlamaIndex](https://www.llamaindex.ai/blog/context-engineering-what-it-is-and-techniques-to-consider)

### Emerging Topic 2: Multi-modal Context (Video + Audio)
**Co to je:** Rozšíření kontextu na video a audio - Gemini již podporuje až 1 hodinu videa v kontextu

**Proč sledovat:** Game-changer pro BA analyzující user research videos, stakeholder interviews, demo recordings

**Maturity:** Early stage - Gemini má to, ostatní platfomy zatím limitovaně

**Doporučení:** Zmínit jako exciting future capability, ukázat Gemini demo pokud čas dovolí

**Zdroje:** [Gemini long context](https://ai.google.dev/gemini-api/docs/long-context)

---

## Komunity & Resources

### Online komunity
- [r/ClaudeAI](https://reddit.com/r/ClaudeAI) - Reddit komunita Claude uživatelů, practical tips, use case sharing
- [r/ChatGPTPro](https://reddit.com/r/ChatGPTPro) - Pro uživatelé ChatGPT, advanced techniques, custom GPT sharing
- [OpenAI Developer Forum](https://community.openai.com) - Oficiální OpenAI forum, technical discussions

### Newslettery & Blogy
- [Anthropic Engineering Blog](https://www.anthropic.com/engineering) - Deep dives do Claude features a best practices
- [The Prompt (Google Cloud)](https://cloud.google.com/transform/the-prompt) - AI trends a practical guides od Google
- [Prompt Engineering Guide](https://www.promptingguide.ai) - Comprehensive guides pro prompting a context engineering

### Courses & Certifications
- [DataCamp: Context Engineering](https://www.datacamp.com/blog/context-engineering) - Free articles a guides
- [Coursera: AI Context Window](https://www.coursera.org/articles/context-window) - Free educational content

---

## Doporučení pro osnovu

Na základě researche doporučuji:

### ✅ Určitě zahrnout:

- [x] **Aktuální velikosti context windows** - Důvod: Claude 1M, Gemini 2M, GPT-4.1 1M+ jsou game changers vs. starší data (8k, 32k). Důležité pro decision making který nástroj kdy použít.

- [x] **Context engineering principles** - Důvod: Industry posunul focus z prompt na context engineering. BA potřebují pochopit tento shift.

- [x] **Custom GPTs hands-on** - Důvod: Nejjednodušší entry point, immediate value, beginner-friendly. Ba můžou vytvořit za 10 minut.

- [x] **Claude Skills hands-on** - Důvod: Pro Claude uživatele perfektní nástroj, file-based = sharable. Good balance simplicity/power.

- [x] **When to start new conversation** - Důvod: Velmi praktické, časté pain point. Research ukázal best practices (summarize, phase transitions).

- [x] **File upload vs. copy-paste decision tree** - Důvod: Časté dilema, research poskytl jasná kritéria (celý dokument vs. excerpt, format considerations).

- [x] **Real-world case studies** - Důvod: JPMorgan 35% savings, Alibaba 22% faster - konkrétní čísla rezonují s BA audience.

- [x] **Cost implications velkých kontextů** - Důvod: Claude 2x cena nad 200k tokens - business audience potřebuje rozumět cost/benefit.

### ⚡ Zvážit přidání:

- [ ] **MCP servery demo (view-only)** - Pros: Zajímavá technologie, roste adoption. Cons: Může být moc technické pro non-dev BA, setup complexity.

- [ ] **Gemini multi-modal demo** - Pros: Wow factor, future-looking. Cons: Niche use case, časová náročnost.

- [ ] **Context caching (API level)** - Pros: Významné úspory. Cons: Většina BA nepracuje s API directly.

### ❌ Nedoporučuji zahrnovat:

- **Technické detaily tokenizace** - Důvod: Příliš technické, low practical value pro BA use cases

- **Custom development MCP serverů** - Důvod: Requires coding skills, mimo scope pro BA audience

- **RAG systems implementace** - Důvod: Developer-level topic, ne practical pro business user workshops

### 🔄 Aktualizovat stávající osnovu:

- **Modul 1: Velikosti context windows** → Aktualizovat čísla: Claude 1M (ne 200k), Gemini 2M, GPT-4.1 1M+

- **Modul 2: Optimalizace** → Přidat: Context caching concept, Information distillation technique, Strategic content placement

- **Modul 3: Pokročilé nástroje** → Více času na Custom GPT (easiest), méně na MCP (complex), přidat Claude Skills conversational creation

- **Modul 4: Context Engineering** → Změnit důraz: Z "jak psát dobré prompty" na "jak designovat celý workflow" (RAG mentions, summarize-and-continue pattern)

---

## Rizika & Výzvy

### Riziko 1: Technická složitost některých nástrojů
**Impact:** MCP servery můžou být overwhelming pro non-technical BA, mohou se cítit frustrated nebo lost
**Likelihood:** Střední - závisí na tech background účastníků
**Mitigation:**
- MCP ukázat jen jako demo, ne hands-on
- Focus na Custom GPTs a Skills (jednodušší)
- Mít připravené pre-configured MCP příklady pro ty, kdo chtějí zkusit

### Riziko 2: Rychlý vývoj features
**Impact:** Některé informace můžou být outdated rychle (context windows se rozšiřují každé quarter)
**Likelihood:** Vysoká - AI space se mění fast
**Mitigation:**
- Důraz na principles přes specific numbers
- Ukázat kde najít aktuální info (docs, release notes)
- Materials označit datem, clarify "aktuální k datu X"

### Riziko 3: Různé úrovně zkušeností v audience
**Impact:** Někteří můžou najít obsah moc basic, jiní moc advanced
**Likelihood:** Střední - "mírně pokročilí" je široké spektrum
**Mitigation:**
- Pre-workshop survey - zjistit konkrétní úrovně
- Optional advanced sekce (MCP) pro rychlejší
- Pair programming při hands-on - zkušenější pomáhají začátečníkům

### Riziko 4: Cost surprises
**Impact:** Účastníci můžou začít používat large contexts bez uvědomění cost implications
**Likelihood:** Střední - většina nesleduje API costs
**Mitigation:**
- Explicitní sekce o pricing (Claude 2x nad 200k)
- Best practices pro cost optimization
- Doporučit začít s free tiers a trackovat usage

---

## Kompletní seznam zdrojů

### Primární zdroje (nejvíc využité)

1. [Claude context window documentation](https://docs.claude.com/en/docs/build-with-claude/context-windows) - 2025 - Oficiální docs, aktuální čísla kontextů
2. [Context Engineering Guide - Prompt Engineering Guide](https://www.promptingguide.ai/guides/context-engineering-guide) - 2025 - Comprehensive guide k principům
3. [Effective context engineering for AI agents - Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) - 2025 - Best practices od tvůrců Claude
4. [How to create custom GPT - Zapier](https://zapier.com/blog/custom-chatgpt/) - 2024 - Praktický tutorial Custom GPTs
5. [Ultimate Guide to Claude MCP Servers](https://generect.com/blog/claude-mcp/) - 2025 - Komplexní MCP průvodce
6. [How to Create Custom Skills - Claude Help](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills) - 2024 - Oficiální Skills docs
7. [ChatGPT context window 2025 rules](https://www.datastudios.org/post/chatgpt-context-window-token-limits-memory-policy-and-2025-rules) - 2025 - Aktuální GPT limity
8. [Google Gemini context window 2025](https://www.datastudios.org/post/google-gemini-context-window-token-limits-memory-policy-and-2025-rules) - 2025 - Gemini specs
9. [Understanding Context Length: 5 Techniques](https://nolongerset.com/understanding-context-length/) - 2024 - When to start new conversation
10. [Context Window Optimization Strategies](https://empathyfirstmedia.com/context-window-optimization/) - 2025 - Business case studies a ROI

### Sekundární zdroje

11. [7 Claude MCP servers - Zapier](https://zapier.com/blog/claude-mcp-servers/) - 2025 - Praktické MCP příklady
12. [The New Skill is Context Engineering](https://www.philschmid.de/context-engineering) - 2024 - Paradigm shift článek
13. [Context Engineering - DataCamp](https://www.datacamp.com/blog/context-engineering) - 2024 - Educational content
14. [Quality over Quantity - tilburg.ai](https://tilburg.ai/2025/03/context-window-management/) - 2025 - Anti-patterns
15. [AI Context Window Practical Examples](https://www.qodo.ai/blog/context-windows/) - 2025 - Case studies
16. [Long Context Windows - Google Cloud Blog](https://cloud.google.com/transform/the-prompt-what-are-long-context-windows-and-why-do-they-matter) - 2024 - Explainer
17. [Introducing Agent Skills - Anthropic](https://www.anthropic.com/news/skills) - 2024 - Skills announcement
18. [Creating a GPT - OpenAI Help](https://help.openai.com/en/articles/8554397-creating-a-gpt) - 2024 - Official GPT docs
19. [Claude Skills explained - Lenny's Newsletter](https://www.lennysnewsletter.com/p/claude-skills-explained) - 2025 - Skills deep dive
20. [Context Window Management - Qolaba](https://blog.qolaba.ai/ai-tools-by-qolaba/context-window-management-maximizing-ai-memory-for-complex-tasks/) - 2024 - Optimization tips

### Zdroje k dalšímu prozkoumání

- [Context Engineering - LangChain](https://blog.langchain.com/context-engineering-for-agents/) - For agents specifically, možná moc advanced
- [RAG systems](https://towardsdatascience.com/why-context-is-the-new-currency-in-ai-from-rag-to-context-engineering/) - Deep dive do RAG, developer-focused

---

## Metadata

**Search queries použité:**
- "Claude context window size 2025 tokens limit"
- "ChatGPT GPT-4 context window size 2025"
- "Google Gemini context window size 2025"
- "AI context management best practices 2025"
- "how to create custom GPT ChatGPT tutorial"
- "Claude MCP servers what are they how to use"
- "Claude skills how to create tutorial"
- "context engineering AI prompts techniques"
- "AI context window optimization tips business analysts"
- "when to start new conversation AI chat context limits"
- "file upload vs copy paste AI context best practices"
- "AI context window practical examples use cases 2025"

**Časové období zdrojů:** Říjen 2024 - Listopad 2025 (focus na aktuální info)
**Geografické pokrytí:** Global (US-heavy, ale applicable worldwide)
**Jazyky:** EN (translated insights to CS)

---

## Next Steps

**Akce na základě researche:**
1. [x] Aktualizovat requirements document s research insights
2. [ ] Reflection - porovnat původní osnovu s research findings
3. [ ] Vybrat finální output materiály (cheat sheet, presentation, exercises, guidelines)
4. [ ] Vytvořit materiály s focus na praktické příklady z researche

**Follow-up research needed:**
- [ ] Zjistit aktuální pricing Gemini vs. Claude vs. ChatGPT (pro cost comparison)
- [ ] Najít více BA-specific use cases (research byl general, potřeba BA focus)

---

*Tento research report slouží jako podklad pro reflexi osnovy a tvorbu obsahu školení. Reference na tento dokument by měly být v dalších materiálech.*
