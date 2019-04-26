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
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082193"
---
# <a name="installing-a-powershell-module"></a>Installazione di un modulo di PowerShell

Dopo aver creato il modulo di PowerShell, è opportuno installare il modulo in un sistema, in modo che può essere utilizzata o da altri. In generale, si tratta semplicemente di Sto copiando il modulo (Internet Explorer, psm1, o l'assieme binario, il manifesto del modulo e tutti gli altri file associati) in una directory in tale computer. Per un progetto molto piccolo, potrebbe essere semplice come copiare e incollare i file con Windows Explorer in un singolo computer remoto. Tuttavia, per soluzioni di maggiori dimensioni si consiglia di usare un processo di installazione più sofisticato. Indipendentemente dal modo in cui viene visualizzato un modulo di sistema, PowerShell può utilizzare una serie di tecniche che permettono agli utenti di trovare e usare i moduli. (Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).) Pertanto, il problema principale per l'installazione consiste nel garantire che PowerShell sarà in grado di trovare il modulo.

In questo argomento contiene le sezioni seguenti:

- Regole per l'installazione dei moduli

- Percorso in cui installare i moduli

- Installazione di più versioni di un modulo

- Conflitti di nomi di comando di gestione

## <a name="rules-for-installing-modules"></a>Regole per l'installazione dei moduli

Le informazioni seguenti si riferiscono a tutti i moduli, tra cui moduli che si creano per il proprio utilizzo, i moduli che si ottengono da altre parti e i moduli distribuiti agli altri utenti.

### <a name="install-modules-in-psmodulepath"></a>Installare i moduli in PSModulePath

Quando possibile, installare tutti i moduli in un percorso elencato nella **PSModulePath** variabile di ambiente o aggiungere il percorso del modulo per il **PSModulePath** valore variabile di ambiente.

Il **PSModulePath** variabile di ambiente ($Env: PSModulePath) contiene i percorsi dei moduli di Windows PowerShell. I cmdlet si basano sul valore di questa variabile di ambiente per trovare i moduli.

Per impostazione predefinita, il **PSModulePath** valore variabile ambiente contiene il sistema seguente e le directory modulo utente, ma è possibile aggiungere e modificare il valore.

- $PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Questo percorso è riservato per i moduli forniti con Windows. È necessario installare i moduli in questo percorso.

- $Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)

  Per ottenere il valore della **PSModulePath** variabile di ambiente, usare uno dei comandi seguenti.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Per aggiungere un percorso del modulo al valore di **PSModulePath** variabile di ambiente valore, utilizzare il comando nel formato seguente. Questo formato utilizza il **SetEnvironmentVariable** metodo del **System. Environment** classe apportare una modifica di sessione indipendente per il **PSModulePath** ambiente variabile.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Dopo aver aggiunto il percorso **PSModulePath**, si deve trasmettere un messaggio di ambiente sulla modifica. La modifica di trasmissione consente ad altre applicazioni, come la shell, rilevi la modifica. Per trasmettere la modifica, che il codice di installazione del prodotto invii un **WM_SETTINGCHANGE** dei messaggi con `lParam` impostato sulla stringa "Ambiente". Assicurarsi di inviare il messaggio dopo che il codice di installazione del modulo è aggiornati **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Usare il nome di Directory di modulo corretto

Un "corretto" è un modulo che viene archiviato in una directory che ha lo stesso nome come nome di base di almeno un file nella directory del modulo. Se un modulo non è corretto, Windows PowerShell non riconosce lo come modulo.

Il nome"base" di un file è il nome senza l'estensione del nome file. In un modulo in formato corretto, il nome della directory che contiene i file di modulo deve corrispondere al nome di base di almeno un file nel modulo.

Ad esempio, nel modulo esempio Fabrikam, la directory che contiene i file di modulo è denominata "Fabrikam" e almeno un file con il nome di base "Fabrikam". In questo caso sia Fabrikam.psd1 Fabrikam.dll hanno il nome di base "Fabrikam".

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

Se il modulo non è ben formato e il percorso non è incluso nel valore della **PSModulePath** variabile di ambiente, le funzionalità di individuazione di base di Windows PowerShell, ad esempio il comando seguente, non funzionano.

- La funzionalità di modulo Auto-caricamento non è possibile importare il modulo automaticamente.

- Il `ListAvailable` parametro il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet non è possibile trovare il modulo.

- Il [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet non è possibile trovare il modulo. Per importare il modulo, è necessario specificare il percorso completo del file di modulo radice o di un file manifesto del modulo.

  Funzionalità aggiuntive, ad esempio il comando seguente, non funzionano a meno che non viene importato il modulo nella sessione. Nei moduli in formato corretto nel **PSModulePath** variabile di ambiente, queste funzionalità a funzionare anche quando il modulo non viene importato nella sessione.

- Il [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet non è possibile trovare i comandi del modulo.

- Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet non può aggiornare o salvare la Guida per il modulo.

- Il [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet non è possibile trovare e visualizzare i comandi nel modulo.

  I comandi del modulo non sono presenti il `Show-Command` finestra in Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Percorso in cui installare i moduli

Questa sezione descrive la posizione nel file system per installare i moduli di Windows PowerShell. Il percorso dipende dal modo in cui viene usato il modulo.

### <a name="installing-modules-for-a-specific-user"></a>Installazione dei moduli per un utente specifico

Se si crea un modulo personalizzato o ottiene un modulo da un'altra entità, ad esempio un sito Web della community di Windows PowerShell, e si vuole che il modulo sia disponibile per l'account utente solo, installare il modulo nella directory di moduli specifici dell'utente.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

Directory dei moduli specifici dell'utente viene aggiunto al valore della **PSModulePath** variabile di ambiente per impostazione predefinita.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installazione dei moduli per tutti gli utenti nei file di programma

Se si desidera che un modulo sia disponibile per tutti gli account utente nel computer, installare il modulo nel percorso di file di programma.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> Per impostazione predefinita in Windows PowerShell 4.0 e versioni successive, il percorso di file di programma viene aggiunto al valore della variabile di ambiente PSModulePath. Per le versioni precedenti di Windows PowerShell, è possibile creare ((%ProgramFiles%\WindowsPowerShell\Modules) il percorso file di programma manualmente e Aggiungi il percorso alla variabile di ambiente PSModulePath, come descritto in precedenza.

### <a name="installing-modules-in-a-product-directory"></a>Installazione dei moduli in una Directory di prodotto

Se si prevede di distribuire il modulo ad altri soggetti, usare il percorso di file del programma predefinito descritto in precedenza oppure creare proprie sottodirectory specifiche della società o specifici del prodotto della directory % ProgramFiles %.

Tecnologie di Fabrikam, una società fittizia, ad esempio, è destinato ad un modulo di Windows PowerShell per il prodotto di gestione Fabrikam. Il programma di installazione del modulo viene creata una sottodirectory di moduli nella sottodirectory product Manager di Fabrikam.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Per abilitare le funzionalità di individuazione del modulo Windows PowerShell trovare il modulo di Fabrikam, il programma di installazione di modulo di Fabrikam aggiunge il percorso del modulo per il valore della **PSModulePath** variabile di ambiente.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installazione dei moduli nella Directory di file comuni

Se un modulo è utilizzato da più componenti di un prodotto o da più versioni di un prodotto, installare il modulo in una sottodirectory specifiche dei moduli della sottodirectory Files\Modules %ProgramFiles%\Common.

Nell'esempio seguente, in una sottodirectory di Fabrikam della sottodirectory Files\Modules %ProgramFiles%\Common è installato il modulo di Fabrikam. Si noti che ogni modulo si trovi in una sottodirectory nella sottodirectory moduli.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Quindi, il programma di installazione verifica che il valore della **PSModulePath** variabile di ambiente include il percorso della sottodirectory moduli file comuni.

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

Per installare più versioni dello stesso modulo, usare la procedura seguente.

1. Creare una directory per ogni versione del modulo. Includere il numero di versione nel nome della directory.

2. Creare un manifesto del modulo per ogni versione del modulo. Nel valore della **ModuleVersion** chiave nel manifesto, immettere il numero di versione del modulo. Salvare il file manifesto (psd1) nella directory specifica della versione per il modulo.

3. Aggiungere il percorso della cartella radice modulo il valore di **PSModulePath** variabile di ambiente, come illustrato negli esempi seguenti.

Per importare una particolare versione del modulo, l'utente finale può usare il `MinimumVersion` oppure `RequiredVersion` i parametri del [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Ad esempio, se il modulo di Fabrikam è disponibile nelle versioni 8.0 e 9.0, la struttura di directory del modulo Fabrikam potrebbe essere simile al seguente.

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

Il programma di installazione aggiunge entrambi i percorsi dei moduli per la **PSModulePath** valore variabile di ambiente.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Quando questi passaggi sono stati completati, il **ListAvailable** parametro delle [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet recupera entrambi i moduli di Fabrikam. Per importare un modulo specifico, usare il `MinimumVersion` oppure `RequiredVersion` i parametri delle [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Se entrambi i moduli vengono importati nella stessa sessione e i moduli contengono cmdlet con gli stessi nomi, i cmdlet che vengano importati per ultimo vengono applicati nella sessione.

## <a name="handling-command-name-conflicts"></a>Conflitti di nomi di comando di gestione

Quando i comandi esportati da un modulo hanno lo stesso nome di comandi nella sessione dell'utente, possono verificarsi conflitti di nome di comando.

Quando una sessione contiene due comandi che hanno lo stesso nome, Windows PowerShell viene eseguito il tipo di comando che ha la precedenza. Quando una sessione contiene due comandi che hanno lo stesso nome e lo stesso tipo, Windows PowerShell esegue il comando che è stato aggiunto alla sessione più recente. Per eseguire un comando che non viene eseguito per impostazione predefinita, gli utenti possono qualificare il nome di comando con il nome del modulo.

Ad esempio, se la sessione contiene una `Get-Date` funzione e `Get-Date` cmdlet di Windows PowerShell esegue la funzione per impostazione predefinita. Per eseguire il cmdlet, anteporre il comando con il nome del modulo, ad esempio:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Per evitare conflitti di nomi, gli autori di moduli è possono usare la **DefaultCommandPrefix** chiave nel manifesto del modulo per specificare un prefisso per tutti i comandi esportati dal modulo.

Gli utenti possono usare la **prefisso** parametro del `Import-Module` cmdlet da usare un prefisso alternativo. Il valore della **Prefix** parametro ha la precedenza sul valore della **DefaultCommandPrefix** chiave.

## <a name="see-also"></a>Vedere anche

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
