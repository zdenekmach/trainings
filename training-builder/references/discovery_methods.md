# Discovery Methods for Training Requirements

This reference provides structured approaches for gathering training requirements based on the completeness of the initial request.

---

## Method Selection Guide

Use this decision tree to choose the right approach:

```
Initial request assessment:
│
├─ Detailed request (clear audience, goals, outline)
│  └─ Use: Quick Validation Method
│     └─ 1-2 iterations, 5 minutes
│
├─ Moderate request (some details, vague in places)
│  └─ Use: 5W1H Framework
│     └─ 2-3 iterations, 10 minutes
│
└─ Vague request (just topic or idea)
   └─ Use: Design Thinking Approach
      └─ 3-5 iterations, 15-20 minutes
```

---

## Method 1: Quick Validation (for well-defined requests)

**When to use:** User has clear vision, most details already defined

**Goal:** Confirm understanding and fill minor gaps

**Process:**

1. **Summarize back** what you understood:
   ```
   "Jestli to dobře chápu:
   - Školení pro [audience]
   - Cíl je naučit je [objectives]
   - Bude to trvat [duration]
   - Formát: [format]
   
   Mám to správně?"
   ```

2. **Ask 2-3 targeted questions** about gaps:
   ```
   "Pár rychlých otázek:
   - [Specific unclear point 1]?
   - [Missing detail 2]?
   - [Confirmation of assumption 3]?"
   ```

3. **Confirm and proceed:**
   ```
   "Super, máme to. Shrnu to do requirements dokumentu 
   a pak můžeme pokračovat researchem."
   ```

**Typical iterations:** 1-2  
**Time:** 5 minutes

**Example dialogue:**
```
User: "Potřebuju workshop o AI v product managementu, 
      pro PM team, 2 hodiny, chci aby uměli používat AI 
      pro user research a ideation."

Claude: "Perfektní, máš to jasně definované. Jen pár 
        upřesnění:
        - Kolik je jich v týmu?
        - Jakou mají zkušenost s AI nástroji teď?
        - Mají už nějaké nástroje, které používají?"

User: [Answers...]

Claude: "Skvělé, mám všechno. Dávám to do requirements 
        dokumentu a jdeme na research."
```

---

## Method 2: 5W1H Framework (for moderate requests)

**When to use:** Core idea clear, but missing important details

**Goal:** Systematically gather missing information

**Framework questions:**

### WHAT (Co)
- Co přesně mají umět po školení?
- Co je pro tebe úspěch tohoto školení?
- Co se nesmí stát? (Anti-goals)

### WHO (Kdo)
- Kdo jsou účastníci? (Role, seniorita)
- Kdo je decision maker na jejich straně?
- Kdo bude školení používat v praxi?

### WHY (Proč)
- Proč teď? Co se změnilo nebo změnit má?
- Proč by je to mělo zajímat?
- Jaký problém to řeší?

### WHEN (Kdy)
- Kdy se to má konat?
- Jak dlouho to má trvat?
- Kdy můžou začít praktikovat naučené?

### WHERE (Kde)
- Kde se bude konat? (Online/offline/hybrid)
- Kde teď jsou skills-wise? (Starting point)
- Kde mají být po školení? (Target state)

### HOW (Jak)
- Jak rychle to potřebujou umět?
- Jak budou praktikovat?
- Jak změříme úspěch?

**Process:**

1. **Start with WHY** (motivation is key):
   ```
   "Abych ti připravil to nejlepší školení, potřebuju 
   pochopit kontext. Proč teď školení o [topic]? 
   Co se děje, že je to aktuální?"
   ```

2. **Then WHO** (audience defines everything):
   ```
   "Super, teď mi pověz o lidech:
   - Jaké mají role?
   - Jak moc jsou v [topic] teď zkušení?"
   ```

3. **Follow with WHAT** (concrete objectives):
   ```
   "Co by pro tebe bylo úspěchem? Co konkrétně mají 
   po školení umět dělat jinak?"
   ```

4. **Clarify WHERE & WHEN** (logistics):
   ```
   "A prakticky:
   - Jak dlouho na to máme čas?
   - Online nebo naživo?"
   ```

5. **Confirm HOW** (measurement):
   ```
   "Jak poznáme že to zabralo? Jaké jsou metriky?"
   ```

**Typical iterations:** 2-3  
**Time:** 10 minutes

**Example dialogue:**
```
User: "Chci školení o agilních metodách pro náš tým."

Claude: "Ok, pomůžu ti to definovat. Nejdřív: proč teď? 
        Co se děje že se rozhodli pro agile školení?"

User: "Hodně projektů se vleče, myslíme že agile pomůže."

Claude: "Chápu. A kdo jsou ty lidi co na to půjdou?"

User: "Projektový tým - 2 PM, 3 vývojáři, 1 designer."

Claude: "Super. Co konkrétně chceš aby po školení uměli 
        dělat? Co je ten main skill?"

User: "Hlavně lepší plánování sprintů a retrospektivy."

Claude: "Perfekt. Ještě pár detailů..."
[Pokračuje s ostatními otázkami]
```

---

## Method 3: Design Thinking Approach (for vague requests)

**When to use:** User has just idea or topic, needs help defining everything

**Goal:** Co-create clear training vision through exploration

**5 Phases:**

### Phase 1: EMPATHIZE (Understand the need)

**Dig into the problem space:**

```
"Začněme od začátku. Řekni mi o lidech, pro který je to školení:
- Co dělají celý den?
- S čím se potýkají?
- Co je štve nebo frustruje?
- Kde cítíš, že by mohli být lepší?"
```

**Listen for:**
- Pain points (problems to solve)
- Aspirations (what they want to achieve)
- Current gaps (knowledge/skills missing)
- Context (why now, what's changing)

### Phase 2: DEFINE (Frame the opportunity)

**Synthesize what you heard:**

```
"Takže jestli to dávám dohromady správně:

Problém: [Pain points identified]
Opportunity: [What training could solve]
Impact: [What would change if successful]

Je to tak?"
```

**Collaboratively refine until clear.**

### Phase 3: IDEATE (Explore possibilities)

**Brainstorm training approaches:**

```
"Teď pojďme vymyslet jak na to. Napadá mě několik možností:

Option A: [Approach 1 - pros/cons]
Option B: [Approach 2 - pros/cons]  
Option C: [Approach 3 - pros/cons]

Co tě víc láká? Nebo máš jinou představu?"
```

**Generate options for:**
- Format (workshop/lecture/course)
- Depth (overview/deep-dive)
- Focus (breadth vs. depth)
- Practical vs. theoretical balance

### Phase 4: PROTOTYPE (Sketch the outline)

**Draft high-level structure together:**

```
"Ok, zkusím nasketčit osnovu. Co třeba takhle:

Module 1: [Topic] - [Time] - [Goal]
Module 2: [Topic] - [Time] - [Goal]
Module 3: [Topic] - [Time] - [Goal]

Jak to sedí? Co změnit?"
```

**Iterate on structure:**
- Add/remove modules
- Adjust time allocation
- Refine focus areas
- Check missing pieces

### Phase 5: TEST (Validate assumptions)

**Reality check:**

```
"Projdeme si to ještě jednou jinak:

Když student přijde: [Current state]
Po školení odchází: [Target state]
Největší challenge bude: [Assumption]

Souhlasíš? Nebo vidíš jinak?"
```

**Validate:**
- Are objectives realistic?
- Is duration appropriate?
- Are prerequisites reasonable?
- Will this solve the actual problem?

**Typical iterations:** 3-5  
**Time:** 15-20 minutes

**Example dialogue:**
```
User: "Chtěl bych něco o AI."

Claude: "AI je široké téma. Pomůžu ti to zúžit. 
        Řekni mi nejdřív - pro koho by to školení bylo?"

User: "Pro náš business tým."

Claude: "A co ti lidi dělají? Jaké mají role?"

User: "Různé - sales, marketing, nějaký product people."

Claude: "Super. A co je vede k tomu že chtějí školení o AI? 
        Co se u vás děje?"

User: "Vidíme že konkurence používá AI a my zaostáváme."

Claude: "Aha, takže jde o to nezůstat pozadu. A konkrétně 
        kde cítíte, že by AI mohla pomoct ve vaší práci?"

User: "No třeba v psaní textů, v analýze dat, v komunikaci..."

Claude: "Okej, takže tam jsou různé use cases. Pojďme na to 
        systematicky. Co je ta největší bolest právě teď?"

User: "Asi že lidi tráví moc času rutinní prací."

Claude: "Výborně, to je konkrétní problém. Tak co kdyby 
        cílem školení bylo naučit je automatizovat 
        nejběžnější úkoly pomocí AI? Myslíš že by to sedlo?"

[Iterates further to define specifics...]
```

---

## Special Cases

### Case: Multiple stakeholders with different needs

**Approach:** Identify primary vs. secondary audience

```
"Vidím že tam je mix rolí. Pojďme je rozdělit:

Primary audience (main focus): [Role X]
- Their needs: [A, B, C]
- Their level: [Beginner/Advanced]

Secondary audience (also present): [Role Y]
- Their needs: [D, E, F]
- Can we address them? [How]

Should we optimize for primary or try to serve both?"
```

### Case: User doesn't know what they don't know

**Approach:** Show examples and get reactions

```
"Ukážu ti pár příkladů školení na podobné téma. 
Řekni mi co tě oslovuje:

Example A: [Brief description]
Example B: [Brief description]
Example C: [Brief description]

Co by pro tvůj tým fungovalo nejlépe?"
```

### Case: Conflicting requirements

**Approach:** Surface the tradeoffs

```
"Vidím tam napětí mezi [X] a [Y]. Nemůžeme mít oboje, 
protože [reason]. Co je důležitější?

Option A: [Trade this for that]
Option B: [Trade that for this]

Čemu dát prioritu?"
```

### Case: Unrealistic expectations

**Approach:** Gentle reality check with alternatives

```
"Rozumím co chceš dosáhnout. Realita je, že [X] 
obvykle trvá [much longer]. V [short time] můžeme:

Realistic option: [What's achievable]
With tradeoff: [What to sacrifice]

Buď upravit rozsah, nebo čas. Co dává větší smysl?"
```

---

## Best Practices Across Methods

### 1. Ask open-ended questions first
❌ "Chceš 2 nebo 4 hodiny?"  
✅ "Jak dlouho podle tebe školení potřebuje trvat?"

### 2. Listen for implicit needs
User says: "Chtěli bychom víc týmové práce."  
Insight: Možná mají problém s komunikací → Důraz na kolaborativní cvičení

### 3. Validate understanding by paraphrasing
```
"Jestli to říkáš správně: [summary]. 
Mám to tak?"
```

### 4. Don't overwhelm with questions
- Max 3 questions at once
- Wait for answers before continuing
- Build on their responses

### 5. Make it conversational
❌ "Target audience demographics?"  
✅ "Kdo jsou ty lidi? Co dělají?"

### 6. Show empathy for constraints
```
"Chápu že máš jen 2 hodiny. To je tight, ale dá se to. 
Budeme muset být selektivní - zaměříme se na 
[core essentials]."
```

### 7. Offer expertise when appropriate
```
"Z mé zkušenosti, pro [this audience] funguje nejlépe 
[approach]. Ale ty je znáš líp - co myslíš?"
```

### 8. Co-create, don't dictate
❌ "Školení musí mít tyto moduly..."  
✅ "Co kdyby osnova vypadala nějak takhle... Co ty na to?"

---

## Red Flags to Watch For

**Flag 1: Too broad scope for time available**
```
Signal: "Chci pokrýt A, B, C, D, E za 2 hodiny"
Response: "To je hodně materiálu. Pojďme prioritizovat - 
         co MUSÍ umět na 100%, a co stačí zmínit?"
```

**Flag 2: Unclear success criteria**
```
Signal: "Prostě aby rozuměli [topic]"
Response: "Rozumět je široký pojem. Co konkrétně mají umět 
         UDĚLAT, co teď neumí?"
```

**Flag 3: Wrong training format for goals**
```
Signal: "Chci aby se naučili [complex skill] z lectury"
Response: "Complex skills potřebujou praxi. Co takhle 
         workshop s hands-on exercises místo jen prezentace?"
```

**Flag 4: Missing prerequisite assessment**
```
Signal: "Je to pro začátečníky... no někteří už [X] znají"
Response: "Takže je tam mix levelů. Jak zajistíme, aby 
         začátečníci nestáli a pokročilí se nenudili?"
```

**Flag 5: Disconnect between stated and real need**
```
Signal: "Chceme školení o [tool]" but problem is process, not tool
Response: "Zajímavé. A proč právě [tool]? Možná problém 
         je jinde a školení by mělo být o [actual need]?"
```

---

## Completion Checklist

Before moving to Research phase, ensure you have:

**Core elements:**
- [ ] Clear target audience description
- [ ] 3-5 SMART learning objectives
- [ ] Detailed outline with time allocation
- [ ] Prerequisites identified
- [ ] Success metrics defined

**Context:**
- [ ] Understanding of WHY now (motivation)
- [ ] Current state vs. desired state clear
- [ ] Constraints acknowledged (time, resources, etc.)

**Logistics:**
- [ ] Format decided (workshop/lecture/course)
- [ ] Duration locked in
- [ ] Delivery method clear (online/offline/hybrid)

**Validation:**
- [ ] User confirmed the requirements document
- [ ] No obvious red flags or misalignments
- [ ] Scope is realistic for time available

---

## Transition to Research Phase

Once requirements are solid:

```
"Perfektní, mám všechno co potřebuju. Shrnu to do 
requirements dokumentu a pak se můžeme vrhnout na research.

Chceš si ten dokument projít nebo můžeme rovnou pokračovat?"

[If they want to review → show document, iterate if needed]
[If they trust it → proceed to research]
```

---

*Use this reference to adapt your discovery approach based on how much the user knows about what they want. The goal is always to get to a clear, actionable requirements document efficiently.*
