---
title: "PRD: CV- og søknadsassistent for studenter"
status: draft
created: 2026-11-02
updated: 2026-11-06
---

# PRD: CV- og søknadsassistent for studenter

## 0. Om dokumentet

PRD-en er skrevet for gruppen (G67), for faglærer og sensor i IBE160, og for de neste stegene i BMAD-flyten: UX, arkitektur, og epics og stories. Den bygger på [brief.md](../../briefs/brief-Seksti-sju-2026-09-18/brief.md) og faglærerens [tilbakemelding](../../briefs/brief-Seksti-sju-2026-09-18/tilbakemelding-product-brief.md), og gjentar ikke problembeskrivelsen og konkurrentanalysen derfra. Der briefen motsier seg selv, følger PRD-en de reviderte seksjonene (Suksesskriterier, Scoringsregel, Testsett, Omfang og Demomodus), se [revisjonshistorikken](../../briefs/brief-Seksti-sju-2026-09-18/revisjonshistorikk-brief.md).

Begrepene i §3 brukes nøyaktig slik de er definert, også i dokumentene som bygger på PRD-en. Funksjonene er gruppert etter trinn, med globalt nummererte krav (FR-1 og videre) som senere dokumenter kan vise til. Det som er antatt uten bekreftelse, er merket [ASSUMPTION] og samlet i §12. Beslutningene bak PRD-en ligger i `.memlog.md` i samme mappe. En skisse av resultatsiden, som faglæreren etterlyste, hører hjemme i UX-steget.

## 1. Visjon

Norske studenter søker jobb med én generisk CV, får standardavslag og vet ikke hvorfor. Samtidig sorteres søknader i økende grad automatisk, etter regler studentene aldri får se. Dette verktøyet lar en student legge inn CV-en sin og én stillingsannonse og se, nøkkelord for nøkkelord, hvorfor CV-en treffer eller ikke: hva stillingsannonsen ber om, hva CV-en viser, og hva som mangler.

Kjernen er forklaringen, ikke tallet. Scoren regnes ut etter en enkel, åpen regel som studenten kan lese, og hvert treff vises med sitatet fra CV-en som utløste det. Verktøyet påstår ikke å gjenskape et bestemt kommersielt ATS. Det viser hvordan nøkkelordbasert sortering fungerer i prinsippet, slik at studenten lærer noe hver gang.

Deretter kan studenten få hjelp til å gjøre CV-en og søknadsbrevet bedre, enten som forslag studenten skriver inn selv eller som omskrevet tekst. Verktøyet skriver aldri inn erfaring som ikke står i CV-en. Til slutt kan studenten opprette en konto, følge søknadene sine over tid og se hvilke gap som går igjen.

## 2. Målgruppe

Norske studenter som aktivt søker jobb eller internship, på tvers av fagfelt. Typisk har de lite arbeidserfaring, søker på mange stillinger i samme periode og gjenbruker én CV fordi det tar for lang tid å tilpasse den.

### 2.1 Jobs to be done

- **Funksjonell:** Når jeg har funnet en stillingsannonse, vil jeg raskt se hvilke krav CV-en min ikke dekker, så jeg vet hva jeg må fremheve eller skaffe meg.
- **Forståelse:** Jeg vil skjønne hvorfor CV-en scorer som den gjør, så jeg blir bedre til å skrive søknader selv.
- **Kontroll:** Jeg vil forbedre CV-en og søknadsbrevet uten at noe blir diktet opp, så jeg kan stå inne for alt jeg sender.
- **Over tid:** Jeg vil se hvilke gap som går igjen på tvers av søknadene mine, så jeg vet hva jeg bør lære eller skaffe meg erfaring med.
- **Trygghet:** Jeg vil vite hva som skjer med CV-en min når jeg legger den inn.

### 2.2 Ikke-brukere (v1)

- Arbeidsgivere, rekrutterere og bemanningsbyråer.
- Karrieresentre eller andre som vil administrere studenter.
- Den som vil sende søknader automatisk uten å lese dem.

### 2.3 Sentrale brukerreiser

[ASSUMPTION: Reisene er skrevet ut fra briefen, ikke fortalt av gruppen. Gå gjennom personene og stegene og rett det som ikke stemmer.]

**UJ-1. Ingrid finner ut hvorfor CV-en ikke treffer.**
Ingrid går siste år på bachelor i økonomi og administrasjon og søker traineeplass. CV-en ligger som PDF, og erfaringen er en deltidsjobb i butikk og et verv i linjeforeningen. Ingrid åpner appen uten å logge inn, limer inn stillingsannonsen og laster opp CV-en. Appen viser teksten den leste ut av PDF-en, og Ingrid trykker «Analyser». Resultatet viser scoren 63 og tolv nøkkelord: sju Treff med sitat fra CV-en, ett Delvis treff («Excel» i CV-en mot «Microsoft Excel» i stillingsannonsen) og fire Ikke funnet, blant dem «budsjettering». Ingrid ser at budsjettarbeidet i linjeforeningen ikke står i CV-en, legger det til og analyserer på nytt mot de samme nøkkelordene. Scoren går til 71, og Ingrid vet hvorfor.
**Kanttilfelle:** Er PDF-en et skannet bilde uten tekst, sier appen at den ikke fant tekst og ber om CV-en som innlimt tekst.

**UJ-2. Jonas analyserer en engelsk stillingsannonse.**
Jonas går tredje år på bachelor i informatikk og har funnet en sommerjobb i et IT-selskap der stillingsannonsen er på engelsk. Jonas limer inn stillingsannonsen og den norske CV-en. Appen sier at CV-en er på norsk og stillingsannonsen på engelsk, og at den bare sammenligner tekster på samme språk. Jonas limer inn den engelske versjonen av CV-en, og analysen går som i UJ-1, med nøkkelord og forklaringer på engelsk og resten av grensesnittet på norsk.

**UJ-3. Ingrid forbedrer CV-en og skriver søknadsbrev.**
Etter analysen i UJ-1 velger Ingrid skrivemodusen Foreslå og får forbedringsforslag, hvert knyttet til et nøkkelord og et sted i CV-en. For «Power BI», som er Ikke funnet, får Ingrid spørsmålet «Har du erfaring med Power BI? Legg det i så fall til selv.» Så prøver Ingrid Skriv om og får omskrevet tekst for to punkter i CV-en, med originalsitatet ved siden av, og et søknadsbrevutkast der hvert avsnitt viser hvilke sitater det bygger på. Ingrid kopierer teksten over i sin egen CV og sitt eget søknadsbrev og redigerer videre der.
**Kanttilfelle:** Nevner søknadsbrevutkastet et nøkkelord som er Ikke funnet, markeres setningen, og Ingrid må ta stilling til den.

**UJ-4. Ingrid følger søknadene over tid.**
Ingrid oppretter en konto, leser hva som lagres, og samtykker. Over noen uker analyserer Ingrid den lagrede CV-en mot fem stillingsannonser uten å laste den opp på nytt. Historikken viser at «SQL» er Ikke funnet i tre av fem analyser, og Ingrid melder seg på et SQL-kurs. Etter at Ingrid har fått jobb, slettes kontoen, og alt som var lagret, er borte.

**UJ-5. Sensoren kjører appen uten gruppens nøkler.**
Kari er sensor i IBE160 og har klonet repoet. Kari følger README, kopierer `.env.example` til `.env`, slår på demomodus og starter appen uten API-nøkkel. Et banner viser at appen kjører i demomodus. Kari velger et av de fem testparene, ser analysen og forklaringene, prøver begge skrivemodusene og logger inn på demokontoen for å se historikken.

## 3. Ordliste

Begrepene brukes nøyaktig slik, uten synonymer, i resten av PRD-en og i dokumentene som bygger på den.

- **Student** — den som bruker verktøyet. Anonym i trinn 1 og 2; kan ha en konto i trinn 3.
- **CV** — studentens CV som tekst, innlimt eller lest ut av en PDF. Én analyse bruker nøyaktig én CV.
- **Stillingsannonse** — teksten i annonsen studenten vil søke på, innlimt. Én analyse bruker nøyaktig én stillingsannonse.
- **Språk** — norsk eller engelsk. CV og stillingsannonse i samme analyse må ha samme språk.
- **Økt** — fra studenten åpner appen til siden lukkes.
- **Språkmodell** — den eksterne KI-modellen verktøyet bruker til nøkkelordutvinning (trinn 1) og til tekst i trinn 2.
- **Promptmal** — den faste instruksen til språkmodellen for nøkkelordutvinning, lagret i kildekoden med versjonsnummer.
- **Nøkkelord** — et krav i stillingsannonsen (ferdighet, verktøy eller kvalifikasjon), hentet ut av språkmodellen. En analyse har 10–15 nøkkelord.
- **Klassifisering** — status for et nøkkelord sett mot CV-en: Treff, Delvis treff eller Ikke funnet. Gjøres i kode, ikke av språkmodellen.
- **Treff** — nøkkelordet står i CV-en.
- **Delvis treff** — et synonym eller en forkortelse for nøkkelordet fra synonymlisten står i CV-en.
- **Ikke funnet** — verken nøkkelordet eller noe synonym står i CV-en.
- **Synonymliste** — en kort, dokumentert liste over likeverdige uttrykk på samme språk (for eksempel «JS» og «JavaScript»), lagret i repoet.
- **Score** — et heltall fra 0 til 100: (antall Treff + 0,5 × antall Delvis treff) ÷ antall nøkkelord × 100, der halvveis rundes opp.
- **Gap** — et nøkkelord med status Ikke funnet. **Gapanalyse** er listen over gapene i en analyse.
- **Sitat** — et ordrett utdrag fra CV-en som underbygger et Treff, et Delvis treff eller tekst fra trinn 2.
- **Forklaring** — for hvert nøkkelord: klassifiseringen, sitatet (ved Treff og Delvis treff) og synonymet som ga treff (ved Delvis treff).
- **Scoringsregel** — nøkkelordutvinning, klassifisering og score samlet, slik FR-4 til FR-6 beskriver dem.
- **Analyse** — én sammenligning av én CV med én stillingsannonse. Gir nøkkelord, klassifisering, score, forklaringer og gapanalyse.
- **Skrivemodus** — studentens valg i trinn 2: **Foreslå** (verktøyet foreslår, studenten skriver) eller **Skriv om** (verktøyet skriver tekst studenten kan bruke).
- **Forbedringsforslag** — i Foreslå: et konkret råd om hva som bør endres i CV-en, hvor (sitat) og hvorfor (nøkkelord).
- **Omskrevet tekst** — i Skriv om: en ny formulering av et sitat fra CV-en, uten ny erfaring.
- **Brevdisposisjon** — i Foreslå: punkter for søknadsbrevet, med sitater, som studenten skriver ut selv.
- **Søknadsbrevutkast** — i Skriv om: et fullt utkast til søknadsbrev.
- **Konto** — en registrert student med e-post og passord (trinn 3). **Demokonto** er en ferdig utfylt konto som bare finnes i demomodus.
- **Historikk** — analysene som er lagret på en konto, med tekst fra trinn 2 som hører til.
- **Tilbakevendende gap** — et nøkkelord som er Ikke funnet i minst to analyser i historikken.
- **Demomodus** — kjøremodus der verktøyet bruker ferdiginnspilte svar i stedet for språkmodellen og ikke trenger API-nøkkel. Motsatt: **normal modus**.
- **Ferdiginnspilt svar** — et lagret svar fra språkmodellen for et testpar, brukt i demomodus og i automatiske tester.
- **Testpar** — én fiktiv CV, én fiktiv stillingsannonse og en fasit.
- **Testsett** — de fem testparene.
- **Fasit** — for hvert testpar: fem forventede gap og nøkkelordene som skal gi Treff eller Delvis treff.
- **Sensor** — den som vurderer prosjektet og kjører appen etter README.

## 4. Funksjoner

### 4.1 Trinn 1 — Analyse av CV mot stillingsannonse

**Beskrivelse:** Studenten legger inn en stillingsannonse og en CV, uten konto. Verktøyet henter ut nøkkelord fra stillingsannonsen med språkmodellen, klassifiserer hvert nøkkelord mot CV-en i kode, regner ut scoren og viser forklaringer og gapanalyse. Resultatsiden viser scoren øverst med fordelingen (antall Treff, Delvis treff og Ikke funnet), så nøkkelordene gruppert etter klassifisering med forklaring, så gapanalysen og en lenke til «Slik regnes scoren». Ingenting lagres. Realiserer UJ-1 og UJ-2.

#### FR-1: Legge inn stillingsannonse

Studenten kan lime inn teksten i en stillingsannonse. Realiserer UJ-1.

- Analysen kan ikke startes med tomt felt; appen sier hva som mangler.
- [ASSUMPTION: Tekst over 15 000 tegn avvises med beskjed om å korte ned.]

#### FR-2: Legge inn CV

Studenten kan lime inn CV-en som tekst eller laste opp en PDF. Realiserer UJ-1.

- Fra en PDF vises den utleste teksten før analysen, slik at studenten kan se og rette det verktøyet leste. [ASSUMPTION]
- En PDF uten lesbar tekst, for eksempel et skannet bilde, gir beskjed om å lime inn teksten i stedet.
- Bare PDF kan lastes opp. [ASSUMPTION: Filer over 5 MB avvises.]

#### FR-3: Språkkontroll

Verktøyet avgjør om CV-en og stillingsannonsen er på norsk eller engelsk før analysen. Realiserer UJ-2.

- Er de på ulike språk, kjøres ingen analyse, og appen forklarer at bare tekster på samme språk sammenlignes.
- Er en av tekstene verken på norsk eller engelsk, kjøres ingen analyse, og appen sier hvilke språk som støttes.
- Språket avgjøres ut fra hovedspråket i teksten; engelske fagord i en norsk CV gjør den ikke engelsk.

#### FR-4: Nøkkelordutvinning

Verktøyet henter ut 10–15 nøkkelord fra stillingsannonsen med ett kall til språkmodellen, med promptmalen. Realiserer UJ-1.

- Nøkkelordene er på samme språk som stillingsannonsen.
- Hvert nøkkelord er kort (1–3 ord) og i grunnform, slik det typisk står i en CV: «Excel» eller «prosjektledelse», ikke «god erfaring med prosjektledelse». Promptmalen ber om denne formen, og svar som bryter den, behandles som svar uten forventet form (NFR-2). Formålet er at klassifiseringen i kode (FR-5) ikke skal gi falske gap (SM-C1).
- [ASSUMPTION: Myke ferdigheter, for eksempel «samarbeid» eller «kommunikasjon», tas bare med når de kan uttrykkes som et kort ord som kan stå i en CV. Vage formuleringer som «positiv innstilling» tas ikke med.]
- Inneholder stillingsannonsen færre enn 10 konkrete krav, vises de som ble funnet, med beskjed om det. [ASSUMPTION]
- Bare stillingsannonsen sendes til språkmodellen; CV-en sendes aldri til språkmodellen i trinn 1. [ASSUMPTION: Følger av at klassifiseringen skjer i kode. Bekreft at dette skal være et krav.]
- Ferdiginnspilte svar er knyttet til versjonen av promptmalen de ble laget med.

#### FR-5: Klassifisering

Verktøyet klassifiserer hvert nøkkelord som Treff, Delvis treff eller Ikke funnet mot CV-en, i kode og etter definisjonene i §3. Realiserer UJ-1.

- Samme nøkkelordliste og samme CV gir alltid samme klassifisering.
- [ASSUMPTION: Treff tåler forskjeller i store og små bokstaver og vanlige bøyningsendelser, for eksempel «prosjekt», «prosjektet» og «prosjekter».]
- Delvis treff krever at synonymet står i synonymlisten; synonymlisten gjelder innenfor ett språk.

#### FR-6: Score

Verktøyet regner ut scoren etter formelen i §3 og viser fordelingen bak den. Realiserer UJ-1.

- 12 nøkkelord med 7 Treff og 1 Delvis treff gir 63 (62,5 rundet opp).
- Uten nøkkelord vises ingen score, men en feilmelding.
- Scoren regnes aldri ut av språkmodellen.

#### FR-7: Forklaring per nøkkelord

Studenten ser forklaringen for hvert nøkkelord. Realiserer UJ-1.

- Treff og Delvis treff viser sitatet fra CV-en; Delvis treff viser også synonymet som ga treff.
- [ASSUMPTION: Sitatet er hele setningen, eller hele linjen i punktlister og tabeller, der nøkkelordet eller synonymet står første gang i CV-en. Treffordet uthevs i sitatet.]
- Ikke funnet sier at verken nøkkelordet eller noe synonym står i CV-en.
- Klassifiseringen vises med tekst eller ikon i tillegg til farge.

#### FR-8: Gapanalyse

Studenten ser gapanalysen samlet under nøkkelordene. Realiserer UJ-1.

- Gapene vises i samme rekkefølge som i nøkkelordlisten.
- Uten gap sier appen at alle nøkkelordene er funnet.

#### FR-9: «Slik regnes scoren»

Studenten kan åpne en forklaring av scoringsregelen fra resultatsiden. Realiserer UJ-1.

- Forklaringen viser de tre klassifiseringene, formelen og et regneeksempel.
- Den sier tydelig at scoren er verktøyets egen regel, og at ekte ATS-er er ulike og ikke offentlige.

#### FR-10: Endre og analysere på nytt

Studenten kan endre CV-teksten og kjøre analysen på nytt mot samme stillingsannonse. Realiserer UJ-1.

- Så lenge stillingsannonsen er uendret i samme økt, gjenbrukes nøkkelordene, slik at endringen i scoren bare skyldes endringen i CV-en.
- Når økten er over, er CV-en, stillingsannonsen og resultatet borte; ingenting lagres på serveren.

### 4.2 Trinn 2 — Forbedringsforslag og søknadsbrev

**Beskrivelse:** Etter en analyse kan studenten be om hjelp med CV-en og søknadsbrevet. Studenten velger skrivemodus før hver generering: Foreslå gir forbedringsforslag og en brevdisposisjon, mens Skriv om gir omskrevet tekst og et søknadsbrevutkast. I begge skrivemodusene bygger alt på CV-en og stillingsannonsen, hvert utsagn om erfaring viser sitatet det bygger på, og verktøyet skriver aldri inn erfaring som ikke står i CV-en. For nøkkelord som er Ikke funnet, stiller verktøyet studenten et spørsmål i stedet for å skrive noe. Teksten er på samme språk som CV-en og stillingsannonsen. Realiserer UJ-3.

#### FR-11: Velge skrivemodus

Studenten velger Foreslå eller Skriv om før hver generering. Realiserer UJ-3.

- [ASSUMPTION: Foreslå er forhåndsvalgt og vises tydelig; studenten kan bytte før hver generering.]
- Før første generering i en økt får studenten vite at CV-en og stillingsannonsen sendes til språkmodellen, og hvilken leverandør det er.

#### FR-12: Forbedringsforslag (Foreslå)

Studenten får forbedringsforslag til CV-en. Realiserer UJ-3.

- Hvert forbedringsforslag viser til minst ett nøkkelord i analysen og har et sitat som viser hvor i CV-en det gjelder.
- For et nøkkelord som er Ikke funnet, er forbedringsforslaget et spørsmål til studenten («Har du erfaring med …? Legg det i så fall til selv»), uten ferdig tekst.
- [ASSUMPTION: Høyst 8 forbedringsforslag per analyse.]

#### FR-13: Omskrevet tekst (Skriv om)

Studenten får omskrevet tekst for deler av CV-en. Realiserer UJ-3.

- Hver omskrevet tekst vises ved siden av sitatet den erstatter.
- Omskrevet tekst kan inneholde nøkkelord som er Treff eller Delvis treff, aldri et nøkkelord som er Ikke funnet. Verktøyet kontrollerer dette i kode og forkaster tekst som bryter regelen.
- Et Delvis treff kan skrives om til nøkkelordets eksakte form, for eksempel «JS» til «JavaScript».
- Nøkkelord som er Ikke funnet, får et spørsmål som i FR-12.

#### FR-14: Brevdisposisjon og søknadsbrevutkast

I Foreslå får studenten en brevdisposisjon; i Skriv om får studenten et søknadsbrevutkast. Realiserer UJ-3.

- [ASSUMPTION: Brevdisposisjonen har punkter for innledning, motivasjon, relevant erfaring og avslutning, og hvert erfaringspunkt har sitater fra CV-en.]
- I søknadsbrevutkastet viser hvert avsnitt hvilke sitater det bygger på.
- En setning i søknadsbrevutkastet som nevner et nøkkelord som er Ikke funnet, markeres, slik at studenten må ta stilling til den.
- [ASSUMPTION: Nøytral, profesjonell tone; studenten kan ikke velge tone i v1.]

#### FR-15: Sitatkontroll

Før noe vises, kontrollerer verktøyet i kode at hvert sitat i forbedringsforslag, omskrevet tekst, brevdisposisjon og søknadsbrevutkast står ordrett i CV-en. Realiserer UJ-3.

- Tekst med et sitat som ikke står i CV-en, forkastes, og verktøyet prøver én gang til. Feiler det igjen, får studenten beskjed.
- [ASSUMPTION: Forskjeller i mellomrom og linjeskift regnes ikke som avvik.]

#### FR-16: Kopiere tekst

Studenten kan kopiere gapanalysen, hvert forbedringsforslag, hver omskrevet tekst, brevdisposisjonen og søknadsbrevutkastet med én knapp. Realiserer UJ-3.

- Ingenting kan lastes ned som fil.
- [ASSUMPTION: Kopiert tekst inneholder ikke sitathenvisninger eller markeringer.]

### 4.3 Trinn 3 — Konto og historikk

**Beskrivelse:** Studenten kan opprette en konto for å lagre analyser og bruke dem videre. Ved registrering får studenten vite hva som lagres, hvor lenge og hvorfor, og må samtykke. Data lagres kryptert til studenten sletter dem. Med konto kan studenten gjenbruke en lagret CV, bla i historikken, se tilbakevendende gap og slette enkeltanalyser eller hele kontoen. Trinn 1 og 2 fungerer fortsatt uten konto. [ASSUMPTION: «Tidligere søknader som kontekst» fra briefen betyr gjenbruk av lagret CV og tilbakevendende gap. Tidligere søknadsbrev sendes ikke til språkmodellen.] Realiserer UJ-4.

#### FR-17: Opprette konto

Studenten kan opprette en konto med e-post og passord. Realiserer UJ-4.

- Kontoen opprettes bare hvis studenten samtykker etter å ha lest hva som lagres, at det lagres til studenten sletter det, og at tekst sendes til språkmodellen i trinn 2.
- [ASSUMPTION: Ingen innlogging med Feide eller Google, ingen e-postbekreftelse og ingen tilbakestilling av passord på e-post i v1, fordi det krever tjenester sensor ikke har.]

#### FR-18: Logge inn og ut

Studenten kan logge inn og ut. Realiserer UJ-4.

- Feil e-post eller feil passord gir samme feilmelding, uten å avsløre om kontoen finnes.

#### FR-19: Lagre analyser

En innlogget student kan lagre en analyse i historikken, sammen med teksten fra trinn 2 som hører til. Realiserer UJ-4.

- [ASSUMPTION: Analysen lagres når studenten trykker «Lagre», ikke automatisk.]
- CV-er, stillingsannonser og resultater lagres kryptert.

#### FR-20: Historikk og gjenbruk av CV

En innlogget student kan se historikken og starte en ny analyse med en lagret CV. Realiserer UJ-4.

- [ASSUMPTION: Historikken viser dato, score og et navn studenten gir analysen ved lagring.]
- En lagret CV kan velges i stedet for å legge inn CV-en på nytt.

#### FR-21: Tilbakevendende gap

En innlogget student kan se tilbakevendende gap. Realiserer UJ-4.

- Et nøkkelord vises som tilbakevendende gap når det er Ikke funnet i minst to lagrede analyser, med antall («Ikke funnet i 3 av 5 analyser»).
- [ASSUMPTION: Nøkkelord sammenlignes på tvers av analyser etter samme regel som Treff i FR-5, så «SQL» og «sql» telles som samme gap.]

#### FR-22: Se lagrede data

En innlogget student kan se alt som er lagret på kontoen. Realiserer UJ-4.

- Oversikten viser hver lagret CV og hver lagret analyse.

#### FR-23: Slette data

En innlogget student kan slette en enkelt analyse, en lagret CV eller hele kontoen. Realiserer UJ-4.

- Etter at kontoen er slettet, finnes ingen rader knyttet til den i databasen.
- Sletting må bekreftes og kan ikke angres.

#### FR-24: Tilgangskontroll

En student får bare tilgang til sin egen konto og historikk. Realiserer UJ-4.

- En forespørsel etter en annen kontos analyse eller CV avvises, også når ID-en er kjent.

### 4.4 Demomodus og kjørbarhet

**Beskrivelse:** Sensor skal kunne kjøre appen lokalt uten gruppens API-nøkler, betalte kontoer eller tjenester. I demomodus bruker verktøyet ferdiginnspilte svar for testsettet i stedet for språkmodellen. Demomodus kommer med allerede i trinn 1, slik at appen kan vurderes selv om senere trinn ikke blir ferdige. Realiserer UJ-5.

#### FR-25: Starte i demomodus

Appen kan startes i demomodus med én miljøvariabel, uten API-nøkkel. Realiserer UJ-5.

- I demomodus gjør appen ingen kall til språkmodellen.
- Et synlig banner viser at appen kjører i demomodus.

#### FR-26: Testpar i demomodus

I demomodus kan sensor eller studenten velge et av de fem testparene og bruke trinn 1 og trinn 2 med begge skrivemodusene. Realiserer UJ-5.

- Hvert testpar gir samme resultat hver gang.
- CV-en i et testpar kan endres og analyseres på nytt (FR-10), fordi nøkkelordene hører til stillingsannonsen. Trinn 2 er bare tilgjengelig for den uendrede CV-en.
- [ASSUMPTION: Egne tekster kan ikke analyseres i demomodus; appen forklarer at bare testparene er tilgjengelige.]

#### FR-27: Demokonto

I demomodus finnes en demokonto med historikk fra testsettet. Realiserer UJ-5.

- Innloggingsdetaljene står i README.
- Demokontoen finnes ikke i normal modus.

#### FR-28: Oppsett etter README

Repoet har en `.env.example` med alle miljøvariabler og plassholdere, og README beskriver to måter å starte på: demomodus uten nøkler, og normal modus med egen API-nøkkel. Realiserer UJ-5.

- En person utenfor gruppen kan starte appen i demomodus ved å følge README, uten hjelp.
- `.env` står i `.gitignore`, og ingen nøkler ligger i repoet.

## 5. Tverrgående ikke-funksjonelle krav

- **NFR-1 Forutsigbarhet:** Klassifisering og score er ren kode og gir samme resultat for samme nøkkelordliste og CV. Bare nøkkelordutvinningen og trinn 2 bruker språkmodellen.
- **NFR-2 Usikre svar fra språkmodellen:** Et svar uten forventet form, for eksempel ikke en liste med nøkkelord, prøves én gang til. Feiler det igjen, får studenten en feilmelding. En analyse vises aldri med halvferdig score.
- **NFR-3 Tidsavbrudd:** [ASSUMPTION: Svarer ikke språkmodellen innen 30 sekunder,] får studenten en feilmelding og kan prøve igjen.
- **NFR-4 Responstid:** [ASSUMPTION: Trinn 1 viser resultatet innen 15 sekunder i normal modus og innen 2 sekunder i demomodus.] Trinn 2 viser fremdrift mens teksten lages.
- **NFR-5 Hemmeligheter:** API-nøkkel og krypteringsnøkkel ligger bare i `.env`, utenfor Git.
- **NFR-6 Sikkerhet i trinn 3:** Passord lagres som sikre hasher, aldri i klartekst. CV-er, stillingsannonser og resultater er kryptert i databasen.
- **NFR-7 Ingen persondata i logger:** CV-er og stillingsannonser skrives aldri til logger, i noe trinn.
- **NFR-8 Språk i grensesnittet:** Grensesnittet er på norsk bokmål. Nøkkelord, forklaringer og tekst fra trinn 2 er på språket til CV-en og stillingsannonsen.
- **NFR-9 Plattform:** [ASSUMPTION: Webapp som kjøres lokalt; den trenger ikke å publiseres på nett for kurset. Den fungerer i oppdaterte versjoner av Chrome, Firefox og Edge på PC og kan brukes på mobilskjerm.]
- **NFR-10 Grunnleggende universell utforming:** Alt kan brukes med tastatur, kontrasten er god nok, og status vises aldri bare med farge. [ASSUMPTION: Ingen full WCAG-revisjon i v1.]

## 6. Begrensninger og rekkverk

### 6.1 Ingen dikting

Verktøyet skal aldri tilskrive studenten erfaring eller kvalifikasjoner som ikke står i CV-en. Dette er en hard grense, og den håndheves i kode, ikke bare i promptene: sitatkontrollen (FR-15), forbudet mot nøkkelord som er Ikke funnet i omskrevet tekst (FR-13), og markeringen av slike nøkkelord i søknadsbrevutkast (FR-14). Scoren presenteres som verktøyets egen regel, aldri som «slik et ATS vurderer deg» (FR-9).

### 6.2 Personvern

- **Trinn 1:** Ingenting lagres. Bare stillingsannonsen sendes til språkmodellen; CV-en blir i appen (FR-4).
- **Trinn 2:** CV-en og stillingsannonsen sendes til språkmodellen. Studenten får vite det, og hvilken leverandør det er, før første generering (FR-11).
- **Trinn 3:** Behandlingsgrunnlaget er samtykke (FR-17). Data lagres kryptert til studenten sletter dem (FR-23), og studenten ser hva som er lagret (FR-22). [NOTE FOR PM: «Til studenten sletter» betyr at data på kontoer som ikke lenger brukes, blir liggende. Det er et bevisst valg for kurset, men bør vurderes på nytt før eventuell bruk utenfor kurset.]
- **Demomodus:** Ingen data forlater maskinen.
- **Testdata:** Bare fiktive CV-er og stillingsannonser, aldri ekte personopplysninger. Dette gjelder også brukertesten (SM-4).

### 6.3 Kostnad

Normal modus koster ett kall til språkmodellen per analyse i trinn 1 og noen få kall per generering i trinn 2. Demomodus koster ingenting. [ASSUMPTION: Gruppen setter et forbrukstak hos leverandøren.] Leverandør og modell velges i arkitekturen.

## 7. Testsett og kvalitetssikring

Testsettet lages før trinn 1 testes og ligger i repoet. [ASSUMPTION: Under `.docs/testdata/`, slik briefen foreslår; arkitekturen kan flytte det.] Det består av fem testpar fra ulike fagfelt, og minst to av dem er på engelsk. [ASSUMPTION: For eksempel økonomi, informatikk, sykepleie, ingeniørfag og lærerutdanning.] Hver fasit har fem forventede gap og nøkkelordene som skal gi Treff eller Delvis treff.

Et gap i fasiten regnes som funnet når et nøkkelord i analysen har status Ikke funnet og tilsvarer gapet etter samme regel som Treff og Delvis treff i FR-5, med synonymlisten. Fasitens «Excel» tilsvarer dermed nøkkelordet «Microsoft Excel» bare hvis paret står i synonymlisten. Samme regel brukes når nøkkelord i fasiten som skal gi Treff eller Delvis treff, sammenlignes med analysen (SM-C1).

Testsettet brukes til:

- automatiske tester av klassifisering, score og gapanalyse mot fasit, med ferdiginnspilte svar;
- automatiske tester av sitatkontrollen og regelen om nøkkelord som er Ikke funnet, i trinn 2;
- demomodus;
- manuell kontroll av svarene fra språkmodellen når promptmalen endres. Da spilles svarene inn på nytt og knyttes til den nye versjonen (FR-4).

[ASSUMPTION: I tillegg lages egne kanttilfeller: CV og stillingsannonse på ulike språk, en tekst på et tredje språk, og en PDF uten tekst.]

## 8. Ikke-mål

- Verktøyet er ikke et ATS og etterligner ikke noe bestemt ATS.
- Verktøyet skriver ikke inn erfaring studenten ikke har, i noen skrivemodus.
- Ingen innsending eller automatisk søking, og ingen funksjoner for arbeidsgivere eller rekrutterere.
- Ingen oversettelse av CV-er og ingen sammenligning av tekster på ulike språk.
- Ingen native mobilapp.

## 9. Omfang og trinnplan

### 9.1 I omfang

V1 bygges i tre trinn, i denne rekkefølgen. Neste trinn starter først når suksesskriteriene for forrige trinn er nådd.

| Trinn | Innhold | Krav | Ferdig når |
|---|---|---|---|
| 1 — kjerne | Analyse av CV mot stillingsannonse, demomodus og README | FR-1–FR-10, FR-25, FR-26 (trinn 1-delen), FR-28 | SM-1, SM-3 og SM-5 er nådd |
| 2 | Skrivemodus, forbedringsforslag, omskrevet tekst og søknadsbrev | FR-11–FR-16, ferdiginnspilte svar for trinn 2 | SM-2 er nådd |
| 3 | Konto, historikk, tilbakevendende gap og sletting | FR-17–FR-24, FR-27 | SM-6 og SM-7 er nådd |

Brukertesten i SM-4 og SM-8 kjøres når trinn 2 er ferdig.

### 9.2 Utenfor omfang i v1

- URL-skraping av stillingsannonser: innliming er nok, og skraping er ustabilt.
- Opplasting av DOC- og DOCX-filer: PDF og innlimt tekst dekker behovet.
- Nedlasting og eksport til fil: studenten kopierer teksten inn i egen CV og eget søknadsbrev.
- Valg av tone i søknadsbrevet. [ASSUMPTION]
- Innlogging med Feide eller Google, e-postbekreftelse og tilbakestilling av passord på e-post. [ASSUMPTION]
- Tidligere søknadsbrev som kontekst for nye. [ASSUMPTION]
- Automatisk sletting etter inaktivitet: valgt bort til fordel for sletting når studenten selv vil.

## 10. Suksesskriterier

**Primære**

- **SM-1 Gapfangst:** For hvert av de fem testparene finner gapanalysen minst 4 av 5 gap i fasiten, sammenlignet etter regelen i §7. Måles automatisk med ferdiginnspilte svar, og manuelt mot språkmodellen når promptmalen endres. Validerer FR-4, FR-5 og FR-8.
- **SM-2 Ingen dikting:** For alle fem testparene, i begge skrivemodusene, står 100 % av sitatene ordrett i CV-en, og ingen omskrevet tekst inneholder et nøkkelord som er Ikke funnet. Måles automatisk. Validerer FR-12–FR-15.
- **SM-3 Kjørbar for sensor:** En person utenfor gruppen starter appen i demomodus etter README, på en maskin uten gruppens nøkler, og ser resultatet for alle fem testparene. Validerer FR-25, FR-26 og FR-28.

**Sekundære**

- **SM-4 Én økt:** I en brukertest med minst tre studenter går hver testperson fra CV og stillingsannonse til gapanalyse, forbedringsforslag og søknadsbrevutkast i én økt, uten hjelp. [ASSUMPTION: tre testpersoner.] [ASSUMPTION: Brukertesten kjøres i normal modus, slik at testpersonene selv limer inn og laster opp tekst (FR-1 og FR-2), men med CV-er og stillingsannonser fra testsettet eller andre fiktive tekster, ikke testpersonenes egne. Da sendes ingen ekte personopplysninger til språkmodellen (§6.2). Vil gruppen la testpersonene bruke sine egne CV-er, må de på forhånd få vite at teksten sendes til språkmodellen, og samtykke skriftlig.] Validerer FR-1–FR-16.
- **SM-5 Scoren følger regelen:** Enhetstester viser at scoren for testsettet og for kanttilfeller (ingen Delvis treff, bare Delvis treff, halvveis avrunding) er lik formelen i §3. Validerer FR-6.
- **SM-6 Sletting:** Etter «Slett konto» finnes ingen rader knyttet til kontoen i databasen. Validerer FR-23.
- **SM-7 Tilgangskontroll:** Automatiske tester viser at en student ikke får hentet en annen kontos analyse eller CV. Validerer FR-24.
- **SM-8 Forståelse:** I brukertesten i SM-4 kan minst to av tre testpersoner forklare med egne ord hvorfor et valgt nøkkelord ble Ikke funnet eller Delvis treff. [ASSUMPTION] Validerer FR-7 og FR-9.

**Motmål (skal ikke optimaliseres)**

- **SM-C1 Falske gap:** Antall nøkkelord som markeres Ikke funnet selv om fasiten sier Treff eller Delvis treff. SM-1 kan nås ved å markere for mye som gap. [ASSUMPTION: Høyst ett falskt gap per testpar.] Motvekt til SM-1.
- **SM-C2 Høy score:** Gjennomsnittsscoren på testsettet skal ikke presses opp. En bredere synonymliste eller en mildere Treff-regel som løfter scoren uten at fasiten endres, gjør verktøyet mindre ærlig og skjuler gap. Motvekt til SM-C1.

## 11. Åpne spørsmål

1. **Språkmodell:** Hvilken leverandør og modell? Avgjøres i arkitekturen, og påvirker kostnaden (§6.3) og hva studenten informeres om (FR-11).
2. **Testsett:** Hvem lager de fem testparene og fasiten, og når? Må være klart før trinn 1 testes.
3. **Frist:** Frister og milepæler for trinnene i semesteret er ikke oppgitt (åpent punkt fra briefen).
4. **Tone:** Skal studenten kunne velge tone i søknadsbrevet i en senere versjon?
5. **Tidligere søknader:** Skal tidligere søknadsbrev brukes som kontekst for nye i en senere versjon?
6. **Synonymliste:** Hvor stor skal den være, og hvem vedlikeholder den?

## 12. Antakelsesindeks

- §2.3 — Brukerreisene er skrevet ut fra briefen, ikke fortalt av gruppen.
- FR-1 — Stillingsannonser over 15 000 tegn avvises.
- FR-2 — Utlest PDF-tekst vises før analysen; PDF-er over 5 MB avvises.
- FR-4 — Færre enn 10 nøkkelord vises med beskjed i stedet for å stoppe analysen.
- FR-4 — CV-en sendes aldri til språkmodellen i trinn 1.
- FR-4 — Myke ferdigheter tas bare med når de kan uttrykkes som et kort ord.
- FR-5 — Treff tåler forskjeller i store og små bokstaver og vanlige bøyningsendelser.
- FR-7 — Sitatet er setningen eller linjen der nøkkelordet står første gang, med treffordet uthevet.
- FR-11 — Foreslå er forhåndsvalgt som skrivemodus.
- FR-12 — Høyst 8 forbedringsforslag per analyse.
- FR-14 — Brevdisposisjonens faste punkter, og nøytral tone uten tonevalg.
- FR-15 — Forskjeller i mellomrom og linjeskift regnes ikke som avvik i sitatkontrollen.
- FR-16 — Kopiert tekst er uten sitathenvisninger og markeringer.
- §4.3 — «Tidligere søknader som kontekst» betyr gjenbruk av lagret CV og tilbakevendende gap.
- FR-17 — Bare e-post og passord; ingen Feide, Google, e-postbekreftelse eller tilbakestilling på e-post.
- FR-19 — Analyser lagres når studenten trykker «Lagre».
- FR-20 — Historikken viser et navn studenten gir analysen.
- FR-21 — Tilbakevendende gap sammenlignes etter Treff-regelen.
- FR-26 — Egne tekster kan ikke analyseres i demomodus.
- NFR-3 — Tidsavbrudd etter 30 sekunder.
- NFR-4 — Responstid på 15 sekunder i normal modus og 2 sekunder i demomodus.
- NFR-9 — Lokal webapp, oppdaterte nettlesere på PC, brukbar på mobilskjerm.
- NFR-10 — Ingen full WCAG-revisjon i v1.
- §6.3 — Gruppen setter et forbrukstak hos leverandøren.
- §7 — Testsettet ligger under `.docs/testdata/`, dekker fem fagfelt med minst to engelske testpar, og har egne kanttilfeller.
- §9.2 — Tonevalg, Feide/Google-innlogging og tidligere søknadsbrev som kontekst er utenfor omfang.
- SM-4 — Brukertesten har tre testpersoner.
- SM-4 — Brukertesten kjøres i normal modus med fiktive tekster, ikke testpersonenes egne CV-er.
- SM-8 — Minst to av tre testpersoner kan forklare en klassifisering.
- SM-C1 — Høyst ett falskt gap per testpar.
