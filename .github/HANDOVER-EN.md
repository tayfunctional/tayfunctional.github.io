# Übergabe: englische Version + offene Januar-Anpassung

## Stand auf diesem Branch (`english-version`)

Die englische Version der Site ist fertig gebaut und QA-geprüft. Enthalten:

- `en/` mit 8 Seiten, 1:1 parallel zur deutschen Site
- Die 8 DE-Seiten ergänzt um Sprachschalter, Locale-Skript und hreflang
- `sitemap.xml` mit 15 URLs (8 DE inkl. `/pace-calculator/`, 7 EN)

Assets, Bilder, `favicon.svg`, `robots.txt` und `CNAME` sind unverändert. Die
EN-Seiten greifen über `../assets/` auf die vorhandenen Bilder zu.

### Mapping DE → EN

| DE | EN |
|---|---|
| `/` | `/en/` |
| `/performance.html` | `/en/performance.html` |
| `/rehab.html` | `/en/rehab.html` |
| `/ruecken-reset.html` | `/en/back-reset.html` |
| `/ueber.html` | `/en/about.html` |
| `/rabatte.html` | `/en/discounts.html` |
| `/impressum.html` | `/en/legal-notice.html` |
| `/datenschutz.html` | `/en/privacy.html` |

### Sprachlogik

Ein Inline-Skript vor `</body>` auf allen 16 Seiten. Verhalten:

- Erster Besuch ohne gesetzte Sprache und `navigator.language(s)` beginnt mit
  `en` → `location.replace` auf die Gegenstück-URL aus der Pfad-Map. Nicht auf
  die Startseite, sondern auf die inhaltlich gleiche Seite, Hash bleibt erhalten.
- Der `DE|EN`-Schalter setzt `tf_lang` in `localStorage` **und** als Cookie
  (`path=/`, ein Jahr, `SameSite=Lax`). Sobald `tf_lang` gesetzt ist, greift die
  Automatik nie wieder. Wer bewusst DE wählt, bleibt auf DE.
- Loop-Schutz über `sessionStorage.tf_redir`.
- Der Klick-Handler hängt an `data-lang` und läuft in der Capture-Phase, damit er
  auch im mobilen Menü funktioniert.

### Bewusste Auslassungen (Vorgabe des Kunden, nicht versehentlich)

- **Pace-Rechner**: aus der EN-Navigation entfernt, keine EN-Version.
- **FITR / "Programme"**: alle externen Links in den EN-Seiten entfernt, die
  Toolbox-Blöcke sind dort rausgebaut.
- Impressum und Datenschutz auf EN sind Höflichkeitsübersetzungen mit Hinweis
  oben, dass nur die deutsche Fassung rechtlich bindend ist, verlinkt auf die
  DE-Seite.
- Calendly-Links identisch, nur `utm_source=website_en` statt `website`.

---

## Offen: Januar-Umstellung für die EN-Seiten

Ab 1.1.2027 ist Tayfun umsatzsteuerpflichtig. Für die deutschen Seiten existiert
die Umstellung bereits als separates Paket (`02-ab-1-januar`), für die
englischen Seiten **noch nicht**. Die EN-Seiten tragen aktuell die
Vor-Umstellungs-Preise.

### Was zu ändern ist

Betroffen: `en/index.html`, `en/performance.html`, `en/rehab.html`,
`en/back-reset.html`

| Vorher | Nachher |
|---|---|
| Hybrid Coaching 450 € / Monat | 490 € / Monat |
| Jahrespaket 5.000 € | 5.390 € (11 × 490, der 12. Monat ist geschenkt) |
| kein MwSt.-Hinweis | "All prices include 19 % VAT" |
| Wertanker (alte Summe) | 300 + 1.800 + 1.470 = 3.570 |

Der Jahrespaket-Text lautet auf Deutsch sinngemäß "Zahl elf Monate, trainier
zwölf", die Ersparnis sind 490 € bzw. 8,3 %. Auf Englisch entsprechend.

Rehab-Preise (600 / 700 / 900) und Personal Training (200 €/h) bleiben
unverändert.

### Harte Vorgaben

- **Keine Gedankenstriche** in irgendeinem Text, weder DE noch EN.
- **Keine erfundenen Preise oder Angebote.** Nur die oben genannten Zahlen.
- Bestandskunden behalten ihren alten Preis. Das steht so auf der DE-Seite und
  gehört sinngemäß auch in die EN-Fassung.
- Der Gladiator-Area-Rabatt ist ein Gentlemen's Agreement und wird **nirgends**
  auf der Website erwähnt.
- CSS bleibt pro Seite inline im `<style>`-Block. Keine externe Stylesheet-Datei,
  das hat die Vorschau beim Kunden schon einmal zerschossen.
- Layout und CSS der EN-Seiten sind 1:1 identisch zur DE-Site. Nur Sprache und
  Locale-Logik unterscheiden sich.
- Kein Overflow auf Mobile. Geprüft wurde bei 390 px und 1440 px.

### Prüfpunkte nach der Änderung

- Preise in DE und EN stimmen überein und sind in sich konsistent (Monatspreis,
  Jahrespaket, Wertanker, FAQ, Schema.org `offers` falls vorhanden).
- Keine deutschen Reste in den EN-Seiten.
- `hreflang` und `canonical` auf allen 16 Seiten unverändert vorhanden.
- Keine toten internen Links, JSON-LD weiterhin valide.
