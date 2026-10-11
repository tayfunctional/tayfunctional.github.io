# Übergabe: Branch `vorschau-mehrwert`

Stand: 08.10.2026. Alles auf diesem Branch ist freigegeben und soll live.

## Was auf dem Branch liegt

**1. Neuer Abschnitt "So arbeite ich" plus Vergleich**
Auf `performance.html`, `rehab.html`, `en/performance.html`, `en/rehab.html`,
jeweils direkt unter dem Preisblock. Drei Karten (Rhythmus, Struktur, Daten)
und darunter eine Vergleichstabelle "Warum das hier mehr kostet".
Auf den Rehab-Seiten hat die Tabelle eine vierte Zeile zum Thema vor Ort, auf
den Performance-Seiten nicht, weil dort keine PT-Termine im Paket sind.

Die Kartenstile (`.care-grid`, `.care`, `.c-tag`, `.fine`) fehlten auf den
Rehab-Seiten und wurden eins zu eins aus `performance.html` ergänzt. Neu sind
ausserdem `.meth-cmp`, `.cmp*` und `.pt-note`, alles inline im `<style>`-Block
der jeweiligen Seite.

**2. Ein zusätzlicher FAQ-Eintrag pro Seite**
Zum Preis-Einwand, hinten angehängt. Sichtbar als `<details>` und zusätzlich
als `Question` im bestehenden FAQPage-Schema. Es wurde kein bestehender
Eintrag entfernt. Vorher sechs, jetzt sieben, sichtbar wie im Schema, auf
allen vier Seiten.

**3. Neue Seite `personal-training-ingolstadt.html`**
Lokale Landingpage für "Personal Trainer Ingolstadt" und "Personal Training
Ingolstadt". Nur Deutsch, keine EN-Fassung, der Sprachschalter führt von dort
auf `/en/`. Verlinkt aus dem Footer aller deutschen Seiten, in der Sitemap
eingetragen, nicht in der Hauptnavigation. Preis: 200 € pro Stunde, der
bestehende, nichts erfunden.

**4. Korrigierte Jahresangaben, deutsch und englisch**
Die Zahlen widersprachen sich auf der eigenen Seite. Richtig ist:

| Aussage | Wert |
|---|---|
| Kampfsport, Kickboxen und K1 | über zehn Jahre |
| Functional Fitness, Kurse | seit 2016 |
| Eins-zu-eins-Coaching | seit fünf Jahren |
| Athleten zurück zur Leistung | 50+ |

Geändert wurden: die mittlere Kachel im roten Zahlenstreifen auf der
Startseite (vorher "Jahre Coaching & Functional Fitness", jetzt nur noch
"Jahre im Sport"), der Satz "seit fünf Jahren Functional Fitness" auf der
Startseite und der Satz "seit fünf Jahren coache ich Functional Fitness" auf
der Über-mich-Seite. Dieselben drei Stellen auf `en/index.html` und
`en/about.html`.

## Was zu tun ist

1. `git fetch origin`, dann `vorschau-mehrwert` nach `main` mergen und pushen.
   Der Branch hängt direkt an `main`, der Merge sollte ein Fast-Forward sein.
2. `preise-2027` auschecken und `main` hineinmergen, damit die Januar-Fassung
   die neuen Abschnitte, die Ingolstadt-Seite und die korrigierten
   Jahresangaben ebenfalls hat. Konflikte sind zu erwarten, weil beide
   Branches dieselben Seiten anfassen. Beide Seiten müssen überleben: die
   neuen Inhalte aus `main` und die Januar-Preise aus `preise-2027`.
3. `preise-2027` pushen, aber **nicht** nach `main` mergen. Der Branch bleibt
   liegen bis zum 1. Januar 2027, ein geplanter Task schaltet ihn dann live.

## Harte Vorgaben

- **Keine Gedankenstriche** in irgendeinem Text, weder DE noch EN.
- **Keine erfundenen Preise, Zahlen, Testimonials oder Garantien.**
- CSS bleibt pro Seite inline im `<style>`-Block. Keine externe Datei.
- Kein Überlaufen auf Mobile, geprüft wird bei 390 und 1440 Pixeln.
- Die neuen Abschnitte enthalten bewusst **keine Preise**, damit sie bei der
  Januar-Umstellung nicht angefasst werden müssen. Das soll so bleiben.
- Ingolstadt gehört in Titel, Meta, Schema und auf die lokale Seite, nicht in
  den Methoden-Abschnitt. Der Rest der Site bleibt DACH-weit formuliert.
- Keine Werbung um Mitglieder des Gladiator-Area-Studios. Die Seite zielt auf
  Leute, die noch kein Studio haben.
- Der Gladiator-Area-Rabatt wird nirgends auf der Website erwähnt.

## Prüfpunkte nach dem Merge

- Jahresangaben stimmen auf allen Seiten überein, DE wie EN.
- FAQ: acht sichtbare Einträge und acht Schema-Einträge auf den vier
  Coaching-Seiten, keiner fehlt.
- `langsw`, `tf_lang`, `hreflang` und `canonical` auf allen Seiten vorhanden.
- JSON-LD überall gültig, keine toten internen Links.
- `personal-training-ingolstadt.html` ist in der Sitemap und aus den Footern
  erreichbar.
