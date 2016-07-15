---
title: "Nuovi scenari e funzionalità in WMF 5.1 (anteprima)"
ms.date: 2016-07-06
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: dcccf6880873c3f5c1b58fb1a8c546901b173879
ms.openlocfilehash: 9341b7fc3feea20cc2434065c3e512d1a8dd2b54

---

# Nuovi scenari e funzionalità in WMF 5.1 (anteprima) #

> Nota: queste informazioni sono provvisorie e soggette a modifiche.

## Edizioni di PowerShell ##
A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

- **Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.
- **Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.

**Altre informazioni sull'uso delle edizioni di PowerShell**
- [Determinare l'edizione di PowerShell in esecuzione]()
- [Dichiarare la compatibilità di un modulo con versioni specifiche di PowerShell]()
- [Filtrare i risultati di Get-Module in base a CompatiblePSEditions]()
- [Impedire l'esecuzione di script a meno che non vengano eseguiti in un'edizione compatibile di PowerShell]()

## Modulo Analysis Cache ##
A partire da WMF 5.1, PowerShell fornisce il controllo sul file che viene usato per memorizzare nella cache i dati relativi a un modulo, ad esempio i comandi esportati.

Per impostazione predefinita, questa cache è archiviata nel file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
La cache viene in genere letta all'avvio durante la ricerca di un comando e viene scritta in un thread in background ad un certo punto dopo l'importazione di un modulo.

Per modificare il percorso predefinito della cache, impostare la variabile di ambiente PSModuleAnalysisCachePath prima di avviare PowerShell. Le modifiche apportate a questa variabile di ambiente influiranno solo sui processi figlio.
Il valore deve denominare un percorso completo (nome di file incluso) per il quale PowerShell dispone dell'autorizzazione per creare e scrivere file.
Per disabilitare la cache del file, impostare questo valore su un percorso non valido, ad esempio:

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Questo imposta il percorso su un dispositivo non valido. Se PowerShell non riesce a scrivere nel percorso, non verrà restituito alcun errore. Sarà tuttavia possibile visualizzare una segnalazione errori mediante un'utilità di traccia:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Quando si scrive nella cache, PowerShell controllerà i moduli non più disponibili per evitare di aumentare inutilmente le dimensioni della cache.
Talvolta questi controlli non sono consigliabili. In questo caso, è possibile disattivarli impostando

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

L'impostazione di questa variabile di ambiente avrà effetto immediato nel processo corrente.

##Specifica della versione del modulo

In WMF 5.1 `using module` si comporta esattamente come altre costruzioni correlate ai moduli di PowerShell. In precedenza, non era possibile specificare una versione particolare del modulo. Se erano presenti più versioni, veniva restituito un errore.


In WMF 5.1:

* L'utente può usare la [tabella hash](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx) `ModuleSpecification`. Questa tabella hash ha lo stesso formato di `Get-Module -FullyQualifiedName`.

**Esempio:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Se sono presenti più versioni del modulo, PowerShell usa la **stessa logica di risoluzione** di `Import-Module` e non restituisce un errore. Comportamento analogo a `Import-Module` e `Import-DscResource`.

## Miglioramenti apportati alla console di PowerShell

Per migliorare l'uso della console, sono state apportate a powershell.exe in WMF 5.1 le modifiche seguenti:

###Supporto per VT100

Windows 10 ha aggiunto il supporto per le [sequenze di escape VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
Quando si calcola la larghezza delle tabelle, PowerShell ignorerà determinate sequenze di escape di formattazione VT100.

PowerShell ha inoltre aggiunto una nuova API che può essere usata per la formattazione di codice in modo da determinare se VT100 è supportato. Ad esempio:

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
Ecco un [esempio](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo che può essere usato per evidenziare le corrispondenze di Select-String.
Salvare l'esempio in un file denominato `MatchInfo.format.ps1xml` quindi per usarlo, nel profilo o altrove, eseguire `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Si noti che le sequenze di escape VT100 sono supportate solo a partire dall'aggiornamento Aniversary di Windows 10. Non sono supportate nei sistemi precedenti.   

### Supporto della modalità vi in PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) aggiunge il supporto per la modalità vi. Per usare la modalità vi, eseguire `Set-PSReadline -EditMode vi`.

### Stdin reindirizzato con input interattivo 

Nelle versioni precedenti, veniva richiesto l'avvio di PowerShell con `powershell -File -` quando stdin veniva reindirizzato e si volevano immettere i comandi in modo interattivo.

Con WMF 5.1, questa opzione di difficile individuazione non è più necessaria. È infatti possibile avviare PowerShell senza opzioni, ad esempio `powershell`.

Si noti che PSReadline al momento non supporta stdin reindirizzato e la funzionalità di modifica della riga di comando integrata con stdin reindirizzato è estremamente limitata, ad esempio non è possibile usare i tasti di direzione.  Questo problema verrà risolto nella versione successiva di PSReadline.   

##Miglioramenti apportati al motore PowerShell

I miglioramenti seguenti apportati al motore di PowerShell principale sono stati implementati in WMF 5.1:


## Prestazioni ##

Le prestazioni sono migliorate in alcune aree importanti:

- Avvio
- Pipelining ai cmdlet quali ForEach-Object e Where-Object più veloce del 50% circa 

Alcuni miglioramenti di esempio (i risultati possono variare in base all'hardware): 

| Scenario | 5.0 - Tempo (ms) | 5.1 - Tempo (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Prima esecuzione di PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Cache di analisi del comando integrata: `powershell -command "Unknown-Command"` | 7000 | 520 |
| '1..1000000 | % { }' | 1400 | 750 |
  
> [!NOTE]  
> Una modifica correlata all'avvio può avere impatto su alcuni scenari non supportati. PowerShell non legge i file `$pshome\*.ps1xml`: questi file sono stati convertiti in C# per evitare il sovraccarico dell'elaborazione di file XML da parte di alcuni file e della CPU. I file supportano ancora V2 side-by-side, pertanto se si modifica il contenuto del file, la modifica non avrà alcun impatto su V5, ma solo su V2. Si noti che la modifica dei contenuti di questi file non ha mai costituito uno scenario supportato.

Un'altra modifica evidente riguarda la modalità di memorizzazione nella cache dei comandi esportati e di altre informazioni relative ai moduli installati in un sistema da parte di PowerShell. In precedenza, la cache veniva archiviata nella directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. In WMF 5.1, la cache è un singolo file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Per altre informazioni dettagliate, vedere [analysis_cache.md]().



## Correzioni di bug ##

Sono stati corretti i bug importanti seguenti:

### Rispetto completo del modulo auto-discovery `$env:PSModulePath` ###

In WMF 3 è stato introdotto il modulo auto-discovery (caricamento automatico di moduli senza un'istanza esplicita di Import-Module quando si chiama un comando). Quando è stata introdotta tale versione, PowerShell cercava i comandi in `$PSHome\Modules` prima di usare `$env:PSModulePath`.

WMF 5.1 modifica questo comportamento per rispettare `$env:PSModulePath` completamente. In questo modo, un modulo creato dall'utente che definisce i comandi di PowerShell (ad esempio `Get-ChildItem`) può essere caricato automaticamente e può sostituire correttamente il comando integrato.

### Reindirizzamento del file non più come hardcoded `-Encoding Unicode` ###

In tutte le versioni precedenti di PowerShell, non era possibile controllare la codifica del file usato dall'operatore di reindirizzamento di file, ad esempio `get-childitem > out.txt` perché PowerShell aveva aggiunto `-Encoding Unicode`.

A partire da WMF 5.1, è ora possibile modificare la codifica del file di reindirizzamento impostando `$PSDefaultParameterValues`, ad esempio

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Correzione di una regressione nell'accesso dei membri di `System.Reflection.TypeInfo` ###

Una regressione introdotta in WMF 5.0 interrompeva l'accesso ai membri di `System.Reflection.RuntimeType`, ad esempio `[int].ImplementedInterfaces`.
Questo bug è stato risolto in WMF 5.1.


### Risolti alcuni problemi con gli oggetti COM ###

In WMF 5.0 è stato introdotto un nuovo strumento di associazione COM per richiamare metodi su oggetti COM e accedere alle proprietà degli oggetti COM.
Questo nuovo strumento di associazione ha migliorato in modo significativo le prestazioni e ha inoltre introdotto alcuni bug che sono stati corretti in WMF 5.1.

#### Le conversioni di argomenti non venivano sempre eseguite correttamente ####

Nell'esempio seguente:

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

Il metodo SendKeys prevede una stringa, ma PowerShell non converte il carattere in una stringa, rinviando la conversione a IDispatch::Invoke che usa VariantChangeType per eseguire la conversione. In questo esempio, ciò ha comportato l'invio di chiavi '1', '7' e '3' anziché la chiave Volume.Mute prevista.

#### Gli oggetti COM enumerabili non venivano sempre gestiti correttamente ####

PowerShell in genere enumera la maggior parte degli oggetti enumerabili, ma una regressione introdotta in WMF 5.0 impediva l'enumerazione di oggetti COM che implementano IEnumerable.  Ad esempio:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

Nell'esempio precedente, WMF 5.0 ha scritto in modo errato Scripting.Dictionary nella pipeline anziché enumerare le coppie chiave-valore.


### `[ordered]` non è consentito all'interno delle classi ###

In WMF 5 sono state introdotte classi con la convalida dei valori letterali di tipo per le classi.  `[ordered]` è simile a un valore letterale di tipo ma non è un tipo .Net.  WMF 5 restituiva erroneamente un errore relativo a `[ordered]` in una classe:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### Supporto non funzionante sugli argomenti della Guida con più versioni ###

Prima di WMF 5.1, se erano installate più versioni di un modulo e tutte condividevano un argomento della Guida, ad esempio about_PSReadline, `help about_PSReadline` restituiva più argomenti e non era possibile visualizzare la Guida vera e propria.

In WMF 5.1 il problema è stato risolto restituendo la Guida per la versione più recente dell'argomento.

Get-Help non fornisce un modo per specificare la versione per la quale si vuole visualizzare la Guida. Per risolvere il problema, passare alla directory dei moduli e visualizzare la Guida direttamente con uno strumento come il proprio editor preferito. 

## Miglioramenti apportati a OneGet
WMF 5.1 include una serie di correzioni e miglioramenti per risolvere alcuni dei problemi rilevati dagli utenti della versione WMF 5.0. 

###Rimozione dell'alias della versione

**Scenario**: se si dispone delle versioni 1.0 e 2.0 di un pacchetto, P1, installate nel sistema e si vuole disinstallare la versione 1.0, è necessario eseguire "uninstall-package -name P1 -version 1.0" e attendere che la versione 1.0 venga disinstallata dopo l'esecuzione del cmdlet. Tuttavia, il risultato è che viene disinstallata la versione 2.0. 
    
Ciò si verifica perché il parametro "-version" è un alias del parametro "-minimumversion". Quando OneGet esegue la ricerca di un pacchetto qualificato con la versione minima 1.0, restituisce la versione più recente. Questo comportamento è previsto nei casi normali, perché trovare la versione più recente è in genere il risultato desiderato. Tuttavia, non dovrebbe applicarsi al caso di uninstall-package.
    
**Soluzione**: in WMF 5.1 l'alias -version viene rimosso completamente in OneGet e PowerShellGet. 

###Più richieste per l'avvio del provider NuGet

**Scenario**: quando si esegue Find-Module o Install-Module o altri cmdlet OneGet nel computer in uso per la prima volta, OneGet tenta di avviare il provider NuGet. Ciò avviene perché il provider PowerShellGet usa anche il provider NuGet per scaricare i moduli di PowerShell. OneGet quindi chiede all'utente l'autorizzazione per installare il provider NuGet. Dopo che l'utente seleziona "Sì" per l'avvio, verrà installata la versione più recente del provider NuGet. 
    
Tuttavia, in alcuni casi, quando si dispone di una versione precedente del provider NuGet installata nel computer in uso, in alcuni casi viene caricata per prima la versione precedente di NuGet nella sessione di PowerShell. Si tratta della race condition di OneGet. Tuttavia PowerShellGet richiede la versione più recente del provider NuGet, pertanto PowerShellGet chiede a OneGet di avviare nuovamente il provider NuGet. Ciò comporta l'esecuzione di più richieste di avvio del provider NuGet.

**Soluzione**: In WMF 5.1, OneGet carica la versione più recente del provider NuGet per evitare l'esecuzione di più richieste di avvio del provider NuGet.

È possibile aggirare il problema anche eliminando manualmente la versione precedente del provider NuGet (NuGet-Anycpu.exe), se presente, da $env:Programmi\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


###Supporto per OneGet nei computer solo con accesso Intranet

**Scenario**: In WMF 5.0, OneGet non supportava i computer che disponevano solo dell'accesso Intranet, ma non Internet.

**Soluzione**: In WMF 5.1, è possibile seguire questa procedura per consentire ai computer Intranet di usare OneGet:

1. Scaricare il provider NuGet usando un altro computer che dispone di una connessione Internet tramite Install-PackageProvider NuGet.

2. Trovare il provider NuGet in $env:Programmi\PackageManagement\ProviderAssemblies\nuget o $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

3. Copiare i file binari in una cartella o in una condivisione di rete a cui il computer Intranet può accedere e quindi installare il provider NuGet con "Install-PackageProvider NuGet -Source <Path to folder>".


###Miglioramenti apportati alla registrazione di eventi

Quando si installano i pacchetti, si modifica lo stato del computer. In WMF 5.1, OneGet registra gli eventi nel registro eventi di Windows per installare, disinstallare e salvare le attività del pacchetto. Il canale dell'evento è identico a quello di PowerShell, ovvero Microsoft-Windows-PowerShell/Operational.

###Supporto per l'autenticazione di base

In WMF 5.1, OneGet supporta la ricerca e l'installazione dei pacchetti da un repository che richiede l'autenticazione di base. È possibile fornire le credenziali ai cmdlet Find-Package e Install-Package. Ad esempio:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
###Supporto per l'uso di OneGet protetto da un proxy

In WMF 5.1, OneGet accetta ora nuovi parametri proxy: -ProxyCredential e -Proxy. Grazie a questi parametri è possibile specificare le credenziali e l'URL del proxy nei cmdlet di OneGet. Per impostazione predefinita, vengono usate le impostazioni proxy del sistema. Ad esempio:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


