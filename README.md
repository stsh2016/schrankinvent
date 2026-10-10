# Vorratsfinder

Eine Web-App fürs iPhone: Schrank fotografieren, Claude erkennt die Vorräte, und du findest sie später über die Suche wieder.

## Funktionen

- **Schrank fotografieren**: Öffnet direkt die Rückkamera. Du gibst an, wo der Schrank steht (z. B. „Küche · Oberschrank links“).
- **Automatische Erkennung**: Claude bestimmt für jeden Artikel Name, Marke, Kategorie, Menge und Position im Schrank. Dazu kommen Suchbegriffe, damit „Pasta“ auch die Spaghetti findet.
- **Suche**: Findet Artikel unabhängig von Groß-/Kleinschreibung und Umlauten. Die Treffer sind nach Ort gruppiert.
- **Pflegen**: Artikel bearbeiten, ein Ablaufdatum setzen, als „Aufgebraucht“ entfernen oder von Hand hinzufügen.
- **Sicherung**: Artikel und Fotos lassen sich als JSON-Datei exportieren und wieder laden.

## Einrichtung

1. In den Repository-Einstellungen unter **Settings → Pages** als Quelle den Branch `main` und den Ordner `/ (root)` wählen.
2. Die Seite `https://stsh2016.github.io/schrankinvent/` in Safari auf dem iPhone öffnen.
3. **Teilen → Zum Home-Bildschirm** wählen. Die App startet dann im Vollbild.
4. Über das Zahnrad einen Claude API-Schlüssel eintragen (erstellen unter [console.anthropic.com](https://console.anthropic.com/settings/keys)).

## Datenschutz und Speicherung

- Alle Artikel und Fotos liegen ausschließlich lokal im Browser (IndexedDB). Es gibt keinen eigenen Server.
- Fotos werden nur zur Erkennung an die Claude-API von Anthropic gesendet.
- Der API-Schlüssel wird nur auf dem Gerät gespeichert (`localStorage`). Wer Zugriff auf das Gerät hat, kann ihn auslesen. Nutze am besten einen eigenen Schlüssel mit Ausgabenlimit.
- Safari kann Website-Daten löschen, wenn eine Seite längere Zeit nicht benutzt wird. Als App auf dem Home-Bildschirm ist das deutlich seltener. Exportiere trotzdem ab und zu eine Sicherung.
- Die Daten werden nicht zwischen Geräten abgeglichen. Ein Umzug geht über Export und Import.

## Technik

Eine einzelne statische `index.html` ohne Build-Schritt. Die Erkennung nutzt das offizielle Anthropic-SDK (`@anthropic-ai/sdk`, über jsDelivr geladen) mit dem Modell `claude-opus-5-5`.
