# Linux gaming esiste?

Sì, su Linux è possibile fare di tutto ricordatelo, è possibile anche giocare, ma diciamo che il processo può ritenersi più complicato, ma il successo è assicurato.

In questo breve tutorial ti piegherò come installare **Steam** e perchè si installa così.

## Come **NON** installare Steam su Linux (Ubuntu)

Se cerchi su internet troverai molti risultati, qua ti riporto i metodi che non devi usare per installarlo:

1. **NON INSTALLARLO DA .deb**: lo dico per te, fidati;
2. **NON INSTALLARLO DA Flatpack o Flathub**: stesso discorso di prima.

## Come installare Steam su Linux (Ubuntu)

Sono un Ubuntu user, quindi in queste guide troverai solo tutorial inerenti a Ubuntu, tra le varie distro non esistono sostanziali differenze, magari qualcosa che riguarda pacchetti o nomi che cambiano da `apt` a `dnf` ma poca roba.

Se sei un utente di un'altra distribuzione non è complicato trasformare quello che ti scrivo e trasformarlo nella tua. Se invece usi distro come **Mint** o comunque **Ubuntu based** non ti preoccupare, questi tutorial riguardano anche te.

**RICORDA**: quando installi qualcosa cerca sempre di fare `sudo apt install ..` se non lo trovi c'è un modo per farlo, se provi ad esempio a fare `sudo apt install steam` questo ti darà errore dato che non trova niente chiamato _steam_.

### 1. Come prima cosa attiva la repository contenente software di vario genere

Nel terminale scrivi:

```bash
sudo add-apt-repository multiverse
```

Poi aggiorna:

```bash
sudo apt-get update
```

### 2. Prova a installare Steam

Prova a digitare:

```bash
sudo apt install steam
```

Dico prova dato che su ubuntu c'è sempre un classico problema, il terminale ti dirà una cosa tipo:

    seguenti pacchetti hanno dipendenze non soddisfatte:
    steam-installer : Dipende: steam-libs-i386 (= 1:1.0.0.79~ds-2) ma non è installabile

Come fare per risolvere? lo vediamo nel punto sucessivo.

### 3. Risolvere le dipendenze di `i386`

Per risolvere tale dipendenza scrivi:

```bash
sudo dpkg --add-architecture i386
```

Così che il tuo sistema sia in grado di sapere che può installare pacchetti `i386`.

Aggiorna con:

```bash
sudo apt update
```

E ora prova a installare direttamente la dipendenza mancante con:

```bash
sudo apt install steam-libs-i386
```

Se continua a darti problemi di dipendenze mancanti scrivi:

```bash
sudo apt --fix-broken install
```

Infine installa steam

```bash
sudo apt install steam
```

### NB

Solitamente quando installi il pacchetto `Steam` contiene già tutte le dipendenze per driver o dispositivi, se comunque dovesse darti problemi installale manualmente in una lista di `sudo apt install` in questa maniera:

```bash
sudo apt install steam-installer steam-libs-i386 steam-devices
```