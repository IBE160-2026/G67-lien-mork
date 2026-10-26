---
title: "Revisjonshistorikk: brief.md"
created: 2026-10-26
---

# Revisjonshistorikk for brief.md

Denne filen samler alle revisjoner som er gjort av `brief.md` i dette repoet, i kronologisk rekkefølge (eldste først), basert på git-historikken.

| # | Commit | Dato | Forfatter | Beskrivelse |
|---|---|---|---|---|
| 1 | `b6959a3` | 2026-09-18 | Edgar Mork | Opprinnelig product brief lagt til (engelsk, med `[ASSUMPTION]`-markører) |
| 2 | `5de1bfd` | 2026-09-18 | Edgar Mork | Antakelser gjort om til faste beslutninger; visjon endret til 6-måneders horisont |
| 3 | `b46903c` | 2026-09-18 | Edgar Mork | Fjernet "(working title)" fra tittelen |
| 4 | `07f6afc` | 2026-09-18 | Fredrik Lien | Oversatt til norsk |
| 5 | `3d1e8d6` | 2026-10-26 | Fredrik Lien | Suksesskriterier gjort testbare/sjekkbare, basert på faglærers tilbakemelding |
| 6 | `598faec` | 2026-10-26 | Fredrik Lien | Omfanget delt i trinn (kjerne → søknadsbrev/CV-forslag → innlogging/lagring), basert på faglærers tilbakemelding |
| 7 | `0247ca7` | 2026-10-26 | Fredrik Lien | Suksesskriterier gjort fullt målbare, scoringsregel for nøkkelord definert, testsett og demomodus planlagt |

## 1. `b6959a3` — Opprinnelig product brief lagt til (2026-09-18)

Briefen ble opprettet på engelsk som del av commit "Add BMad framework and product brief for CV/application generator". Flere seksjoner var merket med `[ASSUMPTION]` der samtalen ikke hadde gitt et klart svar ennå:

- Om prosjektet var ment som kurs-/porteføljenivå eller noe større.
- Om den pedagogiske vinklingen var kjerneposisjonering eller bare beskrivende tekst.
- Om målgruppen faktisk var norske studenter spesifikt.
- Om GDPR var relevant (avhengig av om brukerne er i Norge/EU).
- Suksesskriterier og "Out of scope"-punkter var merket som uavklarte, utledede gjetninger.
- Visjonen var spekulativ, med et 2–3-års tidsperspektiv.

## 2. `5de1bfd` — Antakelser gjort om til beslutninger (2026-09-18)

Alle `[ASSUMPTION]`-markører ble fjernet og erstattet med faste beslutninger:

- Kurs-/porteføljenivå stadfestet som rammen for prosjektet.
- Den pedagogiske vinklingen («vis studenten *hvorfor* et nøkkelord traff eller ikke») stadfestet som kjernedifferensiator, ikke pynt.
- Norske studenter stadfestet som primærmålgruppe, med norsk språkhåndtering, NAV-konvensjoner og GDPR som en konkret konsekvens.
- Visjonsseksjonen endret fra et spekulativt 2–3-års perspektiv til en konkret visjon "om seks måneder".
- "Åpne punkter for brukeren" kuttet ned fra fem punkter til to genuint uavklarte: spenningen mellom lagring og dataminimering for "tidligere søknader", og eventuell frist/konkurrentkontekst.

## 3. `b46903c` — Fjernet "working title"-markør (2026-09-18)

Ren opprydding: fjernet "(working title)" fra både YAML-frontmatter-tittelen og H1-tittelen, siden tittelen nå var ansett som fast.

## 4. `07f6afc` — Oversatt til norsk (2026-09-18)

Hele briefen oversatt fra engelsk til norsk, uten innholdsmessige endringer — samme struktur, samme seksjoner, samme beslutninger som i `5de1bfd`/`b46903c`, men på norsk.

## 5. `3d1e8d6` — Suksesskriterier gjort testbare (2026-10-26)

Gjort som respons på tilbakemelding fra faglærer (`tilbakemelding-product-brief.md`), som påpekte at kriteriene "presise nok til at studenter stoler på dem" og "en standard brukeren ville vært komfortabel med å forsvare" ikke kunne sjekkes eller testes.

Endringer:
- Kriteriet om gapanalyse/ATS-presisjon erstattet med et konkret, testbart krav: for 5 forhåndsdefinerte test-par av CV og stillingsannonse (med kjent fasit), skal gapanalysen finne minst 4 av 5 forventede gap per par, og nøkkelordscoren skal følge en egendefinert, dokumentert scoringsregel (ikke en påstand om å etterligne et reelt ATS).
- Kriteriet om databehandlingsstandard erstattet med et konkret, verifiserbart krav: en bruker kan slette all sin lagrede data, og dataen er verifiserbart borte fra databasen.
- De to øvrige kriteriene (enkeltsesjon-flyt, og sporbarhet til kilde-CV uten fabrikkert innhold) ble beholdt uendret, siden faglærer vurderte dem som allerede sjekkbare.

## 6. `598faec` — Omfanget delt i trinn (2026-10-26)

Også et direkte svar på faglærers tilbakemelding, som påpekte at v1 som beskrevet var for stor til å bli ferdig og stabil på ett semester (tre inputformater, URL-skraping, fire KI-funksjoner, kontosystem, kryptering og historikk, alt i én versjon).

Endringer:
- Omfanget restrukturert fra en flat liste til tre trinn:
  1. **Trinn 1 (kjerne):** én CV (limt inn tekst eller PDF) mot én stillingsannonse (limt inn tekst) → gapanalyse og nøkkelordscore med forklaring. Ingen konto, ingen lagring.
  2. **Trinn 2:** søknadsbrev og CV-forbedringsforslag, med innstilling for omskriving versus forslag.
  3. **Trinn 3:** kontosystem med innlogging og kryptert lagring av CV-er og søknadshistorikk.
- URL-skraping av stillingsannonser, opplasting i DOC-format, og eksport til flere filformater samtidig flyttet fra "med i v1" til "utenfor omfang for v1".
- Beslutningspunktene (omskriving vs. forslag, filformat, språk/stil) omformulert til å vise hvilket trinn de hører til.

## 7. `0247ca7` — Målbare suksesskriterier, scoringsregel, testsett og demomodus (2026-10-26)

Oppfølging av faglærers "Neste steg for gruppen"-punkt 3: "Skriv om suksesskriteriene til målbare krav, definer scoringsregelen, planlegg demomodus, og gå deretter videre til PRD."

Endringer:
- **Suksesskriterier** strammet ytterligere inn: gapanalyse-kriteriet viser nå til scoringsregelen og testsettet under i stedet for å definere dem på nytt; sporbarhetskriteriet presisert til at alle påstander i generert innhold skal kunne kobles til et sitat i kilde-CV-en for hvert av de 5 testparene; slettekriteriet presisert til at sletting verifiseres med et direkte databaseoppslag; nytt kriterium lagt til om at en sensor kan starte appen i demomodus uten gruppens egne nøkler.
- **Ny seksjon "Scoringsregel for nøkkelord"**: definerer en egendefinert, dokumentert fremgangsmåte — nøkkelordutvinning via et fast promptkall, klassifisering av hvert nøkkelord som treff/delvis treff/ikke funnet (med sitat fra CV-en som bevis), og en konkret scoreformel: (antall treff + 0,5 × antall delvise treff) ÷ totalt antall nøkkelord × 100.
- **Ny seksjon "Testsett"**: et fast sett på 5 fiktive CV/stillingsannonse-par med kjent fasit over forventede gap, lagret i repoet, brukt både til å teste scoringsregelen og til demomodus.
- **Ny seksjon "Demomodus og kjørbarhet"**: en `DEMO_MODE`-miljøvariabel som lar appen kjøre mot ferdiginnspilte språkmodell-svar for testsettet i stedet for en ekte LLM-API, en `.env.example` i repoet, og to dokumenterte oppstartsveier i README (demo uten nøkler, og normal modus med egen API-nøkkel).
