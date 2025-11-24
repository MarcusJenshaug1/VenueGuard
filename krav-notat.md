# Juridiske og tekniske krav for "Utestengt"

## 1. Relevante lover og krav

### GDPR (Personvernforordningen)
- Behandlingsgrunnlag må dokumenteres for alle personopplysninger.
- Dataminimering: Kun nødvendige data skal lagres (navn, fødselsdato/år, bilde kun hvis aktivert).
- Rett til innsyn, retting og sletting for registrerte personer.
- Sikker lagring og overføring av data (kryptering, tilgangsstyring).
- Databehandleravtale mellom systemeier og kunde.
- Automatisk sletting/anonymisering etter utløp av lagringstid.

### Diskrimineringslovgivning
- Systemet skal ikke lagre eller behandle sensitive opplysninger (etnisitet, religion, legning, helse).
- Fritekstfelt skal ha advarsel mot å registrere sensitive eller diskriminerende opplysninger.
- Kunde er ansvarlig for lovligheten av utestengelser og innhold.

### Sikkerhetskrav
- All trafikk over HTTPS.
- Kryptering av data "at rest" i databasen.
- Passordlagring med moderne hashing.
- Tofaktorautentisering for administratorer.
- Rollebasert tilgangsstyring.
- Sikkerhetslogg for innlogginger, endringer, sletting og søk.
- Serverplassering i EØS (helst Norge/Norden).

---

## 2. Roller og ansvar
- Systemeier: Databehandler, ansvar for drift og sikkerhet.
- Kunde: Behandlingsansvarlig, ansvar for innhold og lovlighet.
- Brukere: Operativ bruk, ansvar for korrekt registrering.

---

## 3. Datatyper og lagring
- Person: Intern ID, navn, fødselsdato/år, bilde (valgfritt).
- Utestengelse: ID, person-ID, opprettet av, omfang, periode, årsakskategori, kommentar, status.
- Hendelse: ID, person-ID, utestengelse-ID, dato/tid, venue, registrert av, type hendelse, beskrivelse.
- Kunde/Venue: Juridisk navn, org.nr, kontaktinfo, innstillinger.
- Roller/brukere: Tilgangsnivå, logg.

- Automatisk sletting/anonymisering etter innstilt lagringstid.
- Deling av data kun innenfor avtalt nettverk og med logging.

---

## 4. Personvernmekanismer
- Modul for innsyn, retting og sletting.
- Eksport av personopplysninger ved innsynsbegjæring.
- Markering av tvistede saker.
- Advarselstekst ved fritekstfelt.

---

## 5. Oppsummering
Dette dokumentet oppsummerer de viktigste juridiske og tekniske kravene for utvikling av "Utestengt". Dokumentet bør oppdateres fortløpende ved endringer i lovverk eller systemdesign.

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
