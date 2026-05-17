# Marqant — Consulting (holdingside)

Statisk one-pager. Ren HTML/CSS, ingen build-step, ingen dependencies. Google Fonts hentes via CDN.

## Struktur

```
marqant-site/
├── index.html      # hele siden — én fil
├── .gitignore
└── README.md
```

## Lokal preview

Åbn `index.html` direkte i browseren — eller kør en lille lokal server:

```bash
# Python (preinstalleret på macOS)
python3 -m http.server 8000
# → http://localhost:8000
```

## Deploy til Simply

**Anbefalet for én statisk side: brug Simply's standard webhosting + FTP upload.** Git på server giver kun mening hvis du har VPS/Cloud-plan og vil pull'e ved hver opdatering — det er overkill her.

### Simply webhosting (FTP)

1. Log ind på [simply.com](https://simply.com) → Kontrolpanel → vælg dit webhotel
2. Find FTP-oplysninger under **Filer & FTP** (host, brugernavn, password). Eller brug **Filhåndtering** direkte i browseren
3. Upload `index.html` til roden af `public_html/` (eller hvad din plan kalder web-roden — typisk `/www/` eller `/public_html/`)
4. Hvis du vil have flere filer senere (billeder, assets osv.), upload dem til samme mappe og referencer dem relativt

**FTP via CLI** (hvis du bruger Cyberduck/FileZilla er det det samme i GUI):

```bash
# Eksempel med lftp — kræver brew install lftp
lftp -u DIN_BRUGER,DIT_PASSWORD ftp.dit-domæne.dk -e "put index.html -o /public_html/index.html; bye"
```

### Pege domænet på Simply

Hvis du har købt domænet via Simply: det virker automatisk. Hvis det ligger et andet sted: peg DNS A-record på Simply's IP (står i kontrolpanelet under **DNS**).

## GitHub setup

Repo er allerede initialiseret lokalt. For at pushe til GitHub:

```bash
# 1. Opret tomt repo på github.com (uden README/gitignore/license — vi har dem)
#    Eks. navn: marqant-site

# 2. Tilføj remote og push (erstat MIT-BRUGERNAVN)
cd "/Users/frederiksorensen/Documents/Claude/Projects/Marqant design/marqant-site"
git remote add origin git@github.com:MIT-BRUGERNAVN/marqant-site.git
git branch -M main
git push -u origin main
```

Bruger du HTTPS i stedet for SSH:

```bash
git remote add origin https://github.com/MIT-BRUGERNAVN/marqant-site.git
```

## Alternativ: GitHub Pages (gratis hosting)

Hvis du vil teste live uden Simply:

1. Push til GitHub (som ovenfor)
2. Repo → **Settings → Pages → Source: Deploy from a branch → main / root**
3. Live på `https://MIT-BRUGERNAVN.github.io/marqant-site/` indenfor ~1 min

## Vedligehold

- Rediger `index.html`, commit, push:
  ```bash
  git add index.html
  git commit -m "Opdater kontaktinfo"
  git push
  ```
- Re-upload til Simply via FTP efter hver ændring (eller automatisér med GitHub Action hvis det bliver hyppigt)

## TODO før go-live

- [ ] Indsæt rigtig email (placeholder: `hello@marqant.dk`)
- [ ] Indsæt rigtigt telefonnummer (placeholder: `+45 00 00 00 00`)
- [ ] Indsæt rigtig adresse (placeholder: `Bredgade 00, 1260 København K`)
- [ ] Indsæt rigtigt CVR (placeholder: `00 00 00 00`)
- [ ] Overvej favicon (`<link rel="icon" href="favicon.svg">`)
- [ ] Overvej OG-tags til pæn preview ved deling
