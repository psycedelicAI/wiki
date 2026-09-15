# AI-tankpartner i skolan: datatillfällig och lokal kontinuitet

## Status

- Status: Konceptuell systemarkitektur
- Version: 0.1
- Område: Skolkuraterad AI, dataminimering och projektbaserad kontinuitet
- Relaterat koncept: AI-continuity
- Senast uppdaterad: 2026-09-15

---

## Relaterade dokument

- [AI som tankpartner i skolan](AI-Som-Tankpartner-I-Skolan.md)
- [Prompt och YAML](AI-Tankpartner-Prompt-och-YAML.md)
- [Lektionsflöde](AI-Tankpartner-Lektionsflode.md)
- [Säkerhet och ansvar](AI-Tankpartner-Sakerhet.md)
- [Lärarhandledning](AI-Tankpartner-Lararhandledning.md)
- [SkolAI README](README.md)

---

## Sammanfattning

SkolAI ska kunna fungera som en tillfällig arbetsmiljö för tänkande,
idéutveckling och planering.

Systemet använder chattdata under lektionen för att hjälpa eleverna, men ska
inte bygga en permanent profil över barnen.

När lektionen avslutas ska projektets relevanta kontinuitet kunna lämna systemet
som en lokalt sparad workstate.

Den centrala principen är:

> SkolAI ska komma ihåg projektet när eleverna uttryckligen väljer att spara
> det, men inte komma ihåg barnet som person.

---

## Grundmodell

```text
SkolAI = tillfälligt tänkande
Chatten = tillfällig arbetsyta
Cookie = anonymt chatID
Workstate = lokal projektkontinuitet
Elevprofil = skapas inte
Serverhistorik = raderas enligt policy
```

---

## Integritetsprincip

SkolAI ska inte kräva att eleverna skapar personliga konton.

Systemet ska inte behöva veta:

- elevens namn;
- elevens e-postadress;
- elevens personliga konto;
- elevens historik mellan projekt;
- elevens personlighet;
- elevens beteende;
- elevens privata information.

Systemet ska i stället fokusera på:

- lektionens mål;
- projektets problem;
- gruppens idéer;
- elevgruppens beslut;
- testresultat;
- öppna frågor;
- nästa steg.

---

## Separation mellan chatt, workstate och elevprofil

### Chatt

Chatten är en tillfällig arbetsyta där eleverna kan:

- ställa frågor;
- utveckla idéer;
- planera;
- jämföra alternativ;
- diskutera tekniska lösningar;
- reflektera över arbetet.

### Workstate

Workstate är en uttryckligen skapad projektfil som beskriver:

- projektets mål;
- gruppens problem;
- elevernas idéer;
- valda riktningar;
- egna beslut;
- AI-förslag;
- testresultat;
- öppna frågor;
- nästa steg.

### Elevprofil

SkolAI ska inte skapa en permanent elevprofil.

```text
Chatt ≠ elevprofil
Workstate ≠ elevprofil
ChatID ≠ elevidentitet
```

---

## Anonym session utan inloggning

När en elev eller elevgrupp öppnar SkolAI skapas en anonym session.

Systemet behöver inte kräva:

- användarnamn;
- lösenord;
- e-post;
- elevkonto;
- social inloggning;
- personlig identitet.

I stället skapas ett slumpmässigt chatID.

```text
chatID = 7f3c9a2e-4d18-4b61-a912-8e73c0f5b241
```

ChatID:t ska vara:

- slumpmässigt;
- långt;
- svårt att gissa;
- utan inbyggd betydelse;
- utan namn;
- utan klass;
- utan elevinformation;
- utan sekventiellt nummer.

Då betyder chatID:t endast:

> Den här anonyma chatten.

Det ska inte betyda:

> Den här eleven.

---

## Cookie-struktur

Cookien ska inte innehålla själva chatten.

Den ska endast innehålla chatID eller ett säkert sessions-ID som hjälper
webbläsaren och servern att hitta rätt anonym chatt.

```text
Cookie:
chat_id = 7f3c9a2e-4d18-4b61-a912-8e73c0f5b241
```

Exempel på serverinställningar:

```http
Set-Cookie: chat_id=opaque-random-id;
Secure;
HttpOnly;
SameSite=Strict;
Path=/
```

### Cookie ska inte innehålla

- elevens namn;
- elevens e-post;
- klass;
- personliga inställningar;
- personlighetsdata;
- chattinnehåll;
- känsliga uppgifter.

### Cookie betyder

```text
Aktuell anonym session
```

Inte:

```text
Permanent användaridentitet
```

---

## Chatten under lektionen

Under lektionen kan flödet se ut så här:

```text
1. Eleven öppnar SkolAI.
2. En anonym session skapas.
3. Ett chatID skapas.
4. ChatID sparas i cookie.
5. SkolAI laddar rätt systemprompt.
6. Eleven eller gruppen chattar.
7. SkolAI hjälper till med idéer och planering.
8. Chatten används endast inom lektionens ram.
```

Servern kan då känna till:

- vilket SkolAI-läge som används;
- vilken årskursprofil som är aktiv;
- vilket lektionsläge som gäller;
- vilket anonymt chatID som ska laddas;
- vilken chatt som hör till sessionen.

Servern behöver inte känna till elevens identitet.

---

## Serverns roll

Servern kan lagra SkolAI:s funktion och regler centralt:

- systemprompt;
- YAML-konfiguration;
- åldersprofil;
- säkerhetsregler;
- lektionsläge;
- workstate-format;
- raderingspolicy;
- lärarinställningar;
- tekniska driftinställningar.

Servern ska däremot inte behöva lagra en permanent elevhistorik.

```text
Server:
SkolAI-konfiguration och tillfällig bearbetning

Lokal enhet:
Chatt och workstate enligt vald lagringsmodell

Elevprofil:
Skapas inte
```

---

## Lagringsmodeller

### Modell A: Lokal chatt

Chatten sparas lokalt på enheten.

Exempel:

```text
Cookie:
chatID

Lokal webbläsarlagring:
chattinnehåll
```

Lämplig lokal lagring kan vara:

- IndexedDB;
- lokal krypterad lagring;
- en lokal projektfil;
- skolans godkända lokala lagringsyta.

Fördelar:

- mindre serverlagring;
- bättre dataminimering;
- chatten stannar på enheten;
- ingen automatisk överföring;
- enklare att radera lokalt.

Nackdelar:

- data kan försvinna om webbläsardata raderas;
- en trasig enhet kan innebära förlorad chatt;
- chatten följer inte automatiskt med till en annan dator;
- läraren kan inte automatiskt granska chatten.

### Modell B: Tillfällig serverlagring

Chatten sparas tillfälligt på servern och kopplas till ett anonymt chatID.

```text
chatID → tillfällig chatt
```

Fördelar:

- chatten kan fortsätta efter sidladdning;
- chatten kan fungera på flera lektionstillfällen;
- läraren kan granska workstate;
- teknisk återställning blir enklare.

Nackdelar:

- servern behandlar chattinnehåll;
- teknisk metadata kan finnas;
- lagringstid måste definieras;
- raderingen måste kunna verifieras;
- AI-leverantörens databehandling måste granskas.

### Rekommenderad modell

SkolAI bör i första hand använda:

```text
Tillfällig chatt under lektionen
        ↓
Workstate genereras lokalt
        ↓
Läraren eller gruppen granskar
        ↓
Serverchatten raderas enligt policy
```

---

## Lokal workstate

När lektionen avslutas kan SkolAI generera en lokal workstate.

Exempel på filnamn:

```text
project-workstate.md
```

eller:

```text
project-workstate.json
```

Workstate-filen kan sparas:

- på elevgruppens dator;
- på lärarens dator;
- i skolans lokala projektmapp;
- på en godkänd krypterad lagringsplats;
- på annat sätt som skolan uttryckligen godkänt.

Workstate ska inte automatiskt skickas till en central elevprofil.

---

## Workstate-flöde

```text
Eleverna arbetar i SkolAI
        ↓
SkolAI hjälper gruppen
        ↓
Lektionen avslutas
        ↓
SkolAI genererar workstate
        ↓
Elever eller lärare granskar workstate
        ↓
Workstate sparas lokalt
        ↓
Serverchatten raderas enligt policy
```

---

## Workstate-format

```markdown
# Projekt-workstate

## Projekt

Energisnål belysning i klassrummet

## Lektionsmål

Utveckla och planera en teknisk lösning på ett vardagsproblem.

## Problem

Klassrummets lampor är ofta tända även när dagsljuset räcker.

## Elevernas idéer

- rörelsesensorer;
- ljussensorer;
- manuell timer;
- olika belysningszoner.

## Vald riktning

Undersöka en kombination av rörelsesensorer och ljussensorer.

## Elevernas beslut

- modellen ska byggas med kartong;
- lösningen ska kunna stängas av manuellt;
- systemet ska testas på en enkel modell.

## AI-förslag

- jämföra en sensor med två sensorer;
- testa olika placeringar;
- undersöka vad som händer när någon sitter stilla.

## Testresultat

Inget test genomfört ännu.

## Öppna frågor

- Hur ska systemet reagera när någon sitter helt stilla?
- Hur ska man skilja mellan dagsljus och mörker?
- Hur ska läraren kunna stänga av systemet?

## Nästa steg

1. Rita två alternativa modeller.
2. Välja placering för sensorerna.
3. Bygga en enkel prototyp.
4. Testa modellen.

## Provenance

- Elevernas idéer: gruppens diskussion
- AI-förslag: SkolAI
- Slutliga beslut: elevgruppen
- Lärargranskning: ej genomförd
```

---

## Kontinuitet mellan datorer

Chatten ska inte flyttas automatiskt mellan enheter.

Om projektet ska fortsätta på en annan dator kan gruppen eller läraren uttryckligen
flytta workstate.

### Alternativ 1: Ingen överföring

Chatten och workstate stannar på den ursprungliga enheten.

### Alternativ 2: Manuell workstate-export

Eleven eller läraren väljer:

```text
Exportera projekt-workstate
```

Endast den granskade projektinformationen exporteras.

Hela chatthistoriken behöver inte följa med.

### Alternativ 3: QR-kod eller engångskod

En kortlivad engångskod kan användas för att flytta en workstate.

Säkerhetskrav:

- koden används endast en gång;
- koden gäller under kort tid;
- koden kan återkallas;
- koden är inte samma sak som chatID;
- användaren ser vad som flyttas;
- flytten kräver ett aktivt val.

### Alternativ 4: Lärarstyrd import

```text
Elevgrupp skapar workstate
        ↓
Läraren granskar
        ↓
Onödig information tas bort
        ↓
Workstate exporteras
        ↓
Ny dator importerar workstate
        ↓
Ny anonym chattsession skapas
```

Detta är den rekommenderade modellen för skolmiljö.

---

## ChatID och åtkomst

Ett ensamt chatID bör helst inte vara tillräckligt för att öppna en chatt.

Bättre modell:

```text
chatID
+
säker sessionsnyckel
```

eller:

```text
chatID
+
kortlivad engångstoken
```

ChatID identifierar chatten.

Token eller sessionsnyckel visar att användaren får öppna den.

Det minskar risken att någon som råkar få tag på ett chatID kan läsa innehållet.

---

## Slut-på-dagen-process

```text
1. Eleverna arbetar i SkolAI.
2. Läraren avslutar lektionen.
3. SkolAI genererar en workstate.
4. Elever eller lärare granskar workstate.
5. Workstate sparas lokalt.
6. Workstate exporteras endast om projektet ska fortsätta på annan enhet.
7. Serverchatten raderas.
8. ChatID och sessionsdata blir ogiltiga.
9. Temporära serverdata raderas enligt retention-policy.
10. Tekniska loggar hanteras enligt separat och dokumenterad policy.
```

---

## Retention-policy

```yaml
retention:
  chat_content:
    purpose: "Tillfällig AI-bearbetning under lektionen"
    storage: "temporär serverlagring eller lokal lagring"
    lifetime: "lektionens eller dagens arbetsperiod"
    delete_after: "workstate har skapats och granskats"

  chat_id:
    purpose: "Återuppta aktuell anonym session"
    lifetime: "aktuell session"
    delete_after: "sessionen avslutas eller raderas"

  workstate:
    purpose: "Projektets uttryckligen sparade kontinuitet"
    server_storage: false
    local_storage: true
    export: "manuell och synlig"

  technical_logs:
    purpose: "Drift och säkerhet"
    content: "minsta möjliga tekniska metadata"
    lifetime: "kort och dokumenterad"
    personal_profiling: false

  model_training:
    use_chat_content: false

  student_profile:
    created: false
```

---

## Vad som ska raderas

När dagens arbetsperiod är slut ska systemet kunna radera:

- chattinnehåll;
- chatID;
- temporära promptar och svar;
- temporär workstate på servern;
- sessionsdata;
- mellanlagrade filer;
- onödiga tekniska identifierare.

## Teknisk precision

Begreppet “tom på data” måste definieras.

Applikationen kan radera sina egna:

- chattar;
- sessioner;
- chatID:n;
- temporära arbetsobjekt.

Men separat teknisk loggning kan fortfarande finnas hos:

- webbserver;
- driftleverantör;
- nätverk;
- AI-leverantör;
- säkerhetssystem.

Därför måste även dessa datakällor omfattas av en dokumenterad policy.

---

## Adminvy

Adminvyn bör visa rollen eller projektgruppen, inte elevens IP-adress som
huvudidentifierare.

Exempel:

```text
ELEV / GRUPP       CHAT-ID        SKAPAD              STATUS
Elev               7f3c...b241    2026-09-15 14:20   Aktiv
Grupp A            a91d...77e0    2026-09-15 14:24   Workstate
Grupp B            c81a...102f    2026-09-15 14:31   Avslutad
```

Möjliga rolletiketter:

```text
Elev
Grupp A
Grupp B
Lärarläge
```

Etiketten beskriver sessionens roll.

De ska inte innebära att systemet känner till elevens personliga identitet.

```text
Roll: Elev
Identitet: Okänd
Projekt: Grupp A
Chatt: chatID
```

IP-adresser bör inte användas som pedagogisk identitet eller visas som elevens
namn i adminvyn.

Om tekniska IP-loggar behövs för drift eller säkerhet ska de ha:

- tydligt syfte;
- begränsad åtkomst;
- kort lagringstid;
- dokumenterad radering;
- ingen användning för elevprofilering.

---

## Transparens för föräldrar och lärare

SkolAI bör kunna förklara:

```text
Detta används under lektionen:
- anonymt chatID;
- aktuell chatt;
- lektionens systemprompt;
- projektets arbetskontext.

Detta sparas lokalt om workstate skapas:
- projektets mål;
- elevernas idéer;
- gruppens beslut;
- testresultat;
- öppna frågor;
- nästa steg.

Detta skapas inte:
- elevkonto;
- personlighetsprofil;
- kunskapsprofil;
- beteendeprofil;
- permanent elevhistorik.

Detta används inte för:
- reklam;
- kommersiell profilering;
- automatisk betygsättning;
- modellträning utan uttryckligt godkännande.
```

Föräldrar och lärare bör kunna granska:

- vilka prompter som används;
- vilken data som sparas;
- hur länge den sparas;
- vilka loggar som skapas;
- vem som kan se informationen;
- hur data kan rättas;
- hur data kan raderas;
- hur workstate flyttas.

---

## Säkerhetsprinciper

```yaml
privacy:
  student_login_required: false
  permanent_student_profile: false
  chat_id_contains_personal_data: false
  automatic_cross_device_transfer: false
  explicit_workstate_export_required: true
  teacher_review_available: true
  parent_transparency_available: true

security:
  chat_id_unguessable: true
  chat_id_alone_grants_access: false
  https_required: true
  cookie_secure: true
  cookie_httponly: true
  cookie_samesite: "Strict"
  workstate_export_visible: true
  temporary_data_deletion: required

continuity:
  memory_target: "project"
  memory_target_is_student: false
  default_scope: "lesson_or_project"
  local_workstate: true
  server_permanent_history: false
```

---

## Arkitekturens kärna

```text
Ingen elevinloggning
        ↓
Ingen permanent elevprofil
        ↓
Anonym chattsession
        ↓
Cookie innehåller chatID
        ↓
Chatten används under lektionen
        ↓
Workstate genereras lokalt
        ↓
Läraren eller gruppen granskar
        ↓
Serverchatten raderas enligt policy
        ↓
Projektet kan fortsätta genom manuell workstate
```

---

## Slutlig princip

> SkolAI ska vara datatillfälligt.

Systemet använder data under lektionen för att hjälpa eleverna, men ska inte
äga deras historik efteråt.

Kontinuiteten ska lämna systemet som en lokalt sparad projekt-workstate om
elever eller lärare uttryckligen väljer att spara den.

```text
SkolAI = tillfälligt tänkande
Workstate = lokal kontinuitet
Cookie = anonymt chatID
Elevprofil = ingen
```

Det innebär:

> SkolAI kommer ihåg projektets state när människor väljer att spara det,
> men behöver inte komma ihåg barnet.
