# Kartlegging av datatyper og lagring

## 1. Datatyper som skal lagres

### Person
- Intern ID
- Fornavn
- Etternavn
- Fødselsdato eller fødselsår
- Valgfritt bilde (kun hvis aktivert)

### Utestengelse
- Utestengelses-ID
- Tilknyttet person-ID
- Opprettet av (bruker-ID + venue-ID)
- Type omfang (én, flere, alle venues, eksternt nettverk)
- Periode (fra-dato, til-dato eller "inntil videre")
- Årsakskategori
- Kommentar (begrenset fritekst)
- Status (aktiv, midlertidig, avsluttet, slettet/anonymisert)
- Automatisk review-dato

### Hendelse
- Hendelses-ID
- Person-ID
- Utestengelses-ID (kan være null)
- Dato og klokkeslett
- Venue
- Registrert av (bruker-ID)
- Type hendelse
- Kort beskrivelse

### Kunde
- Juridisk navn
- Org.nr
- Fakturaadresse og kontaktperson
- E-post for personvernkontakt
- Innstillinger (varighet, lagringstid, nettverksdeltakelse)

### Venue
- Navn
- Adresse og by
- Type
- Tidsrom for normal drift
- Tilknyttet juridisk enhet
- Innstillinger for deling/adopsjon av utestengelser

### Roller/brukere
- Bruker-ID
- Rolle
- Tilgangsnivå
- Logg

---

## 2. Lagring, deling og sletting

- Data lagres kryptert i database.
- Deling av data kun innenfor avtalt nettverk og med logging.
- Automatisk sletting/anonymisering etter innstilt lagringstid.
- Sletting/anonymisering varsles før frist.
- Personopplysninger eksporteres ved innsynsbegjæring.
- Fritekstfelt har advarsel mot sensitive opplysninger.

---

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
