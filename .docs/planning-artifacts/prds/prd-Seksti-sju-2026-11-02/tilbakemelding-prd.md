# Tilbakemelding på PRD

| | |
|---|---|
| **Gruppe** | G67 – G67-lien-mork |
| **PRD vurdert** | `.docs/planning-artifacts/prds/prd-Seksti-sju-2026-11-02/prd.md` (status: draft, sist endret 2026-11-06, commit 5e8eeee) |
| **Dato** | 2026-11-12 |
| **Type** | Formativ tilbakemelding, ikke karakter |

## 1. Samlet inntrykk

Dette er en sterk PRD med en tydelig tese: forklaringen er produktet, ikke tallet. Scoringsregelen, «ingen dikting» og demomodus er gjort om til krav som kan testes i kode. Størst risiko er omfanget (tre trinn, hvorav trinn 3 er tungt, og ukjente frister) og noen få steder der «ferdig» fortsatt er adjektiver eller en uuttalt antakelse.

## 2. Dette fungerer godt

- **Regelen er åpen og regnbar.** §3 definerer Score med formel, og FR-6 og UJ-1 stemmer med hverandre: «12 nøkkelord med 7 Treff og 1 Delvis treff gir 63 (62,5 rundet opp)», og etter ett nytt treff blir det 71. Dette kan bli en enhetstest rett fra PRD-en.
- **KI-kontrollen ligger i kode, ikke bare i promptene.** §6.1 peker på sitatkontrollen (FR-15), forbudet mot «Ikke funnet» i omskrevet tekst (FR-13) og NFR-2 for usikre svar, med ett nytt forsøk og så en feilmelding. Motmålene SM-C1 og SM-C2 hindrer at SM-1 nås ved å gjette for mye.
- **Ærlig scope og kjørbarhet.** §9 har trinn med «Ferdig når», §8 og §9.2 har tydelige utelatelser, og FR-25–28 med demomodus og `.env.example` svarer direkte på det briefen manglet.

## 3. Oversikt per dimensjon

| Dimensjon | Vurdering | Kort begrunnelse |
|---|---|---|
| Beslutningsklarhet | god | Valg er tatt og begrunnet (to skrivemodi, kun PDF/tekst, lagring som eget trinn). Leverandør, frister og hvem som lager testsettet står åpne (§11). |
| Substans | sterk | Personene, JTBD og NFR-ene er knyttet til beslutninger. Ingen pynte-personas eller boilerplate. |
| Strategisk sammenheng | sterk | Alle trinn tjener «forklar hvorfor». SM-ene måler tesen, og motmål finnes. |
| Testbarhet | god | Kjernen har tallfestede konsekvenser. Noen krav er fortsatt myke (se 4.3, 4.4). |
| Scope og avgrensning | god | Eksplisitte ikke-mål og trinnplan. Realismen for to personer og ukjent frist er ikke avklart (4.1). |
| Brukbarhet for neste fase | sterk | Ordliste, kontinuerlige ID-er, «Realiserer UJ-x» og «Validerer FR-x» gjør uttrekk enkelt. |
| Formtilpasning | sterk | Forbrukerprodukt med brukerreiser med navngitte personer og kanttilfeller. Passer produktet. |

## 4. Viktigste forbedringer

### 4.1 Gjør trinn 3 til et valg med frist, ikke en automatikk
- **Alvorlighet:** høy
- **Hvor:** §9.1 «Neste trinn starter først når suksesskriteriene for forrige trinn er nådd»; §11 punkt 3 «Frister og milepæler … er ikke oppgitt»
- **Problem og hvorfor det betyr noe:** Trinn 3 (konto, kryptert lagring, sletting, tilgangskontroll) er den tyngste delen, og tidsrammen er ukjent. Epics og sprintplan kan ikke lages uten å vite hva som kuttes først. Dessuten er halvferdig trinn 3 verre enn ingen: lagring uten sletting (FR-23) eller tilgangskontroll (FR-24) er et personvernhull.
- **Forslag:** Legg til i §9.1: «Trinn 3 påbegynnes bare hvis trinn 2 er ferdig senest [dato]. FR-17–FR-24 leveres som en helhet eller ikke i det hele tatt. Hvis tiden knapper, kuttes trinn 3, og demomodus uten demokonto (FR-27) er fortsatt komplett.» Flytt spørsmålet om frist fra «åpent» til «må avklares før epics».

### 4.2 Språkkontrollen (FR-3) mangler metode og krasjer med FR-4
- **Alvorlighet:** medium
- **Hvor:** FR-3 «Verktøyet avgjør om CV-en og stillingsannonsen er på norsk eller engelsk»; FR-4 «CV-en sendes aldri til språkmodellen i trinn 1»
- **Problem og hvorfor det betyr noe:** Hvis språket oppdages av språkmodellen, sendes CV-en dit i trinn 1, og personvernløftet i §6.2 brytes. Arkitekturen må vite dette nå, og demomodus må kunne teste det uten nøkkel.
- **Forslag:** «Språket avgjøres i kode, uten språkmodellen. En tekst på færre enn [n] ord gir beskjed om at språket ikke kan avgjøres. Testes med: norsk CV med engelske fagord → norsk; kort tekst → beskjed; tysk tekst → ‘språket støttes ikke’.» Løft «CV-en sendes aldri til språkmodellen» fra [ASSUMPTION] til selvstendig krav (NFR-nivå), siden personvern og arkitektur bygger på det.

### 4.3 Klassifiseringen (FR-5) trenger eksempler som kan bli testtilfeller
- **Alvorlighet:** medium
- **Hvor:** FR-5 «Treff tåler forskjeller i store og små bokstaver og vanlige bøyningsendelser»
- **Problem og hvorfor det betyr noe:** FR-5 avgjør SM-1 og SM-C1, men «vanlige bøyningsendelser» kan bygges på mange måter. Korte nøkkelord som «R», «C#» og «SQL» gir lett falske treff inni andre ord, og flerordsnøkkelord («Microsoft Excel») er uavklart.
- **Forslag:** Legg inn en liten tabell i FR-5, for eksempel: «prosjektledelse» mot «prosjektlederen» → Ikke funnet (eller Treff, velg og skriv det); «R» mot «Power BI, Excel» → Ikke funnet (treff bare på helt ord); «SQL» mot «sql-databaser» → Treff; «Microsoft Excel» mot «Excel» → Delvis treff bare hvis paret står i synonymlisten. Tabellen blir direkte enhetstester og gjør §3-definisjonen av Treff mer presis.

### 4.4 Erstatt adjektiver og fyll hull i testbarhet
- **Alvorlighet:** medium
- **Hvor:** NFR-10 «kontrasten er god nok»; NFR-9 «kan brukes på mobilskjerm»; NFR-6 «er kryptert»; FR-22 «alt som er lagret»; FR-1 har bare «ikke tomt felt»
- **Problem og hvorfor det betyr noe:** Dette er de stedene en utvikler eller tester må gjette. NFR-6, NFR-7 og FR-17–22 mangler også en SM som validerer dem.
- **Forslag:** «Brødtekst har kontrast minst 4,5:1.» «Ved 375 px bredde krever ingen side horisontal rulling.» «NFR-7 testes ved å analysere en kjent CV-tekst og søke i all loggutskrift etter en setning fra den: ingen treff.» «FR-22: oversikten viser alle rader som tilhører kontoen; antallet stemmer med antall rader i databasen.»

### 4.5 Sorter antakelsene
- **Alvorlighet:** medium
- **Hvor:** §12 med ca. 30 punkter; §2.3 «Reisene er skrevet ut fra briefen, ikke fortalt av gruppen»
- **Problem og hvorfor det betyr noe:** Små detaljer («høyst 8 forbedringsforslag», «15 000 tegn») ligger side om side med valg som styrer arkitekturen («CV-en sendes aldri…», «Egne tekster kan ikke analyseres i demomodus»). Da overses de viktige.
- **Forslag:** Gå gjennom §12 og del i tre: bekreftet nå og tag fjernet; beslutning som blir krav; faktisk åpent. Si i §2.3 om reisene nå er bekreftet av gruppen (og helst av en student).

## 5. Mekaniske funn

- ID-er er sammenhengende og unike (UJ-1–5, FR-1–28, NFR-1–10, SM-1–8 + C1–C2), og krysshenvisningene løser seg. Assumption-indeksen i §12 stemmer med de innebygde taggene.
- Glossar-avvik: Treff er definert som «nøkkelordet står i CV-en», men FR-5 utvider det til bøyninger. Oppdater definisjonen. Språk er definert som norsk eller engelsk, mens FR-3 beskriver andre språk; «trinn» brukes overalt, men er ikke i ordlisten.
- SM-1 og SM-2 måles automatisk med ferdiginnspilte svar, som tester koden, ikke språkmodellen. Skriv eksplisitt hva som sikres automatisk, og hva som bare sjekkes manuelt ved ny promptmal. Samme CV og annonse kan også gi ulike nøkkelord i normal modus (NFR-1 sier dette indirekte).

## 6. Før dere går videre

**Må avklares før UX, arkitektur og epics:**
- Frist og kuttregel for trinn 3 (4.1).
- Språkkontroll i kode og «CV sendes ikke i trinn 1» som krav (4.2).
- Hvem lager testsettet og fasiten, og når (§11 punkt 2). Trinn 1 kan ikke testes uten.
- Språkmodell-leverandør og forbrukstak, siden FR-11 og §6.3 avhenger av dem.

**Kan vente:** tonevalg, tidligere søknadsbrev, synonymlistens størrelse (§11 punkt 4–6), og egen skisse av resultatsiden i UX-steget.

**Oppfølging av tilbakemeldingen på product brief:** ja. Kjerneflyten er valgt, trinnene er avgrenset, valgene (Foreslå/Skriv om, PDF og tekst, språk, lagring) er tatt, suksesskriteriene er målbare, scoringsregelen er definert, og demomodus og `.env.example` er krav. Mappenavnet bruker nå bindestrek.

## 7. Refleksjonsspørsmål

1. §2.3 sier at brukerreisene er skrevet ut fra briefen, ikke fortalt av gruppen. Hva ville dere endret hvis dere hadde snakket med to–tre studenter som søker jobb nå, og hvordan vil dere sjekke det før UX?
2. Hvordan kontrollerte dere at KI-forslagene til regler (f.eks. avrunding, bøyningstoleranse, grensen på 30 sekunder) passet gruppens egen forståelse? Hvilke forslag forkastet eller endret dere?

_Vurdert mot kvalitetsrubrikken i bmad-prd. Dette er veiledning, ikke sensur._
