# Facebook-Assets

Alle Dateien sind fertig zum Hochladen – Facebook skaliert selbst.

| Datei | Größe | Verwendung |
|---|---|---|
| `facebook-profilbild.png` | 1080 × 1080 | **Profilbild** (Empfehlung, dunkel) |
| `facebook-profilbild-weiss.png` | 1080 × 1080 | Profilbild, Alternative auf Weiß |
| `facebook-titelbild.png` | 1640 × 624 | **Titelbild** Marke |
| `facebook-titelbild-recruiting.png` | 1640 × 624 | Titelbild während der Kampagne |
| `logo-block-ohne-claim.png` | 400 × 270 | Logo-Block ohne Claim-Schriftzug (transparent) |

## Warum diese Maße

- **Profilbild:** Facebook beschneidet rund und zeigt es je nach Ansicht mit
  176, 96, 48 oder 40 px. 1080 × 1080 liefert genug Reserve für Retina.
  Ein Rechteck passt nur vollständig in den Kreis, solange
  `Breite² + Höhe² ≤ Durchmesser²` – beim Logo-Seitenverhältnis 1,48:1 sind das
  maximal ~82 % Breite. Gesetzt sind 78 %, also mit Luft zum Rand.
- **Titelbild:** Desktop zeigt 820 × 312, Mobil beschneidet auf 640 × 360.
  Die Datei ist mit 1640 × 624 doppelt aufgelöst. Mobil bleiben davon nur die
  mittleren 1109 px sichtbar – links und rechts fallen je 265 px weg.

## Eingehaltene Schutzzonen (in Koordinaten der 1640 × 624-Datei)

| Zone | Bereich | Abstand |
|---|---|---|
| Mobiler Beschnitt | sichtbar x 265 – 1375 | – |
| Textblock | beginnt bei x 470 | 205 px Luft zum Beschnitt |
| Logo oben rechts | endet bei x 1300 | 75 px Luft zum Beschnitt |
| Profilbild-Überlappung (Desktop) | bis ca. x 408 unten links | 62 px Luft zum Text |

Der Textblock sitzt vertikal mittig und hält die unteren ~150 px frei – dort
liegt auf dem Handy das Profilbild.

## Aufteilung Profil / Titel

Das **Profilbild trägt den Logo-Block ohne Claim** (in der 40-px-Ansicht wäre der
Claim ohnehin nicht lesbar und kostet nur Fläche), das **Titelbild trägt den
Claim** „…für den richtigen Durchblick" und das vollständige Logo oben rechts.
Beides zusammen ergibt das komplette Logo, ohne es doppelt zu zeigen.

## Bio (max. 255 Zeichen)

Siehe `bio-facebook.txt`.
