# CSR2-DataBase

Codes (fichiers `.txt`), captures et données de toutes les voitures de **CSR Racing 2**, avec un site pour les parcourir.

*English version below.*

---

## Le site

### En ligne (recommandé) : GitHub Pages
À activer une seule fois par le propriétaire du dépôt :
1. Sur github.com, dans le dépôt : **Settings → Pages**.
2. **Source** : « Deploy from a branch ».
3. Choisir la branche qui contient le site (en général `main`) et le dossier **/ (root)**, puis **Save**.
4. Après une à deux minutes, le site est en ligne à l'adresse `https://<pseudo>.github.io/CSR2-DataBase/`.

Ensuite, chaque push met le site à jour tout seul en une ou deux minutes.

À savoir :
- **La branche.** GitHub Pages ne publie qu'une seule branche. Si les modifications arrivent sur une autre branche, il faut la fusionner dans `main` (pull request) ou choisir cette branche dans Pages.
- **Le fichier `.nojekyll`** à la racine est nécessaire : il ne faut pas le supprimer.
- **Dépôt privé.** GitHub Pages n'est gratuit que pour un dépôt public. Un dépôt privé demande un compte GitHub payant.
- **Sur github.com**, cliquer sur `index.html` affiche le code source de la page, pas le site.

### Sur son ordinateur
Double-cliquer sur `index.html` ouvre le site, mais le navigateur interdit à la page de lire les fichiers `.txt` : le panneau du code affiche alors seulement une explication. Pour tout avoir, lancer un petit serveur local dans le dossier du dépôt :

```
cd chemin/vers/CSR2-DataBase
python3 -m http.server 8000
```

puis ouvrir http://localhost:8000 (Ctrl+C dans le terminal pour arrêter). Sous Windows, remplacer `python3` par `python` ou `py`.

### Utilisation
- **Cars** : choisir une version (Stock, Full, Elite Max), une marque, puis une voiture. La fiche montre :
  - l'identité de la voiture et son historique : 1re apparition (version du jeu, saison et dates), saisons où elle était voiture prix, Prestige Cup, évènements où on pouvait la gagner ou l'acheter ;
  - les pièces de fusion (avec la capture du jeu, agrandissable au clic), les tokens Elite et le réglage (Nitrous / Box / Tyres, record, dyno).
- **Choisir une couleur** ouvre à droite le code de la voiture : boutons Copier et Télécharger. Quand il n'y a qu'une seule couleur, le code s'ouvre tout seul.
- Le site existe aussi en FR, DE, ES et PT-BR (menu en haut à droite).
- **Les pages Fusions, Stage 6, Support gift et Elite discount** génèrent les fichiers correspondants. AMOUNT est remplacé par la quantité saisie.

Repères :
- **Saisons.** Elles sont numérotées comme dans les fichiers officiels du jeu, en comptant les 8 saisons béta de 2016 (« (béta) » à côté des saisons 1 à 8). Les numéros des tableurs de la communauté, qui ne comptent pas les béta, sont donc décalés de 8.
- **Voitures de Boss.** Celles qui ne sont pas jouables (adversaires Tempest des développeurs, etc.) sont affichées sans code.
- **Voitures de la boutique** (SHOP). Elles ont leur propre pattern de fusion ; leur image est celle de la version gacha dans sa couleur par défaut.

## Organisation du dépôt

| Dossier / fichier | Contenu |
|---|---|
| `1.Cars/` | Une fiche par voiture et par couleur : `<Nom> (<Couleur>).txt` (code) et `.jpg` (capture), plus `#fusions.jpg`. Rangement : `<1.Stock / 2.Maxed / 3.Elite Max>/<étoile>/<Marque>/<Voiture>/`. Étoiles : `1.Gold Star`, `2.Purple Star`, `3.Legends` (`1.Unrestored` / `2.Restored`), `4.Unspecified`, `4.TNR`, `5.Shop Cars`. |
| `2.MaxOuts/` | Fichiers de max-out. |
| `3.Fusions/` | Pièces de fusion. |
| `4.Stage6's/` | Fichiers Stage 6. |
| `5.SupportGifts/`, `6.EliteDiscounts/` | Cadeaux du support et remises Elite. |
| `Tables/` | Données des voitures en CSV (séparateur `;`). Voir plus bas. |
| `x.CarVisualConfigs/` | Configurations visuelles des voitures. |
| `x.Site/` | Données, vignettes, logos et icônes du site (généré : ne pas modifier à la main). |
| `index.html` | Le site. |

**Noms des dossiers de voitures** : sans la marque (elle est dans le dossier parent) et sans numéro de saison. Quand deux voitures portent le même nom :
- « X (Season Prize) » pour la voiture de saison, « X (Event) » pour l'autre ;
- « X (2019) » / « X (2024) » pour deux voitures de saison.

### Tables principales
- **`cars.csv`** : une ligne par voiture (crdb = identifiant du jeu). Colonnes :
  - brand, folder, name ;
  - seasons : saisons où la voiture était voiture prix ;
  - prestige_cup_info ;
  - events : évènements limités où on pouvait la gagner ou l'acheter, « Nom (saison) » ;
  - events_other : autres apparitions, non affichées ;
  - first_season / first_date : saison et dates de 1re apparition.
- **`cars_table.csv`** : version du jeu, patterns de fusion, tokens, catégorie (Boss, etc.).
- **`world_records.csv`** : réglages, Spec, records et dyno.
- **`stars.csv`, `colors.csv`, `brands.csv`, `default_paints.csv`** : étoiles, couleurs, marques, couleur par défaut.

Ces fichiers sont mis à jour à chaque nouvelle version du jeu par l'outil de préparation (côté mainteneur). Ensuite, le site est régénéré et le tout est poussé ici.

---

## English

**What this is:** codes (`.txt`), screenshots and data for every CSR Racing 2 car, plus a website to browse them.

**Website online (GitHub Pages).** To set up once:
1. Go to **Settings → Pages**.
2. Choose Source « Deploy from a branch ».
3. Choose the branch holding the site (usually `main`) and **/ (root)**, then Save.
4. The site goes live at `https://<user>.github.io/CSR2-DataBase/` and updates by itself after each push.

Notes:
- Keep `.nojekyll`.
- Pages is free for public repositories only.
- Clicking `index.html` on github.com shows its source, not the site.

**Locally.** Double-clicking `index.html` works, but browsers block reading the `.txt` files, so the code panel only shows a note. Run `python3 -m http.server 8000` in the repository folder and open http://localhost:8000.

**Using the site:**
- Pick a version (Stock / Full / Elite Max), a brand and a car.
- Choosing a colour opens its code on the right, with Copy and Download buttons.
- Seasons follow the official game numbering, including the 8 beta seasons of 2016, so community spreadsheets are shifted by 8.
- Non-playable Boss cars are shown without code.

**Folders:**
- `1.Cars/<version>/<star>/<Brand>/<Car>/<Name> (<Colour>).txt|.jpg` (+ `#fusions.jpg`);
- `2.MaxOuts`, `3.Fusions`, `4.Stage6's`, `5.SupportGifts`, `6.EliteDiscounts`;
- `Tables/` (CSV, `;` separated: cars.csv history, cars_table.csv, world_records.csv…);
- `x.Site/` (generated website data, do not edit by hand);
- `index.html` (the site).
