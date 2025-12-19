# Cos'è un alias?

Gli alias sono dei comandi che si usano al posto di comandi già esistenti, sono uno strumento molto potente dato che oltre un solo comando puoi sostituire una lista di comandi.

# Come creo un alias?

Questa guida fa esattamente quello, creare un alias temporaneo non è complicato (sempre in base a quello che devi scrivere), ma farlo permanente può risultare per i poco esperti abbastanza complicato.

## 1. Primo passo

   Per creare un **alias** anzitutto devi decidere per cosa ti serve, per esempio il primo alias che ho creato l'ho chiamato `routine`, e cosa faceva?
 
   ```bash
   sudo apt update && sudo apt full-upgrade -y && sudo apt autoremove -y
   ```
  
   Un passo che considero "obbligatorio" ogni volta che accendo il computer, ma scrivere tutta sta mercanzia ogni volta è stressante, quindi ora vediamo come creare un alias che faccia questo comando automaticamente.
  
   (Ovviamente il comando sopra indicato contiene la keyword `sudo`, questo implica che a seguire il terminale chiederà la password del sistema)

 ## 2. Creazione dell'alias

  Per creare un nuovo alias hai bisogno di 2 cose: un `nome` con cui sostituire il comando che vuoi e ovviamente il `comando` da rimpiazzare.
  
  Prendiamo come esempio il comando di prima, che vogliamo rimpiazzare con `routine`
  
  1. Apri il terminale
  2. Scrivi:
  ```bash
  nano ~/.bashrc
  ```
## 3. Ora sei nel file in cui inserire tutti gli alias che vuoi e infondo al file scrivi:
  ```bash
  alias nameAlias='command'
  ```
  
  **N.B.** Usa esattamente questa sintassi (spazi inclusi)
  
  Questo è l'esempio:
  
  ```bash
  alias routine='sudo apt update && sudo apt full-upgrade -y && sudo apt autoremove -y'
  ```

  Per uscire premi `Ctrl+o`, `Invio` e infine `Ctrl+x`

## 4. Infine sempre da terminale scrivi:

   ```bash
   source ~/.bashrc
   ```

   Per ricaricare la configurazione e usare liberamente il tuonuovo alias.

## Un alias più complicato

Un altro alias che potresti inserire è un alias che ti permetta di fare il commit automatico e chiamarlo per esempio `gg`.

Potresti crearlo che faccia un commit con un messaggio automatico (e.g. `update`)

Quindi avresti `git add . && git commit -a -m "update" && git push`

Ma se vuoi fare un commit personalizzato puoi scrivere questo nel file `nano ~/.bashrc`:

```bash
gg() {
    git add .
    git commit -a -m "$*"
    git push
}
```

`"$*"` permette di prendere tutto quello che scrivi dopo `gg` e usarlo come messaggio

e.g.

```bash
gg update
```

**Attenzione:**

 - `git add .` è un comando molto potente, se hai dei file che di cui non vuoi fare il commit (e.g. file di log, ecc..) non conviene usare questo alias.
 
 Assicurati sempre di avere un file `.gitignore` ben configurato nel tuo progetto per evitare di caricare file spazzatura per sbaglio.

 - Se vuoi scrivere un messaggio con parentesi potrebbe darti errore, in tal caso usa le virgolette "" per scrivere il tuo messaggio
 
 ```bash
 gg "update (example)"
 ```
 
