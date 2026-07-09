# Mobil-hub — alle prosjekter på telefon

Én hjemskjerm-side med snarveier til **Privatlærer**, **NDT Portalen** og **Galleri Uthuset**, pluss utviklingsverktøy.

## På Android nå

1. Åpne i Chrome:
   **https://polite-coast-08bc95303.7.azurestaticapps.net/prosjekter/**
2. **⋮** → **Legg til på startskjermen**
3. Trykk ikonet **Mine prosjekter**

## Prosjektene

| Prosjekt | Mappe | App / URL | GitHub |
|----------|-------|-----------|--------|
| **Privatlærer** | `C:\Users\Johnn\Projects\privatlaerer` | [Azure](https://polite-coast-08bc95303.7.azurestaticapps.net) | (lokalt) |
| **NDT Portalen** | `OneDrive\...\NDT Portalen V.0` | [portal.ndtoginsp.no](https://portal.ndtoginsp.no) | [NDT-Portal-v1](https://github.com/jekehaug-web/NDT-Portal-v1) |
| **Galleri Uthuset** | `OneDrive\...\Galleri_Uthuset` | Streamlit Cloud *(se under)* | [Galleri-Uthuset](https://github.com/jekehaug-web/Galleri-Uthuset) |

## Jobbe videre fra telefon

| Oppgave | Løsning |
|---------|---------|
| Kode / fikse bugs | [cursor.com/agents](https://cursor.com/agents) — velg repo (NDT, Galleri, …) |
| Se kode / PR | GitHub-app eller nettleser |
| Teste Privatlærer | Azure-lenken (oppdateres med `npm run deploy:azure` på PC) |
| Teste NDT | portal.ndtoginsp.no (deploy fra PC med ACA-skript) |
| Synk mellom PC-er | **Git push/pull** — ikke stol bare på OneDrive for NDT/Galleri |

## Per prosjekt

### Privatlærer
```bash
cd C:\Users\Johnn\Projects\privatlaerer
npm run deploy:azure
```
Guide: `docs/MOBIL-ANDROID.md`

### NDT Portalen
```powershell
cd "C:\Users\Johnn\OneDrive\Documents\Utviklingsprosjekter\NDT Portalen V.0"
git pull origin main
.\scripts\azure\deploy-aca-staging.ps1
```
Guide: `docs/MOBIL.md` · Multi-PC: `MULTI-PC-ARBEID.md`

### Galleri Uthuset
Streamlit-app — publiser på [share.streamlit.io](https://share.streamlit.io) koblet til `jekehaug-web/Galleri-Uthuset`.

1. Koble GitHub-repo
2. Sett Streamlit Secrets (Google service account)
3. Oppdater Galleri-URL i `mobil-hub/index.html` og kjør deploy (under)

## Oppdatere launcher-siden

Kilden ligger i `C:\Users\Johnn\Projects\mobil-hub\index.html`.

Kopieres til Privatlærer ved deploy:
```bash
cd C:\Users\Johnn\Projects\privatlaerer
npm run sync:hub
npm run deploy:azure
```

Da blir hubben tilgjengelig på `/prosjekter/` på samme Azure-adresse som Privatlærer.

## Galleri — Streamlit URL

Standard i hubben: `https://galleri-uthuset.streamlit.app/`

Hvis appen har annet navn på Streamlit Cloud, endre `href` på `#galleri-link` i `index.html`.
