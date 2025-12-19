# Installare Visual Studio Code su Linux

Come dico sempre esistono molti modi per installare qualcosa su Linux, tra i metodi che troverai ci sono robe come `snap` o `flatpack` oppure `file .deb`.

Ecco se puoi **NON farlo**.

## Come installare vs code da `apt`

Se provi ovviamente a fare `sudo apt install code` non funzionerà subito, sarebbe troppo facile.

La prima cosa da fare è aggiungere code ad apt, copia e incolla questo script nel tuo terminale:

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor \
  | sudo install -D -o root -g root -m 644 /dev/stdin /etc/apt/keyrings/packages.microsoft.gpg
echo "deb [arch=amd64,arm64 signed-by=/etc/apt/keyrings/packages.microsoft.gpg] \
  https://packages.microsoft.com/repos/code stable main" \
  | sudo tee /etc/apt/sources.list.d/vscode.list
```

Dopodichè aggiorna:

```bash
sudo apt update
```

Ora puoi digitare senza alcun problema

```bash
sudo apt install code
```

Finito, grazie per la lettura.