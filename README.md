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
