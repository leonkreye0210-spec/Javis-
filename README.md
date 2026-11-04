# Jarvis

Freihändiger Sprachassistent im Browser (Handy und iPad), inspiriert vom Jarvis aus Iron Man.

## Funktionen
- Hört automatisch zu und antwortet per Sprache (Web Speech API)
- Goldenes Hologramm-Design, das beim Sprechen pulsiert
- Kamera: auf „Schau mal, was ist das?" sieht Jarvis hin
- Deutsche, ruhige Männerstimme (bessere Stimmen in den iOS-Einstellungen laden)

## Aufbau
Nur Frontend: eine einzige Datei, `index.html`.
Die Seite schickt Fragen per `POST /api/chat` an ein Backend, das die Claude API aufruft.
Dieses Backend ist nicht Teil dieses Repos.

Erwartete Anfrage:
    { "messages": [{ "role": "user", "content": "…" }], "image": "<base64 jpeg oder null>", "now": "<Datum/Uhrzeit>" }
Header: `x-token: <Zugangscode>`

Erwartete Antwort:
    { "text": "…" }

## Starten
Die Seite von einem Server ausliefern, der `/api/chat` bereitstellt (HTTPS nötig für Mikrofon und Kamera).

## Spotify (optional)
1. Auf developer.spotify.com/dashboard eine App anlegen (Spotify Premium wird zum Steuern benötigt).
2. Als Redirect URI exakt die Adresse eintragen, unter der Jarvis läuft, inklusive Schrägstrich am Ende (zum Beispiel https://jarvis.DEINNAME.workers.dev/).
3. Jarvis öffnen und sagen: „Verbinde Spotify". Die Client ID einmal eingeben und bei Spotify bestätigen.
4. Danach: „Spiel Queen", „Pause", „Weiter", „Nächstes Lied", „Lauter" oder „Lautstärke auf 40".
Die Spotify-App muss auf einem Gerät geöffnet sein, auf dem die Musik laufen soll.

## Direktmodus (ohne Backend, z. B. auf GitHub Pages)
Gibt es unter `/api/chat` kein Backend, fragt Jarvis beim ersten Gespräch nach einem Anthropic-API-Key
(console.anthropic.com) und ruft die Claude API direkt aus dem Browser auf, inklusive Websuche.
Der Key wird nur im Browser dieses Geräts gespeichert (localStorage), nie im Code oder im Repository.
Er darf deshalb nicht in die Dateien eingetragen werden. Für den eigenen Gebrauch ist das in Ordnung;
für eine öffentliche Seite mit mehreren Nutzern ist das Backend die bessere Wahl.
