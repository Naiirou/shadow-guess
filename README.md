# SHADOW//GUESS

Ein simples Anime-Silhouettenquiz für eine Rallye. Kein Build, keine Installation, kein Backend.

## Start

`index.html` im Browser öffnen. Internet ist erforderlich, um die Charakterbilder über die öffentliche Jikan API zu laden. Bei lokalen `file://`-Seiten kann es je nach Browser CORS-Einschränkungen geben; alternativ mit `python -m http.server 8000` im Ordner starten und `http://localhost:8000` öffnen. Auf dem Tablet kannst du den Ordner auf GitHub Pages, Netlify oder einen anderen statischen Hoster legen.

## Spiel

- 3 Schwierigkeitsgrade mit je 9 Figuren
- 6 Versuche (einstellbar)
- Keine Figur wiederholt sich innerhalb einer Gruppe
- Silhouette -> Reveal -> Richtig/Falsch
- Übersicht und Punktestand
- Neue Gruppe startet bei 0

## Punkte und Figuren ändern

Punkte und Versuchszahl unter "Spielregeln & Punkte ändern" auf dem Startbildschirm ändern. Figuren in `characters.js` bearbeiten.

## Bilder – wichtig

Die App lädt **automatisch Charakter-Porträts** über die Jikan API. Die Motive sind deshalb **nicht kuratiert** und oft nur Kopfporträts statt Ganzkörperbilder. Bei Eren und Okarun kann die automatisch geladene Form falsch sein. Für die Rallye empfiehlt es sich, die gewünschten eigenen PNGs (möglichst freigestellte Ganzkörperfiguren) zu verwenden.

Eigene Dateien dauerhaft hinterlegen:
1. `images/` Ordner erstellen.
2. Bild dort ablegen, z.B. `images/pikachu.png`.
3. Beim entsprechenden Eintrag in `characters.js` `image:'images/pikachu.png'` ergänzen.

Alternativ im Quiz über das Datei-Eingabefeld ein Bild wählen; das gilt nur für die aktuelle Sitzung.

Die automatische Silhouette entfernt helle, mit dem Bildrand verbundene Hintergrundbereiche und färbt den Rest schwarz. Das funktioniert gut bei weißem Hintergrund, aber nicht immer bei komplexen Bildern. Manche externe Bildserver verhindern die Canvas-Verarbeitung (CORS). In dem Fall nutzt die App einen CSS-Fallback, der bei nichttransparenten Bildern wieder eine schwarze Box ergeben kann. **Vor der Veranstaltung alle 27 Motive testen.**

## Datenschutz / Technik

Kein Account, keine Datenbank, kein Tracking. Nur die Jikan API und deren Bildserver werden beim Laden der Bilder kontaktiert. Spielstand bleibt nur im geöffneten Tab. Für garantierten Offline-Betrieb eigene Bilder lokal hinterlegen.
