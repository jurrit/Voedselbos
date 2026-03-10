# Voedselbos Biezenmortel — Website

Landingspagina voor Voedselbos Biezenmortel, gebouwd als pure statische one-pager (HTML + CSS + JS).
Geoptimaliseerd voor gratis hosting op **Cloudflare Pages**.

---

## Projectstructuur

```
Voedselboswebsite/
├── index.html       # De volledige one-pager
├── styles.css       # Alle styling
├── script.js        # Navigatie, scroll-animaties
├── _headers         # Cloudflare Pages security headers
├── images/          # Jouw eigen foto's komen hier
│   └── .gitkeep
└── README.md        # Dit bestand
```

---

## Stap 1 — Aanpassen vóór publicatie

Zoek in `index.html` naar `<!-- UPDATE:` — dit zijn alle plekken die jij moet invullen:

| Wat                | Zoek naar                                        |
|--------------------|--------------------------------------------------|
| E-mailadres        | `info@voedselbos-biezenmortel.nl`               |
| Instagram-handle   | `@voedselbos_biezenmortel`                      |
| Instagram-URL      | `https://instagram.com/voedselbos_biezenmortel` |
| Nieuwsberichten    | `<!-- UPDATE: Vervang door jouw eigen nieuwsbericht -->` |
| Exacte locatie     | Regel onder "Biezenmortel, Noord-Brabant"        |

---

## Stap 2 — Foto's toevoegen

1. Zet je foto's in de map `images/` (bijv. `foto1.jpg`, `foto2.jpg`, ...)
2. Open `index.html` en zoek naar de `<div class="foto-placeholder">` blokken
3. Vervang elk blok door:
   ```html
   <img src="images/foto1.jpg" alt="Jouw beschrijving" class="galerij-foto">
   ```

**Tip voor afbeeldingsformaat:** gebruik JPEG, breedte ~1200px, max 300 KB per foto voor snelle laadtijd.

---

## Stap 3 — Contactformulier (optioneel verbeteren)

Het formulier gebruikt nu `mailto:` — dit opent de e-mailclient van de bezoeker.
Voor een volledig werkend formulier **zonder backend** gebruik je [Formspree](https://formspree.io) (gratis):

1. Maak een account op formspree.io
2. Maak een nieuw form aan → je krijgt een URL zoals `https://formspree.io/f/xyzabcde`
3. Vervang in `index.html` de form-action:
   ```html
   <!-- Van: -->
   <form action="mailto:info@voedselbos-biezenmortel.nl" ...>

   <!-- Naar: -->
   <form action="https://formspree.io/f/JOUW_FORM_ID" method="POST">
   ```

---

## Stap 4 — Naar GitHub pushen

### 4a. GitHub-repository aanmaken
1. Ga naar [github.com](https://github.com) en log in
2. Klik op **"New repository"** (groene knop rechtsboven)
3. Geef het een naam, bijv. `voedselbos-biezenmortel`
4. Zet op **Public** (vereist voor gratis Cloudflare Pages)
5. Klik **"Create repository"**

### 4b. Code uploaden via terminal

Open Terminal in de projectmap:

```bash
# Ga naar de projectmap
cd /Users/jurrit/Desktop/Voedselboswebsite

# Initialiseer Git
git init

# Voeg alle bestanden toe
git add .

# Eerste commit
git commit -m "eerste versie voedselbos website"

# Koppel aan je GitHub-repo (vervang JOUW_GEBRUIKERSNAAM)
git remote add origin https://github.com/JOUW_GEBRUIKERSNAAM/voedselbos-biezenmortel.git

# Push naar GitHub
git branch -M main
git push -u origin main
```

### 4c. Alternatief: GitHub Desktop
Geen terminal? Gebruik [GitHub Desktop](https://desktop.github.com):
1. Download en installeer GitHub Desktop
2. Kies "Add existing repository" → selecteer deze map
3. Publiceer naar GitHub via de knop "Publish repository"

---

## Stap 5 — Koppelen aan Cloudflare Pages

1. Ga naar [dash.cloudflare.com](https://dash.cloudflare.com) en log in (of maak gratis account)
2. Klik in het linkermenu op **"Workers & Pages"**
3. Klik op **"Create application"** → kies tabblad **"Pages"**
4. Klik op **"Connect to Git"**
5. Koppel je GitHub-account en selecteer je repository (`voedselbos-biezenmortel`)
6. **Build-instellingen** (dit is een pure statische site, geen bouw-stap nodig):
   - **Framework preset:** `None`
   - **Build command:** *(leeg laten)*
   - **Build output directory:** `/` of `.`
7. Klik op **"Save and Deploy"**

Cloudflare deployt nu automatisch. Je krijgt een gratis URL zoals:
`https://voedselbos-biezenmortel.pages.dev`

---

## Stap 6 — Eigen domein koppelen (optioneel)

Als je een eigen domeinnaam hebt (bijv. `voedselbos-biezenmortel.nl`):

1. Ga in Cloudflare Pages naar jouw project → tabblad **"Custom domains"**
2. Klik **"Set up a custom domain"**
3. Voer je domeinnaam in en volg de instructies (DNS-records aanpassen)

**Tip:** Als je je domein ook bij Cloudflare beheert, gaat dit volledig automatisch.

---

## Automatisch bijwerken

Na de eerste koppeling wordt de website **automatisch bijgewerkt** elke keer dat je naar GitHub pusht:

```bash
# Bewerk je bestanden, sla op, dan:
git add .
git commit -m "update: nieuwsbericht toegevoegd"
git push
```
Cloudflare Pages pikt de wijziging op en deployt binnen ~30 seconden.

---

## Kosten

| Dienst             | Kosten          |
|--------------------|-----------------|
| Cloudflare Pages   | Gratis          |
| GitHub repository  | Gratis (public) |
| Formspree (form)   | Gratis (50/mnd) |
| Eigen domeinnaam   | ~€10/jaar       |

---

## Vragen?

Neem contact op via `info@voedselbos-biezenmortel.nl`
of open een issue in de GitHub-repository.
