
# Cose base che devi sapere su github

## INIZIALIZZAZIONE di git

La prima cosa da fare è ovviamente scaricare git, quindi:

```bash
sudo apt update
sudo apt install git
```

Una volta scaricato eseguiamo il login:


```bash
gh auth login
```

E poi:

```bash
git config --global user.name your-username
git config --global user.email your@email.com
```

## Clonare una repository

Una volta creata la tua repository dal sito di [Github](https://github.com/) accedi al terminale sulla cartella dove vuoi posizionare la cartella (e.g. /home/mikitro04/Desktop) e digita il seguente comando:

```bash
git clone https://github.com/your-username/your-repository
```

ovviamente **sostituisci** your-username e your-repository adeguatamente.

## PRIMA di caricare le cose su github

Se hai pensato che bastasse fare `git push` per caricare le cose su github aspetta un secondo
Prima di tutto:
* Vai su [Github](https://github.com/settings/tokens) (link diretto per saltare i passaggi successivi)
* Premi sul tuo profilo e vai su Settings
* Scrollando tutto verso il basso nella barra di destra dovresti trovarti una voce `<> Developer settings`
* Ora vai su `Personal access tokens` e su `Tokens (classic)`
* Il passaggio è ripetitivo, premi su `Generate new token` --> `Generate new token`
    * Ora in **Nome** metti quello che vuoi, possibilmente qualcosa che ricordi a che repository si sta riferendo
    * Poi in **Expiration** inserisci la durata che può anche essere anche senza fine
    * In `Repository access` seleziona a quale repo è destinato il token
    * Infine inserisci i permessi
* Una volta generato il token **NON PERDERLO** perchè non lo potrai recuperare!

Il token sarà qualcosa del tipo `github_path_...`

## Prossimo passo

Ora una volta che nella cartella clonata da github hai caricato quello che devi caricare esegui questi comandi da terminale:

```bash
git add .
```

Così tutti i file che hai aggiunto verranno riconosciuti dal commit, poi scrivi:

```bash
git commit -a -m "Your upgrade"
```


Sostituisci `Your upgrade` con qualcosa che faccia capire cosa hai aggiornato (non necessariamente qualcosa di serio).

Questo comando esegue il commit di tutti i cambiamenti effettuati nella repository (`-a`), senza questo non credo sia possibile caricare i salvataggi. `-m` serve per inserire il messaggio

Infine devi inserire:

```bash
git push

# in alternativa
git push origin main    # per pushare nel branch main
```

Se tutto va bene **complimenti!** Sei riuscito ad aggiornare la tua repository di github.

Se invece ti chiede di inserire il tuo username inserisci il tuo username, e.g.

```bash
mikitro04
```

E se pensi che la password sia la tua password di github, mi dispiace ma sei stato fregato. Inserisci il token che ti ho fatto creare prima.

Per salvare le credenziali infine digita:

```bash
git config --global credential.helper store
```

## Come fai ad aggiornare la tua cartella locale da quello che vedi dal sito?

Abbastanza semplicemente scrivi 

```bash
git pull
```

## Rimuovere dei file e fare il commit

Come per `git add file1 file2 ..` esiste anche il comando `git rm file1 file2 ..` che permette di far riconoscere al commit quali file deve scartare per eseguire un upgrade della repository.

Prima di tutto fai `git rm file` o `git rm -r directory/`,

Poi lo stesso comando ma senza `git` per eliminarli anche in locale

Infine il commit:

```bash
git commit -a -m "Your upgrade"
```

E il push:

```bash
git push
```

## Soliti problemi

### Forzatura del push/pull

Se ti di ce per esempio che stai cercando di pushare in una repository più aggiornata rispetto a quella che hai pullato prima hai due opzioni:

#### 1. Opzione sconsigliata
Puoi creare un nuovo branch ma non so nemmeno come si fa e non voglio saperlo

#### 2. Opzione consigliata
Metodo _brute force,_ esegui:

```bash
git push --force
```

E su github ti ritroverai la repository che hai in locale

Stessa cosa per il pull, quindi hai aggiornato la tua cartella locale e vuoi caricare gli aggiornamenti presenti su github

```bash
git pull --force
```

### La clone non funziona (errore 403)

Se il comando `git clone https://github.com/your-username/your-repository` non funziona e il teminale restituisce `Errore 403` niente panico.

Prendi il token che hai generato prima e inserisci il seguente comando:

```bash
git clone https://your-username:token-generato-prima@link-repository
```
