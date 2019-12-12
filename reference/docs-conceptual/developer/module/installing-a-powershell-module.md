---
title: Installazione di un modulo di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367070"
---
# <a name="installing-a-powershell-module"></a>Installazione di un modulo di PowerShell

Dopo aver creato il modulo di PowerShell, è probabile che si voglia installare il modulo in un sistema, in modo che l'utente o altri utenti possano usarlo. In generale, è costituito dalla copia dei file di modulo (ad esempio, psm1 o dell'assembly binario, del manifesto del modulo e di qualsiasi altro file associato) in una directory del computer. Per un progetto di dimensioni molto ridotte, può essere semplice copiare e incollare i file con Esplora risorse in un singolo computer remoto. Tuttavia, per soluzioni di dimensioni maggiori è consigliabile usare un processo di installazione più sofisticato. Indipendentemente dal modo in cui si ottiene il modulo nel sistema, PowerShell può usare diverse tecniche che consentono agli utenti di trovare e usare i moduli. Pertanto, il problema principale per l'installazione è garantire che PowerShell sia in grado di trovare il modulo. Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).

## <a name="rules-for-installing-modules"></a>Regole per l'installazione dei moduli

Le informazioni seguenti riguardano tutti i moduli, inclusi i moduli creati per uso personale, i moduli che si ottengono da altre parti e i moduli distribuiti ad altri utenti.

### <a name="install-modules-in-psmodulepath"></a>Installare i moduli in PSModulePath

Quando possibile, installare tutti i moduli in un percorso elencato nella variabile di ambiente **PSModulePath** o aggiungere il percorso del modulo al valore della variabile di ambiente **PSModulePath** .

La variabile di ambiente **PSModulePath** ($ENV:P smodulepath) contiene le posizioni dei moduli di Windows PowerShell. I cmdlet si basano sul valore di questa variabile di ambiente per trovare i moduli.

Per impostazione predefinita, il valore della variabile di ambiente **PSModulePath** contiene le seguenti directory dei moduli di sistema e utente, ma è possibile aggiungere e modificare il valore.

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Questo percorso è riservato ai moduli forniti con Windows. Non installare i moduli in questo percorso.

- `$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  Per ottenere il valore della variabile di ambiente **PSModulePath** , usare uno dei comandi seguenti.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Per aggiungere un percorso del modulo al valore del valore della variabile di ambiente **PSModulePath** , usare il seguente formato di comando. Questo formato usa il metodo **nell'SetEnvironmentVariable** della classe **System. Environment** per apportare una modifica indipendente dalla sessione alla variabile di ambiente **PSModulePath** .

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Una volta aggiunto il percorso di **PSModulePath**, è necessario trasmettere un messaggio di ambiente sulla modifica. La trasmissione della modifica consente ad altre applicazioni, ad esempio la shell, di prelevare la modifica. Per trasmettere la modifica, fare in modo che il codice di installazione del prodotto invii un messaggio di **WM_SETTINGCHANGE** con `lParam` impostato sulla stringa "Environment". Assicurarsi di inviare il messaggio dopo l'aggiornamento del codice di installazione del modulo **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Usa il nome di directory del modulo corretto

Un modulo ben formato è un modulo archiviato in una directory con lo stesso nome del nome di base di almeno un file nella directory del modulo. Se un modulo non è ben formato, Windows PowerShell non lo riconosce come modulo.

Il nome di base di un file è il nome senza l'estensione del nome file. In un modulo ben formato, il nome della directory che contiene i file di modulo deve corrispondere al nome di base di almeno un file nel modulo.

Nel modulo Fabrikam di esempio, ad esempio, la directory che contiene i file di modulo è denominata "Fabrikam" e almeno un file ha il nome di base "Fabrikam". In questo caso, sia Fabrikam. psd1 che Fabrikam. dll hanno il nome di base "Fabrikam".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Effetto dell'installazione non corretta

Se il modulo non è ben formato e la relativa posizione non è inclusa nel valore della variabile di ambiente **PSModulePath** , le funzionalità di individuazione di base di Windows PowerShell, ad esempio le seguenti, non funzionano.

- La funzionalità di caricamento automatico del modulo non è in grado di importare il modulo automaticamente.

- Il parametro `ListAvailable` del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) non riesce a trovare il modulo.

- Il cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) non è in grado di trovare il modulo. Per importare il modulo, è necessario specificare il percorso completo del file del modulo radice o del file manifesto del modulo.

  Le funzionalità aggiuntive, come quelle riportate di seguito, non funzionano a meno che il modulo non venga importato nella sessione. Nei moduli ben formati della variabile di ambiente **PSModulePath** , queste funzionalità funzionano anche quando il modulo non viene importato nella sessione.

- Il cmdlet [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) non è in grado di trovare comandi nel modulo.

- I cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) non possono aggiornare o salvare la guida per il modulo.

- Il cmdlet [show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) non riesce a trovare e visualizzare i comandi nel modulo.

  I comandi nel modulo non sono presenti nella finestra `Show-Command` in Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Posizione in cui installare i moduli

Questa sezione illustra il punto in cui file system installare i moduli di Windows PowerShell. Il percorso dipende dalla modalità di utilizzo del modulo.

### <a name="installing-modules-for-a-specific-user"></a>Installazione dei moduli per un utente specifico

Se si crea un modulo personalizzato o si ottiene un modulo da un'altra parte, ad esempio un sito Web della community di Windows PowerShell e si vuole che il modulo sia disponibile solo per l'account utente, installare il modulo nella directory dei moduli specifici dell'utente.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

Per impostazione predefinita, la directory dei moduli specifici dell'utente viene aggiunta al valore della variabile di ambiente **PSModulePath** .

### <a name="installing-modules-for-all-users-in-program-files"></a>Installazione dei moduli per tutti gli utenti nei file di programma

Se si vuole che un modulo sia disponibile per tutti gli account utente nel computer, installare il modulo nel percorso dei file di programma.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> Il percorso dei file di programma viene aggiunto per impostazione predefinita al valore della variabile di ambiente PSModulePath in Windows PowerShell 4,0 e versioni successive. Per le versioni precedenti di Windows PowerShell, è possibile creare manualmente il percorso dei file di programma ((%ProgramFiles%\WindowsPowerShell\Modules) e aggiungere questo percorso alla variabile di ambiente PSModulePath come descritto in precedenza.

### <a name="installing-modules-in-a-product-directory"></a>Installazione di moduli in una directory di prodotto

Se si distribuisce il modulo ad altre parti, utilizzare il percorso predefinito dei file di programma descritto in precedenza oppure creare una sottodirectory specifica per l'azienda o per il prodotto della directory% ProgramFiles%.

Ad esempio, le tecnologie Fabrikam, una società fittizia, sta spedendo un modulo di Windows PowerShell per il proprio prodotto di gestione fabrikam. Il programma di installazione del modulo crea una sottodirectory Modules nella sottodirectory Product Manager di Fabrikam.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Per abilitare le funzionalità di individuazione dei moduli di Windows PowerShell per trovare il modulo Fabrikam, il programma di installazione del modulo Fabrikam aggiunge il percorso del modulo al valore della variabile di ambiente **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installazione dei moduli nella directory dei file comuni

Se un modulo viene usato da più componenti di un prodotto o da più versioni di un prodotto, installare il modulo in una sottodirectory specifica del modulo della sottodirectory%programmi%\Common Files\Modules

Nell'esempio seguente il modulo Fabrikam viene installato in una sottodirectory Fabrikam della sottodirectory `%ProgramFiles%\Common Files\Modules`. Si noti che ogni modulo risiede nella propria sottodirectory nella sottodirectory modules.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

Quindi, il programma di installazione garantisce che il valore della variabile di ambiente **PSModulePath** includa il percorso della sottodirectory dei moduli di file comuni.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Installazione di più versioni di un modulo

Per installare più versioni dello stesso modulo, attenersi alla procedura riportata di seguito.

1. Creare una directory per ogni versione del modulo. Includere il numero di versione nel nome della directory.
2. Creare un manifesto del modulo per ogni versione del modulo. Nel valore della chiave **ModuleVersion** nel manifesto, immettere il numero di versione del modulo. Salvare il file manifesto (con estensione psd1) nella directory specifica della versione per il modulo.
3. Aggiungere il percorso della cartella radice del modulo al valore della variabile di ambiente **PSModulePath** , come illustrato negli esempi seguenti.

Per importare una versione specifica del modulo, l'utente finale può usare il `MinimumVersion` o `RequiredVersion` parametri del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Se, ad esempio, il modulo Fabrikam è disponibile nelle versioni 8,0 e 9,0, la struttura di directory del modulo Fabrikam potrebbe essere simile alla seguente.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

Il programma di installazione aggiunge entrambi i percorsi del modulo al valore della variabile di ambiente **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Una volta completati questi passaggi, il parametro **ListAvailable** del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) ottiene entrambi i moduli fabrikam. Per importare un modulo specifico, usare il `MinimumVersion` o `RequiredVersion` parametri del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Se entrambi i moduli vengono importati nella stessa sessione e i moduli contengono cmdlet con gli stessi nomi, i cmdlet importati per ultimi sono validi nella sessione.

## <a name="handling-command-name-conflicts"></a>Gestione dei conflitti di nomi di comando

I conflitti di nomi di comando possono verificarsi quando i comandi esportati da un modulo hanno lo stesso nome dei comandi della sessione dell'utente.

Quando una sessione contiene due comandi con lo stesso nome, Windows PowerShell esegue il tipo di comando che ha la precedenza. Quando una sessione contiene due comandi che hanno lo stesso nome e lo stesso tipo, Windows PowerShell esegue il comando aggiunto alla sessione più di recente. Per eseguire un comando che non viene eseguito per impostazione predefinita, gli utenti possono qualificare il nome del comando con il nome del modulo.

Se, ad esempio, la sessione contiene una funzione `Get-Date` e il cmdlet `Get-Date`, Windows PowerShell esegue la funzione per impostazione predefinita. Per eseguire il cmdlet, anteporre il comando al nome del modulo, ad esempio:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Per evitare conflitti di nomi, gli autori di moduli possono usare la chiave **DefaultCommandPrefix** nel manifesto del modulo per specificare un prefisso sostantivo per tutti i comandi esportati dal modulo.

Gli utenti possono utilizzare il parametro **Prefix** del cmdlet `Import-Module` per utilizzare un prefisso alternativo. Il valore del parametro **Prefix** ha la precedenza sul valore della chiave **DefaultCommandPrefix** .

## <a name="see-also"></a>Vedere anche

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
