---
name: training-builder
description: Prepare comprehensive training content in Czech including training requirements definition, research, reflection, and configurable outputs (cheat sheets, student guidelines, presentation slides with presenter notes, exercises with solutions). Use whenever preparing training materials, lectures, workshops, or educational content, especially for topics like AI, AI in business analysis/product design/project management, project management, agile, or organizational transformation. Triggered by requests like "prepare training on X", "create lecture materials", "make workshop content", "design course for Y", or similar educational content preparation tasks.
---

# Training Builder

## Overview

This skill creates comprehensive training materials in Czech through an iterative, research-driven workflow. It specializes in practical, student-friendly content for topics including AI, AI applications in business, project management, agile methodologies, and organizational transformation.

## Workflow Phases

### Phase 0: Discovery - Iterative Requirements Definition

**Goal:** Create a clear Training Requirements Document through dialogue.

**Process:**

1. **Assess completeness of initial request:**
   - If detailed (clear audience, goals, outline) → Quick validation questions only
   - If vague (just topic idea) → Full discovery process

2. **Iterative dialogue to define:**
   - **Target audience:** Who are they? Experience level? Background? Roles?
   - **Training objectives:** What should students be able to DO after? (SMART goals)
   - **Scope & outline:** Topics to cover? Duration? Format (workshop/lecture/self-study)?
   - **Prerequisites:** What should students know beforehand?
   - **Success metrics:** How to measure if training worked?

3. **Discovery method selection** (see `references/discovery_methods.md`):
   - For well-defined requests: Simple clarification questions
   - For vague ideas: 5W1H framework or Design Thinking approach
   - Adapt based on user responses

4. **Output:** Training Requirements Document
   - Save to: `[topic]-requirements.md`
   - Template: `assets/training_requirements_template.md`
   - Contains: Executive summary, audience persona, SMART objectives, detailed outline, prerequisites, success metrics

**Example dialogue:**
```
Claude: "Vidím, že chceš školení o AI. Pomůžu ti to správně definovat. 
Kolik iterací potřebujeme záleží na tom, jak moc máš promyšleno.

Pro koho je to školení určeno? Jakou mají úroveň znalostí?"

[User responds...]

Claude: "Super. Co by měli umět po školení? Dej mi 2-3 konkrétní věci."

[Iterates until clear picture emerges...]
```

**Completion criteria:** User confirms the requirements document captures their vision.

---

### Phase 1: Research - Current Information Gathering

**Goal:** Gather up-to-date information about the training topic from the web.

**Process:**

1. **Ask research depth preference:**
   ```
   "Chceš rychlý research (3-5 zdrojů, ~5 minut) 
   nebo důkladný research (10+ zdrojů, ~15 minut)?"
   ```

2. **Execute web searches:**
   - Quick: 3-5 targeted searches
   - Deep: 10+ comprehensive searches including:
     - Current trends and best practices
     - Recent articles and case studies  
     - Tools and frameworks
     - Common challenges and solutions
     - Real-world applications

3. **Focus areas based on topic:**
   - **AI topics:** Latest models, tools, practical applications, ethical considerations
   - **Business/PM topics:** Current methodologies, case studies, industry trends
   - **Agile/transformation:** Recent approaches, success stories, common pitfalls

4. **Document findings:**
   - Save to: `[topic]-research.md`
   - Template: `assets/research_report_template.md`
   - Include:
     - Executive summary of findings
     - Key insights by category
     - Relevant sources with URLs
     - Quotes and statistics
     - Emerging trends
     - Practical examples found

**Output format:**
```markdown
# Research Report: [Topic]

## Executive Summary
[2-3 key takeaways]

## Key Findings

### Current Trends
- Finding 1 [Source URL]
- Finding 2 [Source URL]

### Best Practices
- Practice 1 [Source URL]

### Tools & Resources
- Tool 1: Description [Source URL]

### Real-World Examples
- Example 1 [Source URL]

## Sources
1. [Title](URL) - Key points
2. [Title](URL) - Key points
```

---

### Phase 2: Reflection - Outline Review & Refinement

**Goal:** Compare initial outline with research findings and propose improvements.

**Process:**

1. **Analyze gaps:**
   - What's in research but missing from outline?
   - What's in outline but needs updating based on research?
   - Are there new tools/approaches to include?

2. **Generate improvement proposals:**
   ```markdown
   ## Reflection on Training Outline
   
   ### Confirmed Strengths
   - [What's good in current outline]
   
   ### Suggested Additions
   - [New topics from research]
   - Reasoning: [Why it's relevant]
   
   ### Suggested Updates
   - [Existing topic] → Update to include [new info]
   - Reasoning: [Why it matters]
   
   ### Optional Enhancements
   - [Nice-to-have additions]
   ```

3. **Iterate with user:**
   - Present reflection
   - Discuss priorities
   - Update requirements document if needed

**Completion criteria:** User approves final outline (either original or refined version).

---

### Phase 3: Output Selection - Choose Materials to Create

**Goal:** Determine which materials to generate based on training type.

**Process:**

1. **Analyze training context:**
   - Format: Workshop, lecture, self-study, blended?
   - Duration: Half-day, full-day, multi-session, course?
   - Audience size: Small group, large audience, individual?
   - Delivery: In-person, online, hybrid?

2. **Propose output combinations:**

   **Workshop (interactive, instructor-led):**
   - ✅ Presentation with presenter notes (essential)
   - ✅ Exercises with solutions (essential)
   - ✅ Cheat sheet (recommended)
   - ⚪ Student guidelines (optional - for pre-work or follow-up)

   **Lecture (primarily presentation):**
   - ✅ Presentation with presenter notes (essential)
   - ✅ Cheat sheet (recommended)
   - ⚪ Student guidelines (optional - for deeper dive)
   - ⚪ Exercises (optional - for homework)

   **Self-study course:**
   - ✅ Student guidelines (essential)
   - ✅ Exercises with solutions (essential)
   - ✅ Cheat sheet (recommended)
   - ⚪ Presentation (optional - if recording videos)

   **Training-the-trainer:**
   - ✅ All materials (presentation, guidelines, exercises, cheat sheet)

3. **Present recommendations:**
   ```
   "Na základě toho, že jde o [workshop/lecture/course], 
   doporučuju vytvořit:
   
   Určitě:
   - [ ] Prezentace s poznámkami pro lektora
   - [ ] Cvičení s řešeními
   
   Hodilo by se:
   - [ ] Cheat sheet
   
   Volitelně:
   - [ ] Studijní materiály
   
   Co z toho chceš vytvořit? Můžeš upravit seznam."
   ```

4. **User confirms selection**

**Available outputs:**
- **Cheat sheet** (`assets/cheatsheet_template.md`) - Quick reference
- **Student guidelines** (`assets/student_guidelines_template.md`) - Comprehensive self-study
- **Presentation** (`assets/presentation_template.md`) - Slides + detailed presenter notes
- **Exercises** (`assets/exercises_template.md`) - Practice tasks with solutions

---

### Phase 4: Content Creation - Generate Selected Materials

**Goal:** Create high-quality, practical training materials.

**Critical: Read brand voice first:**
```bash
view references/content_principles.md
```

**For each selected output:**

1. **Read appropriate template:**
   ```bash
   view assets/[template-name].md
   ```

2. **Gather content sources:**
   - Training Requirements Document
   - Research findings
   - Content principles

3. **Create content following principles:**
   - Write in Czech
   - Casual, friendly tone (but not repetitive)
   - Practical examples over theory
   - Show first, explain after
   - Copy-paste ready code/templates
   - Real-world scenarios

4. **Apply topic-specific best practices:**

   **For AI topics:**
   - Include actual prompts and examples
   - Show common mistakes with AI tools
   - Emphasize practical applications over theory
   - Include ethical considerations naturally
   - Provide ready-to-use templates

   **For Business/PM topics:**
   - Real case studies and scenarios
   - Templates and frameworks to use immediately
   - Concrete action steps
   - Common pitfalls and how to avoid them

   **For Agile/Transformation:**
   - Practical exercises for team dynamics
   - Change management tips
   - Real transformation stories
   - Facilitation guides and scripts

**Creation order (for consistency):**
1. Cheat sheet (if selected) - Sets core messages
2. Student guidelines (if selected) - Detailed content
3. Presentation (if selected) - Visual storytelling
4. Exercises (if selected) - Hands-on practice

---

### Phase 5: Quality Check & Delivery

**Before delivering, verify:**

**Content quality:**
- [ ] All content in Czech
- [ ] Practical examples present in every section
- [ ] No repetitive phrases ("bez zbytečných keců", "bez okolků" overused)
- [ ] Clear learning objectives met
- [ ] Casual tone without buzzwords
- [ ] Research insights incorporated

**Technical quality:**
- [ ] Code examples are complete and working
- [ ] All cross-references work
- [ ] Solutions provided for all exercises
- [ ] Presenter notes detailed enough
- [ ] Templates properly filled

**Completeness:**
- [ ] All selected materials created
- [ ] Files saved to `/mnt/user-data/outputs/`
- [ ] Consistent terminology across materials
- [ ] Requirements document reflects final version

**Package and deliver:**

1. **Create directory structure:**
   ```
   [training-topic]/
   ├── 00-requirements.md
   ├── 01-research.md
   ├── 02-cheatsheet.md (if created)
   ├── 03-student-guide.md (if created)
   ├── 04-presentation.md (if created)
   └── 05-exercises.md (if created)
   ```

2. **Generate all files** in `/mnt/user-data/outputs/[training-topic]/`

3. **Provide links** to each document

4. **Include usage guide:**
   ```markdown
   ## Jak s materiály pracovat
   
   **Pro studenty:**
   1. [Doporučené pořadí]
   2. [Časová dotace]
   
   **Pro lektora:**
   1. [Příprava]
   2. [Doporučený časový plán]
   3. [Interakční body]
   ```

---

## Key Principles (from content_principles.md)

**Always remember:**

**Tone:**
- Casual and friendly but not repetitive
- Direct, practical
- Authentic enthusiasm

**Structure:**
- Examples first, explanations after
- One concept = one clear benefit  
- Simple language, avoid jargon
- Analogies from daily life

**Language:**
- Czech throughout
- Avoid corporate buzzwords
- Explain abbreviations first time
- Simple > Complex

**Examples:**
- Complete, working code
- Copy-paste ready
- Clearly commented
- Show common mistakes too

**Focus:**
- "How to use" over "What it is"
- Real scenarios over theory
- Templates over descriptions
- Immediately applicable

---

## Templates & References

**Templates:** `assets/` directory
- `training_requirements_template.md` - Requirements doc structure
- `research_report_template.md` - Research findings format
- `cheatsheet_template.md` - Quick reference format
- `student_guidelines_template.md` - Self-study structure
- `presentation_template.md` - Slides + notes format
- `exercises_template.md` - Practice with solutions

**References:** `references/` directory  
- `content_principles.md` - Brand voice, writing style (READ FIRST)
- `discovery_methods.md` - Techniques for requirements gathering

---

## Workflow Decision Tree

```
START: User requests training
│
├─ Is request detailed? 
│  ├─ YES → Quick validation (Phase 0-lite)
│  └─ NO → Full discovery (Phase 0-full)
│
├─ Phase 0: Create requirements doc
│  └─ Iterate until user satisfied
│
├─ Phase 1: Ask research depth
│  ├─ Quick (3-5 searches)
│  └─ Deep (10+ searches)
│  └─ Create research report
│
├─ Phase 2: Reflect on outline
│  └─ Propose improvements
│  └─ Update if user agrees
│
├─ Phase 3: Recommend outputs
│  └─ User selects materials to create
│
├─ Phase 4: Generate selected materials
│  └─ Read content principles first
│  └─ Create in order for consistency
│
└─ Phase 5: Quality check & deliver
   └─ Package all files
   └─ Provide usage guide
```

---

## Tips for Success

**Discovery phase:**
- Don't overwhelm with questions - ask 2-3 at a time
- Listen for implicit needs ("We keep repeating mistakes" → include common pitfalls section)
- Validate understanding by summarizing back

**Research phase:**
- For quick research: Focus on authoritative sources and recent articles
- For deep research: Include diverse perspectives, tools, case studies
- Always save URLs for later reference
- Note publication dates to assess recency

**Content creation:**
- Start simple, add complexity gradually
- Every section needs at least one practical example
- Show the "wrong way" to prevent mistakes
- Make everything immediately usable

**For technical content:**
- Test all code examples
- Include copy-paste ready snippets
- Explain WHY, not just HOW
- Provide troubleshooting tips

**For non-technical content:**
- Use concrete scenarios from real work
- Provide templates and checklists  
- Include facilitation tips
- Make it actionable immediately

**When stuck:**
- Re-read content_principles.md
- Ask: "Would I enjoy learning from this?"
- Test: "Can someone use this without my help?"
- Remember: Useful > Perfect, Simple > Complete
