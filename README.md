# Stoll Fensterbau – Karriereseite

Recruiting-Landingpage für die **Stoll Fensterbau GmbH** (Ammerbuch-Pfäffingen).
Offene Stelle: **Fensterbauer / Monteur (m/w/d)**.

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `bilder/` – hier kommen Logo und Fotos hinein (siehe `bilder/HIER-BILDER-ABLEGEN.txt`)
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert

## ⚠️ Vor dem Live-Gang zu erledigen

1. **Web3Forms-Empfängeradresse setzen** – im Web3Forms-Dashboard zum Access-Key
   `eccb3a4e-…` hinterlegen. Dorthin gehen die Bewerbungen mit angehängtem
   Lebenslauf. **Dateianhänge sind ein PRO-Feature** – ohne aktives Abo kommt
   die Mail zwar an, der Anhang aber nicht.
2. **Datenschutz-Link prüfen** – aktuell verlinkt auf
   `https://www.stoll-fensterbau.de/datenschutz/`. Falls der Slug anders heißt,
   an zwei Stellen in `index.html` anpassen (Consent-Text + Footer).

## Aufbau

Struktur 1:1 wie die ALWA-Karriereseite:
Topbar → Sticky Mobile-CTA → Hero → Trust-Band → Offene Stelle → Benefits →
Ablauf → Mid-CTA → Bewerbungsformular → FAQ → Footer.

## CI

Ankerfarbe ist das Türkis aus dem Logo (`Logo-Fensterbau-Stoll_web.png`).

| | |
|---|---|
| Logo-Türkis (Akzent) | `#00998a` |
| Primärfarbe (Buttons, Links) | `#00796d` – abgedunkelt, 4,9:1 auf Weiß (WCAG AA) |
| Dunkle Flächen | `#0d3c37` · `#0a5f57` · `#00625a` |
| Hell | `#e2f4f1` · Akzent auf Dunkel `#5fd6c6` |
| Schrift | Poppins (Google Fonts) – geometrische Grotesk als Entsprechung zur Website-Schrift |

Das reine Logo-Türkis erreicht auf Weiß nur 3,5:1 und ist deshalb dem Akzent
vorbehalten (Verlauf, Fortschrittsbalken, Hero-Punkt); alles, was Text trägt,
nutzt die abgedunkelte Variante.

## Bilder

Eingehängt in `index.html`:

- **Logo** – `bilder/Logo-Fensterbau-Stoll_web.png` in Header, Hero und Footer.
  Liegt eine Negativ-Variante als `bilder/logo-weiss.png` (oder `.svg`) im Ordner,
  wird sie auf den dunklen Flächen automatisch bevorzugt.
- **Hero** – `bilder/27 - Stoll Fensterbau-27.jpg` (Montage einer Schiebetür im
  Neubau). Zum Tauschen den ersten Eintrag in der Liste `cands` im Script
  ändern; als Alternativen sind Foto 38 und 9 bereits hinterlegt. Leerzeichen
  im Dateinamen als `%20` schreiben. Liegt eine Datei `bilder/hero.jpg` im
  Ordner, gewinnt immer diese.

Die übrigen Fotos (4, 9, 18, 21, 38) sind für die Meta-Ads-Creatives reserviert.

## Vorfilterung im Formular

Sechs Schritte: fünf Screening-Fragen (je eine pro Schritt) plus Kontaktdaten.

| # | Frage | Kategorie | K.-o. bei |
|---|---|---|---|
| 1 | Montageerfahrung | **Pflicht** | „Noch keine“ |
| 2 | Deutschkenntnisse (Kundenkontakt) | **Pflicht** | „Kaum / keine“ |
| 3 | Führerschein Klasse B | optional | – |
| 4 | Staplerschein | optional | – |
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

## Benefits

Kommuniziert werden (Stand Onboarding):

übertarifliche, leistungsgerechte Bezahlung · 14 € Spesen netto pro Arbeitstag ·
50 € netto extra im Monat · Anwesenheitsprämie · Weihnachts- & Urlaubsgeld ·
Gewinnbeteiligung · BAV · VWL · Wellpass · JobRad · 38-Stunden-Vertrag bei
40 bezahlten Stunden · freitags Feierabend um 12 Uhr · Sommerfest & Wasen ·
Familien- und Meisterbetrieb seit 1971 · Weiterbildung.

**Bewusst nicht kommuniziert:** Firmenwagen zur Heimnahme (auf Kundenwunsch).

## Mobile Laufruhe

Beim Wechsel von Frage zu Frage bleibt der Viewport **exakt stehen**:

- kein `window.scrollTo`, kein `scrollIntoView`, kein automatisches `focus()`,
  kein Reload, kein Anker-/Hash-Sprung beim Schrittwechsel
- die Höhe des Fragenbereichs wird per JS auf den höchsten Frage-Schritt fixiert
  (`lockHeight()`, fraktionale Messung mit Aufrunden), Fortschrittsanzeige und
  Weiter-Button bleiben dadurch exakt an derselben Position – gemessen 0,000 px
  Abweichung über alle fünf Fragen
- neu gemessen wird nur bei echter Breitenänderung – das Ein-/Ausblenden der
  mobilen Adressleiste löst also keine Sprünge aus
- ein kompletter Frage-Schritt ist auf Standard-Handydisplays ohne Scrollen
  sichtbar (geprüft auf 360×640, 375×667 und 390×844)

## Felder im Webhook-Payload

`vorname`, `nachname`, `email`, `telefon`, `stelle`, `montageerfahrung`,
`deutsch`, `fuehrerschein`, `staplerschein`, `verfuegbarkeit`,
`wunschkriterien`, `datum`, `lebenslauf`, `datenschutz`, `quelle`, `seite`

Der Webhook der LeadTable-Kachel ist in `index.html` in `WEBHOOK_URL` hinterlegt.

## Lebenslauf-Upload (Web3Forms)

Der Upload im letzten Schritt ist optional und läuft über **Web3Forms**
(`WEB3FORMS_KEY` in `index.html`): eine Datei bis **5 MB**, PDF/Word/JPG/PNG/WebP.
Web3Forms verschickt die komplette Bewerbung samt Anhang per E-Mail; die
Empfängeradresse steht im Web3Forms-Dashboard, nicht im Code.

Der Upload kann die Bewerbung **nie blockieren**. Das Feld `lebenslauf` im
LeadTable-Datensatz sagt, was passiert ist:

| Wert | Bedeutung |
|---|---|
| `per E-Mail zugestellt (dateiname.pdf)` | Anhang ist raus |
| `Upload fehlgeschlagen – bitte Unterlagen beim Bewerber anfragen` | Web3Forms nicht erreichbar, Bewerbung ist trotzdem da |
| `nicht hochgeladen` | Bewerber hat keine Datei angehängt |

Ist `WEB3FORMS_KEY` leer, wird das Upload-Feld gar nicht erst angezeigt und die
Bewerbung läuft ganz normal ohne Datei.

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`.
2. Nach ein paar Minuten ist die Seite unter `https://saviold.github.io/stoll-fensterbau/`
   erreichbar (bzw. unter der hinterlegten Custom-Domain).
