# Portfolio Marcel Rittau

Statische Seite ohne Build-Schritt, ohne externe Schriften und ohne Tracking. Läuft auf jedem Hosting, z. B. GitHub Pages.

## Dateien

| Datei / Ordner | Zweck |
|---|---|
| `index.html` | Die Seite: Arbeiten, Agentur Kunden, Vibe Coded Tools, Über mich, Kontakt |
| `arbeiten.js` | Texte, Bilder und Videos der 9 Arbeiten (aus dem Adobe-Portfolio übernommen) |
| `bilder/` | Logo und Bilder der Arbeiten (max. 1.800 px breit) |
| `kunden.enc.js` | Verschlüsselte Kundenprojekte (Texte + Schlüssel für die Bilder), Passwort `rittau` |
| `kunden/*.bin` | Die Kundenbilder, jedes einzeln verschlüsselt |
| `kunden-verschluesseln.html` | Werkzeug zum Bearbeiten, Bilder hinzufügen, Passwort ändern. **Nicht hochladen.** |
| `impressum.html`, `datenschutz.html` | Rechtliches. Im Datenschutz noch den Hosting-Anbieter eintragen |
| `tools/` | Platz für Loop Lab und die Photoshop-Skripte |

## Lokal ansehen

Die Kundenbilder laden nur über einen Webserver, nicht per Doppelklick. Im Ordner im Terminal:

    python3 -m http.server 8000

Dann http://localhost:8000 öffnen.

## Arbeiten ändern

- Kachel (Titel, Untertitel, Bereiche, Kontext): oben in `index.html` im Block `ARBEITEN`
- Detailseite (Texte, Bilder, Videos): `arbeiten.js`. Blöcke: `{"t":"text","p":["Absatz"]}`, `{"t":"img","src":"bilder/…"}`, `{"t":"embed","src":"https://…"}`
- Bildmodule wie im alten Portfolio: `{"t":"grid","rows":[[{"src":"bilder/…","w":49.7},{"src":"…","w":49.7}]]}`. `w` ist die Breite in Prozent, jede Zeile wird mittig gesetzt.
- Kunden-Kacheln zeigen ein Standbild mit 40 % Deckkraft und den Firmennamen. Beim Hovern läuft die Animation. Ein Logo kann pro Projekt im Feld `logo` hinterlegt werden.

## Kundenbereich

1. `kunden-verschluesseln.html` über den lokalen Webserver öffnen.
2. Bisheriges Passwort, „Entschlüsseln und laden“.
3. JSON bearbeiten. Neue Bilder über „Bilder wählen“ verschlüsseln, die ZIP in `kunden/` entpacken und die kopierten Einträge ins JSON setzen.
4. Passwort wählen, neue `kunden.enc.js` herunterladen und die alte ersetzen.

Beim Passwortwechsel bleiben die Bilder gültig. Ein kurzes Passwort wie `rittau` lässt sich durch Ausprobieren knacken, für heikle Arbeiten lieber ein längeres nehmen.

## Downloads für Tools

Datei in `tools/` legen und bei der Aktion `href` eintragen, z. B. `{typ:"datei",label:"Loop Lab öffnen",href:"tools/loop-lab.html"}`. Solange `href:null` ist, ist der Button deaktiviert.
