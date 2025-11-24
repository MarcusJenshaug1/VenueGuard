# Databasevalg for "Utestengt"

## Valgt database: PostgreSQL

### Begrunnelse
- **Relasjonell og robust**: PostgreSQL er en av de mest brukte og pålitelige relasjonsdatabasene.
- **Støtte for komplekse relasjoner**: Passer godt til systemer med mange tabeller og relasjoner (kunde, venue, person, utestengelse, hendelse, roller).
- **Sikkerhet**: God støtte for kryptering, tilgangsstyring og logging.
- **Skalerbarhet**: Kan håndtere store datamengder og mange samtidige brukere.
- **Dataintegritet**: ACID-kompatibel, sikrer konsistens og pålitelighet.
- **Støtte for automatisering**: Cron-jobber og automatisert sletting/anonymisering kan enkelt implementeres.
- **God integrasjon med Node.js/Express**: Mange ferdige ORM-løsninger (f.eks. Sequelize, TypeORM).

### Alternativer vurdert
- **MySQL**: Også robust, men PostgreSQL har bedre støtte for avanserte datatyper og relasjoner.
- **MongoDB**: Egnet for dokumentbaserte systemer, men mindre egnet for relasjonelle krav i dette prosjektet.

---

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
