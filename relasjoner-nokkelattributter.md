# Relasjoner og nøkkelattributter for "Utestengt"

## Relasjoner mellom tabeller

- **Kunde (customer)**
  - Har mange venues og brukere.
  - PK: id

- **Venue**
  - Tilhører én kunde (customer_id FK).
  - Har mange brukere, personer, utestengelser og hendelser.
  - PK: id
  - FK: customer_id

- **Person**
  - Kan ha mange utestengelser og hendelser.
  - PK: id

- **Utestengelse (ban)**
  - Tilhører én person (person_id FK).
  - Opprettes av én bruker (opprettet_av_user_id FK) og én venue (opprettet_av_venue_id FK).
  - PK: id
  - FK: person_id, opprettet_av_user_id, opprettet_av_venue_id

- **Hendelse (event)**
  - Tilhører én person (person_id FK).
  - Kan være knyttet til én utestengelse (ban_id FK, nullable).
  - Opprettes av én bruker (registrert_av_user_id FK) og én venue (venue_id FK).
  - PK: id
  - FK: person_id, ban_id, registrert_av_user_id, venue_id

- **Bruker (user)**
  - Tilhører én kunde (customer_id FK), kan være tilknyttet én venue (venue_id FK, nullable).
  - PK: id
  - FK: customer_id, venue_id

- **Revisjonslogg (audit_log)**
  - Knyttes til bruker (user_id FK) og handling.
  - PK: id
  - FK: user_id

## Nøkkelattributter

- **customer.id**: Unik identifikator for kunde.
- **venue.id**: Unik identifikator for venue.
- **person.id**: Unik identifikator for person.
- **ban.id**: Unik identifikator for utestengelse.
- **event.id**: Unik identifikator for hendelse.
- **user.id**: Unik identifikator for bruker.
- **audit_log.id**: Unik identifikator for revisjonslogg.

- **customer.org_nr**: Organisasjonsnummer, identifiserer juridisk enhet.
- **venue.customer_id**: Kobler venue til kunde.
- **ban.person_id**: Kobler utestengelse til person.
- **event.person_id**: Kobler hendelse til person.
- **user.customer_id**: Kobler bruker til kunde.

---

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
