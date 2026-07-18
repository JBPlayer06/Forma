<p align="center">
  <img src="formalogo.png" width="110" alt="Forma Logo">
</p>

<h1 align="center">Forma</h1>

<p align="center">
  Wochenplan, Trainings und Fortschritt – eine Übersicht über alle Sport-Apps.<br>
  Dunkles Apple-Fitness-Design · komplett offline · keine Server, keine Accounts.
</p>

---

## Was ist Forma?

Forma ist eine persönliche Fitness-Web-App im Look von Apple Fitness. Sie führt die
Trainingsplanung an einem Ort zusammen:

- **Heute** – die Tages-Kachel mit Training, Aktivitätsringen, Abhaken (Haken/X),
  zusätzlichem Training übers Rad und Direktsprung in die Übungs-Bibliothek.
- **Woche** – alle 7 Tage im Überblick. Trainings lassen sich per **Drag & Drop**
  verschieben: Mitte einer Kachel = stapeln (weisser Rahmen), zwischen zwei
  Kacheln = einfügen (weisser Strich). Rückgängig über die Undo-Leiste.
- **Fortschritt** – Wochenfortschritt pro Kategorie als Apple-Ringe oder
  Balkendiagramm, mit Batterie-Segmenten in der Ring-Ansicht.

Dazu: Wahltage mit Pflicht-Erinnerung, automatischer Tages-/Wochenwechsel (auch
ohne App-Neustart), Plan-Editor mit Kraft-/Cardio-Phasen und Perioden,
Übungs-Bibliothek mit eigenen Einträgen, helles/dunkles Design.

**Alle Daten bleiben auf dem Gerät** (localStorage). Die App lädt nichts nach und
sendet nichts – eine einzige HTML-Datei ohne Abhängigkeiten.

## Auf dem iPhone installieren

1. GitHub Pages für dieses Repo aktivieren (Settings → Pages → Branch `main`, Ordner `/root`).
2. Die Pages-URL in **Safari** öffnen (sie zeigt direkt die App).
3. **Teilen → Zum Home-Bildschirm**. Das Forma-Logo erscheint als App-Icon,
   die App startet im Vollbild ohne Browser-Leiste.

Die Trainings-Buttons in der Topbar (Health, Fitness, Bevel, NTC) öffnen die
jeweiligen Apps über Apple-Kurzbefehle (`shortcuts://`) – dafür muss auf dem
iPhone je ein gleichnamiger Kurzbefehl existieren.

## Aufbau des Repos

| Pfad | Inhalt |
|---|---|
| `index.html` | Die komplette App (HTML + CSS + JS, self-contained) |
| `appletouchicon.png`, `favicon16/32.png`, `icon192/512.png`, `formalogo.png` | App-Icons aus dem Forma-Logo (Pfeile «Wachsend», Runde 3 Variante 3.4), flach im Root |
| `manifest.webmanifest` | PWA-Manifest (Name, Icons, Standalone-Modus) |
| `design/` | Design-Unterlagen aus Claude Design |
| `design/forma-phone.dc.html` | Desktop-Vorschau der App im iPhone-Rahmen |
| `design/forma-logos.dc.html` | Logo-Entwürfe (Runde 1) |
| `design/kachel-umrandungen.dc.html` | 30 Alternativen zu den Aktivitätsringen |
| `design/farbabgleich.dc.html` | Farbabgleich mit dem Apple-Fitness-Screenshot |
| `design/chats/` | Design-Chatverlauf (Entscheidungen & Iterationen) |

Die `design/*.dc.html`-Seiten sind Prototyp-Ansichten aus dem Design-Werkzeug;
sie laden React über ein CDN und brauchen daher Internet. Die App selbst nicht.

## Entwicklung

Kein Build-Schritt. `index.html` direkt im Browser öffnen oder lokal serven:

```bash
python3 -m http.server 8000
# http://localhost:8000  – Handy-Vorschau mit iPhone-Schutzbereichen: ?frame=1
```

Gespeichert wird unter den localStorage-Schlüsseln `sportapp_v1_*`
(Plan, Woche, eigene Übungen, Einstellungen).
