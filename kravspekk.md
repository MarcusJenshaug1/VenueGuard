# 1. Formål og omfang

**Formål:**
Systemet skal gjøre det mulig for utesteder i Norge å:

* Registrere og administrere utestengte gjester
* Dokumentere hendelser som grunnlag for utestengelse
* Dele utestengelser mellom venues innenfor samme juridiske enhet og/eller et frivillig samarbeidsnettverk
* Gjennomføre dette i tråd med GDPR og norsk diskrimineringslovgivning, så langt det teknisk lar seg gjøre

**Målgruppe:**

* Nattklubber, barer, konsertsteder, arrangementssteder
* Vaktledere, dørvakter, driftsledere, eiere
* Eventuelle kjeder/grupperinger som har flere venues

---

# 2. Rolle- og rettighetsmodell

## 2.1 Systemroller

1. **Systemeier (deg / driftsselskap)**

   * Eier og hoster plattformen
   * Er databehandler for hvert utested
   * Har kun tilgang til:

     * systemkonfigurasjon
     * tekniske logger
     * aggregerte, anonymiserte data (ikke personidentifiserbare hendelser uten særskilt grunnlag)
   * Skal ikke bruke data til egne formål utover drift, sikkerhet og feilretting

2. **Kunde-eier (juridisk enhet / kjede)**

   * Typisk aksjeselskap som driver ett eller flere utesteder
   * Behandlingsansvarlig for personopplysninger i løsningen
   * Kan administrere:

     * egne venues
     * egne brukere
     * valg om deltakelse i samarbeidsnettverk

3. **Venue-administrator**

   * Knutepunkt mellom juridisk enhet og den konkrete venue
   * Kan:

     * opprette/endret venue-profiler
     * se og administrere utestengte gjester for sin venue
     * beslutte om utestengelser skal gjelde én, flere eller alle venues under samme eier (der det er avtalt)

4. **Vaktleder / driftsleder**

   * Kan:

     * opprette nye utestengelser
     * forlenge/korte ned utestengelsesperiode
     * se detaljerte hendelseslogger for egen venue og eventuelt delte saker (der tillatt)

5. **Dørvakt / operativ bruker**

   * Kan:

     * søke opp personer
     * se “trafikklys”-visning (utestengt/ikke utestengt + kort kategori + periode)
     * registrere enkel hendelseslogg (standardisert, begrenset fritekst)

6. **Revisor / juridisk kontakt (valgfri rolle per kunde)**

   * Lesetilgang til:

     * revisjonslogger
     * eksport av personopplysninger ved innsynsbegjæring

---

# 3. Kunde- og venue-struktur

## 3.1 Kunde (juridisk enhet)

Obligatoriske felter:

* Juridisk navn
* Org.nr
* Fakturaadresse og kontaktperson
* E-post for personvernkontakt
* Rolle: behandlingsansvarlig

Innstillinger per kunde:

* Standard varighet for utestengelser (eks. 3, 6, 12 måneder)
* Maksimal lagringstid før automatisk sletting/anonymisering
* Deltakelse i:

  * interne nettverk (alle egne venues)
  * eksterne samarbeidsnettverk (lokale bar-/utelivssamarbeid)

## 3.2 Venue

Hver venue er en “underenhet”.

Felter:

* Navn på venue
* Adresse og by
* Type (bar, nattklubb, konsertscene osv.)
* Tidsrom for normal drift (kan brukes til rapportering)
* Tilknyttet juridisk enhet (kunde-id)

Innstillinger per venue:

* Om venue skal:

  * bare bruke egne utestengelser
  * automatisk adoptere utestengelser fra andre venues under samme eier
  * delta i ett eller flere lokale samarbeidsnettverk (se kapittel 6)

---

# 4. Håndtering av utestengte gjester

## 4.1 Datamodell – minimumsdata

For personlig registrering (person-tabell):

* Intern ID
* Fornavn
* Etternavn
* Fødselsdato eller fødselsår (avklares med jurist ift. nødvendighet)
* Valgfritt bilde (kun hvis kunden aktivt skrur på denne funksjonen)

Dataminimering:

* Ingen felter for etnisitet, religion, legning, helse osv.
* Ingen opplasting av dokumenter med slike opplysninger

## 4.2 Utestengelse (suspension-objekt)

Felter:

* Utestengelses-ID
* Tilknyttet person-ID
* Opprettet av (bruker-ID + venue-ID)
* Type omfang:

  * Kun én venue
  * Alle venues under samme juridiske enhet
  * Utvalgte venues under samme juridiske enhet (flervalg)
  * Deling i eksternt samarbeidsnettverk (kun hvis aktivt valgt og avtale foreligger)
* Periode:

  * Fra-dato (obligatorisk)
  * Til-dato (obligatorisk), eller «inntil videre» med systempålagt maksgrense (eks. 2 år)
* Årsakskategori (nedtrekksliste, obligatorisk):

  * Vold/trusler
  * Seksuell trakassering
  * Skadeverk
  * Grov ordensforstyrrelse
  * Nektet å forlate lokalet etter gjentatte beskjeder
  * Annet (kan deaktiveres i innstillinger; hvis aktiv: krever kort faktabasert begrunnelse)
* Kommentar (begrenset fritekstfelt, maks X tegn, med tydelig advarsel om hva som IKKE skal skrives)
* Status:

  * Aktiv
  * Midlertidig suspendert
  * Avsluttet
  * Slettet/anonymisert

For hvert objekt:

* Automatisk “review-dato” (før utløp) for vurdering av videre lagring

## 4.3 Hendelseslogg

Egen tabell for hendelser knyttet til en person og/eller utestengelse:

* Hendelses-ID
* Person-ID
* Utestengelses-ID (kan være null hvis det er første hendelse)
* Dato og klokkeslett
* Venue
* Registrert av (bruker-ID)
* Type hendelse:

  * Avvist i døren
  * Forsøkte å komme inn til tross for utestengelse
  * Ny uønsket adferd
* Kort beskrivelse (maks X tegn, tydelig advarselstekst)

Tilgang:

* Full logg: vaktleder og administrator
* Begrenset visning: dørvakt (kun siste X hendelser og/eller oppsummert status)

---

# 5. Søk og visning ved døren

## 5.1 Søkefunksjon

Søk skal kunne gjøres på:

* Navn
* Fødselsdato/år
* Kombinasjon navn + år

Det skal være mulig å konfigurere:

* Om det er lov å ta bilde ved inngang (f.eks. i stridssituasjoner) – dette må vurderes nøye juridisk
* Hvor lenge slike bilder eventuelt kan lagres

## 5.2 Resultatvisning (“trafikklys”)

For operativ bruker (dørvakt):

* Grønn: Ikke utestengt i relevante venues
* Gul: Utestengelse som er avsluttet siste X måneder (kun hvis kunden skrur på)
* Rød: Aktiv utestengelse

Ved rød status:

* Vis:

  * Hvilke venues utestengelsen gjelder
  * Gyldighetsperiode
  * Kort årsakskategori (ikke detaljert fritekst)
* Ikke vis:

  * Full loggtekst
  * Interne notater uten relevans ved inngangskontroll

---

# 6. Samarbeid mellom venues

## 6.1 Internt samarbeid (samme juridiske enhet)

Funksjoner:

* Ved opprettelse av utestengelse:

  * Valg: “Gjelder”:

    * Kun denne venue
    * Alle venues under [kundenavn]
    * Valgte venues (checkbox-liste)

* Standardinnstilling kan settes av kunde-eier:

  * f.eks. “Som standard gjelder utestengelser alle venues i kjeden”

Systemkrav:

* Utestengelsesobjekt må kunne ha flere tilknyttede venues
* Søk ved døren skal ta hensyn til:

  * hvilke venues brukeren tilhører
  * om det finnes relevante utestengelser

## 6.2 Eksternt samarbeid (lokale bar-/utelivssamarbeid)

Dette er juridisk sensitivt og bør kun implementeres dersom:

* det foreligger:

  * skriftlig avtale mellom alle deltakende juridiske enheter
  * avklart behandlingsansvar (sannsynligvis felles behandlingsansvar)
  * gjennomført DPIA

Teknisk modell:

* Opprett “Samarbeidsnettverk”:

  * Navn (f.eks. “Sentrum Utelivsnatt [By]”)
  * Geografisk område
  * Liste over tilknyttede venues
* Ved opprettelse av utestengelse kan vaktleder:

  * hake av: “Del i nettverk [navn]”

Delte data til andre venues i nettverket:

* Personens navn
* Eventuelt bilde
* Årsakskategori
* Periode
* Opprettende venue-navn (ikke detaljerte loggtekster)

Systemet skal:

* Logge alle oppslag på nettverksdata (hvem, hva, når, hvorfra)
* Ha egne innstillinger for:

  * hvilke roller som kan se nettverksdata
  * om dørvakter ser detaljer eller kun “utestengt via nettverk”

---

# 7. Personvern og sikkerhet

## 7.1 Teknisk sikkerhet

* All trafikk over HTTPS
* Kryptering av data “at rest” i databasen
* Servere i EØS (helst Norge/Norden)
* Passordlagring med moderne hashing
* Tofaktorautentisering som standard for alle admin-lag
* Rollebasert tilgangsstyring
* Sikkerhetslogg for:

  * innlogginger
  * opprettelse og endring av utestengelser
  * sletting/anonymisering
  * søk på personer

## 7.2 Personvernhjelp inne i systemet

Innbygde funksjoner:

* Generering av:

  * databehandleravtale-mal
  * personvernerklærings-mal for kunden
* Modul for innsyn:

  * søk på person
  * eksport av alle registrerte opplysninger i standard format (PDF + JSON/CSV)
* Modul for retting/sletting/innvending:

  * markere en utestengelse/person som “tvistet”
  * logge vurdering og beslutning

## 7.3 Sletting og anonymisering

Innstillinger per kunde:

* Maksimal varighet for:

  * aktiv utestengelse
  * lagring av historikk etter utløp
* Automatisk jobb (cron/worker) som:

  * varsler før slettedato
  * anonymiserer eller sletter poster etter frist

---

# 8. Logging, revisjon og rapportering

Systemet skal støtte:

* Revisjonslogg per kunde:

  * endringer av utestengelser
  * hvem som har sett hva (ved detaljert visning)
* Eksport av:

  * anonymisert statistikk (antall utestengelser, årsakskategorier osv.)
* Mulighet for systemeier til å:

  * avdekke misbruk (uvanlig høyt antall søk, søk uten tilknytning til driftstid osv.)
  * sperre brukere eller kunder ved åpenbart misbruk

---

# 9. Ansvarsfraskrivelse og vilkår

Du kan ikke “friskrive” deg helt fra alt ansvar, men du kan:

* definere tydelig rollefordeling
* begrense ansvar for innhold som kundene legger inn
* kreve at kundene følger loven
* forbeholde deg retten til å stenge kontoer ved misbruk

Dette må inn i:

* Plattformsavtale / Tjenestevilkår
* Databehandleravtale

Et grovt utkast til struktur (formuleringen bør en advokat finpusse):

1. **Rollefordeling**

   * Kunden er behandlingsansvarlig for all persondata som registreres i løsningen.
   * Systemeier er databehandler og behandler data kun etter kundens dokumenterte instruks.

2. **Kundens ansvar**

   * Kunden er alene ansvarlig for:

     * lovligheten av grunnlaget for utestengelser
     * innholdet som registreres i systemet, inkludert fritekst
     * informasjon til gjester om bruk av systemet
   * Kunden forplikter seg til å:

     * ikke registrere sensitive opplysninger (etnisitet, religion osv.)
     * ikke bruke systemet på en måte som er diskriminerende eller ulovlig

3. **Systemeiers ansvar**

   * Systemeier er ansvarlig for:

     * teknisk drift, sikkerhet og tilgjengelighet innenfor avtalte SLA-nivåer
     * å implementere beskrevne tekniske og organisatoriske tiltak for informasjonssikkerhet
   * Systemeier har ikke ansvar for:

     * kundens vurderinger av hvem som utestenges
     * konsekvenser av feilaktige eller ulovlige registreringer gjort av kunden

4. **Skadesløsholdelse**

   * Kunden plikter å holde systemeier skadesløs for krav fra tredjepart som følge av:

     * kundens brudd på personvernregelverket
     * kundens brudd på diskrimineringslovgivningen
     * kundens registrering av uriktige eller ærekrenkende opplysninger

5. **Rett til å gripe inn**

   * Systemeier har rett, men ikke plikt, til å:

     * stanse eller begrense kundens tilgang ved mistanke om grovt misbruk eller ulovlig bruk
     * slette eller sperre enkeltregistreringer ved klare brudd på vilkår eller lov

6. **Ansvarsbegrensning**

   * Avtalt ansvarsbegrensning for direkte økonomisk tap opp til et visst beløp per år
   * Ingen ansvar for indirekte tap (tap av omdømme, forventet fortjeneste osv.), med unntak for tilfeller der ufravikelig lovgivning sier noe annet

---

# 10. Admin-grensesnitt for systemeier

Systemeier skal ha et eget panel hvor man kan:

* Se oversikt over kunder og venues
* Se teknisk status (drift, logger, køer)
* Se anonymisert statistikk (antall kunder, antall aktive utestengelser osv.)
* Håndtere:

  * sperring av kunder
  * sletting/avslutning av kundeforhold (med kontrollert nedstenging og sletting)
* Tilgang til:

  * revisjonslogg for å ettergå alvorlige klager / henvendelser fra Datatilsynet