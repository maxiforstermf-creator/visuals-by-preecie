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
- Hero zeigt zuerst das Werk: aktuellster Flyer (SYNC) mit dem Label "Latest Work". Der Hintergrund bewegt sich nur dezent ("Atmen"), kein Mond und kein Planet.
- Überschriften "Portfolio" und "About me" auf Englisch, alle anderen Texte auf Deutsch, Anrede "du".
- Kein Ablauf-Abschnitt, kein Zahlungssystem. Die Seite zeigt nur Referenzen und Kontaktwege.
- Header-Button: Instagram-Verlauf "DM für Anfrage" → https://ig.me/m/visualsbypreecie
- Kunden/Clubs als Logo-Wand (`.logo-wall`): weiße Logos in `img/logos/`. Kunden ohne Logo-Datei stehen als Schriftzug (`.wm`) drin. Am Desktop zeigt Hover eine Flyer-Vorschau.
- Die Logos von Savage, Filmcasino, Barfly und Collective Flow sind aus den Flyern freigestellt. Sobald Originaldateien da sind (PNG/SVG weiß auf transparent), ersetzen. Für 333 Club, 794 Studio, Destination Gaswerk und Voyage fehlen die Logos noch.

## Technik, die bewusst so ist
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
- [x] Domain `https://www.visualsbypreecie.de` eingetragen (index.html, robots.txt, sitemap.xml, `CNAME`-Datei für GitHub Pages)
- [ ] Impressum: Name, Adresse, Telefon, E-Mail, ggf. USt-IdNr./W-IdNr. Die Platzhalter sind rosa markiert (`class="ph"`).
- [ ] Datenschutz: Anschrift/E-Mail eintragen (Name Fabian Pinkawa und BayLDA sind fertig).
- [ ] Optional WhatsApp/E-Mail als Kontaktweg. Die Zeilen in `index.html` sind auskommentiert, der WhatsApp-Abschnitt in `datenschutz.html` ebenfalls (Nummern dann anpassen).
- [ ] GitHub: Repo anlegen, Settings → Pages → Branch `main` / root. Custom domain `www.visualsbypreecie.de` eintragen, danach "Enforce HTTPS".
- [ ] Hostinger-DNS: nur die 4 A-Records 185.199.108.153 / .109 / .110 / .111.153 auf `@` + CNAME `www` → `<github-name>.github.io`. ALLE anderen A/AAAA-Records löschen (sonst kein SSL, siehe BeautyBar).
- [ ] `lastmod` in `sitemap.xml` aktualisieren.
- [ ] Nach dem Upload prüfen: 404-Seite, HTTPS-Weiterleitung, Ladezeit
- [ ] About-Foto `img/fabian.webp` ist aus einem Instagram-Screenshot ausgeschnitten: durch Originaldatei ersetzen (800 × 1000, 4:5). Fotograf klären bzw. Credit in die figcaption.
- [ ] Bildrechte: Drake-Flyer ersetzen oder Rechte klären. Für Flyer mit Fotos von Artists/Fotografen Einverständnis der Kunden einholen.
