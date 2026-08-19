# Daily Cockpit · v1.0

Apple-like Tages-Dashboard als Single-File-PWA — Aufgaben, Termine, Mail-Feed,
Multi-Device-Sync. Live: `https://eskoiv-crypto.github.io/Daily-Tasks/`

## Features

- **Heute**: Activity-Ring, Tages-Kennzahlen, Termin-Leiste, Aufgaben
  (Überfällig → Anstehend → Erledigt), QuickAdd mit Zeit-Parsing
  (`14:00 Odoo Lots prüfen`) und automatischer Kategorie-Erkennung
- **Feed**: Chronik der Mail-Quintessenzen und Infos (füllt der Triage-Agent),
  mit Deeplinks zur Original-Mail
- **Woche**: 7-Tage-Balken, Ø-Quote, beste Serie, 12-Wochen-Heatmap
- **Routinen**: wiederkehrende Aufgaben je Wochentag, pausierbar
- **Links**: Schnellzugriff-Kacheln (frei belegbar)
- **Setup**: Sync, Benachrichtigungen, Theme, Export/Import, 7-Tage-Snapshots

## Architektur

- **Persistenz**: localStorage, synchron bei jeder Änderung + Auto-Snapshots
- **Sync**: Supabase-Raum (Room-ID, Revision + Compare-and-Swap, Poll 8 s,
  Hintergrund-Tabs 1×/min). Status-Pille zeigt ehrlich „Lokal", bis verbunden.
  Einrichtung pro Gerät: Setup → Zugangsdaten (oder 1-Tap aus Zwischenablage).
  Zugangsdaten stehen bewusst NICHT im Code (Repo ist public).
- **PWA**: Service Worker (network-first, offline-Fallback), Manifest, Icons —
  am iPhone „Zum Home-Bildschirm" für App-Look + Funkloch-Betrieb
- **Agent-Integration**: Ein lokaler Claude-Scheduled-Task trianguliert das
  Outlook-Postfach alle 15 Min, schreibt Aufgaben/Feed/Termin-Leiste/Heartbeat
  in den Sync-Raum und pusht bei Handlungsbedarf. Die App zeigt den
  Agent-Status als Pille (grün = lebt, rot = still → PC prüfen).

## Deployment

```
git push origin main
```
GitHub Pages liefert automatisch aus (Branch `main`, root). Bei App-Änderungen
den Cache-Namen in `sw.js` hochzählen (cockpit-vN), damit Clients das Update
melden.
