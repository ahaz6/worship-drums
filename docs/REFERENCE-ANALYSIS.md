# Analyse der Worship-Referenzen

Untersucht am 6. Oktober 2026 anhand der folgenden Repository-Stände:

| Repository | Commit | Rolle |
| --- | --- | --- |
| [worship-mix](https://github.com/ahaz6/worship-mix/tree/da4b5a2e283b8c5aa48538d1c65dc6f33e0d7377) | `da4b5a2e283b8c5aa48538d1c65dc6f33e0d7377` | Beispiel einer Designübernahme für ein anderes Produkt |
| [worship-keys](https://github.com/ahaz6/worship-keys/tree/985cc15845987aa5937d9fc4cdae878598ebf1e1) | `985cc15845987aa5937d9fc4cdae878598ebf1e1` | Klare Token- und CSS-Referenz |
| [worship-loops](https://github.com/ahaz6/worship-loops/tree/e18dc21c910364f6d48ff24de33c87d95daf57cd) | `e18dc21c910364f6d48ff24de33c87d95daf57cd` | Ursprüngliche Produkt-/Layoutreferenz |

## Befunde

Die `Design-Art.md` in Keys/Loops und `docs/Design-Art.md` in Mix sind
bytegleich. Die gemeinsame Version 1.1 wurde unverändert nach Drums übernommen.

Keys bietet ein übersichtlich gegliedertes `app/globals.css`. Mix dokumentiert
in `docs/DESIGN.md` die Übernahme von Keys und verwendet in
`frontend/app/globals.css` dieselben Tokens mit `--wm-` statt `--wk-`.
Das zeigt, wie eine neue App die Familie übernimmt und ihre Aufgaben eigenständig hält.

Loops enthält mehrere historische CSS-Schichten: zunächst Gold, anschließend
kräftigere Nebula-Farben, danach zurückhaltendere Regeln und schließlich
`Worship Suite 1.1`. Für die gemeinsamen Tokens ist der spätere Suite-Abschnitt
maßgeblich. Ein Kopieren des gesamten Stylesheets würde auch alte Regeln und
Loops-spezifische Komponenten übernehmen.

Die Layouts von Keys/Loops laden Geist Sans und Mono und setzen `lang="en"`.
Branding verwendet getrennte Produktlogos und eigene Browser-Icons.

## Übertragbare Grundlagen und Produktgrenzen

| Bereich | Für Drums übernehmen | Produktspezifisch belassen |
| --- | --- | --- |
| Marke | WORSHIP / Produktname, dunkle Grundwelt | Logos, Claims, Metadaten der Geschwister |
| Styles | Farben, Radien, Motion, Typografie-Regeln | Vollständige CSS-Dateien mit App-spezifischen Selektoren |
| Layout | Klare Trennung von Navigation, Arbeit und Kontext | Setlist, Songbibliothek oder Modulnavigation ohne eigenen Anwendungsfall |
| Keys | Lesbare Zustände, zugängliche Controls | Pad-Engine, Akkorderkennung, Nashville, Voice, Session-Rollen |
| Loops | Ruhiger musikalischer Arbeitsbereich | YouTube-Import, Waveform, Stem-Separation, A/B-Loops |
| Mix | Dokumentierte Übernahme gemeinsamer Komponenten | Mischpultanbindung, Raum-/Mixanalyse, Python-Backend |

Loops ist laut Handoff bereits eine Practice-App für Drummer. Deshalb ist die
Abgrenzung von Worship Drums zu Loops eine zentrale offene Produktentscheidung.
Der Name Drums allein legt weder einen Sequencer noch einen Drum-Trainer fest.

## Technikempfehlung, noch keine Architekturentscheidung

Alle drei Referenzen verwenden Next.js 16, React 19 und TypeScript sowie eine
Node-Untergrenze von 22.13.0. Keys/Mix verwenden Vitest, Loops Node-Tests;
die Laufzeitdienste unterscheiden sich deutlich. Keys hat unter anderem einen
eigenen LAN-Session-Server, Mix ein FastAPI-Backend und Loops eine lokale Medien-API.

Für eine spätere Web-App ist Next.js/React/TypeScript eine naheliegende gemeinsame
Basis. Backend, Speicherung, Offlinebetrieb, Authentifizierung und Audio/MIDI
werden erst aus dem Drums-Anwendungsfall abgeleitet. Jetzt werden keine
Abhängigkeiten oder Dienste vorsorglich installiert.

Analyseumfang: Design-Dokumente, CSS, Paketdefinitionen sowie relevante README-,
Handoff- und Layout-Abschnitte. Die Schwester-Apps wurden nicht gestartet und
ihre Funktions- oder Testberichte nicht unabhängig nachgeprüft.
