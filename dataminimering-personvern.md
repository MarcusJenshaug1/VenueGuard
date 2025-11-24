# Dataminimering og personvernmekanismer i datamodellen

## Dataminimering
- Kun nødvendige personopplysninger lagres:
  - Fornavn, etternavn, fødselsdato/år, intern ID
  - Valgfritt bilde (kun hvis aktivert av kunde)
- Ingen lagring av sensitive opplysninger:
  - Etnisitet, religion, legning, helse, dokumenter med slike opplysninger
- Fritekstfelt har advarsel mot å registrere sensitive eller diskriminerende opplysninger
- Begrenset fritekstlengde for kommentarer og hendelser
- Automatisk sletting/anonymisering av data etter innstilt lagringstid
- Review-dato for vurdering av videre lagring før utløp

## Personvernmekanismer
- Rollebasert tilgangsstyring: Kun nødvendige roller har tilgang til persondata
- Modul for innsyn, retting og sletting:
  - Søk på person
  - Eksport av alle registrerte opplysninger (PDF, JSON/CSV)
  - Markering av tvistede saker
  - Logg av vurdering og beslutning
- Sikkerhetslogg for alle sensitive operasjoner
- Kryptering av data "at rest" og under overføring
- Tofaktorautentisering for administratorer
- Serverplassering i Norge/EØS
- Databehandleravtale mellom systemeier og kunde

---

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
