# CLAUDE.md – beo-dialog Website

## Projektübersicht

Statische Website der Beratergruppe **beo-dialog GbR** (Münster).
Stack: reines HTML/CSS/JS – kein Build-Tool, kein Framework, kein npm.
Deployment: GitHub → Netlify (noch einzurichten).

**Seitenmodell seit 08.09.2026: One-Pager.** Alle Angebote liegen als
Anker-Sections auf `index.html` und stehen als Hauptnavigationspunkte oben.
Unterseiten gibt es **nur noch für die vier Personen**. Grundlage der Texte
ist `texte-entwurf.md` (Stand 28.07.2026).

---

## Dateistruktur

```
beo-dialog/
├── index.html                    # One-Pager: Hero, 3 Säulen, 5 Angebote,
│                                 #   Spannungsband, Über uns, FAQ, Kontakt
├── style.css                     # Einzige CSS-Datei für alle Seiten
├── paul-fortmeier.html           # Personen-Profil
├── sabine-reese-fortmeier.html   # Personen-Profil
├── dafni-bouzikou.html           # Personen-Profil
├── christoph-holbein-munske.html # Personen-Profil
├── archiv/                       # Nicht mehr verlinkt, nur zur Textsicherung
│   ├── supervision.html
│   ├── coaching.html
│   ├── teamentwicklung.html
│   ├── organisationsberatung.html
│   └── training.html
├── bilder/                       # Alle Bilder (jpg)
├── texte-entwurf.md              # Textgrundlage des One-Pagers
├── texte-entwurf-kommentiert.md  # Herkunft jeder Passage
├── profilseiten-entwurf.md       # Texte der vier Personenseiten
└── fotoshooting-shotliste.md
```

---

## Navigation (identisch auf allen Seiten)

Sieben Punkte, keine Dropdowns. Auf `index.html` Anker (`#…`),
auf den Personenseiten `index.html#…`.

```
Supervision & Coaching · Teamentwicklung · Organisationsberatung ·
Training · Seminare · Über uns · Kontakt
```

- **Training** meint ausschließlich **gruppendynamisches Training**
  (H2 im Block lautet entsprechend „Gruppendynamisches Training").
- **Seminare** meint Methoden-/Verfahrensformate: Soziokratie, TZI,
  Konfliktklärung, Moderation.
- Mobiles Burger-Menü ab **≤ 1024px** (nicht 768px – sieben Labels
  brauchen die Breite).
- Der aktive Punkt wird beim Scrollen per IntersectionObserver
  mit `.current` markiert.

---

## Sections auf index.html

| # | Section | id | Hintergrund |
|---|---------|-----|-------------|
| 1 | Hero (Foto, H1, Intro, CTA) | – | warm-white |
| 2 | Drei Säulen | – | weiß |
| 3 | Supervision & Coaching | `#supervision-coaching` | warm-white |
| 4 | Teamentwicklung | `#teamentwicklung` | weiß (`.alt`) |
| 5 | Organisationsberatung | `#organisationsberatung` | warm-white |
| 6 | Gruppendynamisches Training | `#training` | weiß (`.alt`) |
| 7 | Seminare | `#seminare` | warm-white |
| 8 | Spannungsband (5 Paare) | – | dunkel |
| 9 | Über uns + 4 Porträts | `#ueber-uns` | warm-white |
| 10 | FAQ (Accordion) | `#faq` | weiß |
| 11 | Kontakt | `#kontakt` | rot |

Angebotsblöcke folgen alle demselben Muster:
`.angebot > .section-inner.wide > .angebot-grid` mit
`.angebot-titel` (H2 links) und `.angebot-text` (Fließtext + `.angebot-liste`).
Zweispaltig ab 1025px, darunter untereinander.

---

## Design-System

### Farben (CSS Custom Properties in `:root`)

| Variable         | Wert      | Verwendung                        |
|-----------------|-----------|-----------------------------------|
| `--beo-red`     | `#d04507` | Primärfarbe, Headlines, CTAs      |
| `--beo-red-dark`| `#a63705` | Hover-Zustand für CTAs            |
| `--warm-white`  | `#FAF8F5` | Seitenhintergrund                 |
| `--warm-gray`   | `#E8E4DF` | Trennlinien, Tags                 |
| `--text-dark`   | `#2C2825` | Fließtext, Spannungsband, Footer  |
| `--text-medium` | `#5A5550` | Body-Text in Sections             |
| `--text-light`  | `#8A8580` | Subtitles, Labels, sekundär       |

### Typografie

- **Display / Überschriften:** `Source Serif 4` (Google Fonts, opsz 8–60, weight 400/600)
- **Body / UI:** `Work Sans` (Google Fonts, weight 300/400/500/600)
- Basis-Fontsize: `18px`, Line-height: `1.7`

### Spacing

`--space-xs: 0.5rem · --space-sm: 1rem · --space-md: 2rem · --space-lg: 4rem · --space-xl: 6rem · --space-xxl: 10rem`

---

## Team

| Name                   | Datei                          | E-Mail                  | Telefon          | Foto |
|-----------------------|-------------------------------|-------------------------|------------------|------|
| Paul Fortmeier        | paul-fortmeier.html           | pf@beo-dialog.de        | 0173 358 4904    | 838.jpg |
| Sabine Reese-Fortmeier| sabine-reese-fortmeier.html   | srf@beo-dialog.de       | 0173 28 11 980   | 450_JPG_1500pixel.jpg |
| Dafni Bouzikou        | dafni-bouzikou.html           | db@beo-dialog.de        | 0176 260 338 65  | 468_JPG_1500pixel.jpg |
| Christoph Holbein-Munske | christoph-holbein-munske.html | chm@beo-dialog.de    | 0177 50 75 251   | 508_JPG_1500pixel.jpg |

Hero-Bild: `592_JPG_1500pixel.jpg` · Über-uns-Bild: `815_JPG_1500pixel.jpg`
Keine Rollenzeilen unter den Porträts – alle machen fast alles. Die beiden
echten Exklusivitäten stehen im jeweiligen Angebotsblock: Gruppendynamik
(alle außer Christoph), TZI und Soziokratie (nur Christoph).

Zentrale Kontaktadresse: kontakt@beo-dialog.de · 0251 53 09 71 83
Adresse: Nikolaus-Groß-Weg 5, 48167 Münster

---

## Offene TODOs

- [ ] **Bilder ohne Wasserzeichen** – alle jpg in `bilder/` tragen noch das
      Wasserzeichen der Fotografin. Vor Livegang durch Freigabe-Dateien ersetzen.
- [ ] **FAQ: vier Antworten fehlen** – Regionen/online, Dauer, Kosten,
      Kostenträger (siehe `offene-fragen.md`)
- [ ] FAQPage-Schema (JSON-LD) für die FAQ ergänzen – Rich Snippets bei Google
- [ ] Impressum und Datenschutz-Seiten erstellen (Footer-Links sind noch `#`)
- [ ] Netlify-Deployment einrichten (GitHub-Repo → Netlify verbinden)
- [ ] Telefonnummer in den Kontaktblock?
- [ ] Favicon ergänzen
- [ ] `test.md` löschen (nur Sync-Test)
- [ ] Bilder komprimieren (aktuell 0,7–1,5 MB pro Datei – zu schwer fürs Web)

---

## Hochladen zu GitHub

Repo: `christophholbein/beo-dialog` (öffentlich). Schrittweise Anleitung inklusive
Fehlerbehandlung: `Abbeney/_setup/Website-auf-GitHub-hochladen.md`.

Kurzfassung:
```powershell
cd "C:\Users\chris\Documents\Claude Code\beo-dialog"
git status ; git add -A ; git commit -m "warum, nicht was" ; git push
```
Aus Cowork heraus ist nur `commit` möglich, kein `push` – dort fehlen die
GitHub-Zugangsdaten. Der Push muss lokal in PowerShell oder VS Codium erfolgen.

Was nicht ins Repo gehört, steht in `.gitignore` – vor allem die internen
Textentwürfe und `offene-fragen.md`. Bei einem späteren Netlify-Deployment würde
sonst jede Datei im Repo auch als Website ausgeliefert.

## Konventionen

- Alle Änderungen direkt in den HTML/CSS-Dateien, kein Build-Step
- CSS nur in `style.css`, keine `<style>`-Tags in HTML
- **Keine neuen Unterseiten für Angebote.** Neue Angebote werden zusätzliche
  Anker-Sections auf `index.html` plus ein Navigationspunkt.
- Neue Personenseiten folgen dem Muster der bestehenden vier
- Nav und Footer sind auf allen Seiten identisch – bei Änderungen alle
  fünf HTML-Dateien anfassen
- Bilder immer in `bilder/`
