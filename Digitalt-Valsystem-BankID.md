# Digitalt valsystem med BankID, anonym QR-token och vallokalsplattor

> Ett koncept för hur kommun-, region- och riksdagsval skulle kunna genomföras
> digitalt i vallokal utan att koppla väljarens identitet till den avgivna rösten.

---

## Status

**Koncept / Förstudie / Ej validerat**

Detta dokument beskriver en möjlig systemidé. Det är inte ett färdigt
valsäkerhetssystem, juridiskt förslag eller rekommendation att ersätta dagens
svenska valsystem.

---

# 1. Grundidé

Väljaren använder BankID en gång för att verifiera sin identitet och rösträtt.

Efter kontrollen separeras identiteten från själva röstningen. Väljaren får
därefter en slumpmässig, kortlivad och engångsbaserad QR-token som används på
en säkrad surfplatta i vallokalen.

```text
BankID
   ↓
Kontroll av identitet och rösträtt
   ↓
Anonymisering
   ↓
Slumpmässig engångs-QR
   ↓
Röstning på vallokalsplatta
   ↓
Krypterad digital valurna
```

Den centrala principen är:

> **BankID får bekräfta att personen har rösträtt, men får aldrig kunna kopplas
> till vad personen röstar på.**

---

# 2. Vilka val omfattas?

Ett gemensamt röstningsflöde kan omfatta:

1. Kommunfullmäktige
2. Regionfullmäktige
3. Riksdagen

Väljaren kan rösta i alla val som personen är röstberättigad till.

Systemet ska också kunna hantera att väljaren:

- avstår från ett val;
- röstar blankt;
- ändrar sitt val innan slutlig bekräftelse;
- lämnar ett val ofullständigt;
- behöver hjälpmedel eller språkstöd.

---

# 3. Vad BankID används till

BankID används endast för identitets- och behörighetskontroll.

Det kan kontrollera:

- vem väljaren är;
- att personen är röstberättigad;
- vilket valdistrikt personen tillhör;
- vilka val personen får delta i;
- att personen inte redan har registrerats som färdigröstande.

BankID ska inte:

- signera partivalet;
- lagra röstens innehåll;
- skapa ett kvitto som avslöjar hur personen röstade;
- vara den enda möjliga vägen att rösta;
- ha tillgång till den färdiga rösten.

---

# 4. Röstningsprocess

## Steg 1: Ankomst till vallokalen

En valarbetare startar en ny röstningssession på en särskild vallokalsplatta.

Plattan ska vara:

- låst till valsystemet;
- kontrollerad före valet;
- fri från privata appar;
- utan aktiv kamera och mikrofon;
- utan möjlighet att ta skärmdumpar;
- konfigurerad för automatisk rensning efter avslutad session.

---

## Steg 2: BankID-kontroll

Väljaren skannar en tillfällig QR-kod eller använder en annan godkänd
anslutningsmetod för att starta BankID.

BankID och röstlängdssystemet returnerar endast behörighetsinformation:

```text
Röstberättigad: Ja
Kommunval: Ja
Regionval: Ja
Riksdagsval: Ja
Redan röstad i detta flöde: Nej
```

Själva identiteten får inte följa med till röstningsdelen.

---

## Steg 3: Identiteten separeras

När rösträtten är kontrollerad skickas en begränsad och signerad
behörighetstoken till ett separat anonymiseringslager.

```text
Identitetslager
    vet vem väljaren är
        ↓
Anonymisering
    utfärdar en oanvänd rösttoken
        ↓
Röstningslager
    vet att token är giltig
    vet inte vem väljaren är
```

Identitetslagret och röstningslagret måste vara tekniskt, organisatoriskt och
juridiskt separerade.

Ingen enskild aktör bör kunna återskapa kopplingen mellan:

```text
Väljare → röst
```

---

## Steg 4: Slumpmässig QR-token

Väljaren får en QR-kod som innehåller en kryptografiskt slumpmässig
engångstoken.

Token ska vara:

- unik;
- kortlivad;
- omöjlig att förutsäga;
- omöjlig att återanvända;
- fri från personnummer;
- fri från partival;
- fri från direkt identifierande information.

QR-koden ska inte fungera som ett röstkvitto.

```text
QR-token = rätt att starta en anonym röstningssession
```

Inte:

```text
QR-token = bevis på hur personen har röstat
```

---

## Steg 5: Röstning på plattan

Väljaren skannar QR-koden på vallokalsplattan.

Plattan visar endast de val som väljaren har behörighet att delta i.

Exempel:

```text
Välj val:

[ Kommunfullmäktige ]
[ Regionfullmäktige ]
[ Riksdagen ]
```

Varje val ska hanteras som en separat röstkomponent:

```text
Kommunröst  → separat krypterad röst
Regionröst  → separat krypterad röst
Riksdagsröst → separat krypterad röst
```

Väljaren ska kunna granska sina val före slutlig inlämning.

---

## Steg 6: Kryptering och inlämning

När väljaren bekräftar skickas rösten krypterad till den digitala valurnan.

Efter inlämningen ska systemet:

- markera den anonyma token som använd;
- radera sessionens lokala data;
- inte spara väljaren tillsammans med röstinnehållet;
- generera ett icke-avslöjande mottagningsbevis;
- kunna visa att rösten accepterats utan att visa vad den innehöll.

---

# 5. Valhemlighet

Valhemligheten är systemets viktigaste krav.

Systemet måste förhindra att någon kan se eller bevisa hur en specifik person
har röstat.

Det innebär att följande inte får förekomma:

```text
Personnummer + partival
BankID-identitet + röst
QR-token + röst i samma databas
Röstkvitto som visar valt parti
```

Möjliga tekniska mekanismer kan vara:

- blind signering;
- anonymiseringstjänst;
- mix-nätverk;
- homomorf kryptering;
- flerpartsnycklar;
- offentlig verifiering utan avslöjande av enskilda röster;
- separata och oberoende revisionssystem.

Tekniken måste granskas av oberoende experter innan den kan användas i ett
verkligt val.

---

# 6. Vad väljaren får veta

Efter inlämning kan väljaren få beskedet:

> Din röst har tagits emot av systemet.

Väljaren bör inte få ett kvitto som avslöjar röstens innehåll.

Ett möjligt mottagningsbevis kan vara:

```text
Röst mottagen: Ja
Session avslutad: Ja
Röstens innehåll: Ej tillgängligt
```

Systemet måste hitta balansen mellan:

- väljarkontroll;
- valhemlighet;
- skydd mot röstköp;
- möjlighet till teknisk revision.

---

# 7. Reservrutiner

Digital röstning får aldrig vara beroende av att allt fungerar perfekt.

Systemet behöver reservrutiner för:

- nätverksavbrott;
- BankID-avbrott;
- trasig surfplatta;
- överbelastning;
- strömavbrott;
- felaktiga tokens;
- misstänkt manipulation;
- förlorad eller avbruten session;
- väljare som saknar BankID;
- väljare som inte kan använda digital teknik.

En möjlig princip är:

```text
Digitalt system fungerar
    → digital röstning

Digitalt system fungerar inte
    → fysisk och manuellt kontrollerad reservprocess
```

Ingen väljare får förlora sin rösträtt på grund av ett tekniskt fel.

---

# 8. Tillgänglighet

Systemet måste kunna användas av personer med olika behov.

Det kan inkludera:

- större text;
- hög kontrast;
- skärmläsarstöd;
- hörsel- och synstöd;
- flera språk;
- förenklade instruktioner;
- fysisk hjälp utan att hjälparen kan se röstinnehållet;
- alternativ till BankID;
- möjlighet att rösta utan egen smartphone.

Digitalisering får inte skapa ett nytt krav på teknisk kompetens för att kunna
delta i valet.

---

# 9. Säkerhetsprinciper

Systemet bör bygga på följande principer:

## Minsta möjliga information

Varje komponent ska endast känna till den information den behöver.

## Separata ansvarsområden

Identitet, rösträtt, röstning, lagring och rösträkning ska inte ligga hos samma
system eller aktör.

## Ingen dold tillit

Systemet ska inte kräva att väljaren litar blint på en leverantör.

## Öppen granskning

Teknisk dokumentation, testresultat och säkerhetsmodeller ska kunna granskas av
oberoende experter.

## Versionskontroll

Alla ändringar i system, programvara, regler och valdata ska dokumenteras.

## Mänsklig kontroll

Valfunktionärer och oberoende kontrollorgan måste kunna stoppa, granska och
återställa processen.

## Säkerhet före snabbhet

Ett långsammare men verifierbart system är bättre än ett snabbt system som inte
går att kontrollera.

---

# 10. Möjliga fördelar

Ett digitalt system skulle kunna ge:

- ett sammanhållet flöde för tre val;
- färre fel vid ifyllnad eller registrering;
- bättre tillgänglighet;
- snabbare preliminär sammanräkning;
- bättre stöd för flera språk;
- tydligare användargränssnitt;
- enklare kontroll av om en person redan röstat;
- bättre dokumentation av systemets status och händelser.

---

# 11. Risker

De största riskerna är:

- att väljaren kan kopplas till sin röst;
- att en angripare manipulerar plattorna;
- att skadlig kod ändrar väljarnas val;
- att BankID används som ett dolt röstkvitto;
- att en leverantör får för stor kontroll;
- att systemet inte fungerar vid driftstörning;
- att väljaren inte kan kontrollera att rösten blev rätt;
- att digitalt utanförskap ökar;
- att en attack påverkar många röster samtidigt;
- att systemet blir för svårt för allmänheten och granskare att förstå;
- att en central administratör kan ändra eller radera valdata;
- att förtroendet för resultatet blir sämre även om systemet tekniskt fungerar.

---

# 12. Vad QR-lösningen faktiskt löser

En randomiserad QR-kod kan lösa:

- start av en engångssession;
- tillfällig behörighetsöverföring;
- skydd mot återanvändning;
- separation mellan identifiering och röstning;
- enkel anslutning mellan mobil och vallokalsplatta.

QR-koden löser inte ensam:

- valhemlighet;
- korrekt rösträkning;
- säker programvara;
- skydd mot tvång;
- oberoende revision;
- tillgänglighet;
- reservrutiner;
- juridiska krav.

---

# 13. Föreslagen prototyp

Den första prototypen bör inte användas för riktiga nationella val.

## Testnivå 1: Simulerat val

Använd:

- fiktiva partier;
- testidentiteter;
- test-QR-koder;
- två eller flera surfplattor;
- simulerad röstlängd;
- anonymiseringslager;
- krypterad valurna.

Testa särskilt:

- dubbelröstning;
- återanvändning av QR-kod;
- avbruten session;
- nätverksavbrott;
- manipulation av platta;
- felaktiga behörigheter;
- försök att koppla identitet till röst;
- felaktig rösträkning.

## Testnivå 2: Förenings- eller elevrådsval

Systemet kan därefter testas i ett frivilligt, icke-statligt val där resultatet även
kan verifieras med en annan metod.

## Testnivå 3: Oberoende granskning

Innan någon politisk pilot krävs:

- offentlig hotmodell;
- oberoende säkerhetsgranskning;
- tillgänglighetstest;
- juridisk granskning;
- kryptografisk revision;
- plan för fysisk reservröstning;
- dokumenterad omräkning;
- öppet redovisade begränsningar.

---

# 14. Centrala forskningsfrågor

1. Kan BankID användas för rösträttskontroll utan att skapa spår till röstens
   innehåll?

2. Kan identitetslagret och röstningslagret separeras så att ingen enskild aktör
   kan återskapa kopplingen?

3. Kan väljaren kontrollera att rösten mottagits utan att kunna bevisa hur den
   avgavs?

4. Kan systemet verifieras av allmänheten utan att kräva orimlig teknisk
   kompetens?

5. Kan systemet återhämta sig efter intrång eller driftstopp?

6. Hur hanteras väljare utan BankID?

7. Kan alla tre valen genomföras i ett flöde utan att röster blandas ihop?

8. Hur bevaras möjlighet till omräkning?

9. Hur bevisas att programvaran på plattan gjorde exakt det som systemet
   specificerade?

10. Är digital röstning faktiskt säkrare och mer tillförlitlig än fysisk
    röstning?

---

# 15. Preliminär systemmodell

```text
Väljare
   ↓
BankID-identifikation
   ↓
Rösträttskontroll
   ↓
Separering av identitet och röstbehörighet
   ↓
Slumpmässig engångstoken
   ↓
Vallokalsplatta
   ↓
Val av kommun, region och riksdag
   ↓
Krypterad röst
   ↓
Anonym digital valurna
   ↓
Oberoende verifiering och sammanräkning
```

---

# 16. Förhållande till PsycedelicAI

Konceptet kan utvecklas med samma tänkande som används i andra
PsycedelicAI-projekt:

- **AI Continuity Architecture Method** kan dokumentera systemets
  arbetskontext, beslut, versioner och osäkerheter.
- **High-Security Facility Concept** kan bidra med identitet, zoner,
  behörigheter, övervakning och återställning.
- **Symbiosis** kan hjälpa till att definiera relationen mellan mänsklig
  auktoritet och tekniskt system.
- **PsycedelicAI Wiki** kan fungera som dokumentations- och orienteringslager.

Detta innebär inte att projekten automatiskt är samma system.

De bidrar med olika arkitektoniska perspektiv till ett nytt koncept.

---

# 17. Sammanfattning

Den föreslagna lösningen är:

```text
BankID
    = verifierar identitet och rösträtt

Anonymisering
    = bryter kopplingen mellan väljare och röst

Randomiserad QR-token
    = startar en tidsbegränsad engångssession

Vallokalsplatta
    = presenterar valen och tar emot rösten

Krypterad digital valurna
    = lagrar rösten utan väljaridentitet

Oberoende kontroll
    = granskar att systemet räknar korrekt
```

Den största designregeln är:

> **Ett digitalt valsystem måste kunna bevisa att rätt röst räknats utan att kunna
> bevisa hur en viss person röstat.**

Det är den princip som hela den fortsatta utvecklingen måste kretsa kring.
