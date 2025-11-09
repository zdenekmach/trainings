# Multi-Step Research Flow - Cheat Sheet
## One-page reference pro složité analytické projekty

> **Print this!** Rychlá reference pro orchestraci AI nástrojů v research projektech.

---

## 🔄 5-fázový Flow (Overview)

```
1. DEFINE        2. RESEARCH       3. VALIDATE       4. SYNTHESIZE     5. CREATE
   ↓                ↓                  ↓                 ↓               ↓
ChatGPT o1      Perplexity        Claude           NotebookLM      Claude/GPT
Claude          Gemini            Perplexity       Claude          MS Copilot
                MS Copilot        Manual                           Gemini
```

---

## 📍 Fáze 1: DEFINE - Doladění cíle

**Cíl:** Vágní zadání → Strukturovaný research plán

**Nástroje:**
- 🥇 ChatGPT o1 (extended reasoning)
- 🥈 Claude Sonnet 4 (extended thinking)

**Quick Prompt:**
```markdown
Vágní zadání: [tvůj topic]

Úkol:
1. Identifikuj 5 research questions
2. Navrhni strukturu výzkumu
3. Definuj success criteria
4. Prioritizuj (co první)

Output: Research roadmap
```

**Output:**
- ✅ 3-5 konkrétních research questions
- ✅ Strukturovaný plán
- ✅ Success criteria

**💾 Ulož:** Notion / Google Docs / SharePoint

---

## 🔍 Fáze 2: RESEARCH - Sběr informací

**Cíl:** Systematicky nasbírat relevantní info z důvěryhodných zdrojů

### 2A: Online Research

**Nástroj:** Perplexity (Deep Research mode)

**Kdy:** Potřebuješ aktuální info, citace, široký přehled

**Quick Prompt:**
```markdown
Research question: [konkrétní otázka]

Requirements:
- Comprehensive (min 800 slov)
- Academic + industry zdroje
- Citace ke každému tvrzení

Output: Analýza s odkazy
```

### 2B: Document Analysis

**Nástroj:** Gemini 2.5 Pro

**Kdy:** Máš PDFs/dokumenty k analýze, potřebuješ cross-doc patterns

**Quick Prompt:**
```markdown
[Upload documents]

Research question: [otázka]

Úkol:
1. Extrahuj key findings
2. Identifikuj shody a rozdíly
3. Flag conflicting info

Output: Tabulka findings
```

### 2C: Internal Research

**Nástroj:** MS Copilot

**Kdy:** Info je v SharePoint/Teams/M365

**Quick Prompt:**
```markdown
Research topic: [topic]

Prohledej:
- SharePoint: [site]
- Teams: [channels]
- OneDrive: [folder]

Output: Seznam dokumentů + summary
```

### Organization During Research:

**Tag findings:**
- 🟢 High confidence (multiple sources)
- 🟡 Medium (single credible source)
- 🔴 Low confidence (needs validation)
- ❓ Conflicting information

**Output:**
- ✅ Structured notes s findings
- ✅ Links ke zdrojům
- ✅ Preliminary confidence tags

---

## ✅ Fáze 3: VALIDATE - Ověření

**Cíl:** Eliminovat halucinace, zvýšit důvěryhodnost

**Nástroje:**
- 🥇 Claude Sonnet 4 (fact-checking)
- 🥈 Perplexity (cross-reference)
- 🥉 Manual checks (kritická tvrzení)

**Quick Prompt (Claude):**
```markdown
Role: Critical fact-checker

Findings: [paste z Fáze 2]

Pro každý finding:
1. Source credibility
2. Logical consistency
3. Potential biases
4. Flag co needs verification

Output: Tabulka
| Finding | Confidence | Issues | Action |
```

**Quick Prompt (Perplexity - pro 🔴 Low confidence):**
```markdown
Fact-check: [konkrétní claim]

Úkol:
1. Find 3-5 independent sources
2. Support/contradict/nuance?
3. Current consensus?

Output: Verification summary
```

**Manual Checklist (pro kritická tvrzení):**
- [ ] Link funguje
- [ ] Zdroj říká co AI tvrdí
- [ ] Zdroj je credible
- [ ] Data aktuální
- [ ] Statistiky mají kontext

**Output:**
- ✅ Validated findings (high confidence)
- ✅ Flagged items
- ✅ Contradictions resolved

---

## 🧬 Fáze 4: SYNTHESIZE - Syntéza

**Cíl:** Raw findings → Insights + Narrative

### 4A: Quick Synthesis

**Nástroj:** NotebookLM

**Kdy:** Rychlý overview, máš 10+ zdrojů, chceš audio summary

**Postup:**
1. Upload sources do NotebookLM
2. Generate audio overview (poslech)
3. Query pro insights:
   - "5 most important insights?"
   - "What patterns emerge?"
   - "Where do sources disagree?"

### 4B: Deep Synthesis

**Nástroj:** Claude Sonnet 4

**Kdy:** Nuanced analysis, executive summary, strategic thinking

**Quick Prompt:**
```markdown
Role: Senior research analyst

Findings: [validated findings]

Úkol:
1. PATTERNS: 3-5 hlavních themes
2. INSIGHTS: Co to znamená? Implications?
3. NARRATIVE: Coherent story
4. GAPS: Co stále nevíme?

Format: Strukturovaný dokument, min 1500 slov

Tone: Professional, analytical, accessible
```

**Output:**
- ✅ Synthesis document (insights)
- ✅ Narrative (ne jen bullets)
- ✅ Patterns a trendy
- ✅ Implications + recommendations

---

## 🎨 Fáze 5: CREATE - Finální výstup

**Cíl:** Syntéza → Publikovatelný formát

### 5A: Research Report / White Paper

**Nástroj:** Claude Sonnet 4

**Structure:**
1. Executive Summary (1 str)
2. Introduction (500 slov)
3. Findings (60% délky, by themes)
4. Analysis (20%)
5. Recommendations (15%)
6. Limitations (5%)

**Tip:** Writeuj po sekcích, ne všechno najednou

### 5B: Blog Post / Article

**Nástroj:** ChatGPT GPT-4.1

**Structure:**
1. Hook (compelling stat)
2. Setup (context)
3. Main Content (3-4 sections, each = insight)
4. Implications (so what?)
5. Conclusion (CTA)

**Style:** Short paragraphs, no jargon, analogies

### 5C: Presentation

**Nástroj:** MS Copilot (PowerPoint) nebo Gemini (Google Slides)

**Quick Prompt:**
```markdown
Create presentation from synthesis

Topic: [topic]
Source: [link]
Audience: [who]
Length: 15-20 slides

Structure:
1. Title + Agenda
2. Exec Summary (problem + findings)
3. Methodology (1 slide)
4. Findings (8-10 slides, by themes)
5. Insights (2-3 slides)
6. Recommendations (2-3 slides)
7. Next Steps + Q&A

Design: Professional, max 5 bullets/slide
```

**Alternative:** Claude/GPT pro content → manual design

### 5D: Executive Summary (1-pager)

**Nástroj:** Claude nebo GPT

**Must have:**
- Context (2-3 věty)
- Key Findings (3-5 bullets)
- Implications (2-3 věty)
- Recommendations (3 bullets s priority)
- Next Steps (2 bullets, owners/timelines)

**Constraint:** MAX 1 strana A4, 11pt font

---

## 🛠️ Tool Selection Matrix

| Co potřebuješ | Použij | Proč |
|---------------|--------|------|
| **Define research plan** | ChatGPT o1 | Extended reasoning |
| **Online research + citace** | Perplexity Deep | Search-first, sources |
| **Analyzovat PDFs** | Gemini 2.5 Pro | 2M context |
| **Internal docs (M365)** | MS Copilot | SharePoint integration |
| **Fact-checking** | Claude Sonnet | Critical thinking |
| **Quick synthesis** | NotebookLM | Auto-synthesis, audio |
| **Deep synthesis** | Claude Sonnet | Nuanced analysis |
| **Write report** | Claude Sonnet | Long-form depth |
| **Write blog** | ChatGPT GPT-4.1 | Engaging, polished |
| **Create slides (M365)** | MS Copilot | Direct PPT generation |
| **Create slides (Google)** | Gemini | Direct Slides generation |

---

## 💡 Best Practices

### Do's ✅

- ✅ **Plan first** - 30 min v Define ušetří hodiny
- ✅ **Document real-time** - ne všechno nakonec
- ✅ **Tag confidence** - 🟢🟡🔴 během researche
- ✅ **Right tool per phase** - ne všechno v jednom AI
- ✅ **Validate critical claims** - double-check exec summary items
- ✅ **Synthesize before create** - insights happen here
- ✅ **Iterate** - first pass nikdy není finální

### Don'ts ❌

- ❌ **Single AI pro všechno** - suboptimal
- ❌ **Skip Validation** - halucinace se stávají
- ❌ **Fake citations** - ověř linky
- ❌ **Syntéza příliš brzy** - dej researchi čas
- ❌ **Zapomenout audience** - C-level ≠ technical team
- ❌ **Infinite research loop** - time-box fáze

---

## ⚡ Quick Start Workflow

**Minimal viable research project (6-8 hodin):**

**Day 1:**
1. **DEFINE** (1 hod): ChatGPT o1 → 3 research questions
2. **RESEARCH** (3 hod): Perplexity → 10-15 findings
3. **VALIDATE** (1 hod): Claude → fact-check top 5

**Day 2:**
4. **SYNTHESIZE** (2 hod): NotebookLM + Claude → insights
5. **CREATE** (2 hod): Claude/GPT → 1-pager nebo slides

**Total:** ~8 hodin
**Saved vs manual:** ~20-30 hodin

---

## 🎯 When to Use This Flow

**Use this flow when:**
- ✅ Complex analytical project (5+ hours manual work)
- ✅ Need synthesis from multiple sources
- ✅ Output must be credible/defensible
- ✅ Strategic decisions depend on findings

**DON'T use when:**
- ❌ Simple fact lookup (just use Perplexity)
- ❌ Single-source summary (just use Claude)
- ❌ Time-critical quick task (overkill)

---

## 🔄 Iterative Refinement

Research není lineární. Běžné iterace:

```
DEFINE → RESEARCH → (new questions?) → back to DEFINE
SYNTHESIS → (gaps?) → back to RESEARCH
VALIDATE → (conflicts?) → more RESEARCH
```

**To je normální!** Ale time-box to:
- Max 2 týdny research
- 80% confidence je good enough
- Ship, iterate later if needed

---

## 🆘 Quick Troubleshooting

| Problem | Solution |
|---------|----------|
| **Research nekončí** | Time-box fáze. Define "good enough" threshold. |
| **Contradictory findings** | Acknowledge v reportu. Critical? Manual deep-dive. |
| **AI halucinuje citace** | VŽDY verify links. Nefunguje? Discard. |
| **Synthesis = jen summary** | Better prompt: "implications", "so what?", "surprising?" |
| **Output příliš generic** | Specify tone + audience. Dej examples. Iterate. |
| **Nevím který tool** | Use Tool Selection Matrix výše. Default: Claude/GPT. |

---

## ✅ Pre-Flight Checklist

Než začneš další research projekt:

- [ ] Research questions defined? (3-5)
- [ ] Success criteria clear?
- [ ] Notion/Google Doc ready pro notes?
- [ ] Vím které nástroje použít kdy?
- [ ] Time-boxed phases? (max X hodin per phase)
- [ ] Target audience defined?
- [ ] Output format chosen? (report/blog/slides)

---

## 📊 Example: Market Research (2 týdny)

**Week 1:**
- Den 1: DEFINE (2h) → ChatGPT o1
- Den 2-3: RESEARCH online (4h) → Perplexity
- Den 4: RESEARCH docs (3h) → Gemini
- Den 5: VALIDATE (2h) → Claude

**Week 2:**
- Den 6: SYNTHESIZE (3h) → NotebookLM + Claude
- Den 7-8: CREATE report (6h) → Claude
- Den 9: CREATE slides (3h) → Copilot
- Den 10: Exec summary (1h) → Claude

**Total:** ~25 hodin | **Saved:** 60-80 hodin

---

## 🎓 Try It Yourself

**Mini exercise (3-4 hodiny):**

1. Zvol research topic (competitive analysis, tech eval, trend analysis)
2. Run through flow:
   - DEFINE (30 min) → 3 questions
   - RESEARCH (90 min) → 10-15 findings
   - VALIDATE (30 min) → check top 5
   - SYNTHESIZE (45 min) → 3 insights
   - CREATE (30 min) → 1-pager

3. Compare s manuálním přístupem
4. Note time + quality difference

---

## 💬 Key Takeaways

**Multi-step flow ≠ "používám více AI"**

**Multi-step flow = orchestrace správných nástrojů ve správnou chvíli**

**Results:**
- 🚀 50-70% time savings (po learning curve)
- 📈 Higher quality outputs (systematic > ad-hoc)
- ✅ More credible (validation built-in)
- 🎯 Better insights (synthesis phase)

**Investment:**
- First project: +30 min (learning)
- Second: +20 min (getting comfortable)
- Third+: -50% time (mastery)

**ROI: Massive**

---

**TL;DR:**
1. **DEFINE** cíl (ChatGPT o1)
2. **RESEARCH** systematicky (Perplexity + Gemini + Copilot)
3. **VALIDATE** claims (Claude + manual)
4. **SYNTHESIZE** insights (NotebookLM + Claude)
5. **CREATE** output (right tool per format)

**Tag confidence. Document real-time. Iterate. Ship.**

---

**Print-friendly:** Vytiskni a měj u počítače pro příští research projekt.

---

**Verze:** 1.0 | **Listopad 2025** | **Pro:** Školení Prompt Engineering
**Detailní guide:** [05-multi-step-research-flow.md](./05-multi-step-research-flow.md)
