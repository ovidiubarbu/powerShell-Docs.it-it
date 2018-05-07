# <a name="installing-powershell-core-on-macos"></a>Installazione di PowerShell Core in macOS

PowerShell Core supporta macOS 10.12 e versioni successive.
Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.
Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installazione tramite Homebrew in macOS 10.12

[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.
Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].

Dopo aver installato Homebrew, installare PowerShell sarà semplice.
Prima installare [Homebrew-Cask][cask] in modo da poter installare più pacchetti:

```sh
brew tap caskroom/cask
```

A questo punto, è possibile installare PowerShell:

```sh
brew cask install powershell
```

Infine, verificare che l'installazione funzioni correttamente:

```sh
pwsh
```

Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento
> e aggiornare i valori visualizzati in $PSVersionTable.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a>Installazione tramite download diretto

Scaricare il pacchetto PKG `powershell-6.0.2-osx.10.12-x64.pkg` dalla pagina delle [versioni][] nel computer macOS.

È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Archivi di file binari

Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme macOS e Linux per abilitano scenari di distribuzione avanzati.

### <a name="installing-binary-archives-on-macos"></a>Installazione degli archivi binari in macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>Disinstallazione di PowerShell Core

Se PowerShell è stato installato con Homebrew, disinstallarlo è semplice:

```sh
brew cask uninstall powershell
```

Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi][] in questo documento e rimuovere i percorsi con `sudo rm`.

> [!NOTE]
> Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.

[Percorsi]:#paths

## <a name="paths"></a>Percorsi

* `$PSHOME` è `/opt/microsoft/powershell/6.0.0/`
* I profili utente vengono letti da `~/.config/powershell/profile.ps1`
* I profili predefiniti vengono letti da `$PSHOME/profile.ps1`
* I moduli utente vengono letti da `~/.local/share/powershell/Modules`
* I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`
* I moduli predefiniti vengono letti da `$PSHOME/Modules`
* La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

I profili rispettano la configurazione di PowerShell per ogni host.
Di conseguenza, i profili specifici dell'host predefinito sono presenti in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.

PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.

Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.
Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.0.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
