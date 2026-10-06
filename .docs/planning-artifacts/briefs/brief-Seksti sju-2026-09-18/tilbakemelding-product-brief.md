# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G67 – G67-lien-mork |
| **Product brief** | `.docs/planning-artifacts/briefs/brief-Seksti sju-2026-09-18/brief.md` (commit `07f6afc`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

## Samlet vurdering

- **Bør revideres før dere går videre.** Rett punktene markert «Endre» før dere lager PRD og arkitektur.

**Det som er bra:**

1. «Hva som gjør dette annerledes» er uvanlig ærlig: dere sier rett ut at kategorien er overfylt (Teal, Rezi, Jobscan, Jobbki, Cvenn, SøknadGPT) og peker på en konkret vinkling – den pedagogiske, der studenten får se *hvorfor* et nøkkelord traff eller ikke.
2. Den harde grensen om at ingen kvalifikasjon eller erfaring skal diktes opp, og at alt må kunne spores tilbake til kilde-CV-en, er et godt og testbart kvalitetsprinsipp.
3. Personvern er tatt på alvor med en egen seksjon, og dere har selv identifisert spenningen mellom «tidligere søknader som kontekst» og dataminimering.

**De viktigste endringene:**

1. Omfanget i v1 er i praksis hele forslag 2 og mer: opplasting i tre formater, annonse via URL, søknadsbrev, CV-forslag, gapanalyse, ATS-scoring, kontosystem, kryptert lagring og søknadshistorikk. Velg en kjerneflyt og flytt resten ut.
2. Det som definerer produktet er ikke bestemt: om verktøyet skal skrive om eller bare foreslå, hvilke filformater, hvilket språk, og om historikk skal lagres. Ta disse beslutningene før PRD.
3. Suksesskriteriene kan ikke testes slik de står («presise nok til at studenter stoler på dem», «en standard brukeren ville vært komfortabel med å forsvare»). Påstanden om at ATS-scoren bruker «de samme mekanismene et reelt ATS ville brukt» kan dere heller ikke kontrollere. Skriv konkrete og sjekkbare kriterier.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Middels**

**Sammenlignbart med:** 2) AI CV- og søknadsassistent (middels). Briefen tar utgangspunkt i dette forslaget med samme inn- og utdata. Med innlogging, kryptert lagring og historikk i tillegg ligger v1 slik den er beskrevet i øvre del av middels.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Middels | Nøkkelordmatching og ATS-poengsum, gapanalyse og sporbarhet til kilde-CV. Scoren kan beregnes i kode, men hvordan er ikke beskrevet. |
| Datamodell – antall entiteter og relasjoner mellom dem | Middels | Bruker, CV (versjoner), stillingsannonse, søknad, analyse og preferanser, med historikk på tvers. |
| Brukere, roller og innlogging | Middels | Kontosystem med innlogging er satt som krav i v1. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Høy | Søknadsbrev, CV-forslag, gapanalyse og ATS-gjennomgang bygger alle på språkmodellen, og bruk av tidligere søknader som kontekst gjør promptene mer komplekse. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Middels | Språkmodell-API, og skraping av annonser via URL. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Lav | Ikke relevant. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Høy | Opplasting av PDF, DOC og TXT, og eksport til DOC, Markdown og/eller PDF. Dette er krevende å få pålitelig. |
| Sikkerhet og personvern | Høy | Kryptert lagring av CV-er og søknadshistorikk, innlogging, sletting og informasjon om LLM-underleverandør. Mye å implementere og teste. |

**Hva vanskelighetsgraden betyr for dere:**

- _Middels:_ Et godt balansert valg. Pass på at kjerneflyten blir ferdig og stabil før dere legger til mer. Her betyr det at analysen av én CV mot én annonse må virke godt før dere bygger kontoer, historikk og eksport.

### Gjennomførbarhet med BMAD og Claude Code

Dere skal planlegge med BMAD (product brief → PRD → arkitektur → epics og stories) og implementere med Claude Code. Vurderingen under tar hensyn til at det må være tid til hele denne flyten, og til testing, retting og README til slutt.

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | Stor risiko | Fire KI-funksjoner, tre inputformater pluss URL, eksport i flere formater, innlogging og kryptert historikk er for mye for to personer på et semester. Det finnes ennå ingen PRD. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | Risiko | Problem og posisjonering er tydelige, men flere produktdefinerende valg står åpne. PRD-en vil enten gjette eller bli svært stor. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | En webapp med innlogging, database og LLM-kall er godt dokumentert. Kryptering og filkonvertering krever mer oppfølging. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | Risiko | Dere kan ikke vite hvordan reelle ATS-er vurderer. Definer heller deres egen, åpne scoringsregel og kontroller den. Lag faste eksempel-CV-er og annonser med forventede gap. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | Risiko | Scoreregel, sporbarhet (finnes det sitert i CV-en?), innlogging, tilgangskontroll og sletting kan testes. KI-tekstens kvalitet må testes med faste eksempler. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Stor risiko | Ikke omtalt. Appen trenger en LLM-nøkkel og en krypteringsnøkkel. Planlegg demomodus og `.env.example`. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | Risiko | Briefen nevner LLM-API som mulig underleverandør, men ingen valg, kostnad eller testmodus. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart med justert omfang.** Se forslagene under.

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Kjerne for v1: én CV (innlimt tekst eller PDF) mot én annonse (innlimt tekst) → gapanalyse og nøkkelordscore med forklaring av hvorfor hvert nøkkelord traff eller ikke. Det er den pedagogiske vinklingen dere selv kaller kjernen.
2. Andre trinn: søknadsbrev og CV-forslag, med en innstilling for «foreslå» versus «skriv om». Tredje trinn: innlogging og lagring av historikk. URL-skraping, DOC-støtte og eksport i flere formater flyttes til «utenfor omfang».
3. Lagrer dere ikke noe i v1, faller kravet om kryptering og innlogging bort, og personvernrisikoen blir mye mindre. Velger dere lagring, gjør det til et bevisst og dokumentert trinn.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Tydelig: CV og annonse inn, søknadsbrev, CV-forslag, gapanalyse og ATS-score ut, med studenten som beslutningstaker. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | OK | Konkret og godt begrunnet, særlig poenget om at studenter med tynn erfaring ikke vet hvorfor de blir filtrert bort. |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | Juster | Beskriver resultatene, men ikke flyten. Beskriv hva studenten gjør steg for steg og hvordan «hvorfor traff nøkkelordet» vises. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig om konkurrentene. Den pedagogiske vinklingen er en god differensiator, men «tillitsbasert datahistorie» og «norsk tilpasning» er svakere, siden flere norske verktøy allerede finnes. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | Juster | «Norske studenter på tvers av fagfelt» er bredt. Gjør det konkret, f.eks. bachelorstudenter i siste år som søker sommerjobb eller trainee. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Endre | Bare det første og tredje kriteriet kan sjekkes. Erstatt «presise nok til at studenter stoler på dem» og «en standard brukeren ville vært komfortabel med» med konkrete krav, f.eks. «for 5 testannonser finner appen minst 4 av 5 forhåndsdefinerte gap» og «en bruker kan slette all sin data, og den er borte fra databasen». |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Endre | V1 er for stor, og produktdefinerende valg (omskriving vs. forslag, format, språk, lagring) står åpne. Bestem dem og kutt v1. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | Juster | Visjonen om et verktøy studentene kommer tilbake til, avhenger av historikk og lagring. Det er greit som visjon, men da bør historikk ikke også være et krav i v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Historikken viser at antakelser er gjort om til beslutninger og at briefen er oversatt og bearbeidet. Bra. Ta de åpne beslutningene og dokumenter dem før PRD. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | Endre | For mange store funksjonsområder i v1. Velg kjerneflyten og legg resten i tydelige trinn. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Endre | Lag målbare kriterier, en åpen scoringsregel og et sett fiktive CV-er og annonser med fasit. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | Juster | Den pedagogiske vinklingen gir et godt designfokus. Skisser resultatsiden med forklaring av treff og mangler. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | Juster | Teknologi er ikke valgt. Kryptering og innlogging gjør arkitekturen mer kompleks enn kjerneflyten trenger; vurder dem som senere trinn. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Endre | Planlegg demomodus med lagrede svar og tydelig nøkkeloppsett, slik at sensor kan kjøre appen. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | API- og krypteringsnøkler i `.env` utenfor Git, og kun fiktive CV-er som testdata. Mappenavnet med mellomrom (`brief-Seksti sju-…`) kan gi problemer i kommandolinjen; vurder å bruke bindestrek. |

## 3. Neste steg for gruppen

1. Ta de åpne beslutningene (foreslå vs. skriv om, input- og outputformat, språk, lagring eller ikke) og skriv dem inn i briefen.
2. Kutt v1 til kjerneflyten (gapanalyse og forklart nøkkelordscore), og legg søknadsbrev, kontoer og historikk i tydelige senere trinn.
3. Skriv om suksesskriteriene til målbare krav, definer scoringsregelen, planlegg demomodus, og gå deretter videre til PRD.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
