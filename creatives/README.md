# Meta-Ads Creatives

Drei Konzepte in je zwei Formaten, gebaut ausschließlich aus dem Bildmaterial
in `bilder/`.

| Konzept | Winkel | Foto |
|---|---|---|
| `geld` | Benefits konkret – zieht über Lohn und Arbeitszeit | 9 |
| `koenner` | Qualitätsfilter – setzt Montageerfahrung voraus, ohne abzuwerten | 27 |
| `familie` | Sicherheit & Perspektive – Familienbetrieb in 3. Generation | 38 |
| `region` | Einsätze vor der Haustür, abends daheim | 4 |
| `aufstieg` | Weiterbildung & Perspektive im Betrieb | 18 |

Noch offen: Für ein Konzept rund ums Team fehlt ein Gruppenfoto der
Mannschaft. Mit dem vorhandenen Material lässt sich „Team" nicht glaubhaft
bebildern, ohne ein bereits belegtes Motiv zu wiederholen.

| Format | Datei | Platzierung |
|---|---|---|
| 4:5 · 1080 × 1350 | `creative-<konzept>-4x5.jpg` | Feed (Facebook & Instagram) |
| 9:16 · 1080 × 1920 | `creative-<konzept>-9x16.jpg` | Stories & Reels |

## Split-Layout `creative-stelle-*`

Nativ in allen vier Meta-Formaten gebaut – jede Platzierung bekommt ihre
eigene Datei, damit Meta nichts automatisch beschneidet:

| Datei | Größe | Platzierung |
|---|---|---|
| `creative-stelle-9x16.jpg` | 1080 × 1920 | Stories & Reels |
| `creative-stelle-4x5.jpg` | 1080 × 1350 | Feed |
| `creative-stelle-1x1.jpg` | 1080 × 1080 | quadratisch |
| `creative-stelle-1.91x1.jpg` | 1200 × 628 | Querformat, rechte Spalte |

Die Aufteilung Foto/Fläche ist je Format unterschiedlich (42 % Foto im
Hochformat, 49 % im Feed, 40 % quadratisch, senkrechter Split im Querformat),
damit der Textblock überall vollständig und in gleicher physischer Größe steht.
Im Hochformat liegen Logo und Text zwischen den Meta-UI-Zonen (oben 13 %,
unten 22 %), die Typografie ist dort 10 % größer.

## Schutzzonen

Im 9:16-Format bleiben oben 11,5 % und unten 16 % frei – dort liegt die
Meta-UI (Profilzeile oben, CTA-Leiste unten). Im 4:5-Format 5,5 % Rand.
Typografie ist im Hochformat um 14 % größer, weil es kleiner ausgespielt wird.

Unter dem Textblock liegt ein zusätzlicher Scrim, damit die Eyebrow-Zeile auch
über hellen Bildstellen lesbar bleibt.

## Werbetexte

Siehe `werbetexte.txt` – ein Textsatz für alle Creatives, nicht pro Bild.
