# Visuals by Preecie – Portfolio-Website

> **Branch `experiment` = Konzept „Vireal – Visuals & Web“** (Fabian + Max gemeinsam, noch NICHT auf `main` übernehmen, nur auf Zuruf „übernehmen“).
> Unterschiede zu `main`: Logo „Vireal“ (Vektor aus Fabis Vorlage: `img/vireal-logo.svg`, im HTML als Symbol `#logo` mit `.logo`, Farbe per `color`; groß im Statement mit Unterzeile „Visuals & Web“ in Mono; Icons/og.jpg aus dem Logo, Favicon = „Vi“), Hero = Latest Visual (Flyer-Druckbogen) + Latest Web (Browser + Handy, `.web-src`), am Handy/Tablet hoch wischbar (`.hero-rail`, Balken `.hero-dots`);
> Portfolio mit Bereichen Visuals / Web (`.chapters`, `#ch-visuals`, `#ch-web`); Web-Projekte als `.case` (Screenshots ganze Seite in `img/web/`: Desktop 1200 px, Handy 540 px, .webp + .avif; im Rahmen scroll-gekoppelt);
> Großansicht Web `#webview` (Desktop + Handy synchron, am Handy Umschalter); About us mit zwei Personen (`.crew`, Foto Max fehlt: `.ph-photo`); Logo-Wand als Flex (letzte Reihe mittig), Beautybar mit Tag „Web“;
> Anfrage: zuerst „Visual oder Web?“ (`.modes`). Visual = Schriftmuster: Was brauchst du? (Flyer, Motion, Flyer-Serie) · Format · Vibe · Inspirationen. Web = Website-Bedienelemente, Fragen nach Briefing-Best-Practice (recherchiert Nov 2026): Was soll die Seite bringen? · Wer soll draufkommen? + Was macht euch besonders? · Wie groß? (Einzelauswahl) · Was muss sie können? (Schalter) · Welcher Look? (Mini-Vorschauen) · Was ist schon da? + Was sollen wir übernehmen? · Online-Stand (aktuelle Seite, Vorbilder, Konkurrenz) · Rahmen (Budget-Spannen mit Max abstimmen, Betreuung danach). Danach für beide Farben + Eckdaten. Web-Plakat = Browserfenster, zeigt nur ausgefüllte Zeilen.
> Gearbeitet mit: KEINE Logos (Rechte unklar), nur Namen als Abspann (abwechselnd voll/Kontur), Hover-Vorschau bleibt; auch der content.json-Loader setzt nur Namen ein. `img/logos/` wird nicht mehr genutzt.
> Portfolio: nur noch Flyer und Motion Design (DJ Graphics + Branding raus). Bereichs-Leiste `.chapters` = zwei Hälften in Inter Tight mit Mono-Unterzeile, Inhalt jeweils mittig, ohne Pfeile, klar getrennt von „Portfolio“ (Archivo) und den Kategorie-Tabs.
> Neutral statt nur Club/Nachtleben (Wunsch Fabi): Zielgruppe Läden, Studios, Gastro, Events, Marken (Tattoo, Sport, Autohandel …). Vibes: Clean, Edel, Modern, Natürlich, Warm, Bold, Retro, Dark, Bunt, Überrasch mich (Neon/Chrome/Y2K/Grunge raus). Platzhalter neutral, Ticket-Kleintext „Anfrage · Visual & Web“.
> Feinschliff 19.11.: Flyer groß in fester Reihenfolge Winter Tour (YE) · Winter Opening (Serie) · Doubledown (gelb) · Shake Sum · Jersey Night · SYNC, alle anderen im Archiv. Richtungsfilter aus (`return;` im Filter-Skript). Format-Hinweis kurz („Feed · 4:5“). Kein Satz „Auffallen …“ mehr. CTAs einheitlich „Projekt anfragen“: Header = ruhiger Umriss-Button (führt zu #kontakt), Statement = Druckbogen-Button `.cta-sheet` (heller Bogen mit Schnittmarken an den Ecken, rasten beim Sichtbarwerden einmal ein, gehen beim Überfahren auseinander; ersetzt das Ticket); Verlauf nur noch beim Absenden. Hero-Zeile `.hero-claim` „Vireal — Flyer, Motion & Websites – aus einer Hand“. Ton: „Hey Vireal!“, „Schnelle Antwort.“
> Web-Projekt-Infos (`.case-info`): ruhig in Inter Tight, keine Mono-Tabelle (wirkte nach Baukasten): Titel, `.case-meta`, Satz, `.case-facts` (Umfang, Funktionen, Farben), weißer Button „Desktop + Handy ansehen“ + Link „Live ansehen“.
> Handy-Rahmen `.pf` schlank (1,1 % Rand, feine Kante) – nicht wieder dick machen.
> Alle Links/Kontakte auf Vireal: Instagram @vireal.media (`https://www.instagram.com/vireal.media/`, DM `https://ig.me/m/vireal.media`), Domain vorerst `https://www.vireal.media/` (Annahme, noch bestätigen), Icons + og.jpg mit „VI“/„VIREAL“. Impressum/Datenschutz nennen noch nur Fabian – bei gemeinsamem Auftritt (GbR) beide eintragen.

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
- Kunden/Clubs als Logo-Wand (`.logo-wall`): weiße Logos in `img/logos/`. Kunden ohne Logo-Datei stehen als Schriftzug (`.wm`) drin. Am Desktop zeigt Hover eine Flyer-Vorschau. Logos laden sofort mit der Seite (kein `loading="lazy"`, sonst erscheinen sie erst beim Hinscrollen).
- Die Logos von Savage, Filmcasino, Barfly und Collective Flow sind aus den Flyern freigestellt. Sobald Originaldateien da sind (PNG/SVG weiß auf transparent), ersetzen. Für 333 Club, 794 Studio, Destination Gaswerk und Voyage fehlen die Logos noch.

## Technik, die bewusst so ist
- Anfrage-Bereich (`#brief`) ist ein Live-Briefing-Plakat: Auswahl als Schriftmuster (jeder Vibe in seinem Stil), danach Feld „Inspirationen“ (Links/Accounts/Worte → Zeile „Inspiration:“); die Fragen-Überschriften (`.q-t`) in normaler Schrift (Inter Tight, kein Versal); statt Hinweistext trägt jede Option ein kleines rosa „+“ (gewählt dreht es zum „×“) und neben der Frage steht „N gewählt“; Optionen leuchten beim ersten Sichtbarwerden einmal nacheinander auf. Neue Frage „Welches Format?“ (Feed 4:5, Story 9:16, Screen 16:9, Druck – je mit Rechteck im echten Seitenverhältnis), landet als Zeile „Format:“ in der Nachricht. Eckdaten als Felder darunter. Das Plakat zeigt live die fertige DM-Nachricht („Wagwan Preecie!“ + Datenblatt), gewählte Farben färben Glow und Farbbalken. Enter springt zum nächsten Feld, Tippen daneben schließt die Tastatur.
- Hintergrund `.space`: Nebel + Sternenhimmel (zwei ruhige Sternebenen + zwei Ebenen `.space i`, die langsam funkeln, nur opacity; bewusst dezent: Ebenen .3 / .22, Funkeln max .45). Nicht kräftiger machen – Kunde wollte es nach Test wieder dezenter.
- Zwischen Intro und Portfolio steht bewusst nichts (kein Laufband, kein Trenner) – Laufband wirkte wie Baukasten.
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
- Bilder 1080 px breit als `.webp` + `.avif`. Feed 4:5 ist Standard. Story 9:16: im `style` der `button.flyer` `--ar:1080 / 1920` setzen und `class="is-story"` an die `<figure>`. Storys erscheinen dann automatisch im schlichten Handy-Rahmen (CSS, `<picture>` = Gehäuse) ; jede Bildunterschrift bekommt per JS einen Format-Hinweis (`.cap-tags` > `.fmt-tag`: „Feed · 4:5 · Instagram-Post“ bzw. „Story · 9:16 · Handy-Vollbild“, Serien-Hinweis in derselben Zeile); Feed-Posts bleiben frei. Die Großansicht zeigt immer das reine Bild.
- Serie (Hauptflyer + Infoseiten): `<figure data-series="img/a-2.webp, img/a-3.webp">`. Das Skript legt die Seiten als Stapel dahinter, schreibt „Serie · N Motive“ und die Großansicht blättert durch alle Seiten (Balken oben). Auf der Seite selbst kann man die Serie seitlich durchwischen wie ein Karussell (`.ser-peek` = Nachbarbild schiebt mit; Serienbilder werden vorgeladen, sobald die Serie in die Nähe kommt, bis dahin zeigt das Nachbarbild die Vorschau aus `img/t/` – nie grau; am Handy eigene Touch-Geste, die bei seitlicher Bewegung das Seiten-Scrollen blockiert; Maus/Trackpad/Pfeiltasten, ohne Pfeil-Buttons; Balken unter dem Bild, verschoben wird per CSS `translate`, nicht `transform`, weil das Hover-Zoom auf `transform` liegt). Antippen öffnet die Großansicht beim gerade sichtbaren Motiv.
- Richtung: `data-sector="Club &amp; Event"` / `"Gastro"`. Ab zwei Richtungen erscheint unter „Flyer“ die Filterleiste.
- „Mehr aus dem Archiv“ ist eine Slideshow: Skript packt die Figures in `.more-track` und bewegt sie per Web Animation (`track.animate`, läuft auf dem Grafik-Thread; kein scrollLeft und keine JS-Schleife, sonst zittert es am iPhone). Läuft ab dem Laden der Seite, auch wenn sie noch nicht sichtbar ist (beim Runterscrollen schon in Bewegung). Stoppt bei Maus/Fokus, ziehbar mit Maus/Finger/Trackpad. Bilder dort sind 720-px-Vorschauen aus `img/t/` (eager, niedrige Priorität); die Großansicht lädt immer das volle Bild aus `img/`. Neuer Archiv-Flyer: Vorschau in `img/t/` mit anlegen (720 px breit, .avif + .webp).
- Richtungsfilter: Bei „Gastro“ o. Ä. rücken die ersten 5 Treffer groß nach oben (`.featured`), der Rest in die Slideshow; „Alle“ stellt die Originalreihenfolge wieder her. Die Großansicht blättert nur durch sichtbare Flyer in Seitenreihenfolge.
- Großansicht: Pfeile sind fest an der Bühne verankert (nicht am Bild), bleiben bei Story-Formaten an derselben Stelle.
- Motion: Videos in `media/` (720 px breit, H.264, ohne Ton, ~3 MB) + Poster `.webp`; spielen nur, wenn sichtbar. Jede Kachel ist ein `button.clip-btn` (darin `span.clip-box` + `video.clip`) und öffnet das Video groß in derselben Großansicht (`#v-vid`), blättern zwischen den Videos möglich. Bildunterschrift bekommt „Video · 9:16 · Story“.
- Rohdateien kommen aus Fabians Drive-Ordner „Grafiken Olo“ (Normal / Motion).

## Neuen Flyer hinzufügen
1. Bild als `.webp` UND `.avif` in `img/` ablegen.
2. Eine `<figure>` wie die bestehenden kopieren, entweder in `.featured` (große, versetzte Flyer) oder in `.more` ("Mehr aus dem Archiv").

Die Großansicht erkennt alle `button.flyer` automatisch.
Wechselt der Hero auf einen neuen Flyer: in `.intro` Bild, Farbschein (`.ambient img`, kleine unscharfe Version des Flyers), Texte, Farbbalken (`.swatch`) und Druckbogen-Angaben (`.pC-spec`) anpassen. Der Farbschein läuft per `mask-image` auf `.ambient` nach unten/seitlich ins Transparente aus und geht so nahtlos in den Seitenhintergrund (`.space`) über – kein Strich am Hero-Ende. Nie wieder auf deckendes `var(--bg)` auslaufen lassen.

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
