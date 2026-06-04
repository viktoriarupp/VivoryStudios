# Vivory Landingpages

Drei statische Landingpages mit DSGVO-konformem Lead-Formular (Double-Opt-In + Newsletter-Einwilligung).

## Dateien

| Datei | Zweck |
|-------|-------|
| `index.html` | Übersichtsseite, verlinkt alle drei Angebote |
| `mastermind.html` | Salespage Vivory Mastermind (Warteliste) |
| `chatbot.html` | Leadmagnet: kostenloser Chatbot |
| `videokurs.html` | Reduzierter Online-Videokurs |
| `assets/vivory.css` | Gemeinsames Stylesheet (Markenfarben aus der Extension) |
| `assets/vivory.js` | Formular-Logik (Validierung, Demo-Modus, Versand) |

## Ansehen

Einfach eine der `.html`-Dateien im Browser öffnen. Ohne angeschlossenen
E-Mail-Dienst laufen die Formulare im **Demo-Modus** (zeigen nur die
Danke-Meldung, senden nichts).

## E-Mail-Dienst anschließen

In jeder HTML-Datei steht im `<form>`-Tag:

```html
<form data-lead-form data-endpoint="REPLACE_WITH_YOUR_FORM_ENDPOINT">
```

Ersetze `REPLACE_WITH_YOUR_FORM_ENDPOINT` durch die Formular-/Action-URL
deines Anbieters:

- **Brevo (Sendinblue):** URL aus dem Brevo-Formular-Editor
- **CleverReach:** Action-URL aus dem „HTML-Formular"
- **Mailchimp:** die `.../subscribe/post`-URL
- **Eigener Server:** deine eigene POST-Route

Die Feldnamen, die abgesendet werden: `vorname`, `email`,
`newsletter_consent`, `quelle` (kennzeichnet die Herkunft je Seite).
Passe sie ggf. an die Pflichtfeldnamen deines Anbieters an.

## DSGVO-Checkliste (bitte vor Live-Gang prüfen)

- [ ] **Double-Opt-In** beim E-Mail-Dienst aktivieren (Bestätigungsmail).
- [ ] Die Einwilligungs-Checkbox ist **nicht vorausgewählt** – so lassen.
- [ ] Links **Datenschutzerklärung** und **Impressum** einsetzen
      (aktuell `href="#"` Platzhalter im Footer und im Consent-Text).
- [ ] Einwilligung **dokumentieren** (Zeitstempel/Text – macht i.d.R. der
      E-Mail-Dienst).
- [ ] Wenn Google Fonts lokal gehostet werden sollen (strengere DSGVO-Auslegung):
      Schriften herunterladen und die `<link>`-Tags durch lokale `@font-face`
      ersetzen. Aktuell werden Fraunces + Inter über das Google-CDN geladen.

## Anpassen

- **Texte/Preise:** direkt im HTML (Preise stehen in `mastermind.html`).
- **Farben/Look:** zentral in `assets/vivory.css` über die `:root`-Variablen.
- **Teilnehmer-Zitate:** in `mastermind.html` ist ein Platzhalter-Zitat markiert.