# Stoll Fensterbau – Karriereseite

Recruiting-Landingpage für die **Stoll Fensterbau GmbH** (Ammerbuch-Pfäffingen).
Offene Stelle: **Fensterbauer (m/w/d)**.

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `bilder/` – hier kommen Logo und Fotos hinein (siehe `bilder/HIER-BILDER-ABLEGEN.txt`)
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert

## ⚠️ Vor dem Live-Gang zu erledigen

1. **LeadTable-Webhook eintragen.** In `index.html` ganz oben im `<script>`-Block:
   ```js
   var WEBHOOK_URL   = "";   // ← hier die LeadTable-Webhook-URL einsetzen
   ```
   Solange das Feld leer ist, wird **keine** Bewerbung versendet – der Bewerber
   sieht stattdessen den Fehlerhinweis mit der E-Mail-Adresse.
2. **Supabase-Bucket anlegen** – `supabase-bewerbungen.sql` einmal im
   Supabase-SQL-Editor ausführen (sonst schlägt der optionale CV-Upload fehl).
3. **Bildmaterial hochladen** – siehe `bilder/HIER-BILDER-ABLEGEN.txt`.
4. **Datenschutz-Link prüfen** – aktuell verlinkt auf
   `https://www.stoll-fensterbau.de/datenschutz/`. Falls der Slug anders heißt,
   an zwei Stellen in `index.html` anpassen (Consent-Text + Footer).

## Aufbau

Struktur 1:1 wie die ALWA-Karriereseite:
Topbar → Sticky Mobile-CTA → Hero → Trust-Band → Offene Stelle → Benefits →
Ablauf → Mid-CTA → Bewerbungsformular → FAQ → Footer.

## CI

| | |
|---|---|
| Primärfarbe | `#29615a` (aus der Stoll-Karriereseite entnommen) |
| Abstufungen | `#123832` · `#23564f` · `#1c4741` · `#e8f1ef` |
| Akzent hell | `#7fd0bf` |
| Schrift | Poppins (Google Fonts) – geometrische Grotesk als Entsprechung zur Website-Schrift |

Logo: wird automatisch geladen, sobald es in `bilder/` liegt. Bis dahin steht
dort der Schriftzug **STOLL · FENSTERBAU · SEIT 1971**.

## Vorfilterung im Formular

Sechs Schritte: fünf Screening-Fragen (je eine pro Schritt) plus Kontaktdaten.

| # | Frage | Kategorie | K.-o. bei |
|---|---|---|---|
| 1 | Qualifikation / Ausbildung | **Pflicht** | „Weder noch“ |
| 2 | Führerschein Klasse B | **Pflicht** | „Nein, keinen Führerschein“ |
| 3 | Deutschkenntnisse (Kundenkontakt) | **Pflicht** | „Kaum / keine“ |
| 4 | Smarthome-/Technikerfahrung | optional | – |
| 5 | Verfügbarkeit | optional | – |

- **Pflichtfrage nicht erfüllt** → Bewerbung endet sofort mit einem freundlichen
  Hinweis. Es wird **nichts** an den Webhook übertragen.
- **Optionale Frage nicht erfüllt** → Bewerber läuft ganz normal weiter; die
  Antwort wird übertragen und im Datensatz als `(Wunschkriterium NICHT erfüllt)`
  markiert. Zusätzlich gibt es das Sammelfeld `wunschkriterien`.
- Abgefragt werden ausschließlich berufsbezogene Kriterien (AGG-konform) –
  keine Fragen zu Alter, Herkunft, Gesundheit, Religion oder Familienstand.

Fragen und Logik stehen gebündelt im Objekt `SCREENING` in `index.html` und
lassen sich dort anpassen, ohne das Markup anzufassen.

## Mobile Laufruhe

Beim Wechsel von Frage zu Frage bleibt der Viewport **exakt stehen**:

- kein `window.scrollTo`, kein `scrollIntoView`, kein automatisches `focus()`,
  kein Reload, kein Anker-/Hash-Sprung beim Schrittwechsel
- die Höhe des Fragenbereichs wird per JS auf den höchsten Frage-Schritt fixiert
  (`lockHeight()`), Fortschrittsanzeige und Weiter-Button bleiben dadurch an
  derselben Position
- neu gemessen wird nur bei echter Breitenänderung – das Ein-/Ausblenden der
  mobilen Adressleiste löst also keine Sprünge aus
- ein kompletter Frage-Schritt ist auf Standard-Handydisplays ohne Scrollen
  sichtbar (geprüft auf 360×640, 375×667 und 390×844)

## Felder im Webhook-Payload

`vorname`, `nachname`, `email`, `telefon`, `stelle`, `qualifikation`,
`fuehrerschein`, `deutsch`, `smarthome`, `verfuegbarkeit`, `wunschkriterien`,
`datum`, `lebenslauf`, `datenschutz`, `quelle`, `seite`

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`.
2. Nach ein paar Minuten ist die Seite unter `https://saviold.github.io/stoll-fensterbau/`
   erreichbar (bzw. unter der hinterlegten Custom-Domain).
