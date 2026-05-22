# 🍫 Snackkasse – Büro-Snackkiosk als PWA

Eine kleine Web-App (PWA) für den Vertrauens-Snackkiosk im Büro:
Kollegen tippen ihren Snack an, scannen den PayPal-QR mit dem eigenen Handy und
zahlen sofort den aufgerundeten Preis. Du behältst Bestand, Ausgaben und Einnahmen
im Blick.

## Was drin ist
- `index.html` – die ganze App
- `qrcode.min.js` – QR-Generator (offline, getestet)
- `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png` – PWA-Beiwerk (Homescreen, offline)

## So funktioniert die App
- **Startseite:** Kacheln mit allen Snacks, Symbol, Name, Preis und Restbestand.
  Tippen → QR mit fertigem Betrag erscheint → „Bezahlt & genommen" → Bestand −1.
- **⚙️ Admin (PIN, Standard `1234`):**
  - **Snacks:** neuen Snack anlegen (Einkaufspreis → automatisch auf 10 ct aufgerundet
    = Verkaufspreis), Bestand mit −/+ nachfüllen, löschen.
  - **Kasse:** Eingenommen (Soll), Ausgegeben, Saldo, Warenwert im Bestand. CSV-Export.
  - **Einstellungen:** PayPal.Me-Name eintragen, PIN ändern, Ausgaben korrigieren,
    alles löschen.

> Wichtig: „Eingenommen" ist die **Soll-Summe** aller Käufe. Ob das Geld wirklich
> da ist, siehst du in deinem PayPal-Konto – das kann die App nicht prüfen.

## ⚠️ Datenhaltung – bitte lesen
Die Daten liegen im Browser des Geräts (`localStorage`), es gibt **keine zentrale
Datenbank**. Darum: **ein zentrales Gerät als Kasse** verwenden – ein altes Tablet
oder Smartphone neben der Snackbox. Alle buchen dort, zahlen aber mit dem eigenen
Handy per QR. So bleibt der Bestand konsistent.

(Wenn du später eine echte geteilte Datenbank willst, lässt sich das mit einem
kleinen Backend nachrüsten – z. B. auf deinem eigenen Server.)

## Hosten auf GitHub Pages (kostenlos, mit HTTPS)
HTTPS ist nötig, damit „zum Homescreen hinzufügen" und der Service Worker laufen.

1. GitHub-Account anlegen (falls nicht vorhanden), auf github.com einloggen.
2. **New repository** → Name z. B. `snackkasse` → **Public** → Create.
3. **Add file → Upload files** → alle Dateien aus diesem ZIP hochladen
   (index.html, qrcode.min.js, manifest.json, sw.js, icon-192.png, icon-512.png)
   → **Commit changes**.
4. **Settings → Pages** → unter „Build and deployment" bei „Branch" `main` und
   `/ (root)` wählen → **Save**.
5. Nach 1–2 Minuten erscheint dort die URL, z. B.
   `https://DEINNAME.github.io/snackkasse/`
6. Diese URL auf dem Kassen-Tablet öffnen → Browser-Menü →
   **„Zum Startbildschirm hinzufügen"**. Fertig, sieht aus wie eine App.

### Zum Schluss
- In der App **⚙️ → Einstellungen → PayPal.Me-Namen eintragen** (nur den Namen,
  nicht die ganze URL).
- Ersten Snack anlegen und Bestand setzen.
- Optional: einen QR-Code mit der GitHub-Pages-URL ausdrucken und neben die
  Snackbox hängen, dann können Kollegen die App auch auf dem eigenen Handy öffnen.

## Alternativen zum Hosten
Geht genauso mit **Netlify Drop** (netlify.com/drop – ZIP-Inhalt einfach
reinziehen) oder **Cloudflare Pages**. Alle drei sind kostenlos und liefern HTTPS.
