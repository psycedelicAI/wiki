# AI-tankpartner i skolan: lektionsflöde

## Status

- Status: Konceptuell arbetsmodell
- Version: 0.1
- Område: Skolkuraterad AI, teknikundervisning och kreativ problemlösning
- Relaterat koncept: AI-continuity
- Senast uppdaterad: 2026-09-15

---

## Relaterade dokument

- [AI som tankpartner i skolan](AI-Som-Tankpartner-I-Skolan.md)
- [Prompt, YAML och arbetsflöde](AI-Tankpartner-Prompt-och-YAML.md)
- [AI-tankpartner: lektionsflöde](AI-Tankpartner-Lektionsflode.md)

Det första dokumentet beskriver idén och den pedagogiska visionen.

Det andra dokumentet beskriver AI:ns promptstruktur, YAML-konfiguration och
systemregler.

Detta dokument beskriver hur AI-tankpartnern används under en faktisk lektion.

---

## Syfte

Lektionsflödet ger läraren och eleverna en tydlig struktur för hur AI kan
användas som en kreativ och teknisk tankpartner.

AI:n ska stödja:

- idéutveckling;
- problemlösning;
- tekniskt tänkande;
- planering;
- testning;
- reflektion;
- dokumentation av projektets utveckling.

AI:n ska inte:

- göra skoluppgiften åt eleverna;
- skapa färdiga inlämningar;
- fungera som facit;
- ersätta praktiskt arbete;
- ersätta lärarens pedagogiska ansvar.

---

## Grundmodell

```text
Läraren skapar ramen
        ↓
Eleverna tänker själva först
        ↓
AI:n ställer frågor
        ↓
Eleverna utforskar idéer
        ↓
Gruppen väljer riktning
        ↓
AI:n hjälper till med planering
        ↓
Eleverna bygger, testar eller undersöker
        ↓
AI:n hjälper till med reflektion
        ↓
Läraren granskar projektets workstate
```

---

## Översikt över lektionen

| Fas | Ansvarig | Huvudsyfte |
|---|---|---|
| 1. Förberedelse | Lärare | Skapa lektionsramen |
| 2. Introduktion | Lärare | Presentera problem och mål |
| 3. Första tanke | Elev eller grupp | Formulera egna idéer |
| 4. Utforskning | Elev och AI | Utveckla möjliga riktningar |
| 5. Beslut | Elev eller grupp | Välja egen riktning |
| 6. Planering | Elev och AI | Skapa en genomförbar plan |
| 7. Praktiskt arbete | Elev eller grupp | Bygga, testa eller undersöka |
| 8. Reflektion | Elev och AI | Förstå vad som hände |
| 9. Workstate | AI och lärare | Dokumentera projektets läge |
| 10. Fortsättning | Lärare och grupp | Bestämma nästa steg |

---

## Fas 1: Läraren förbereder lektionen

Läraren bestämmer:

- årskurs;
- ämne;
- lektionsmål;
- tidsram;
- gruppstorlek;
- uppgiftens problem;
- tillgängliga material;
- säkerhetsregler;
- vilka AI-funktioner som får användas;
- vad som får sparas efter lektionen.

## Exempel

```yaml
lesson:
  grade: "årskurs 5"
  subject: "teknik"
  duration_minutes: 60
  goal: >
    Eleverna ska utveckla och planera en teknisk lösning på ett vardagsproblem.
  problem: >
    Hur kan vi göra det enklare att hitta och organisera saker i klassrummet?
  materials:
    - "kartong"
    - "papper"
    - "tejp"
    - "pennor"
    - "sax"
  ai_mode:
    enabled: true
    mode: "tankpartner"
    generate_finished_assignment: false
    teacher_review_required: true
```

---

## Fas 2: Läraren introducerar uppgiften

Läraren presenterar:

- vilket problem eleverna ska undersöka;
- varför problemet är relevant;
- vad eleverna ska skapa eller planera;
- vilka begränsningar som gäller;
- vilka material som finns;
- vilka säkerhetsregler som gäller;
- hur AI får användas.

## Instruktion till eleverna

> AI:n ska hjälpa er att tänka vidare.
>
> Den ska inte ge er ett färdigt svar eller göra arbetet åt er.
>
> Ni ska själva välja idé, fatta beslut, bygga, testa och förklara.

---

## Fas 3: Eleverna tänker själva först

Innan AI:n används ska eleverna få:

- tänka individuellt;
- skissa;
- skriva ned en första idé;
- diskutera med gruppen;
- formulera vad de tycker är problemet.

## Eleverna dokumenterar

```text
Vårt första problem:
____________________________________

Vår första idé:
____________________________________

Varför tror vi att idén kan fungera?
____________________________________

Vad är vi osäkra på?
____________________________________
```

AI:n ska inte ersätta elevens första tanke.

Den första tanken kan vara ofärdig, konstig eller opraktisk. Det är en del av
den kreativa processen.

---

## Fas 4: AI:n börjar som frågeställare

AI:n ska inte börja med att ge en lång lösning.

Den ska först ställa frågor som hjälper eleverna att förtydliga:

- vilket problem de försöker lösa;
- vem lösningen är till för;
- vilka begränsningar som finns;
- vad de redan har tänkt på;
- vad som behöver undersökas.

## Exempel

**Eleverna:**

> Vi vill bygga något som gör klassrummet bättre.

**AI:n:**

> Vad är det som fungerar dåligt i klassrummet just nu?
>
> Är problemet ljud, ljus, temperatur, ordning eller något annat?
>
> Vad har ni själva redan funderat på?

AI:n ska ställa ett begränsat antal frågor åt gången.

Målet är dialog, inte ett långt föredrag.

---

## Fas 5: AI:n hjälper gruppen att utforska idéer

När gruppen har beskrivit problemet kan AI:n visa flera möjliga riktningar.

## Exempel

**Eleverna:**

> Det är ofta stökigt när vi ska hitta våra saker.

**AI:n:**

> Då kan ni undersöka tre riktningar:
>
> 1. Ett smartare förvaringssystem.
> 2. Färgkodning eller symboler.
> 3. En enkel teknisk lösning som visar var saker ska ligga.
>
> Vilken riktning tycker ni verkar mest intressant, och varför?

AI:n bör:

- visa flera alternativ;
- förklara skillnader;
- peka på möjliga problem;
- undvika att utse en vinnare;
- fråga vad eleverna själva tycker.

---

## Alternativ ska inte presenteras som facit

AI:n ska använda formuleringar som:

- ”En möjlig riktning är...”
- ”Ni skulle kunna undersöka...”
- ”En fördel kan vara...”
- ”En möjlig begränsning är...”
- ”Vad tror ni själva?”
- ”Hur skulle ni kunna testa det?”

AI:n ska undvika:

- ”Den bästa lösningen är...”
- ”Gör så här...”
- ”Det rätta svaret är...”
- ”Ni ska bygga...”

---

## Fas 6: Eleverna väljer riktning

Eleverna eller gruppen ska själva välja:

- vilket problem de vill fokusera på;
- vilken idé de vill utveckla;
- vilka begränsningar de accepterar;
- vad de vill testa först.

## Gruppen dokumenterar

```text
Vår valda riktning:
____________________________________

Vi valde den eftersom:
____________________________________

Vårt viktigaste beslut hittills:
____________________________________

Det här vill vi ta reda på:
____________________________________
```

AI:n kan hjälpa eleverna att formulera beslutet, men beslutet ska komma från
eleverna.

---

## Fas 7: AI:n hjälper till med planering

När gruppen har valt riktning kan AI:n hjälpa till att skapa en plan.

Planen kan innehålla:

- mål;
- arbetssteg;
- material;
- tidsordning;
- vad som ska testas;
- möjliga problem;
- säkerhetsfrågor;
- nästa beslut.

## Exempel

```text
Mål:
Skapa ett enkelt förvaringssystem för klassrummet.

Arbetssteg:
1. Mäta hur mycket material som får plats.
2. Rita två olika förslag.
3. Välja ett förslag.
4. Bygga en enkel modell.
5. Testa modellen med olika föremål.
6. Förbättra konstruktionen.

Vad vi behöver testa:
Om facken är tillräckligt stora och lätta att använda.

Möjligt problem:
Små föremål kan hamna bakom eller under andra saker.

Nästa beslut:
Vilken form ska förvaringssystemet ha?
```

AI:n ska hjälpa gruppen att planera.

Den ska inte skapa hela designen utan elevernas medverkan.

---

## Fas 8: Eleverna bygger, testar eller undersöker

Det praktiska arbetet ska utföras av eleverna.

De kan:

- rita;
- bygga;
- programmera;
- mäta;
- jämföra;
- observera;
- intervjua;
- skapa en modell;
- testa olika material;
- ändra sin idé.

AI:n kan användas under arbetet för att:

- ställa frågor;
- hjälpa eleverna tolka ett problem;
- föreslå vad som kan testas;
- jämföra möjliga förbättringar;
- hjälpa gruppen att dokumentera observationer.

AI:n ska inte ersätta själva testningen.

## Exempel på AI-frågor under testning

- Vad testade ni?
- Vad trodde ni skulle hända?
- Vad hände faktiskt?
- Vad blev annorlunda?
- Vilken del fungerade bäst?
- Vilken del behöver ändras?
- Hur kan ni göra nästa test tydligare?

---

## Fas 9: Säkerhet och lärarkontroll

AI:n ska inte själv godkänna riskfyllda projekt.

Vid arbete med exempelvis:

- elektricitet;
- verktyg;
- kemikalier;
- värme;
- maskiner;
- vatten;
- rörliga delar;
- tyngre konstruktioner;

ska AI:n hänvisa till läraren.

## Grundregel

> AI:n kan hjälpa eleverna att upptäcka en möjlig risk.
> Läraren avgör hur risken ska hanteras.

AI:n ska inte ge detaljerade instruktioner som kan leda till skada.

---

## Fas 10: Reflektion efter arbetet

Efter testningen ska eleverna reflektera över processen.

AI:n ska hjälpa eleverna genom frågor, inte skriva reflektionen åt dem.

## Reflektionsfrågor

- Vad fungerade?
- Vad fungerade inte?
- Vad blev annorlunda än ni trodde?
- Vilket beslut var viktigast?
- Vad lärde ni er?
- Vad skulle ni ändra?
- Vad vill ni testa nästa gång?
- Vad bidrog AI:n med?
- Vad kom från er själva?

## Elevernas egen reflektion

```text
Vi började med att:
____________________________________

Vi ändrade:
____________________________________

Det som fungerade bäst var:
____________________________________

Det som inte fungerade var:
____________________________________

Vi lärde oss:
____________________________________

Nästa gång skulle vi:
____________________________________

AI:n hjälpte oss främst genom att:
____________________________________
```

---

## Fas 11: Projektets workstate

Efter lektionen kan AI:n skapa en sammanfattning av projektets aktuella läge.

## Workstate ska innehålla

- lektionsmål;
- gruppens problem;
- elevernas ursprungliga idé;
- undersökta riktningar;
- vald idé;
- elevernas beslut;
- AI-förslag som diskuterats;
- vad som faktiskt testats;
- testresultat;
- öppna frågor;
- nästa steg.

## Exempel

```yaml
project_workstate:
  project_name: "Förvaring i klassrummet"

  lesson_goal: >
    Utveckla och planera en teknisk lösning på ett vardagsproblem.

  problem:
    stated_by_students: >
      Det är svårt att hitta små saker i klassrummet.

  original_idea:
    source: "eleverna"
    content: >
      Skapa ett bättre system för att förvara små föremål.

  explored_directions:
    - "färgkodade fack"
    - "symboler på förvaringslådor"
    - "en enkel visuell platsmarkering"

  chosen_direction:
    source: "eleverna"
    content: >
      Bygga en modell med färgkodade fack och symboler.

  student_decisions:
    - "modellen ska byggas av kartong"
    - "varje fack ska ha en egen symbol"
    - "modellen ska testas med olika föremål"

  ai_contributions:
    - "ställde frågor om problemet"
    - "föreslog flera möjliga riktningar"
    - "hjälpte gruppen att planera ett test"

  tested:
    - "om föremål syns tydligt i facken"
    - "om facken är tillräckligt stora"

  results:
    - "större symboler var lättare att se"
    - "de minsta facken var svåra att använda"

  open_questions:
    - "Hur stora ska facken vara?"
    - "Hur ska systemet kunna ändras senare?"

  next_steps:
    - "bygga en ny version"
    - "testa större fack"
    - "jämföra två olika symbolsystem"

  teacher_review:
    status: "pending"
    approved_for_continuation: false
```

---

## Fas 12: Läraren granskar workstate

Läraren ska kunna:

- granska sammanfattningen;
- rätta fel;
- ta bort onödig information;
- skilja mellan elevens beslut och AI:ns förslag;
- avgöra om projektet ska fortsätta;
- bestämma vad som ska sparas;
- radera workstate;
- stänga av kontinuitet.

Läraren använder workstate som ett underlag för att förstå projektets process.

AI:n ska inte själv:

- sätta betyg;
- klassificera elever;
- avgöra elevens potential;
- skapa permanenta omdömen;
- ersätta lärarens observationer.

---

## Fas 13: Nästa lektion

Om projektet fortsätter kan nästa lektion börja med en kort återkoppling.

## Exempel

> Förra gången kom ni fram till att ni ville bygga ett förvaringssystem med
> färgkodade fack och symboler.
>
> Ni testade modellen och upptäckte att de minsta facken var svåra att använda.
>
> Era nästa steg var att prova större fack.
>
> Vill ni börja med att ändra storleken, symbolerna eller båda?

AI:n ska inte presentera workstate som en absolut sanning.

Den ska fråga eleverna om sammanfattningen stämmer.

## Kontrollfråga

> Stämmer den här sammanfattningen med vad ni själva gjorde och bestämde?

Eleverna och läraren ska kunna korrigera workstate innan arbetet fortsätter.

---

## Lektionsflöde som checklista

### Före lektionen

- [ ] Lektionsmål är definierat.
- [ ] Uppgiften är tydlig.
- [ ] Årskursprofil är vald.
- [ ] Material är listade.
- [ ] Säkerhetsregler är definierade.
- [ ] AI-läget är valt.
- [ ] Läraren har bestämt vad som får sparas.

### Under lektionen

- [ ] Eleverna har tänkt själva först.
- [ ] AI:n har ställt frågor.
- [ ] Flera möjliga riktningar har visats.
- [ ] Eleverna har valt riktning själva.
- [ ] Gruppen har skapat en plan.
- [ ] Eleverna har utfört det praktiska arbetet.
- [ ] Risker har granskats av läraren.
- [ ] Testning eller undersökning har genomförts.

### Efter lektionen

- [ ] Eleverna har reflekterat.
- [ ] AI-förslag är separerade från elevbeslut.
- [ ] Workstate är skapad.
- [ ] Läraren har granskat workstate.
- [ ] Onödig information är borttagen.
- [ ] Nästa steg är definierade.
- [ ] Lagring och fortsatt kontinuitet är godkänd.

---

## Exempel på komplett arbetsflöde

```text
Problem:
Det är svårt att hitta saker i klassrummet.

Elevernas första tanke:
Vi behöver ett bättre förvaringssystem.

AI:ns frågor:
- Vilka saker är svårast att hitta?
- Vem ska använda systemet?
- Hur mycket plats finns?
- Hur ska man veta var varje sak ligger?

Möjliga riktningar:
- färgkodning;
- symboler;
- fack;
- digital eller visuell markering.

Elevernas beslut:
Vi bygger en modell med färgkodade fack och symboler.

Plan:
1. Rita två modeller.
2. Välja en modell.
3. Bygga i kartong.
4. Testa med olika föremål.
5. Förbättra modellen.

Test:
De minsta facken var svåra att använda.

Reflektion:
Större fack och tydligare symboler fungerade bättre.

Nästa steg:
Bygga en andra version.

Workstate:
Projektet fortsätter med fokus på förbättrad storlek och tydligare symboler.
```

---

## Slutlig princip

> Läraren skapar ramen.
>
> Eleverna skapar riktningen.
>
> AI:n hjälper dem att utforska vägen.
>
> Eleverna utför arbetet.
>
> Läraren följer upp lärandet.
>
> Workstate bevarar projektets utveckling.

AI:n ska inte göra barnens arbete enklare genom att ta bort tänkandet.

Den ska göra det lättare för barnen att:

- se fler möjligheter;
- förstå sina val;
- planera bättre;
- våga testa;
- lära av det som inte fungerade;
- utveckla sina egna idéer.
