# AI-tankpartner i skolan: lärarhandledning

## Status

- Status: Konceptuell handledning
- Version: 0.1
- Område: Skolkuraterad AI, teknikundervisning och kreativ problemlösning
- Relaterat koncept: AI-continuity
- Senast uppdaterad: 2026-09-15

---

## Relaterade dokument

- [AI som tankpartner i skolan](AI-Som-Tankpartner-I-Skolan.md)
- [Prompt, YAML och arbetsflöde](AI-Tankpartner-Prompt-och-YAML.md)
- [AI-tankpartner: lektionsflöde](AI-Tankpartner-Lektionsflode.md)
- [AI-tankpartner: säkerhet och ansvar](AI-Tankpartner-Sakerhet.md)
- [AI-tankpartner: lärarhandledning](AI-Tankpartner-Lararhandledning.md)

---

## Syfte

Denna handledning hjälper lärare att använda en skolkuraterad AI som
tankpartner under lektioner.

AI:n ska ge eleverna stöd att:

- utveckla idéer;
- formulera problem;
- förstå tekniska möjligheter;
- planera projekt;
- jämföra lösningar;
- testa antaganden;
- reflektera över sitt arbete.

AI:n ska inte användas för att göra elevernas skoluppgifter eller skapa färdiga
svar som eleverna lämnar in som sitt eget arbete.

---

## Lärarens huvudroll

Läraren är den pedagogiska ledaren.

AI:n kan bidra med frågor, struktur och perspektiv, men läraren bestämmer:

- vad eleverna ska lära sig;
- hur uppgiften ska genomföras;
- vilka AI-funktioner som får användas;
- vilka material som är tillåtna;
- vilka säkerhetsregler som gäller;
- vad som får sparas;
- hur elevernas arbete ska bedömas.

> AI:n stödjer lektionen.
> Läraren leder lektionen.

---

## Grundprinciper för läraren

### 1. Eleverna ska tänka själva först

Ge eleverna tid att:

- fundera;
- skriva;
- skissa;
- diskutera;
- formulera en första idé.

AI:n ska inte få ersätta den första kreativa impulsen.

### 2. AI:n ska vara en tankpartner

Eleverna ska kunna använda AI:n för att:

- ställa frågor;
- undersöka möjligheter;
- jämföra alternativ;
- planera;
- hitta begränsningar;
- föreslå tester.

### 3. Eleverna ska fatta besluten

AI:n får föreslå, men eleverna ska välja:

- problem;
- riktning;
- material;
- arbetssätt;
- test;
- förbättringar.

### 4. Praktiskt arbete ska utföras av eleverna

Eleverna ska själva:

- rita;
- bygga;
- programmera;
- mäta;
- testa;
- observera;
- dokumentera;
- presentera.

### 5. AI:n ska inte vara ett facit

AI:n ska hjälpa eleverna att se fler möjligheter, inte tala om vilken lösning
som är rätt.

---

## När passar AI-tankpartnern?

AI-tankpartnern passar särskilt bra när eleverna ska:

- utveckla en teknisk idé;
- planera en konstruktion;
- skapa en prototyp;
- lösa ett vardagsproblem;
- undersöka hållbarhet;
- jämföra material;
- skapa en teknisk modell;
- planera ett test;
- analysera varför något inte fungerade;
- utveckla en idé tillsammans i grupp.

---

## När bör AI:n inte användas?

AI-tankpartnern bör begränsas eller stängas av när:

- eleverna ska visa vad de kan helt utan stöd;
- uppgiften är en individuell kunskapskontroll;
- AI-användningen skulle dölja elevens egen förståelse;
- uppgiften kräver personlig reflektion;
- eleverna arbetar med känsliga personuppgifter;
- det saknas möjlighet för läraren att kontrollera användningen;
- ett praktiskt moment innebär risk som AI:n inte kan bedöma.

---

## Förberedelse före lektionen

Läraren bör besvara följande frågor:

```text
Vad ska eleverna lära sig?
____________________________________

Vilket problem ska de undersöka?
____________________________________

Vad ska eleverna skapa, planera eller testa?
____________________________________

Vilka material finns?
____________________________________

Vilka begränsningar gäller?
____________________________________

Vilka säkerhetsrisker finns?
____________________________________

När får AI:n användas?
____________________________________

Vad får AI:n hjälpa till med?
____________________________________

Vad får AI:n inte göra?
____________________________________

Vad ska sparas efter lektionen?
____________________________________
```

---

## Lektionsprofil

Läraren kan skapa en enkel lektionsprofil:

```yaml
lesson_profile:
  grade: "årskurs 5"
  subject: "teknik"
  duration_minutes: 60

  learning_goal: >
    Eleverna ska kunna utveckla och planera en teknisk lösning på ett
    vardagsproblem.

  challenge: >
    Hur kan vi göra det enklare att hitta och organisera saker i klassrummet?

  available_materials:
    - "papper"
    - "kartong"
    - "tejp"
    - "pennor"
    - "sax"

  ai_allowed_for:
    - "idéutveckling"
    - "frågor"
    - "jämförelse"
    - "planering"
    - "reflektion"

  ai_not_allowed_for:
    - "färdigt svar"
    - "färdig inlämning"
    - "personlig reflektion"
    - "betyg"

  safety_rules:
    - "Använd sax på ett säkert sätt."
    - "Fråga läraren innan andra verktyg används."

  continuity:
    enabled: true
    scope: "gruppens projekt"
    teacher_review_required: true
```

---

## Rekommenderad lektionsstruktur

### Del 1: Introduktion

Läraren förklarar:

- uppgiften;
- målet;
- tidsramen;
- materialet;
- säkerhetsreglerna;
- AI:ns roll.

### Del 2: Egen första idé

Eleverna tänker och skissar utan AI.

### Del 3: AI-dialog

Eleverna använder AI:n för att:

- förtydliga problemet;
- utveckla idéer;
- jämföra riktningar;
- upptäcka begränsningar.

### Del 4: Eget gruppbeslut

Gruppen väljer idé och motiverar beslutet.

### Del 5: Planering

AI:n hjälper gruppen att skapa en plan.

### Del 6: Praktiskt arbete

Eleverna bygger, testar eller undersöker.

### Del 7: Reflektion

Eleverna analyserar vad som fungerade och vad som behöver ändras.

### Del 8: Workstate

AI:n sammanfattar projektets aktuella läge.

### Del 9: Lärarens granskning

Läraren granskar och godkänner, ändrar eller raderar workstate.

---

## Lärarens instruktion till eleverna

Läraren kan använda denna introduktion:

> Ni får använda AI som en tankpartner.
>
> AI:n får hjälpa er att ställa frågor, utveckla idéer, jämföra lösningar och
> planera.
>
> Men AI:n ska inte göra arbetet åt er.
>
> Ni ska själva tänka, välja, bygga, testa och förklara.
>
> Om AI:n föreslår något är det fortfarande ni som måste avgöra om idén är
> användbar och hur den ska testas.

---

## Exempel på bra elevdialog

**Elev:**

> Vi vill göra klassrummet bättre.

**AI:**

> Vad fungerar dåligt i klassrummet just nu?
>
> Är problemet ljud, ljus, temperatur, ordning eller något annat?
>
> Vad har ni själva redan funderat på?

**Elev:**

> Det är svårt att hitta våra saker.

**AI:**

> Ni skulle kunna undersöka:
>
> 1. färgkodade förvaringsfack;
> 2. symboler som visar var saker ska ligga;
> 3. ett system som gör det lättare att se vad som saknas.
>
> Vilken idé verkar mest intressant för er, och varför?

**Lärarens roll:**

Läraren lyssnar efter om eleverna:

- förstår problemet;
- fattar egna beslut;
- kan motivera sin riktning;
- planerar något som går att testa.

---

## Frågor läraren kan ställa under lektionen

### Om elevernas idé

- Vad försöker ni lösa?
- Vem är lösningen till för?
- Varför valde ni just det problemet?
- Vad var er första tanke?
- Har idén förändrats?

### Om planeringen

- Vad behöver ni göra först?
- Vilket material behöver ni?
- Vad måste ni ta reda på?
- Vad kan ni testa redan idag?
- Vad kan gå fel?

### Om elevernas beslut

- Vilka alternativ jämförde ni?
- Varför valde ni denna riktning?
- Var det ert beslut eller ett förslag från AI:n?
- Vad skulle få er att ändra riktning?

### Om testningen

- Vad trodde ni skulle hända?
- Vad hände faktiskt?
- Vad fungerade bäst?
- Vad behöver förbättras?
- Hur vet ni att lösningen fungerar?

### Om AI-användningen

- Vad hjälpte AI:n er med?
- Vad kom från er själva?
- Vilka AI-förslag valde ni bort?
- Var AI:n osäker någon gång?
- Kan ni förklara projektet utan att fråga AI:n?

---

## Lärarens observationspunkter

Läraren kan observera:

- om eleverna vågar formulera egna idéer;
- om eleverna ställer egna frågor;
- om eleverna jämför alternativ;
- om eleverna kan motivera beslut;
- om eleverna tar ansvar för praktiskt arbete;
- om eleverna testar sina antaganden;
- om eleverna kan ändra en idé efter ett misslyckande;
- om eleverna förstår skillnaden mellan AI-förslag och egna beslut;
- om AI-användningen stärker eller försvagar elevens självständighet.

---

## Bedömning

AI:n ska inte automatiskt sätta betyg.

Läraren kan i stället bedöma exempelvis:

- förståelse av problemet;
- tekniskt resonemang;
- förmåga att planera;
- förmåga att samarbeta;
- förmåga att testa;
- förmåga att dra slutsatser;
- förmåga att motivera beslut;
- förmåga att reflektera;
- förmåga att använda AI ansvarsfullt.

## Möjliga bedömningsfrågor

```text
Kan eleven förklara problemet?

Kan eleven beskriva sin egen idé?

Kan eleven motivera sina beslut?

Kan eleven planera ett test?

Kan eleven tolka vad som hände?

Kan eleven föreslå en förbättring?

Kan eleven skilja mellan eget arbete och AI-stöd?
```

---

## Lärarens granskning av workstate

Efter lektionen ska läraren kontrollera:

- om gruppens idé är korrekt återgiven;
- om besluten kommer från eleverna;
- om AI-förslag är tydligt märkta;
- om testresultaten stämmer;
- om öppna frågor är relevanta;
- om nästa steg är säkra;
- om onödiga personuppgifter har tagits bort;
- om workstate behöver sparas.

## Workstate-status

```yaml
teacher_review:
  status: "pending"

  possible_values:
    - "pending"
    - "approved"
    - "corrected"
    - "rejected"
    - "deleted"

  teacher_comment: ""
  approved_for_continuation: false
```

---

## Fortsättning vid nästa lektion

Om projektet fortsätter ska AI:n börja med att kontrollera workstate:

> Förra gången skrev ni att ni ville bygga färgkodade förvaringsfack. Ni upptäckte
> att de minsta facken var svåra att använda.
>
> Stämmer den sammanfattningen?

Eleverna ska kunna:

- korrigera sammanfattningen;
- ändra riktning;
- radera delar;
- förklara vad de minns själva;
- bestämma nästa steg.

AI:n ska aldrig behandla en gammal sammanfattning som mer sann än elevernas
egen återkoppling.

---

## Om AI:n ger ett dåligt förslag

Läraren kan använda situationen pedagogiskt.

Fråga eleverna:

- Varför tror ni att AI:n föreslog detta?
- Är förslaget rimligt?
- Vad saknas i AI:ns förslag?
- Hur skulle ni kunna kontrollera det?
- Finns det någon risk?
- Kan ni skapa en bättre idé själva?

Ett dåligt AI-förslag kan bli en övning i:

- källkritik;
- teknisk granskning;
- problemlösning;
- självständigt tänkande.

---

## Om eleverna försöker få ett färdigt svar

Läraren kan säga:

> Be AI:n om en fråga, en ledtråd eller två möjliga riktningar i stället.

Eller:

> Förklara först vad ni själva har tänkt. Då kan AI:n hjälpa er att utveckla
> idén i stället för att göra den åt er.

AI:n bör svara med:

- en fråga;
- en ledtråd;
- ett exempel på principnivå;
- en uppmaning att testa;
- en jämförelse mellan alternativ.

---

## Säkerhet

Läraren måste alltid ha sista ordet när arbetet omfattar:

- elektricitet;
- verktyg;
- kemikalier;
- värme;
- vatten;
- maskiner;
- rörliga delar;
- tunga eller instabila konstruktioner.

Se även:

- [AI-tankpartner: säkerhet och ansvar](AI-Tankpartner-Sakerhet.md)

---

## Integritet

Läraren bör undvika att elever skriver in:

- fullständiga namn;
- privata familjeuppgifter;
- hälsouppgifter;
- känsliga personliga uppgifter;
- information om andra elever;
- sådant som inte behövs för projektet.

Kontinuiteten bör normalt vara kopplad till:

- gruppen;
- projektet;
- uppgiften;
- arbetsprocessen.

Inte till en permanent profil över barnet.

---

## Lärarens checklista

### Före lektionen

- [ ] Lektionsmål är tydligt.
- [ ] Uppgiften är åldersanpassad.
- [ ] AI:ns roll är förklarad.
- [ ] Material och säkerhetsregler är klara.
- [ ] AI-funktionerna är begränsade.
- [ ] Regler för lagring är bestämda.

### Under lektionen

- [ ] Eleverna har tänkt själva först.
- [ ] AI:n används som tankpartner.
- [ ] Eleverna ställer egna frågor.
- [ ] Eleverna fattar egna beslut.
- [ ] Eleverna utför det praktiska arbetet.
- [ ] Risker kontrolleras.
- [ ] Läraren följer gruppernas arbete.

### Efter lektionen

- [ ] Eleverna har reflekterat.
- [ ] AI-förslag och elevbeslut är separerade.
- [ ] Workstate är granskad.
- [ ] Onödiga personuppgifter är borttagna.
- [ ] Nästa steg är tydliga.
- [ ] Fortsatt lagring är motiverad.

---

## Kort modell för läraren

```text
Förklara ramen.
Låt eleverna tänka själva.
Låt AI:n ställa frågor.
Låt eleverna välja.
Låt eleverna bygga och testa.
Använd AI:n för reflektion.
Granska workstate.
Bestäm nästa steg.
```

---

## Slutlig princip

> Läraren skapar den pedagogiska miljön.
>
> Eleverna äger sina idéer och beslut.
>
> AI:n hjälper dem att tänka vidare.
>
> Praktiskt arbete och lärande sker hos eleverna.
>
> Workstate bevarar projektets utveckling.
>
> Läraren avgör vad som är pedagogiskt, säkert och ansvarsfullt.
