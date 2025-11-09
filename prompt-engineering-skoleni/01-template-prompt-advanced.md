# Pokročilá šablona pro tvorbu promptů

> **Verze:** 2.0 (Listopad 2025)
> **Účel:** Univerzální šablona pro tvorbu efektivních promptů pro všechny hlavní AI modely
> **Složitost:** Plná verze - použij jen sekce, které potřebuješ

---

## 📋 JAK TUTO ŠABLONU POUŽÍVAT

**Progresivní přístup (doporučeno):**
1. **Začni jednoduše** - použij jen sekce: Úkol + Formát výstupu
2. **Pokud výstup není dobrý**, přidej: Kontext + Role
3. **Stále nesedí?** Přidej: Proces & Metodologie + Příklady
4. **Pro kritické úkoly**, použij celou šablonu

**Typy úkolů a doporučené sekce:**
- **Jednoduchý dotaz** → Hlavní úkol + Formát výstupu
- **Analytický úkol** → + Kontext + Proces & Metodologie
- **Kreativní úkol** → + Role + Referenční příklady
- **Komplexní/kritický úkol** → Všechny sekce

---

## 🎯 HLAVNÍ ÚKOL
> **Proč je tahle sekce první:** Začni s tím nejdůležitějším - co vlastně chceš.

**Úkol:**
[Jeden jasný, konkrétní, měřitelný úkol. Použij aktivní sloveso: "Analyzuj", "Vytvoř", "Navrhni", "Zhodnoť"]

**Příklad špatně:** "Potřebuju něco s našimi daty"
**Příklad dobře:** "Analyzuj poslední kvartální data prodejů a identifikuj 3 hlavní trendy"

**Success criteria (měřitelné výsledky):**
- ✓ [Konkrétní měřitelný výsledek 1 - např. "Obsahuje min. 3 datové pohledy"]
- ✓ [Konkrétní měřitelný výsledek 2 - např. "Každý trend má kvantitativní podporu"]
- ✓ [Konkrétní měřitelný výsledek 3 - např. "Délka max. 2 strany A4"]

---

## 📝 FORMÁT VÝSTUPU
> **Proč je důležité:** Bez jasného formátu dostaneš wall of text. S jasným formátem dostaneš strukturovaný výstup.

**Struktura (použij konkrétní template):**

```markdown
# [Nadpis hlavní]

## Sekce 1: [Název]
[Obsah sekce 1]

## Sekce 2: [Název]
[Obsah sekce 2]

### Podsekce 2.1
- Bullet point 1
- Bullet point 2

## Závěr
**3 klíčové takeaways:**
1. [Takeaway 1]
2. [Takeaway 2]
3. [Takeaway 3]
```

**Alternativní formáty:**
- **Tabulka:** Pro srovnání nebo kategorizaci
- **JSON:** Pro strukturovaná data
- **Checklist:** Pro akční kroky
- **Vizuální struktura:** Pro hierarchie nebo flowcharty (textové)

---

## 🎭 KONTEXT & POZADÍ
> **Kdy použít:** Když úkol vyžaduje pochopení situace nebo AI potřebuje doménové znalosti.

**Situace:**
[Popište aktuální stav, problém nebo příležitost. 2-4 věty stačí.]

**Relevantní informace:**
- **Klíčový fakt 1:** [např. "Projekt má deadline 31.12.2025"]
- **Klíčový fakt 2:** [např. "Budget je omezený na 500k Kč"]
- **Omezení prostředí:** [např. "Pracujeme v regulovaném prostředí farma"]

**Cílová skupina:**
[Pro koho je výstup určen - úroveň expertízy, role]
- Příklad: "Senior management bez technického backgroundu"
- Příklad: "Junior vývojáři s 1-2 roky zkušeností"

**💡 Pro tip:** Dej nejdůležitější kontext **na začátek NEBO na konec** promptu (primacy/recency effect).

---

## 👤 ROLE & EXPERTIZA
> **Kdy použít:** Když potřebuješ specifickou perspektivu nebo odbornost.

Vystupuj jako **[specifická role/expert]** s těmito charakteristikami:
- **Kompetence 1:** [např. "15+ let v business analýze"]
- **Kompetence 2:** [např. "Expert na requirements elicitation"]
- **Perspektiva:** [např. "Pragmatický přístup s důrazem na ROI"]

**Tone of voice:**
- [ ] Profesionální/formální
- [ ] Přátelský/konverzační
- [ ] Technický/precizní
- [ ] Kreativní/experimentální
- [ ] Výukový/vysvětlující

**Pro pokročilé:**
```
Jsi senior business analytik s 15 lety zkušeností v enterprise prostředí.
Tvůj přístup kombinuje best practices (BABOK, Agile) s pragmatismem.
Komunikuješ jasně, bez zbytečného žargonu, vždy s konkrétními příklady.
```

---

## 🔄 PROCES & METODOLOGIE
> **Kdy použít:** Pro komplexní úkoly, kde je důležitý způsob zpracování, ne jen výsledek.

**Postupuj krok za krokem:**

**1. [Krok 1 - Analýza vstupů]**
   - Přečti a pochop všechny poskytnuté dokumenty
   - Identifikuj klíčové oblasti a témata
   - *Očekávaný mezioutput:* Seznam hlavních témat

**2. [Krok 2 - Identifikace patterns]**
   - Hledej opakující se vzory, konflikty, mezery
   - Kategorizuj nálezy podle důležitosti
   - *Očekávaný mezioutput:* Kategorizovaný seznam nálezů

**3. [Krok 3 - Syntéza a doporučení]**
   - Syntetizuj nálezy do koherentního celku
   - Navrhni konkrétní akční kroky
   - *Očekávaný mezioutput:* Finální doporučení s reasoning

**Pro komplexní úkoly:**
> "Před finálním výstupem ukaž své uvažování (chain-of-thought reasoning). Vysvětli proč jsi dospěl/a k těmto závěrům."

**💡 Pro tip:** Pro analytické úkoly přidej: "Pokud narazíš na ambiguitu nebo konflikt, explicitně to uveď a nabídni možnosti řešení."

---

## ✅ POŽADAVKY & SPECIFIKACE
> **Kdy použít:** Když máš specifické nároky na kvalitu, rozsah nebo obsah.

### Obsahové požadavky:
- ✓ [Požadavek 1 s konkrétním kritériem - např. "Každé tvrzení má zdroj nebo datovou podporu"]
- ✓ [Požadavek 2 - např. "Obsahuje min. 3 alternativní pohledy na problém"]
- ✓ [Požadavek 3 - např. "Identifikuje rizika a jejich mitigaci"]

### Technické požadavky:
- **Délka:** [min-max slova/znaky/stránky - např. "800-1200 slov"]
- **Jazyk:** [CS/EN + úroveň - např. "Čeština, odborná ale srozumitelná"]
- **Formát:** [markdown/JSON/CSV/prostý text]
- **Struktura:** [počet sekcí, hloubka zanoření]

### Kvalitativní požadavky:
- **Hloubka analýzy:** [povrchní/střední/hluboká]
- **Originalita:** [standardní/kreativní/inovativní přístup]
- **Přesnost:** [přibližné odhady OK / musí být precizní]
- **Praktičnost:** [teoretická/prakticky použitelná/přímo implementovatelná]

---

## 📚 REFERENČNÍ PŘÍKLADY (Few-Shot Learning)
> **Kdy použít:** Když chceš specifický styl výstupu nebo AI nerozumí tvému požadavku z popisu.

### Příklad 1: [Pozitivní příklad - jak TO dělat]

**Scénář:** [Konkrétní situace]

**Vstup:**
```
[Ukázkový vstup]
```

**Očekávaný výstup:**
```
[Ukázkový ideální výstup - buď konkrétní a detailní]
```

**Proč je tento příklad dobrý:**
- [Důvod 1]
- [Důvod 2]

### Příklad 2: [Negativní příklad - jak to NEDĚLAT]

**Vstup:**
```
[Ukázkový vstup]
```

**Špatný výstup:**
```
[Ukázka špatného výstupu]
```

**Co je špatně:**
- ❌ [Problém 1]
- ❌ [Problém 2]

**💡 Pro tip:**
- 1-2 příklady: základní směrování
- 3-5 příkladů: konzistentní styl
- 5+ příkladů: komplex pattern recognition

---

## 🚫 OMEZENÍ & GUARDRAILS
> **Kdy použít:** Když potřebuješ zabránit nežádoucím výstupům nebo přístupům.

### NEDĚLEJ:
- ❌ [Konkrétní zakázaný přístup - např. "Nepoužívej technický žargon bez vysvětlení"]
- ❌ [Co přeskočit - např. "Nevynechávej reasoning - vždy vysvětli PROČ"]
- ❌ [Čeho se vyvarovat - např. "Nedělej předpoklady o datech, která nejsou poskytnutá"]

### LIMITY:
- **Rozsah:** [max/min rozsah - např. "Max 3 stránky, min 1 stránka"]
- **Čas/komplexita:** [např. "Quick analysis, ne deep research"]
- **Zdroje:** [např. "Používej jen poskytnuté dokumenty, ne externí znalosti"]

### ETICKÉ & COMPLIANCE HRANICE:
- [např. "Respektuj GDPR - nesdílej osobní údaje"]
- [např. "Vyhni se bias - zajisti diverse perspectives"]
- [např. "Fact-check tvrzení pokud nejsi 100% jistý"]

---

## ✔️ VALIDAČNÍ CHECKLIST
> **Kdy použít:** Pro kritické úkoly, kde je nutná vysoká kvalita.

**Instrukce pro AI:**
"Před odevzdáním výstupu projdi tento checklist. Pokud něco nesedí, oprав to."

**Checklist:**
- [ ] **Úplnost:** Jsou splněny všechny požadavky ze sekce Success Criteria?
- [ ] **Formát:** Je dodržen template z sekce Formát Výstupu?
- [ ] **Relevance:** Je každá část výstupu relevantní k hlavnímu úkolu?
- [ ] **Faktická správnost:** Jsou všechna tvrzení podložená nebo označená jako odhad?
- [ ] **Délka:** Je dodržen požadovaný rozsah?
- [ ] **Jazyk:** Je tone of voice a jazyk vhodný pro cílovou skupinu?
- [ ] **Konzistence:** Neodporují si části výstupu navzájem?
- [ ] **Actionability:** Jsou doporučení konkrétní a použitelná?

---

## 🔁 ITERACE & ZPĚTNÁ VAZBA
> **Pro interaktivní konverzace.**

**Po prvním výstupu:**
1. ✅ Prezentuj výstup
2. 🤔 Zeptej se: *"Odpovídá tento výstup tvým očekáváním, nebo bys chtěl/a něco upravit?"*
3. 🔧 Buď připraven na:
   - Upřesnění specifických sekcí
   - Změnu úhlu pohledu
   - Rozšíření/zkrácení
   - Změnu formátu

**Pro opakované úkoly:**
"Pokud budeš dělat podobné úkoly, řekni mi a já optimalizuji svůj přístup na základě tvé zpětné vazby."

---

## 🏷️ METADATA (Volitelné)
> **Pro organizaci a prioritizaci.**

- **Priorita:** [ ] Vysoká [ ] Střední [ ] Nízká
- **Složitost:** [ ] Jednoduchý [ ] Střední [ ] Komplexní
- **Časový odhad:** [ ] Rychlý (<5 min) [ ] Střední (5-15 min) [ ] Hloubkový (15+ min)
- **Model preference:** [ ] Any [ ] Claude [ ] GPT [ ] Gemini [ ] Specific (viz důvod)
- **Důvod preference:** [např. "Claude - lepší na dlouhé analytické úkoly"]

---

## 📊 POKROČILÉ TECHNIKY (Volitelné)

### Chain-of-Thought (CoT) Reasoning
Pro komplexní analytické úkoly přidej:
```
Před finální odpovědí:
1. Ukaž své uvažování krok za krokem
2. Vysvětli alternativy, které jsi zvažoval/a
3. Odůvodni proč jsi vybral/a tuto cestu
```

### Self-Consistency Check
Pro kritické úkoly:
```
Po dokončení výstupu:
1. Přečti si ho znovu
2. Identifikuj možné konflikty nebo slabá místa v argumentaci
3. Pokud něco nesedí, uprav to
4. Pokud si nejsi jistý, explicitně to uveď
```

### Structured Thinking
Pro strategické úkoly:
```
Použij framework: [SWOT/PESTLE/5 Why's/Jobs-to-be-Done]
Aplikuj ho systematicky na každý aspekt problému.
```

### Multi-Perspective Analysis
Pro komplexní business problémy:
```
Analyzuj problém z těchto perspektiv:
1. Stakeholder A (jejich priority a concerns)
2. Stakeholder B (jejich priority a concerns)
3. Technical perspective
4. Business perspective
5. End-user perspective

Identifikuj konflikty a navrhni balancované řešení.
```

---

## 💡 QUICK TIPS

1. **Začni jednoduše, iteruj:** Nepoužívej celou šablonu hned. Začni s úkolem + formátem.
2. **Buď specifický:** "Dobře" ≠ konkrétní. "Max 500 slov, 3 bullet points, formální tón" = konkrétní.
3. **Dej příklady:** Jeden dobrý příklad > 3 odstavce vysvětlování.
4. **Struktura matters:** AI (i lidé) se líp orientují v #headings a bullet points.
5. **Prioritizuj kontext:** Nejdůležitější info dej na **začátek** nebo **konec** promptu.
6. **Testuj a optimalizuj:** První prompt je vždycky draft. Iteruj na základě výsledků.

---

## 🎓 DALŠÍ KROKY

**Po použití této šablony:**
1. **Ulož si funkční prompt** - můžeš ho použít jako template pro podobné úkoly
2. **Vytvoř si Custom GPT/Skill** - pokud budeš úkol opakovat (viz školení o kontextu)
3. **Sdílej s týmem** - standardizované prompty = konzistentní výstupy
4. **Iteruj** - zjistíš co u tvého use case funguje nejlíp

---

**Verze dokumentu:** 2.0
**Poslední update:** Listopad 2025
**Optimalizováno pro:** Claude Sonnet 4, GPT-4.1, Gemini 2.5 Pro, MS Copilot
**Autor:** Expert na prompt engineering
**Licence:** Použij jak chceš, sdílej s kýmkoli
