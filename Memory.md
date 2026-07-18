# Fitness-App V4 – Memory

> Projektgedächtnis für den Neubau der Fitness-Tracking-App (V4).
> Lese diese Datei am Sessionstart, bevor du irgendetwas anderes tust.

---

## Status

- **Version:** V4.0 (Neubau, Fresh Start)
- **Datum Start:** 2026-05-01
- **Vorgänger:** Fitness-App (V1–V3.0) – Backup unter `Projekte/Fitness-App/`
- **Ausgabe-Datei V4 (HTML-Single-File):** `trainingsplan-app-v4.html` im Projektordner
- **Neuaufbau «Forma» (Sport-App, seit 29.06.2026):** alle Dokumente im Unterordner `Forma/`

### Unterordner `Forma/` (Stand 17.07.2026)

| Datei | Inhalt |
|---|---|
| `index.html` | **aktuelle, finalisierte App** (Titel «Forma», auf GitHub Pages deployed). Löst `Forma_App_2026-07-07.html` als aktiven Stand ab |
| `manifest.webmanifest` | PWA-Manifest (Name, Icons, Standalone-Modus) |
| `appletouchicon.png`, `favicon16.png`, `favicon32.png`, `icon192.png`, `icon512.png`, `icon512maskable.png`, `formalogo.png` | App-Icons (**Pfeil-Logo «Wachsend», Runde 3 Variante 3.4**, seit 17.07.), flach im Ordner. Namen bewusst ohne Bindestrich (siehe Log 12.07.) |
| `README.md` | Repo-Beschreibung (Aufbau, iPhone-Installation) |
| `.nojekyll`, `.gitignore` | GitHub-Pages-Hilfsdateien (Punkt-Namen 12.07. korrigiert) |
| `Forma Logos.dc.html`, `Forma Phone.dc.html`, `Farbabgleich.dc.html` | Claude-Design-Vorschauen (nur im Design-Tool lauffähig, laden React via CDN) |
| `Forma_Icon-Entwuerfe_Runde2_2026-07-15.html` | 50 neue Icon-Entwürfe (Runde 2, ohne Personen/Strichmenschen), eigenständiges HTML, direkt im Browser lauffähig |
| `Forma_Icon-Pfeile_Runde3_2026-07-15.html` | Runde 3: 12 Varianten des gewählten Pfeil-Motivs (Entwurf 3 «Aufstieg»), eigenständiges HTML |
| `Forma_App_2026-07-07.html` | vorherige App-Version (überholt, auf JB-Wunsch behalten) |
| `Spec_Sport-App_Final_2026-07-04.md` | Finalspec, Grundlage des Baus |
| `Planner_Sport-App-Neuaufbau_2026-06-29.md` | Planner-Lauf, aus dem der Neuaufbau hervorging |
| `Sport-App_Stufe1-Demo_2026-07-04.html` | erste Stufe-1-Demo |
| `icons/` | Higgsfield-Icon-PNG (Bau-Quelle) |
| `bilder/` | 6 Fotos (App-Logos, Haken/X-Kacheln) als Bau-Vorlagen |

**Alt-Logo-Archiv:** `fitness-app-v2-files/Logo-Alt_Entwurf15/` (neben `Forma/`, bewusst ausserhalb des Repo-Spiegels) enthält seit 17.07. das komplette alte Logo-Set (Entwurf 15): die 7 alten Icon-PNGs als Kopie, `forma_icon_variante_15.png` und das ChatGPT-Quellbild (beide aus `Forma/` dorthin verschoben) sowie `index_vor-logo-tabbar-fix_2026-07-17.html` als Sicherung der index.html vor Logo-Wechsel und Tab-Bar-Fix.

---

## Design-Entscheidungen

### Farben / Theme
- Dark Mode Standard (pure black #000000), Light Mode optional via Einstellungen
- Folgt strikt dem Apple UI Design System (`KNOWLEDGE/ueber_mich_kb/Wiki/design-system-hub.md`)
- Intensitätszonen-Farben:
  - Leicht (1–3): `#30D158` (Grün)
  - Mässig (4–6): `#FF375F` (Magenta, wie Apple Fitness Move-Ring)
  - Schwer (7–8): `#FF9F0A` (Orange)
  - Sehr schwer (9–10): `#FF453A` (Rot)

### Layout
- Tab-Bar: 3 Tabs – Wochenplan | Kalender | Einstellungen
- Quick-Actions Icon-Leiste oben im Wochenplan: Health, Fitness, NTC, Bevel
- Fortschritts-Ring: 1 grüner Ring (nicht 3), zeigt X von 7
- Karten: Kompakt (Name, Variante, Dauer, Status)
- Intensitäts-Slider erscheint ERST nach Abhaken
- Vor dem Berühren: geplante Intensität als Referenz angezeigt
- Nach Berühren: tatsächliche Intensität, Toggle bei gleichem Wert

### Kalender
- Jahresansicht → Monatsansicht (Ringe) → Tagesdetail (Bottom Sheet)
- Ring-Segmente: proportional zur Intensität, stärkste oben, Uhrzeigersinn
- Ring-Dicke: wie Apple Watch Activity Ring

### Design-Critique (2026-06-15)
- **Lime Green `#B5E853`** ist als Farbe für Daten und aktive UI-Elemente bestätigt (analog Apple Exercise Ring). **Nicht** für dekorative Chrome-Elemente verwenden — dort war das Farb-System inkonsistent.
- **Select-Dropdown** ist nicht nativ (iOS-Look fehlt) → noch zu beheben.
- **Pentagon-Chart** bleibt bewusst so.
- Für Claude Design wurden zwei getrennte Prompts erstellt: einer nur für Farben, einer nur für Text.

---

## Trainings-Katalog

| Familie | Variante | Fixiert | Std-Dauer | Std-Intensität | HIIT-Regel |
|---|---|---|---|---|---|
| Laufen flach | 16 × 400 m | Ja | 60 min | 9 | Nein |
| Laufen flach | Frei | Nein | 60 min | 9 | Nein |
| Laufen Hügel | 8 × 800 m | Ja | 70 min | 10 | Nein |
| Laufen Hügel | Frei | Nein | 60 min | 9 | Nein |
| Indoor Bike | Schnell | Nein | 60 min | 8 | Nein |
| Indoor Bike | Locker | Nein | 90 min | 6 | Nein |
| Core & Stabilität | – | Nein | 20 min | 7 | Nein |
| Beweglichkeit | – | Nein | 20 min | 3 | Nein |
| Kraft | Mittel | Nein | 30 min | 7 | Nein |
| Kraft | Hart | Nein | 60 min | 10 | Nein |
| HIIT | – | Nein | 20 min | 7 | Ja |
| Schwimmen | – | Nein | 60 min | 10 | Nein |

HIIT-Regel: ≤10 min → 5 (Mässig), 11–20 min → 7 (Schwer), >20 min → 9 (Sehr schwer)

---

## Standard-Wochenplan

| Tag | Training | Variante |
|---|---|---|
| Mo | Laufen flach | 16 × 400 m |
| Di | HIIT | – |
| Mi | Core & Stabilität | – |
| Do | Laufen Hügel | 8 × 800 m |
| Fr | Beweglichkeit | – |
| Sa | Indoor Bike | Locker (90 min) |
| So | Indoor Bike | Schnell (60 min) |

---

## Einstellungen (Settings-View)

- Dark / Light Mode Toggle
- Standard-Wochenplan-Editor (pro Tag änderbar)
- Woche zurücksetzen (mit Bestätigungsdialog)
- Alle Daten löschen (mit Bestätigungsdialog)

---

## Storage Keys

- `fitapp_v4_week` – aktueller Wochenplan + Status
- `fitapp_v4_hist` – Trainingshistorie (datumsbasiert)
- `fitapp_v4_prefs` – Präferenzen (Theme, custom DefaultWeek)

---

## Änderungs-Log

| Datum | Änderung |
|---|---|
| 2026-05-01 | V4 Projektordner angelegt, Memory.md erstellt |
| 2026-05-01 | V4.0 initial gebaut (Fresh Start) |
| 2026-05-28 | Memory-Pflege: 4-Phasen-Rotationsplan und Logistik dokumentiert, SF-Pro-Schrift gelöst (`-apple-system`-Keyword, numerische Weights), Base44-Prompt-Set v2 |
| 2026-06-20 | Memory-Pflege: Design-Critique vom 15.06. dokumentiert (Lime `#B5E853` nur für Daten/aktive UI, Select-Dropdown nicht nativ, Pentagon-Chart bleibt, zwei getrennte Claude-Design-Prompts) |
| 2026-07-04 | **Stufe 2 gebaut:** `OUTPUT/Sport-App_v1_2026-07-04.html` nach Finalspec umgesetzt (Bau-Chat). Drei Tabs (Heute/Woche/Fortschritt), 3D-Flip A4 (0.25s), Rad-Picker C3 (Einrasten legt fest, Zurück-Knopf), Drag-Umplanen mit Undo-Balken, Drei-Farben-Ring, Übungs-Bibliothek (Kern-Seed Handgelenk-Training + eigene Einträge via localStorage), Plan-Editor mit Perioden-Validierung, Erinnerungs-Sheet, Dark/Light. 17 Set-Icons base64. Speicher `sportapp_v1_*`. Verifiziert: 20 Logik-Tests + 30 DOM-Tests bestanden, Design-Token-/PWA-/Storage-Checks sauber. Offen: Gerätetest iPhone (Flip-Optik, Drag-Gefühl, Safe-Areas), echte Absprung-Logos, eigenes Pilates-Icon. |
| 2026-07-04 | **Feedback-Runde 1 umgesetzt** (gleiche Datei ersetzt): Tageswechsel nur noch automatisch beim App-Start an neuem Tag (zweiphasiger, ruhigerer Flip; Wischen/Pfeile/«zu heute» entfernt, Kachel zeigt immer heute), Heute-Tab-Icon neu `flame.fill`, Erinnerung als zentrierter Pflicht-Dialog ohne Wegklick (Fallback: rote Hinweis-Pill oben zwischen den Buttons, öffnet Dialog; Status vergangener Tage in Woche nur via Reset+Neu-Bewertung änderbar), Haken-Knopf heisst «Erledigt», UI-Hinweistexte entfernt, Übungs-Bibliothek als Vollbild-Fenster (Slide von rechts), Abhak-/Erinnerungs-Knöpfe getönt (Grün-/Rot-Tint statt Vollgrün/Schwarz), Fenster-Köpfe: nur X im schwarzen Kreis links (kein Zurück-Knopf). Verifiziert: 41 DOM-Tests + 14 Logik-Tests, 0 Fehler. |
| 2026-07-04 | **Feedback-Runde 2 umgesetzt:** Abhak-Knöpfe kompakt rechts unten in der Kachel, Rad-Zurück links unten als reiner Kreis-Knopf (nur Pfeil-Symbol), Status+Rückgängig ebenfalls im Kachel-Fuss. Rad-Picker in Demo-Optik (Fade-Maske, kein Auswahlbalken), grösser (220 px) und neu mit «Bestätigen»-Knopf — Auswahl legt sich nicht mehr per Einrasten fest. NTC-Knopf im Nike-Look (schwarz, echtes NTC-Logo). App-Logos Health/Fitness/Bevel/NTC als SVG nachgebaut (Squircles einheitlich #1C1C1E auf JBs Wunsch), in Topbar eingebaut. Fortschritts-Ringe mit Startpunkt-Glyphen wie Apple (Farbpunkt + schwarzes Kategorie-Symbol bei 12 Uhr). Bugfix: Icon-Stapeln im Erinnerungs-Dialog beim mehrfachen Trainings-Wählen (Icon wird jetzt ersetzt). Verifiziert: 24 DOM-Tests, 0 Fehler. |
| 2026-07-05 | **Feedback-Runde 3 umgesetzt** (Subagenten-Lauf: 4 Bau- + 4 Prüf-Agenten, sequenziell): (1) Liquid-Glass-Tab-Bar als schwebende Pille mit wanderndem Indicator-Feld (Tap+Drag, nach JBs Referenzcode; Prüfer fand+fixte Pointer-Capture-Bug der Taps geschluckt hätte). (2) Friktionsfrei: Trainings vergangener Tage mit feststehendem Training werden automatisch «erledigt» (autoResolvePast), auf der Kachel nur noch rotes X-Quadrat («nicht gemacht»); offen bleiben nur ungewählte Wahltage (Pflicht-Dialog «Offene Wahltage»: runder schwarzer X-Kreis immer aktiv auch ohne Trainingswahl, runder Haken grau→blau nach Pill-Wahl); Bestätigen unterm Rad = blauer Haken-Kreis; Woche-Status done=grüner Ring/weisser Haken, skip=rotes Mini-X-Quadrat, Toggle done↔skip mit Bestätigung; Topbar-Pill ersetzt durch rotes Zahl-Badge am Woche-Tab (WhatsApp-Stil) + rote Badges an offenen Wochen-Zeilen (Klick öffnet Dialog). (3) Fortschritt: Umschalt-Knopf oben rechts in der Ring-Karte toggelt Ring ↔ vertikales Balkendiagramm (3 Säulen, Tint-Track, persistiert in prefs.progView); Tab-Icons neu: Heute=dot.square.fill, Fortschritt=chart.bar.fill; Einstellungs-Zahnrad als selbst gezeichnetes gearshape.fill-SVG. (4) Echte App-Logos (JBs Fotos aus INPUT/) via Container-Rundung+Zoom eingepasst (Bilder unbeschnitten, Eckreste weg, Schwarzton einheitlich ab Werk). Endtest: 7 jsdom-Suiten inkl. 62-Check-E2E alle grün, statische Checks (Palette, shortcuts, Storage, PWA-Meta, keine externen Ressourcen) sauber. |
| 2026-07-05 | **Feedback-Runde 4 umgesetzt:** Balken-Ansicht im Fortschritt jetzt vollflächig (Karte dehnt sich bis zum unteren Rand, Prozentlinien-Karten ausgeblendet, «x von y»-Zähler unter den Säulen-Captions). Haken/X/Zurück-Pfeil überall selbst gezeichnet als dicke Strich-SVGs mit runden Kappen (keine Set-Icons mit eingebautem Kreisrand mehr): Dialog-X schwarz rund / Haken grau→blau gleich gross, Bestätigen-Haken, Kachel-X dicker, Zurück-Kreis nur Pfeil auf vollem Hellgrau, Woche-Status (grüner Ring/weisser Haken, rotes Mini-X-Quadrat). Rad-Picker im Demo-Look: bg3-Kasten + «Gewählt: X»-Zeile darunter (live beim Drehen). Woche: Tipp auf Wahltag mit gewähltem Training setzt Wahl+Bewertung mit Bestätigung zurück → Tag erscheint wieder als offener Punkt (Badge/Dialog/Rad). Tab-Icon Heute = rectangle.fill.on.rectangle.angled.fill (Karten), Fortschritt-Toggle zeigt gezeichnetes 3-Ringe-Symbol. Ungenutzte Set-Icons aus dem Build entfernt (−34 KB). Tests: 7 Regressions-Suiten + neuer 22-Check-Runde-4-Test alle grün. |
| 2026-07-05 | **Feedback-Runde 5 umgesetzt:** Haken auf blauen Knöpfen (Bestätigen, Dialog) jetzt weiss; Woche-Erledigt im gleichen Design als voller grüner Kreis mit weissem Haken. Rad-Picker endlos (Optionen 9x wiederholt, rundum drehbar) und bewusst zäh/abgestuft: eigene Pointer-Steuerung ohne Momentum, Fingerweg gedrittelt (~3x Wischweg pro Stufe), Einrasten beim Loslassen; Perioden-Räder bleiben nativ. NTC-Knopf in der Kachel = nur noch App-Logo-Squircle (42 px, wie Topbar). Zurück-Kreis invertiert (heller Grund, dunkler Pfeil, kein Icon-Rand). Wahltag in der Woche: Klick auf Zeile ODER Status verlangt jetzt immer zuerst die Trainingswahl (Bestätigung → Reset → Dialog mit Pill-Zwang); done/skip-Direkt-Toggle nur noch bei festen Tagen. Offen-Badge sitzt in der Kachel-Ecke (-5/-5, Liste mit Innenabstand gegen Clipping). Einstellungs-Sheet öffnet bis zur Oberkante der App-Logos (100dvh − safe-area − 8px). Alle X in Fenster-Köpfen/Dialog/Formular gezeichnet mit Strichstärke 3.8 (wie das rote X), Form/Grösse unverändert. Tests: 8 Regressions-Suiten + neuer 20-Check-Runde-5-Test alle grün. |
| 2026-07-05 | **Feedback-Runde 6 umgesetzt:** Dialog-Haken-Kreis wieder sichtbar (bg2 + feiner Ring statt bg3-auf-bg3). Rad ~15% leichter (Weg /2.6 statt /3), Rad-Icons in Kategorie-Farben (gedimmt, Mitte satt). Rotes X in der Woche auf 34 px (proportional zum grünen Kreis). Tab-Badge sitzt an der Icon-Ecke. NTC-Logo-Knopf 60 px. Balken-Ansicht neu im Apple-Chart-Stil (nach Bildrecherche Apple-Fitness-Charts): feine gepunktete Referenzlinien 25/50/75/100 % über die volle Breite mit Skala rechts, feste Grundlinie, schlanke Säulen (48 px, runde Kappe), Wert über der Säule, Label+Zähler bündig darunter; 0 % statt «–», «0 von 0» statt «keine Einheiten». Umschalt-Symbol zeigt Ringe in verschiedenen Füllständen (Bögen) statt voller Kreise. Tests: 9 Suiten alle grün. |
| 2026-07-06 | **Feedback-Runde 7 umgesetzt** (Datei heisst neu `OUTPUT/index.html`): Heute-Kachel: Trainings-Kreis/Figur/Titel/Kategorie ~10% grösser; drei Deko-Aktivitätsringe um den Kreis (Füllstand je Trainingsart: Joggen voll, Indoorbike ~90, Kraft/HIIT/Pilates ~2/3, Yoga ~50; innen führt immer, unregelmässig gestuft), Ringdurchmesser füllt die Kachel bis auf schmalen Rand. Status-Schnellwechsel auf der Kachel: statt Badge zeigt der Fuss die Gegenteil-Aktion (X↔grüner Haken-Kreis), Rückgängig-Kreis bleibt. Plus-Knopf oben rechts (schwarzer Kreis, dickes Plus) fügt per Rad+Bestätigen ein zweites Training hinzu (zählt als eigener Slot); x2-Tipp rotiert jetzt strikt durch ALLE Einheiten (auch bewertete, einzeln umstellbar). Drag&Drop: Aktivierung per kurzem Halten/klarem Zug (weniger rutschig), Kachel-Mitte=stapeln, Lücke=blauer Einfüge-Strich → Tage rotieren (Bsp. Mi zwischen Mo+Di → Mi wird Di, Di rutscht auf Mi); Undo über Schnappschüsse (alte Move-Einträge migriert). Rad überall im Apple-Wecker-Look (transparent, heller Auswahlbalken, grosse zentrierte Werte, endlos; auch Plan-Editor-Tageswahl und Perioden-Monate als Räder, Monate 12×9 Wiederholungen). Toggle-Symbol im Fortschritt: drei Bögen ~95/66/28%. 100%-Linie mit mehr Abstand zum Knopf (margin 44px). Tab-Bar auf native Höhe (60px, Icons 25px). Haken/X/Plus-Zeichen deutlich grösser/fetter im Verhältnis zur Form (wie Plus-Referenz). Annahme dokumentiert: Kraft-Ringe ~2/3 gemäss JBs detaillierter Aufzählung (die frühere Aussage «ganz geschlossen» als Diktat-Korrektur gewertet). Tests: neue 38-Check-Suite (suite7) komplett grün. |
| 2026-07-06 | **Nachbesserung Runde 7:** Kachel-Fuss bei bewertetem Training: Zurück-Kreis springt in die rechte Ecke (Position von X/Haken), Wechsel-Symbol (Haken bzw. X) daneben — schnelles Hin- und Herschalten plus Undo an fixer Eckposition. Deko-Ringe neu in den Original-Apple-Fitness-Farben (#FA114F/#A8F80B/#00E5DD), 20er-Stroke, lückenlos aneinander und am Trainings-Kreis anliegend (Icon-Kreis jetzt prozentual 42.5% des Ringfelds, skaliert sauber), Tracks abgedunkelt (0.22). Trainings-Titel nochmals grösser (37px). Suite7: 38/38 grün. |
| 2026-07-06 | **Feinschliff Ringe:** Trainings-Kreis in der Ringmitte auf 47% vergrössert (Ringe folgen lückenlos: Radien 66/85/104, Stroke 19), Ringfarben leicht gedeckt statt grell (#E11250/#8FD60D/#00C9C2). Suite7 grün. |
| 2026-07-11 | **Projektzuordnung geklärt (JB-Entscheid):** Die Sport-App ist keine eigene Projektlinie, sondern der Neuaufbau innerhalb von Fitness-App V2. Sämtliches Material aus `OUTPUT/` und `INPUT/` in den neuen Unterordner `Forma/` verschoben (Planner, Finalspec, Stufe-1-Demo, App-Datei, Icon-PNG, 6 Bilder). `OUTPUT/index.html` dabei in `Forma/Forma_App_2026-07-07.html` umbenannt, weil der Name im Projektordner nichts aussagte. Offene Frage aus der Memory-Pflege damit erledigt. |
| 2026-07-12 | **Finalisiert, auf GitHub deployed, Icon-Bug behoben.** App mit Claude Design fertiggestellt (neue `index.html`, Titel «Forma», ~205 KB) und in ein GitHub-Repo (GitHub Pages) hochgeladen. **Bug:** Beim «Zum Home-Bildschirm» in Safari erschien statt des Logos nur der Anfangsbuchstabe des Namens. **Ursache:** Die Icon-Dateien hatten ihre Bindestriche verloren — der Code verwies auf `apple-touch-icon.png`/`favicon-16/32.png`/`icon-192/512.png`, auf der Platte (und auf GitHub) liegen sie aber als `appletouchicon.png`/`favicon16/32.png`/`icon192/512.png`. Safari fand `apple-touch-icon.png` nicht (404) und nahm den Fallback (Buchstabe). **Fix (JB-Entscheid: Code an Dateinamen anpassen statt umbenennen, weniger Upload):** Verweise in `index.html` und `manifest.webmanifest` auf die real vorhandenen bindestrichlosen Namen umgebogen; JB lädt genau diese zwei korrigierten Dateien neu auf GitHub (überschreiben gleichnamig). **Nicht blockierend, offen:** `nojekyll`/`gitignore` fehlt der führende Punkt (`.nojekyll`/`.gitignore`) — betrifft nur GitHub-Feinheiten, nicht das Icon. Gesamtes OUTPUT-Forma-Material (App, Manifest, Icons, README, 3 Design-HTMLs, Logo-Bilder) direkt in `Forma/` gelegt, alte Dateien belassen (JB-Wunsch). INPUT enthielt nur ein Duplikat der Phone-Vorschau + leeren `sport-app-icons/`-Ordner, nichts Zusätzliches nötig. |
| 2026-07-17 | **Neues Logo (Pfeil 3.4) eingebaut + Tab-Bar-Position gefixt.** JB hat Variante 3.4 «Wachsend» gewählt (drei nach oben wachsende Pfeile: grau klein, orange mittel, gelb gross). (1) Komplettes Icon-Set neu generiert im Aufbau der alten Dateien (vollflächig `#16161A`, gleiche Namen): appletouchicon 180, favicon16/32, icon192/512, icon512maskable (Motiv 70 % für Android-Maske), formalogo 1024 (Squircle auf Schwarz, fürs README). (2) Altes Logo-Set nach `Logo-Alt_Entwurf15/` archiviert (Kopien; variante_15 + ChatGPT-Quellbild aus `Forma/` verschoben; index.html-Sicherung). (3) **Tab-Bar-Bug:** Auf JBs iPhone 17 Pro sass die Bar ~83 pt über dem Rand. Ursache per Simulation verifiziert: iOS meldet in der PWA ein aufgeblähtes `safe-area-inset-bottom` (~96 px), die alte Formel `margin-bottom:max(12px, sab−13px)` machte daraus 83 px. Fix in `index.html`: Bar auf `position:fixed` mit `bottom:clamp(12px, sab−13px, 21px)` (Deckel 21 px = native Höhe; Stil/Höhe/Breite unverändert), `#main` erhält passendes `padding-bottom`, Inhalt nutzt die frei gewordene Fläche. Headless geprüft: normaler Fall unverändert 21 px, Inflations-Fall alt 83 px → neu 21 px. (4) README-Icon-Zeile aktualisiert. **GitHub-Upload nötig (9 Dateien, überschreiben):** index.html, README.md, appletouchicon.png, favicon16.png, favicon32.png, icon192.png, icon512.png, icon512maskable.png, formalogo.png. manifest.webmanifest unverändert. Auf GitHub liegt zudem noch `forma_icon_variante_15.png` (altes Logo, nicht referenziert) — kann JB dort löschen oder lassen. Nach Upload: App am iPhone einmal löschen und neu «Zum Home-Bildschirm», damit iOS das neue Icon zieht. |
| 2026-07-15 | **Icon-Runde 3 erstellt (Pfeile, 12 Varianten).** JB hat aus Runde 2 Entwurf 3 «Aufstieg» (drei gestapelte Pfeile/Chevrons, Grau-Orange-Gelb) gewählt und ~10 Varianten mit unterschiedlich grossen und langen Pfeilen verlangt. Ergebnis: `Forma/Forma_Icon-Pfeile_Runde3_2026-07-15.html` mit 12 Varianten (3.1–3.12): Original als Referenz, breit, steil, wachsend, zulaufend, Duo (2 Pfeile), Quartett (4 Pfeile mit Rot), diagonal versetzt, gefüllte Bänder, Einzelpfeil massiv, App-Farben kalt (Blau/Cyan/Lime), monochrom Gelb in 3 Opacity-Stufen. Visuell verifiziert (Headless-Screenshots, keine Nachbesserung nötig). **Offen:** JB wählt finale Variante, dann PNG-Export fürs Icon-Set (appletouchicon, favicons, icon192/512) und GitHub-Upload. |
| 2026-07-15 | **Icon-Runde 2 erstellt (50 Entwürfe).** JB ist mit dem aktuellen App-Icon (Entwurf 15, geschichtetes F mit Grün-Blau-Violett-Verlauf) nicht zufrieden. Vorgaben aus Rückfragen: komplett offen neu denken (nichts vom F-Verlauf behalten müssen), Farbwelt frei, dunkle Squircles wie bisher, keine Personen/Strichmenschen; Motiv-Mix mit bewusst wenig Daten-Motiven. Ergebnis: `Forma/Forma_Icon-Entwuerfe_Runde2_2026-07-15.html` mit 50 handgezeichneten SVG-Entwürfen in 4 Sektionen (1–15 abstrakt/geometrisch, 16–29 F-Monogramme, 30–43 Sport-Gegenstände, 44–50 Daten & Fortschritt), je mit 160-px-Icon, 46-px-Homescreen-Vorschau plus Wortmarke, Name und Idee. Anders als die alten `.dc.html` als eigenständiges HTML gebaut, damit JB es direkt im Browser öffnen kann. Visuell verifiziert (Headless-Screenshots aller 50, drei Entwürfe nachgebessert: Sechskant-Symmetrie, Stoppuhr-Zeiger, Matte). **Offen:** JB wählt Favoriten (per Nummer), dann Ausarbeitung der gewählten Richtungen und PNG-Export fürs echte Icon-Set. |
| 2026-07-12 | **Aufräumen + Repo-Feinschliff (JB-Berechtigung).** `nojekyll`/`gitignore` im Projektordner auf `.nojekyll`/`.gitignore` umbenannt (führender Punkt). README-Logo-Verweis korrigiert (`icons/forma-logo.png` → `formalogo.png`, im flachen Repo sonst totes Bild). INPUT und OUTPUT von allem Forma-Material geleert: die im Projekt gesicherten Dateien nach `SYSTEM/_Archiv/INPUT-Originale-2026-07-12/` bzw. `SYSTEM/_Archiv/OUTPUT-Deliverables/2026-07-12/` verschoben (harte Löschung im OneDrive gesperrt → Archiv = leeren, JB kann Archiv am PC von Hand endgültig löschen). In INPUT bewusst belassen: Schul-/BM2-Material (Bruchterme, Thema 3b, Lehrmittel-PDF) — nicht Forma, noch nicht verarbeitet. In OUTPUT belassen: `DeepMind-zu-pruefen.md` (aktive Review-Inbox) und `Anmeldebestaetigung_BBZ.eml` (nicht Forma, unverarbeitet). |
