# Worship Drums — Designgrundlage

Stand: 6. Oktober 2026. Status: Designbasis festgelegt, Produkt in Planung.

## Verbindliche Quellen

[Design-Art.md](../Design-Art.md) enthält die unveränderte Suite-Art-Direction
Version 1.1. Die dort genannten `/Users/...`-Pfade sind historische Pfade der
Referenzprojekte, keine Voraussetzungen für diese Cloud-Umgebung. Die nutzbaren
Repository-Quellen und untersuchten Commits stehen in
[REFERENCE-ANALYSIS.md](REFERENCE-ANALYSIS.md).

Dieses Dokument konkretisiert die gemeinsame Art Direction für Drums.
Keys-/Loops-Beispiele in der Suite-Vorlage sind keine Drums-Anforderungen.

## Marke und visuelle Regeln

- Wortmarke zweizeilig: `WORSHIP` / `DRUMS`, Großbuchstaben mit ruhigem Tracking.
- Eigenes Produktlogo ist offen. Keine Logos der Schwesterprodukte umbenennen.
  Später Original unverändert aufbewahren, Header- und Favicon-Varianten separat erzeugen.
- Schwarz dominiert; Violett und Blau markieren Fokus, Auswahl und Hauptaktion.
- Dunkle Panels, feine Trennlinien und zurückhaltende radiale Lichtfelder.
- Keine animierten Sterne, Neonrahmen oder dekorativen Audioanzeigen.
- Sichtbare UI vollständig Englisch; interne Dokumentation darf Deutsch sein.
- Geist Sans für UI, Geist Mono für Zahlen und technische Werte. Die tatsächliche
  Fonteinbindung wird mit dem App-Gerüst umgesetzt, nicht durch die Tokens bereitgestellt.

## Implementierte Tokens

[styles/tokens.css](../styles/tokens.css) übernimmt die Werte aus Worship Keys
mit dem Präfix `--wd-`. Worship Mix verwendet dieselben Werte; Worship Loops
gleicht sie in seinem späteren Suite-Stylesheet-Abschnitt an.

| Bereich | Festlegung |
| --- | --- |
| Hintergrund | `--wd-bg-deep: #09090c`, `--wd-bg: #0d0d12` |
| Panels | `#121216`, erhöht `#17171e`, aktiv `#20202a` |
| Text | Haupttext `#efeff4`, weich `#b5b3c1`, gedämpft `#85858f` |
| Akzente | Violett `#7668b7`, Fokus `#9d8cff`, Indigo `#4e5fc6`, Blau `#5d7fe6` |
| Status | Erfolg `#67a89e`, Warnung `#c89b61`, Fehler `#c76f7b` |
| Radien | Controls 9 px, Cards 14 px, Modals 20 px |
| Bewegung | 170 ms, `cubic-bezier(0.32, 0.72, 0.35, 1)` |

Import für das spätere globale Stylesheet (Pfad relativ zu dessen Ablage anpassen):

```css
@import "../styles/tokens.css";
```

Die Datei definiert Variablen und `color-scheme: dark`, aber noch keine
Komponenten oder Seiten. `--wd-text-faint` ist für dekorative/untergeordnete
Details gedacht, nicht für notwendige Beschriftungen. Textkontrast muss immer
gegen die tatsächlich verwendete Fläche geprüft werden.

## Layout und Komponenten für die spätere Umsetzung

Die Suite trennt Navigation/Marke, Hauptarbeitsbereich und Kontext. Ob Drums alle
drei Bereiche benötigt, entscheidet der erste konkrete Nutzerablauf.
Die Rail-Tokens 268/300 px sind Referenzwerte, keine verpflichtende Shell.
Keys/Mix-Breakpoints 1180/820 px sind Ausgangspunkte; Layout anhand der Inhalte prüfen.

Sobald ein Hauptscreen feststeht, zuerst die dafür benötigten Grundkomponenten
umsetzen: Marke, Primary-/Secondary-Button, Panel, beschriftetes Eingabefeld und
Statusanzeige. Slider und Dialoge nur bei tatsächlichem Bedarf hinzufügen.
Pro Screen eine erkennbare Hauptaktion; keine unbegründete Navigation oder
vorgetäuschten Live-/Connected-Zustände.

## Qualitätskriterien für die erste Oberfläche

- Tastaturbedienung und gut sichtbarer `:focus-visible`-Zustand.
- Mindestens 44 × 44 px Touchfläche für Primäraktionen.
- Zustände durch Text/Symbol zusätzlich zur Farbe vermitteln.
- `prefers-reduced-motion` respektieren; keine permanente Hintergrundbewegung.
- WCAG-AA-Kontrast für relevante Texte und Controls prüfen.
- Desktop, Tablet und Mobile anhand echter Screenshots und Bedienung prüfen.
- Falls später Audio/MIDI benötigt wird: Berechtigungen bewusst anfordern;
  tatsächlichen Audiostatus anzeigen, keine automatische Wiedergabe behaupten.

Diese Kriterien sind noch keine bestandenen UI-Tests: Es gibt derzeit keine Oberfläche.
