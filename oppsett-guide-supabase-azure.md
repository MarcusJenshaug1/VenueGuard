# Steg-for-steg guide: Oppsett med Supabase, Azure Static Web Apps og App Service

## 1. Opprett Supabase-prosjekt og database
1. Gå til https://supabase.com og opprett en gratis konto.
2. Opprett et nytt prosjekt.
3. Velg region (helst Europa/Norden for personvern).
4. Noter database-URL, API-nøkkel og annen tilkoblingsinfo.
5. Opprett tabeller i Supabase etter datamodellen (bruk SQL eller Supabase GUI).

## 2. Opprett backend med Node.js/Express på Azure App Service
1. Initialiser et nytt Node.js-prosjekt (`npm init`).
2. Installer nødvendige pakker:
   - `express` (webserver)
   - `@supabase/supabase-js` (Supabase-klient)
3. Lag API-endepunkter for CRUD mot Supabase.
4. Test lokalt.
5. Push koden til GitHub.
6. Opprett gratis App Service i Azure Portal.
7. Koble App Service til GitHub-repo for automatisk deploy.
8. Legg inn Supabase-URL og API-nøkkel som miljøvariabler i App Service.

## 3. Opprett frontend med React på Azure Static Web Apps
1. Initialiser et nytt React-prosjekt (`npx create-react-app`).
2. Installer Supabase-klient (`npm install @supabase/supabase-js`).
3. Konfigurer Supabase i frontend (bruk miljøvariabler for URL og nøkkel).
4. Lag innloggingsside med Supabase Auth.
5. Lag sider for visning og administrasjon av data.
6. Push koden til GitHub.
7. Opprett gratis Static Web App i Azure Portal.
8. Koble Static Web App til GitHub-repo for automatisk deploy.
9. Legg inn Supabase-URL og API-nøkkel som miljøvariabler i Static Web App.

## 4. Testing og drift
1. Test at frontend og backend kommuniserer med Supabase.
2. Sjekk at autentisering og tilgangsstyring fungerer.
3. Sjekk at data lagres og hentes korrekt.
4. Overvåk og administrer via Supabase og Azure Portal.

---

## Nyttige lenker
- Supabase docs: https://supabase.com/docs
- Azure Static Web Apps docs: https://learn.microsoft.com/en-us/azure/static-web-apps/
- Azure App Service docs: https://learn.microsoft.com/en-us/azure/app-service/

Dato: 24.11.2025
Ansvarlig: Marcus Jenshaug
