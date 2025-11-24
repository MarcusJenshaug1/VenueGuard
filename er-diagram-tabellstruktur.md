# ER-diagram og tabellstruktur for "Utestengt"

## ER-diagram (tekstlig beskrivelse)

- **Kunde** (customer)
  - id (PK)
  - juridisk_navn
  - org_nr
  - kontaktperson
  - epost_personvern
  - innstillinger

- **Venue**
  - id (PK)
  - navn
  - adresse
  - by
  - type
  - driftstid
  - customer_id (FK)
  - innstillinger

- **Person**
  - id (PK)
  - fornavn
  - etternavn
  - fodselsdato_eller_aar
  - bilde_url

- **Utestengelse** (ban)
  - id (PK)
  - person_id (FK)
  - opprettet_av_user_id (FK)
  - opprettet_av_venue_id (FK)
  - omfang_type
  - periode_fra
  - periode_til
  - arsakskategori
  - kommentar
  - status
  - review_dato

- **Hendelse** (event)
  - id (PK)
  - person_id (FK)
  - ban_id (FK, nullable)
  - dato_tid
  - venue_id (FK)
  - registrert_av_user_id (FK)
  - type
  - beskrivelse

- **Bruker** (user)
  - id (PK)
  - navn
  - epost
  - rolle
  - venue_id (FK, nullable)
  - customer_id (FK)
  - passord_hash
  - 2fa_secret

- **Revisjonslogg** (audit_log)
  - id (PK)
  - user_id (FK)
  - action
  - target_type
  - target_id
  - timestamp
  - details

## Relasjoner
- Kunde har mange venues og brukere.
- Venue tilhører én kunde, har mange brukere, personer, utestengelser og hendelser.
- Person kan ha mange utestengelser og hendelser.
- Utestengelse tilhører én person, opprettes av én bruker og én venue.
- Hendelse tilhører én person, kan være knyttet til én utestengelse, opprettes av én bruker og én venue.
- Bruker tilhører én kunde, kan være tilknyttet én venue.
- Revisjonslogg knyttes til bruker og handling.

---

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
