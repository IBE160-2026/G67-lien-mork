---
title: "Produktbeskrivelse: CV- og søknadsassistent for studenter"
status: draft
created: 2026-09-18
updated: 2026-09-18
---

# Produktbeskrivelse: CV- og søknadsassistent for studenter

## Sammendrag

Studenter som søker jobb og internship møter et misforhold: hver utlysning ønsker et søknadsbrev og en CV tilpasset sitt eget språk og sine egne krav, men de fleste studenter skriver én generisk versjon og gjenbruker den overalt. Samtidig er KI allerede dypt forankret på den andre siden av ansettelsesprosessen — screening, rangering og filtrering av søknader — og studenter får sjelden se hvordan dette maskineriet faktisk leser det de sender inn.

Dette verktøyet tetter begge hullene på én gang. En student laster opp en CV og en stillingsannonse; verktøyet lager et skreddersydd søknadsbrev, avdekker konkrete CV-forbedringer, flagger kvalifikasjoner annonsen etterspør som CV-en ikke viser, og gir en poengsum basert på ATS-lignende nøkkelordmatching — de samme mekanismene et reelt søkersporingssystem (ATS) ville brukt. Studenten beholder kontrollen over hvor mye verktøyet skal skrive om versus bare foreslå, i hvilken tone, og i hvilket format.

Fordi produktet lagrer CV-er, jobbhistorikk og tidligere søknader, behandles kryptert lagring og autentisert tilgang som grunnleggende, ikke valgfritt — dette er personopplysninger håndtert med en reell grad av persistens (tidligere søknader gir kontekst til fremtidige), som er nøyaktig den typen profil som må bygges forsvarlig fra dag én, ikke ettermonteres.

Dette er avgrenset som et kurs-/porteføljenivå-prosjekt — grundighet tilpasset et solid studentprosjekt eller en avsluttende oppgave, ikke en investor- eller bedriftscompliance-leveranse.

## Problemet

Studenter som søker jobb i dag gjør typisk følgende:

- Skriver én CV og én søknadsbrevmal, og redigerer den lett per søknad — fordi å skreddersy hver innsending manuelt er tidkrevende og gevinsten per annonse er usikker.
- Har ingen innsikt i *hvorfor* en søknad blir filtrert bort. Tilbakemelding, når den i det hele tatt kommer, er et generisk avslag — ikke "CV-en din manglet nøkkelordet X" eller "denne annonsen screener på kvalifikasjonen Y som du ikke har oppgitt."
- Vet ikke hva et ATS (Applicant Tracking System / søkersporingssystem) faktisk gjør med innsendingen deres. KI-systemene som utfører filtreringen er ugjennomsiktige for dem som blir filtrert.
- Møter dette spesielt som studenter: tynn arbeidserfaring betyr at hver søknad må jobbe hardere for å koble den lille erfaringen de har til det annonsen ber om — nettopp den typen hull-identifisering og formuleringsarbeid som er mest tungvint å gjøre manuelt, per annonse, i stort volum.

Kostnaden ved dagens praksis er søknader som teknisk sett er sendt inn, men dårlig tilpasset — både til den menneskelige leseren og til det automatiserte filteret som ofte leser den først.

## Løsningen

Et verktøy som tar en students CV og en målrettet stillingsannonse og produserer, per søknad:

- Et skreddersydd søknadsbrev, tilpasset annonsens språk og studentens angitte tone-/stilpreferanse.
- Konkrete CV-forbedringsforslag spesifikke for den aktuelle annonsen.
- En gapanalyse: kvalifikasjoner annonsen ber om som CV-en for øyeblikket ikke viser.
- En ATS-optimaliseringsgjennomgang — nøkkelord-/formattilpasning til hvordan automatisert screening faktisk tolker innsendinger.

I stedet for et ett-klikks "generer og send inn"-verktøy, forblir studenten beslutningstaker: de velger hvor mye verktøyet skal skrive om direkte versus bare flagge for at studenten selv skal håndtere det, i hvilket filformat, og på hvilket språk-/stilnivå av formalitet. Verktøyets rolle ligner kvalitativt mer på en coach med innsyn i filtreringsmekanikken enn en spøkelsesskribent.

## Hva som gjør dette annerledes

Kjernemekanikken her — CV/stillingsannonse-matching, ATS-scoring, gapanalyse, KI-utkast til søknadsbrev — er **ikke ny**. Dette er en overfylt kategori: Teal, Rezi, Kickresume, Jobscan, Enhancv og Resume Worded gjør alle versjoner av dette internasjonalt, og norske markedsverktøy finnes allerede og gjør stort sett det samme på norsk (Jobbki, Cvenn, SøknadGPT/cvcv.no). Enhver beskrivelse som later som noe annet ville vært uærlig om den faktiske konkurransesituasjonen.

Det som skiller dette verktøyet:

- **En reell pedagogisk vinkling, som er kjernen i produktet, ikke bare pynt.** Verktøyet produserer ikke bare et resultat — det viser studenten *hvordan* den KI-drevne filtreringen det etterligner faktisk vurderer materialet deres: det synliggjør *hvorfor* et nøkkelord traff eller ikke, ikke bare en poengsum. Dette er et grunnleggende annerledes produkt enn "lim inn CV + stillingsannonse → få et brev", og er utformet eksplisitt for dette, ikke behandlet som en ettertanke.
- En tillitsbasert datahistorie (kryptert lagring, klar retensjons-/slettingspraksis, GDPR-tilpasset håndtering) som et eksplisitt salgsargument overfor et studentpublikum som overleverer CV-er og søknadshistorikk — i stedet for den implisitte, uuttalte holdningen de fleste konkurrenter har.
- **Tilpasning til det norske markedet og norske institusjoner**: språk, lokale konvensjoner i arbeidsmarkedet, og et produkt bygget rundt norske studenters faktiske jobbsøkerkontekst, ikke en generisk internasjonal en.

## Hvem dette er for

**Primærbruker: norske studenter** som aktivt søker jobb/internship, søker på flere annonser og for øyeblikket gjenbruker generisk materiale fordi tilpasning per annonse er for tidkrevende å gjøre manuelt. Produktet er bygget rundt norsk språkhåndtering, NAV/lokale konvensjoner i arbeidsmarkedet, og GDPR-håndtering rettet mot et norsk publikum.

Generell på tvers av fagfelt — ingen spesifikk studieretning eller institusjon er målgruppen.

Suksess for denne brukeren: de sender inn en søknad som er reelt sterkere — mer spesifikt tilpasset annonsen, med reelle hull identifisert i stedet for tildekket — og de sitter igjen med forståelse for *hvorfor* den er sterkere, ikke bare har overlatt oppgaven til en svart boks.

## Suksesskriterier

- Brukere kan gå fra CV + stillingsannonse til et brukbart utkast til skreddersydd søknadsbrev, CV-forslag og en gapanalyse i én økt.
- For et fast sett på 5 forhåndsdefinerte test-par av CV og stillingsannonse (med kjent fasit over forventede gap), finner gapanalysen minst 4 av 5 forhåndsdefinerte gap per par, og nøkkelordscoren beregnes etter en egendefinert, dokumentert scoringsregel — ikke en påstand om å etterligne et reelt ATS, som verken kan verifiseres eller kontrolleres.
- Ingen kvalifikasjon eller erfaring dikteres opp i generert innhold som ikke kan spores tilbake til kilde-CV-en — dette er en hard korrekthetsgrense, ikke en ambisjon, gitt den dokumenterte hallusinasjonsrisikoen i denne produktkategorien.
- En bruker kan slette all sin lagrede data (CV-er, søknadshistorikk og analyser) via kontoinnstillingene, og denne dataen er verifiserbart borte fra databasen etter sletting.

## Omfang

Omfanget er delt i trinn etter tilbakemelding om at den opprinnelige v1 var for stor til å bli ferdig og stabil på ett semester. Hvert trinn bygges først når det forrige er ferdig og stabilt.

**Trinn 1 — kjernen i v1 (må være ferdig og stabil før resten bygges):**
- Input: én CV (limt inn som tekst, eller PDF-opplasting) og én stillingsannonse (limt inn som tekst).
- Output: gapanalyse (kvalifikasjoner annonsen ber om som CV-en ikke viser) og nøkkelordscore, med forklaring av *hvorfor* hvert nøkkelord traff eller ikke — den pedagogiske vinklingen som er kjernen i produktet.
- Ingen kontosystem og ingen lagring i dette trinnet: analysen er statsløs. Det holder personvernrisikoen og kompleksiteten nede til lagring er en bevisst, dokumentert beslutning (se trinn 3).

**Trinn 2 — bygges etter at trinn 1 er ferdig og stabilt:**
- Tailored søknadsbrev og CV-forbedringsforslag.
- En innstilling for grad av omskriving versus forslag (se beslutningspunkt under) — produktets "coach, ikke spøkelsesskribent"-posisjon gjøres om til en faktisk valgmulighet her.

**Trinn 3 — bygges etter at trinn 2 er ferdig og stabilt:**
- Kontosystem med innlogging og kryptert lagring av CV-er og søknadshistorikk, inkludert bruk av tidligere søknader som kontekst.

**Eksplisitt åpent — ikke besluttet ennå (brukerens egne "beslutningspunkter"):**
- **Grad av omskriving versus forslag** (trinn 2): skal verktøyet utarbeide fullstendig erstatningstekst, eller kun flagge/foreslå og la skrivingen være opp til studenten? Dette er et produktdefinerende valg og bør ikke stilltiende defaultes — det trenger trolig å være en innstilling, ikke en engangs arkitekturbeslutning.
- **Utdataformat for filer** (trinn 2): hvilket format søknadsbrev og CV-forslag leveres i som standard — avklares når trinn 2 planlegges, ikke før.
- **Språk-/stilnivå**: hvor mye kontroll studenten får over tone/formalitet, og på hvilket(e) språk verktøyet opererer.
- **Lagring i trinn 3**: om og hvor lenge data lagres, se spenningen beskrevet under Data og personvern.

**Utenfor omfang for v1** (flyttet ut etter tilbakemelding om at disse gjør kjernen unødig krevende å få pålitelig): direkte innsending/auto-søking til jobbportaler, funksjoner rettet mot arbeidsgivere/rekrutterere, flerspråklig CV-oversettelse, native mobilapp, URL-skraping av stillingsannonser (kun lim inn tekst), opplasting i DOC-format, eksport til flere filformater samtidig.

## Data og personvern

Trukket frem som egen seksjon fordi brukeren flagget dette direkte, og forskningsgrunnlaget for denne beskrivelsen bekrefter at det er bærende, ikke en avkrysningsboks:

- CV-er og søknadshistorikk er personopplysninger. Kryptert lagring og autentisert tilgang (begge angitt som krav) er minimumsstandarden, ikke taket.
- Brukerne er i Norge/EU, så GDPR gjelder konkret: et rettslig grunnlag (trolig eksplisitt samtykke), dataminimering og en retensjons-/slettingspolicy (ikke lagring på ubestemt tid som standard), og — hvis et eksternt LLM-API brukes til å behandle CV-er — informasjon til brukerne om denne underleverandøren.
- **Fortsatt åpent**: skal data lagres for å gi funksjonen "tidligere søknader" reell verdi (som taler for lengre lagring), eller minimeres aggressivt (som taler mot det)? Dette er en direkte spenning mellom en oppgitt input ("tidligere søknader") og god praksis for dataminimering, og fortjener et bevisst svar fremfor en standardløsning.

## Visjon — om seks måneder

Om seks måneder er dette et verktøy norske studenter faktisk kommer tilbake til gjennom en hel jobbsøkerprosess — ikke en engangsgenerator de prøver én gang, men noe som brukes søknad etter søknad fordi det holder på reell kontekst: hva som er prøvd, hvilke formuleringer som har ført til intervjuer, hvor de tilbakevendende hullene er. Den pedagogiske vinklingen er en synlig, distinkt del av opplevelsen, ikke en fotnote — å bruke verktøyet lærer studenten noe konkret om hvordan KI-drevet rekruttering faktisk filtrerer materialet deres, hver gang de bruker det. Tillit til hvordan dataene deres håndteres (kryptering, klar retensjon, ingen overraskende bruk av CV-en deres) er en del av grunnen til at de kommer tilbake, ikke bare kvaliteten på skrivingen.

---

## Åpne punkter for brukeren

De fleste antagelsene fra førsteutkastet er nå avklart til beslutninger ovenfor. To ting er fortsatt reelt åpne:

1. **Spenningen mellom retensjon og minimering** for data om "tidligere søknader" (se Data og personvern) — bevisst avgjørelse gjenstår.
2. Eventuell frist, oppgavekontekst, eller spesifikke konkurrentverktøy du bevisst forholder deg til — ikke oppgitt ennå.
