---
title: "Coachingplan for G67 — fra PRD til ferdig app"
status: draft
created: 2026-11-06
---

# Coachingplan for G67

Denne planen beskriver hvordan gruppen (Fredrik H Lien og Edgar Mork) kommer seg fra ferdig PRD til en app sensor kan kjøre. Den sier hva vi gjør i hvilken rekkefølge, hvilke spørsmål vi skal stille oss underveis, og hvordan vi vet at et steg er ferdig. Planen bygger på [PRD-en](planning-artifacts/prds/prd-Seksti-sju-2026-11-02/prd.md) og [faglærerens tilbakemelding](planning-artifacts/briefs/brief-Seksti-sju-2026-09-18/tilbakemelding-product-brief.md). Den følger kriteriene for del 1 av mappen.

## 1. Hvor vi står (2026-11-06)

- Briefen er revidert etter tilbakemeldingen.
- PRD-en er et utkast med FR-1–FR-28 og SM-1–SM-8. Fire presiseringer ble lagt inn 2026-11-06.
- Antakelsene i §12 er ikke gjennomgått av gruppen. Forslag 5–14 fra PRD-gjennomgangen er ikke behandlet (se `.logs/edgar-mork/issues.md`).
- Ingen UX, ingen arkitektur, ingen testdata og ingen kode ennå.
- Frister og milepæler i semesteret er ikke kjent (PRD §11, punkt 3). **Første oppgave er å fylle inn datoene i §3 under.**

## 2. Prinsipper for hvordan vi jobber

1. **Gruppen bestemmer, KI-en foreslår.** Alle beslutninger som former produktet, tar vi selv og skriver inn i dokumentene. Et forslag fra KI-en blir ikke en beslutning før en av oss har lest det og sagt ja.
2. **Kjernen først.** Trinn 1 skal virke og være stabilt før vi starter trinn 2. Blir tiden knapp, kutter vi trinn 3, ikke kvaliteten i trinn 1.
3. **Alt skal kunne spores.** Hver story viser til FR-er i PRD-en, og hver test viser til en FR eller et SM. Sensor skal kunne følge veien fra plan til kode.
4. **Vi kontrollerer KI-ens arbeid.** Vi forstår koden vi committer, og vi tester mot fasiten, ikke mot magefølelsen.
5. **Små steg, ofte i Git.** Pull før vi starter, logg økten, og push når vi er ferdige.

## 3. Faser og milepæler

Datoene fyller vi inn når fristene er kjent. Rekkefølgen er fast. Fase 2 og 3 kan gå parallelt, med én person på hver.

| # | Fase | BMAD-skill | Ferdig når | Kriterium i mappen | Frist |
|---|---|---|---|---|---|
| 0 | Lukke PRD-en | `bmad-prd` | Antakelsene i §12 er bekreftet eller rettet, forslag 5–14 er behandlet, og status er `final` | 1 Prosess | [fyll inn] |
| 1 | UX | `bmad-ux` | DESIGN.md og EXPERIENCE.md finnes, med skisse av resultatsiden | 4 Design | [fyll inn] |
| 2 | Arkitektur | `bmad-architecture` | Stack, språkmodell, lagring, kryptering og demomodus er valgt og begrunnet | 5 Arkitektur | [fyll inn] |
| 3 | Testsett | — | Fem testpar med fasit ligger i repoet (PRD §7) | 3 Testing | [fyll inn] |
| 4 | Epics, stories og sprintplan | `bmad-create-epics-and-stories`, `bmad-sprint-planning` | Alle FR-er er dekket av stories, og sprintstatusen er generert | 1 Prosess | [fyll inn] |
| 5 | Bygge trinn 1 | `bmad-build`, `bmad-code-review` | SM-1, SM-3 og SM-5 er nådd | 2 Funksjonalitet, 6 Kjørbarhet | [fyll inn] |
| 6 | Bygge trinn 2 + brukertest | `bmad-build`, `bmad-code-review` | SM-2 er nådd, og brukertesten (SM-4, SM-8) er gjennomført | 2, 3, 4 | [fyll inn] |
| 7 | Bygge trinn 3 | `bmad-build`, `bmad-code-review` | SM-6 og SM-7 er nådd | 2, 3 | [fyll inn] |
| 8 | Avslutning | `bmad-retrospective` | README er testet av en utenforstående, repoet er ryddet, og retrospektiven er skrevet | 6 Kjørbarhet, 7 Ryddighet | [fyll inn] |

**Buffer:** Vi setter av minst én uke mellom fase 7 og innleveringen. Ligger vi etter når fase 5 er ferdig, flytter vi trinn 3 til «utenfor omfang» og skriver begrunnelsen i PRD-en.

## 4. Coachingspørsmål per fase

Spørsmålene tar vi opp sammen før vi går videre til neste fase. Svarene skriver vi kort inn i sesjonsloggen.

**Fase 0 — Lukke PRD-en**
- Hvilke antakelser i §12 er vi faktisk enige i, og hvilke godtok vi bare fordi KI-en skrev dem?
- Kan vi forklare scoringsregelen og regelen om ingen dikting for faglæreren uten å se i dokumentet?
- Er det noe i PRD-en vi ikke tror vi rekker?

**Fase 1 — UX**
- Forstår en student på resultatsiden *hvorfor* et nøkkelord er Ikke funnet, uten å lese «Slik regnes scoren»?
- Hvordan ser appen ut når noe går galt: PDF uten tekst, ulikt språk, språkmodellen svarer ikke?
- Kan alt brukes med tastatur, og vises status med noe annet enn farge (NFR-10)?

**Fase 2 — Arkitektur**
- Er stacken så enkel som appen trenger, og kan vi begge forklare hver del av den?
- Hvordan skal demomodus fungere, og kan sensor starte appen uten noen av våre nøkler?
- Hva koster normal modus per analyse, og hvor setter vi forbrukstaket?

**Fase 3 — Testsett**
- Ville en rekrutterer vært enig i fasiten for hvert testpar?
- Dekker testparene kanttilfellene (engelsk, Delvis treff, få nøkkelord)?
- Er alle tekstene fiktive?

**Fase 4 — Epics og stories**
- Kan hver story bygges og testes på én eller to økter?
- Viser hver story til en FR, og er hver FR dekket?
- Hvilke stories kan vi kutte uten at kjerneflyten brekker?

**Fase 5–7 — Bygging**
- Forstår vi koden KI-en skrev, godt nok til å rette en feil i den selv?
- Kjører testene mot fasiten, og hva gjør vi når en test feiler: endrer vi koden eller fasiten, og hvorfor?
- Kan appen fortsatt startes i demomodus etter siste endring?

**Fase 8 — Avslutning**
- Kan en person utenfor gruppen starte appen etter README uten hjelp (SM-3)?
- Ligger det nøkler, ekte persondata eller rot i repoet?
- Hva ville vi gjort annerledes, og står det i retrospektiven?

## 5. Faste rutiner

| Rutine | Når | Hva |
|---|---|---|
| Ukesmøte | Én gang i uken, 30 min | Hver av oss svarer på: Hva ble ferdig? Hva står fast? Hva gjør jeg neste uke? Så går vi gjennom `issues.md` hos begge og bestemmer hva som lukkes. |
| Start av økt | Hver økt | `git pull`, og les egen og den andres siste logg i `.logs/`. |
| Slutt på økt | Hver økt | Sesjonsloggen (`sesjonslogg`-skillen), deretter push. |
| Kodegjennomgang | Før hver story regnes som ferdig | Den som *ikke* bygde storyen, leser endringene og kjører `bmad-code-review`. |
| Fasesjekk | Ved slutten av hver fase | Gå gjennom spørsmålene i §4 og kolonnen «Ferdig når» i §3. |

## 6. Arbeidsdeling

Forslag, som bekreftes på første ukesmøte:

- **Hovedansvar** for hver fase deles mellom oss, men begge leser og godkjenner resultatet.
- Fase 2 (arkitektur) og fase 3 (testsett) kan deles, med én på hver, fordi de ikke avhenger av hverandre.
- Under byggingen tar vi stories annenhver gang, så begge kjenner hele kodebasen. Ingen av oss eier en del av koden alene.

| Fase | Hovedansvar | Leser og godkjenner |
|---|---|---|
| 0 Lukke PRD-en | [fyll inn] | [fyll inn] |
| 1 UX | [fyll inn] | [fyll inn] |
| 2 Arkitektur | [fyll inn] | [fyll inn] |
| 3 Testsett | [fyll inn] | [fyll inn] |
| 4 Epics og stories | [fyll inn] | [fyll inn] |
| 8 Avslutning | [fyll inn] | [fyll inn] |

## 7. Sjekkliste for å kontrollere KI-ens arbeid

Før vi godtar et dokument eller en endring fra KI-en:

- [ ] Jeg har lest alt, ikke bare oppsummeringen.
- [ ] Endringen gjør det storyen eller oppgaven ba om, og ikke mer.
- [ ] Det finnes en test, og den feiler uten endringen.
- [ ] Testene mot testsettet går fortsatt grønt.
- [ ] Ingen nøkler, ekte persondata eller CV-tekst havner i kode, logger eller Git.
- [ ] Jeg kan forklare endringen for den andre i gruppen.

## 8. Varseltegn og hva vi gjør da

| Varseltegn | Tiltak |
|---|---|
| En fase tar mer enn dobbelt så lang tid som planlagt | Ta det opp på ukesmøtet, og kutt eller forenkle før vi går videre. |
| Testene mot fasiten feiler gjentatte ganger (SM-1) | Se først på formen på nøkkelordene og promptmalen (FR-4), deretter på synonymlisten. Fasiten endres ikke for å få testene grønne (SM-C2). |
| Bare én av oss forstår en del av koden | Den andre tar neste story i den delen. |
| Demomodus slutter å virke | Rettes før noe annet. Uten demomodus kan ikke sensor kjøre appen. |
| Trinn 1 er ikke ferdig halvveis i byggeperioden | Trinn 3 flyttes ut av omfang, og det dokumenteres i PRD-en. |

## 9. Egenvurdering mot kriteriene i mappen

Vi fyller ut tabellen ved slutten av fase 4 og fase 8, og bruker den til å se hvor vi bør legge innsatsen.

| Kriterium (vekt) | Hva sensor ser etter | Vår status | Tiltak |
|---|---|---|---|
| 1 Prosess og KI-styring (30 %) | En sporbar vei fra brief til kode, og dokumenterte beslutninger | | |
| 2 Funksjonalitet og omfang (20 %) | En ferdig og stabil kjerneflyt | | |
| 3 Kvalitetssikring og testing (15 %) | Tester mot fasit og målbare kriterier | | |
| 4 Design og brukeropplevelse (10 %) | En resultatside som forklarer treff og mangler | | |
| 5 Kodekvalitet og arkitektur (10 %) | Begrunnede valg, ikke mer komplekst enn nødvendig | | |
| 6 README og kjørbarhet (10 %) | Kan kjøres lokalt uten våre nøkler | | |
| 7 Ryddighet i repoet (5 %) | Nøkler utenfor Git, kun fiktive testdata | | |

## 10. Første steg

1. Finne fristene i semesteret og fylle inn kolonnen «Frist» i §3.
2. Avtale fast tidspunkt for ukesmøtet og fylle inn arbeidsdelingen i §6.
3. Gå gjennom antakelsene i PRD-ens §12 og forslag 5–14 sammen (fase 0).
