# Brand Voice a Content Principy

## Základní hlasový profil

### Tón komunikace
- **Kamarádský přístup:** Mluv přirozeně, jako když vysvětluješ něco známému
- **Přímočarost:** Jdi rovnou k věci
- **Upřímnost:** Přiznej, když je něco složité nebo není perfektní
- **Pozitivita:** Autentické nadšení, ne umělý hype

### Co NIKDY

❌ **Korporátní buzzwords:**
- "Leverage synergies"
- "Best practices" (raději "co funguje")
- "Going forward" (raději "od teď" nebo "dál")
- "Deep dive" (raději "podívat se detailně")
- "Game-changing" / "Revolutionary"
- "Cutting-edge" / "State-of-the-art"

❌ **Tech-speak:**
- Zbytečné anglicismy, když existuje české slovo
- Složité technické termíny bez vysvětlení
- Zkratky bez rozepsání (aspoň napoprvé)

❌ **Nafouknutá mluva:**
- "Implementovat strategii" → raději "začít dělat"
- "Optimalizovat procesy" → raději "zrychlit/zjednodušit"
- "Facilitovat workshop" → raději "vést workshop"

### Slovník - Používej vs. Nepoužívej

| ❌ Nepoužívej | ✅ Používej |
|--------------|-------------|
| Implementovat | Udělat, začít používat |
| Facilitovat | Pomoct, vést |
| Utilize | Použít |
| Leverage | Využít |
| Stakeholder | Člověk/tým, co to ovlivní |
| Touch base | Probrat, říct si |
| Best practice | To, co funguje |
| Pain point | Problém, co štve |

## Struktura obsahu

### Princip "Ukázat, ne vysvětlovat"

**Špatně:**
```
React hooks jsou moderní způsob, jak spravovat stav v React komponentách. 
Umožňují použití state a dalších React features bez psaní class komponenty.
```

**Dobře:**
```
Potřebuješ si pamatovat hodnotu? Použij useState:

const [count, setCount] = useState(0);

Teď máš proměnnou count a funkci setCount, která ji mění. 
To je celé.
```

### Pravidlo "Proč to koho zajímá"

Každý koncept vysvětluj s jasným benefitem:
- Ne: "useState je React hook pro state management"
- Ano: "useState ti umožní mít v komponentě hodnotu, co se mění - třeba počítadlo kliků"

### Struktura vysvětlení

1. **Co to je** (1 věta, jednoduše)
2. **Proč je to užitečné** (reálný příklad)
3. **Jak to použít** (živý příklad kódu)
4. **Časté chyby** (co nedělat)

## Praktičnost > Teorie

### Více příkladů, méně teorie

**Špatně:**
```
Factory pattern je creational design pattern, který poskytuje interface 
pro vytváření objektů v nadřazené třídě, ale umožňuje podřízeným třídám...
```

**Dobře:**
```
Představ si, že děláš různé typy tlačítek - primary, secondary, danger.
Místo psaní:
  if (type === 'primary') { return <PrimaryButton /> }
  if (type === 'secondary') { return <SecondaryButton /> }
  
Použiješ factory:
  ButtonFactory.create(type)
  
A máš hotovo.
```

### Ready-to-use šablony

Vždycky poskytni:
- Kód, který lze zkopírovat a použít
- Jasné označení, co změnit pro vlastní použití
- Výchozí hodnoty, které fungují

**Příklad:**
```javascript
// Zkopíruj tenhle kód a změň si názvy podle tvého projektu
function useFetchData(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  
  // ... zbytek kódu
}
```

## Vysvětlování složitých konceptů

### Metoda "Od známého k neznámému"

Začni s něčím, co student zná:
```
"Znáš Google Docs? Jak tam můžeš psát současně s někým jiným? 
WebSockets fungují podobně - server a prohlížeč si posílají zprávy 
tam a zpátky v reálném čase."
```

### Analogie z běžného života

```
"API je jako číšník v restauraci:
- Ty (frontend) si objednáš jídlo
- Číšník (API) to odnese do kuchyně  
- Kuchyň (backend) to připraví
- Číšník ti to přinese zpátky"
```

### Co vynechat

Soustřeď se na 80% use cases, ne 20% edge cases:
- Uč základní funkci, ne všechny možné parametry
- Často používané patterny, ne exotické corner cases
- Praktické tipy, ne teoretickou dokonalost

## Příklady kódu

### Best practices pro code snippets

**Vždycky:**
- Přidej komentáře v kódu
- Ukaž kompletní fungující příklad, ne jen fragmenty
- Označ, co je důležité

```javascript
// Základní useState hook - tohle budeš používat často
const [count, setCount] = useState(0); // 0 je výchozí hodnota

// Pro změnu hodnoty VŽDYCKY používej setter (setCount)
setCount(count + 1); // ✅ Správně

// NIKDY neměň přímo proměnnou
count = count + 1; // ❌ Takhle ne!
```

### Formát příkladů

```
[Krátký popis, co to dělá]

[Kompletní kód]

[Vysvětlení krok po kroku]

[Časté chyby a jak se jim vyhnout]
```

## Cvičení a úkoly

### Princip postupnosti

1. **Warm-up:** Velmi jednoduchý úkol na rozkoukání (2 min)
2. **Základní:** Aplikace hlavního konceptu (5-10 min)
3. **Pokročilý:** Kombinace více konceptů (15-20 min)
4. **Výzva:** Reálný problém z praxe (30+ min)

### Dobrý vs. špatný úkol

**Špatně:**
```
Vytvořte komponentu, která zobrazí seznam uživatelů s možností 
filtrování, řazení a stránkování. Použijte TypeScript a dodržte 
SOLID principy.
```

**Dobře:**
```
Úkol: Udělaj TODO list
- [ ] Zobraz seznam úkolů
- [ ] Přidej tlačítko na přidání nového
- [ ] Označ, když je hotovo

Bonus: Ulož do localStorage, aby se neztratilo po refreshi

Čas: 15 minut
```

## Cheat Sheets

### Struktura

1. **Hlavní myšlenky** (3-5 bodů)
2. **Rychlý přehled** (konzentráty info)
3. **Praktický příklad** (copy-paste ready)
4. **Časté chyby** (tabulka problém → řešení)

### Co na cheat sheet patří

✅ **ANO:**
- Nejpoužívanější příkazy/funkce
- Běžné patterny
- Syntax reminders
- Rychlé řešení častých problémů

❌ **NE:**
- Vysvětlování teorie
- Kompletní dokumentace
- Vzácné edge cases
- Všechno možné "pro jistotu"

## Gramatika a styl

### Tykaní vs. vykaní
- **Vykej** v oficiálnějších materiálech (studijní materiály)
- **Tykej** v příležitostnějších (komentáře, tipy, interakce)

### Délka vět
- Kratší je lepší
- Jedna myšlenka = jedna věta
- Odstavce max 3-4 věty

### Formátování
- **Bold** pro důležité koncepty (ne příliš často)
- `Code` pro kód, příkazy, názvy souborů
- > Bloky pro tipy nebo varování
- Emoji 💪 občas, ale ne všude

### Struktura odstavců

Každý odstavec:
1. První věta = hlavní myšlenka
2. Zbytek = podpora, příklad
3. Pokud je dlouhý, rozdel

## Interakce a zapojení

### Otázky pro zapojení

**Místo:**
"Rozumíte tomu? Máte nějaké otázky?"

**Používej:**
- "Zkuste si teď tohle..."
- "Kdo z vás narazil na tahle situaci?"
- "Co myslíte, že se stane když..."

### Tone indicators

- 💡 Pro tipy a triky
- ⚠️ Pro důležitá upozornění  
- ✅ Pro správný přístup
- ❌ Pro častá chyby
- 🚀 Pro pokročilé techniky
- 💪 Pro výzvy a úkoly

## Checklist kvalitního obsahu

Každý materiál zkontroluj:

- [ ] Je to v češtině?
- [ ] Tone je přirozený a kamarádský?
- [ ] Vysvětlil jsem "proč je to užitečné"?
- [ ] Jsou tam praktické příklady?
- [ ] Kód je copy-paste ready?
- [ ] Ukázal jsem časté chyby?
- [ ] Žádné buzzwords nebo tech-speak?
- [ ] Studenti to pochopí za 5 sekund čtení?
- [ ] Je to užitečné hned teď, ne "teoreticky jednou"?

---

## Varování: Neopakuj se

Vyhni se opakovanému používání stejných frází. Například:

**Přetížené fráze k omezení:**
- "bez zbytečných keců"
- "bez okolků"
- "to je celé"
- "a máš hotovo"

**Místo opakování stejných fází, variruj:**
- "jednoduše řečeno..."
- "v kostce..."
- "přímo k věci..."
- "prakticky..."
- "shrnutě..."

Kamarádský tón neznamená používat stále stejné výrazy. Přirozenost znamená variabilitu.
