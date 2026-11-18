# Visuals by Preecie – Portfolio-Website

Portfolio von Fabian Pinkawa ("Preecie"): Grafikdesigner, arbeitet deutschlandweit (Kunden bisher v. a. Augsburg/München; auf der Seite bewusst "deutschlandweit", keine Städte). Er macht Club-Flyer, Motion Design, DJ Graphics und Branding. Logos bietet er NICHT mehr an.
Statische Seite ohne Build-Schritt (HTML/CSS/JS). Hosting: GitHub Pages (dieser Ordner ist das Repo-Root, Branch `main`). Domain bei Hostinger, DNS zeigt auf GitHub.

## Dateien
- `index.html`: die ganze Startseite, CSS und JS inline
- `impressum.html`, `datenschutz.html`, `legal.css`: Rechtsseiten
- `404.html`: Fehlerseite mit absoluten Pfaden (`/…`), wird von GitHub Pages automatisch genutzt
- `img/`: jeder Flyer als `.webp` + `.avif` (über `<picture>`), `og.jpg`, Icons
- `fonts/`: lokale, gesubsettete woff2-Schriften (DSGVO: kein Google Fonts)
- `.nojekyll` (GitHub Pages liefert die Dateien 1:1 aus, ohne Jekyll), `robots.txt`, `sitemap.xml`, `site.webmanifest`, `favicon.ico`

## Lokal ansehen
`python -m http.server 8765` in diesem Ordner, dann http://localhost:8765/ aufrufen. Alternativ die VS-Code-Erweiterung "Live Server".

## Feste Vorgaben des Kunden (nicht ändern ohne Rückfrage)
- Fabian wird NICHT als DJ dargestellt (kein "selbst DJ", kein "hinter dem Pult"). Zielgruppe breit: Clubs, Events, Gastro, Marken.
- Dunkel, clean, elegant, "Künstler-Look". Nicht verspielt und kein Baukasten-Look.
- Maximal 3 Schriften: Archivo (Display, kursiv/condensed), Inter Tight (Text), Geist Mono (Labels).
- Keine Nummerierungen wie 01/02/03.
- Hero zeigt zuerst das Werk: aktuellster Flyer (YE Tour 26/27, ohne Serie; die Winter-Opening-Serie steht im Portfolio) mit dem Label "Latest Work". Der Hintergrund bewegt sich nur dezent ("Atmen"), kein Mond und kein Planet.
- Überschriften "Portfolio" und "About me" auf Englisch, alle anderen Texte auf Deutsch, Anrede "du".
- Kein Ablauf-Abschnitt, kein Zahlungssystem. Die Seite zeigt nur Referenzen und Kontaktwege.
- Header-Button: Instagram-Verlauf "DM für Anfrage" → https://ig.me/m/visualsbypreecie
- Kunden/Clubs als Logo-Wand (`.logo-wall`): weiße Logos in `img/logos/`. Kunden ohne Logo-Datei stehen als Schriftzug (`.wm`) drin. Am Desktop zeigt Hover eine Flyer-Vorschau.
- Die Logos von Savage, Filmcasino, Barfly und Collective Flow sind aus den Flyern freigestellt. Sobald Originaldateien da sind (PNG/SVG weiß auf transparent), ersetzen. Für 333 Club, 794 Studio, Destination Gaswerk und Voyage fehlen die Logos noch.

## Technik, die bewusst so ist
- Anfrage-Bereich (`#brief`) ist ein Live-Briefing-Plakat: Auswahl als Schriftmuster (jeder Vibe in seinem Stil), Fragen als große Überschriften mit rosa Hinweis „Antippen · mehrere möglich“, Optionen leuchten beim ersten Sichtbarwerden einmal nacheinander auf. Eckdaten als Felder darunter. Das Plakat zeigt live die fertige DM-Nachricht („Wagwan Preecie!“ + Datenblatt), gewählte Farben färben Glow und Farbbalken. Enter springt zum nächsten Feld, Tippen daneben schließt die Tastatur.
- Ticket-CTA: Innenleben hat `pointer-events: none`, damit iOS Safari die ganze Fläche als Link trifft.
- Frischer Seitenaufruf startet immer oben (Absicherung für Vorschau-Umgebungen). Zurück/Vor, #Anker und Text-Fragmente bleiben unberührt.
- Großansicht der Flyer ist ein `<dialog>` mit `history.pushState`: Die Zurück-Geste schließt die Großansicht, Doppelklick ist abgesichert.
- Bilder laden eager mit niedriger Priorität, ohne Einblend-Animation (Ladetempo war ein Kundenwunsch).
- `prefers-reduced-motion` wird respektiert.

## Portfolio-Kategorien
Unter "Portfolio" kann man zwischen den Kategorien Flyer / Motion Design / DJ Graphics / Branding wechseln. Am Desktop geht das über Tabs und Pfeile, am Handy über eine wischbare Leiste (`.cat-bar`, Panels `#p-flyer`, `#p-motion`, `#p-dj`, `#p-branding`).
Nur Flyer hat bisher Inhalt. Die anderen Kategorien zeigen den Platzhalter `.cat-soon` ("In Arbeit"). Wenn Arbeiten dazukommen: Inhalt ins jeweilige Panel einfügen und `.cat-soon` löschen.
- Bilder: wie bei den Flyern als `<figure>` mit `button.flyer`
- Motion: `<video muted loop playsinline autoplay>` mit Poster

Ohne JS ist nur Flyer sichtbar.

## Formate, Serien, Richtungen
- Bilder 1080 px breit als `.webp` + `.avif`. Feed 4:5 ist Standard. Story 9:16: im `style` der `button.flyer` `--ar:1080 / 1920` setzen und `class="is-story"` an die `<figure>`.
- Serie (Hauptflyer + Infoseiten): `<figure data-series="img/a-2.webp, img/a-3.webp">`. Das Skript legt die Seiten als Stapel dahinter, schreibt „Serie · N Motive“ und die Großansicht blättert durch alle Seiten (Balken oben). Auf der Seite selbst kann man die Serie seitlich durchwischen wie ein Karussell (`.ser-peek` = Nachbarbild schiebt mit; am Handy eigene Touch-Geste, die bei seitlicher Bewegung das Seiten-Scrollen blockiert; Maus/Trackpad/Pfeiltasten, ohne Pfeil-Buttons; Balken oben im Bild, verschoben wird per CSS `translate`, nicht `transform`, weil das Hover-Zoom auf `transform` liegt). Antippen öffnet die Großansicht beim gerade sichtbaren Motiv.
- Richtung: `data-sector="Club &amp; Event"` / `"Gastro"`. Ab zwei Richtungen erscheint unter „Flyer“ die Filterleiste.
- „Mehr aus dem Archiv“ ist eine Slideshow: Skript packt die Figures in `.more-track` und bewegt sie per Web Animation (`track.animate`, läuft auf dem Grafik-Thread; kein scrollLeft und keine JS-Schleife, sonst zittert es am iPhone). Stoppt bei Maus/Fokus, ziehbar mit Maus/Finger/Trackpad. Bilder dort sind 720-px-Vorschauen aus `img/t/` (eager, niedrige Priorität); die Großansicht lädt immer das volle Bild aus `img/`. Neuer Archiv-Flyer: Vorschau in `img/t/` mit anlegen (720 px breit, .avif + .webp).
- Richtungsfilter: Bei „Gastro“ o. Ä. rücken die ersten 5 Treffer groß nach oben (`.featured`), der Rest in die Slideshow; „Alle“ stellt die Originalreihenfolge wieder her. Die Großansicht blättert nur durch sichtbare Flyer in Seitenreihenfolge.
- Großansicht: Pfeile sind fest an der Bühne verankert (nicht am Bild), bleiben bei Story-Formaten an derselben Stelle.
- Motion: Videos in `media/` (720 px breit, H.264, ohne Ton, ~3 MB) + Poster `.webp`; spielen nur, wenn sichtbar.
- Rohdateien kommen aus Fabians Drive-Ordner „Grafiken Olo“ (Normal / Motion).

## Neuen Flyer hinzufügen
1. Bild als `.webp` UND `.avif` in `img/` ablegen.
2. Eine `<figure>` wie die bestehenden kopieren, entweder in `.featured` (große, versetzte Flyer) oder in `.more` ("Mehr aus dem Archiv").

Die Großansicht erkennt alle `button.flyer` automatisch.
Wechselt der Hero auf einen neuen Flyer: in `.intro` Bild, Texte, Farbbalken (`.swatch`) und Druckbogen-Angaben (`.pC-spec`) anpassen.

## Automatik (n8n + content.json)
- Der n8n-Workflow committet neue Dateien nach `auto/` und die `content.json` direkt in dieses Repo (GitHub-API, ein Commit pro Lauf). Vor eigenem Arbeiten also immer erst `git pull`.
- `content.json` wird vom n8n-Workflow geschrieben (siehe `n8n/ANLEITUNG-Automatik.md`). Sind die Listen leer, bleibt der fest eingebaute Stand.
- Ein Loader-Skript (`window.__vbpReady`) rendert daraus: Hero (neuester Flyer), Portfolio, die Tabs Motion/DJ/Branding und Logos. Großansicht, Hover-Vorschau und Druck-Details starten erst danach.
- Erlaubte Pfade in der JSON: nur `auto/…`, `img/…`, `media/…`. Texte werden immer als Text eingesetzt, nie als HTML.

## Vor dem Livegang offen
- [x] Domain `https://www.visualsbypreecie.de` eingetragen (index.html, robots.txt, sitemap.xml)
- [ ] `CNAME`-Datei (Inhalt: `www.visualsbypreecie.de`) erst anlegen, wenn die Domain gekauft ist und auf GitHub zeigt – sonst leitet github.io auf eine tote Domain um
- [ ] Impressum: Name, Adresse, Telefon, E-Mail, ggf. USt-IdNr./W-IdNr. Die Platzhalter sind rosa markiert (`class="ph"`).
- [ ] Datenschutz: Anschrift/E-Mail eintragen (Name Fabian Pinkawa und BayLDA sind fertig).
- [ ] Optional WhatsApp/E-Mail als Kontaktweg. Die Zeilen in `index.html` sind auskommentiert, der WhatsApp-Abschnitt in `datenschutz.html` ebenfalls (Nummern dann anpassen).
- [x] GitHub: Repo `maxiforstermf-creator/visuals-by-preecie`, Pages aus Branch `main` / root (Vorschau: https://maxiforstermf-creator.github.io/visuals-by-preecie/).
- [ ] Nach Domainkauf: Settings → Pages → Custom domain `www.visualsbypreecie.de` eintragen, danach "Enforce HTTPS".
- [ ] Hostinger-DNS: nur die 4 A-Records 185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153 auf `@` + CNAME `www` → `maxiforstermf-creator.github.io`. ALLE anderen A/AAAA-Records löschen (sonst kein SSL, siehe BeautyBar).
- [ ] `lastmod` in `sitemap.xml` am Livegang-Tag aktualisieren (zuletzt 2026-11-18).
- [ ] Nach dem Upload prüfen: 404-Seite, HTTPS-Weiterleitung, Ladezeit
- [ ] About-Foto `img/fabian.webp` ist aus einem Instagram-Screenshot ausgeschnitten: durch Originaldatei ersetzen (800 × 1000, 4:5). Fotograf klären bzw. Credit in die figcaption.
- [ ] Bildrechte: Drake-Flyer ersetzen oder Rechte klären. Für Flyer mit Fotos von Artists/Fotografen Einverständnis der Kunden einholen.
