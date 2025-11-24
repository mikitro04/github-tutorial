# Create a desktop shortcut (e.g. for AppImage) in Linux
Se come me non scarichi le cose usando snap ti sarai reso conto che con `apt` non riuscirai a trovare tutto quanto quello che ti serve, per questo motivo sei costretto ad andare nel sito del produttore e scaricare un eseguibile che sarà rinchiuso in una cartella del tuo PC, e ogni volta per aprirla dovrai fare `./your/path/application &`.

Se anche tu non hai voglia di fare tutto questo giro ogni volta ho creato questo file per facilitarti il compito:

## 1. Per prima cosa entra dal terminale nella cartella in cui vuoi vedere la tua applicazione

e.g.

```bash
cd home/mikitro04/Desktop
```

## 2. Creiamo il collegamento alla cartella di destinazione

Inserisci questo comando

```bash
nano your-application.desktop
```

ovviamente sostituisci `your-application` con il nome che vuoi.

Poi incolla questo prompt

```bash
[Desktop Entry]
Name=NomeApplicazione
Comment=Il commento che preferisci
Exec=/path/to/your/application.extension
Icon=/path/to/your/application.png
Terminal=false
Type=Application
Categories=Categorie;Della;Tua;Applicazione;
```

### NB

1. L'uguale va lasciato attaccato e.g. `Name=NomeApplicazione`
2. Il commento **può** contenere spazi
3. Il path che scrivi su Exec e Icon deve contenere l'applicazione o immagine che andranno ad eseguire/mostrare
4. Le categorie sono _customizzabili,_ quindi puoi inseire quelle che preferisci, divise da un `;` **senza spazi**.

## Salviamo ed usciamo

Infine premi `Ctrl+o` + `Enter` + `Ctrl+x` per salvare ed uscire.

## Classici problemi

Solitamente quando creiamo la nostra shortcut non sempre è immediatamente eseguibile, per questo premi sull'icona col tasto _destro_, poi vai su `Proprietà` e abilita `Eseguire come programma`

Se ancora hai problemi vai da terminale nella cartella in cui è presente la shortcut e digita:

```bash
chmod +x your-shortcut.desktop
```

Ora dovrebbe andare tutto liscio
