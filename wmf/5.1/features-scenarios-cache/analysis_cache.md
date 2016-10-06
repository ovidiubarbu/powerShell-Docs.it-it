# Modulo Analysis Cache #

A partire dalla versione 5.1, PowerShell fornisce il controllo seguente sul file che viene usato per memorizzare nella cache i dati relativi a un modulo, ad esempio i comandi esportati.

Per impostazione predefinita, questa cache è archiviata nel file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
La cache viene in genere letta all'avvio durante la ricerca di un comando e viene scritta in un thread in background ad un certo punto dopo l'importazione di un modulo.

Per modificare il percorso predefinito della cache, impostare la variabile di ambiente PSModuleAnalysisCachePath prima di avviare PowerShell. Le modifiche apportate a questa variabile di ambiente influiranno solo sui processi figlio.
Il valore deve denominare un percorso completo (nome di file incluso) per il quale PowerShell dispone dell'autorizzazione per creare e scrivere file.
Per disabilitare la cache del file, questo valore può essere impostato su un percorso non valido, ad esempio

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Questo imposta il percorso su un dispositivo non valido. Non verrà visualizzato alcun errore se PowerShell non riesce a scrivere nel percorso, benché sia possibile visualizzare una segnalazione errori mediante un'utilità di traccia:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Quando si scrive nella cache, PowerShell controllerà i moduli non più disponibili per evitare di aumentare inutilmente le dimensioni della cache.
Talvolta questi controlli non sono consigliabili. In questo caso, è possibile disattivarli impostando

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

L'impostazione di questa variabile di ambiente avrà effetto immediato nel processo corrente.

<!--HONumber=Aug16_HO3-->


