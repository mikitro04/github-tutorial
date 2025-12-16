# Annidare repository su github

## Cosa vuol dire

Annidare delle repository su github permette a te di avere una repo principale con una o più repository al suo interno.

Questo vorrebbe dire che hai uan directory del genere:

```
main_repository/            <-- La cartella della repo principale
├── .git/                   <-- Questa gestisce la tua repo principale
├── README.md
├── index.html
└── nest_repository/        <-- La cartella della repo annidata
    ├── .git/               <-- Questa gestisce la tua repo annidata
    ├── README.md
    └── appunti.txt
```

In questo esempio vediamo una repo principale di github con dentro una repo annidata.

## Come fare?

Per fare ciò non basta fare una `git clone` all'interno della repo principale, perchè questo incasinerebbe github, visto che nota che esistono due cartelle `.git/`.

Se hai fatto già così puoi risolvere semplicemente scrivendo:

```bash
git rm --cached nome_cartella_annidata
```

Quello che devi fare invece è:
1. Eliminare la cartella da git `git rm -rf nome_cartella_annidata` e poi in locale `rm -rf nome_cartella_annidata`

2. Creare un submodule nella tua cartella principale (devi fare questo anzichè fare la `git clone`):
  ```bash
  git submodule add https://github.com/tuo-user/repo-annidata.git nome_cartella_annidata
  ```
3. Salva e invia le modifiche (nella repo principale):
  ```bash
  git add .gitmodules nome_cartella_annidata
  git commit -m "Fix: Aggiunto submodule correttamente"
  git push origin main
  ```

## NB
Quando andrai a fare il push di qualcosa devi farlo nella cartella che ti interessa:

e.g. Se modifichi qualcosa in `nest_repository` devi andare in quella cartella e fare il push da lì; se invece modifichi qualcosa dentro `main_repository` ma non dentro `nest_repository` (vedendo l'esempio sopra modifichi il file `index.html`) fai il push da lì(`main_repository`).
