# Systemarkitektur for "Utestengt"

## Oversikt over moduler
- **Autentisering og tilgangsstyring**: Håndterer innlogging, roller og 2FA.
- **Kunde- og venue-modul**: CRUD for kunder og venues, innstillinger og nettverksdeltakelse.
- **Person- og utestengelsesmodul**: CRUD for personer og utestengelser, status, review-dato.
- **Hendelseslogg**: Registrering og visning av hendelser, begrenset/full tilgang.
- **Søk og visning**: Søkefunksjon, trafikklys-visning, bildeopplasting.
- **Samarbeidsnettverk**: Deling av utestengelser, logging av oppslag.
- **Personvern og sikkerhet**: Eksport, innsyn, sletting/anonymisering.
- **Admin-grensesnitt**: Panel for systemeier, drift, statistikk, revisjon.

## API-struktur
- RESTful API med følgende hovedendepunkter:
  - /auth (innlogging, 2FA, roller)
  - /customers (kunder)
  - /venues (venues)
  - /persons (personer)
  - /bans (utestengelser)
  - /events (hendelser)
  - /search (søk)
  - /network (samarbeidsnettverk)
  - /admin (admin-funksjoner)

## Sikkerhetsmekanismer
- All trafikk over HTTPS
- Kryptering av data "at rest" og under overføring
- Passordlagring med moderne hashing
- Tofaktorautentisering for adminroller
- Rollebasert tilgangsstyring
- Sikkerhetslogg for alle sensitive operasjoner
- Automatisk sletting/anonymisering
- Serverplassering i Norge/EØS

---

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
