# Daily Cockpit

Apple-like DailyTasks-Dashboard (Single-File, `index.html`).

- **Persistenz:** localStorage pro Gerät (sofort bei jeder Änderung) + 7-Tage-Snapshots + JSON-Export
- **Multi-Device-Sync (optional):** Supabase — Setup-Tab in der App enthält Anleitung + SQL
- **Hosting:** GitHub Pages (Settings → Pages → Branch `main` → root)

## Deployment

```
git push origin main
```

Danach unter Settings → Pages den Branch `main` (root) aktivieren.
Die App ist dann unter `https://eskoiv-crypto.github.io/Daily-Tasks/` erreichbar —
auf dem iPhone: Teilen → „Zum Home-Bildschirm" für Standalone-Look.

⚠️ Auf einem kostenlosen GitHub-Konto ist Pages nur bei **öffentlichen** Repos verfügbar.
Die App enthält keine Daten (die liegen in localStorage/Supabase), aber die
Routine-Namen im Seed sind sichtbar.
