---
title: Importazione di un modulo di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082246"
---
# <a name="importing-a-powershell-module"></a>Importazione di un modulo di PowerShell

Una volta di aver installato un modulo in un sistema, è opportuno importare il modulo. L'importazione è il processo che carica il modulo in memoria attiva, in modo che un utente può accedere a tale modulo nella sessione di PowerShell. In PowerShell 2.0, è possibile importare un modulo di PowerShell appena installato con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet. In PowerShell 3.0, PowerShell è in grado di importare in modo implicito un modulo quando una delle funzioni o cmdlet nel modulo viene chiamata da un utente. Si noti che entrambe le versioni si supponga di installa un modulo in una posizione in cui è in grado di trovarlo; PowerShell per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md). È possibile usare un manifesto del modulo per limitare le parti del modulo vengono esportate ed è possibile usare parametri del `Import-Module` chiamate per limitare quali parti vengono importate.

## <a name="importing-a-snap-in-powershell-10"></a>L'importazione di uno Snap-In (PowerShell 1.0)

I moduli non esisteva in PowerShell 1.0: al contrario, era necessario registrare e usare gli snap-in. Tuttavia, si consiglia di non a questo punto, si utilizza questa tecnologia come i moduli vengono in genere più semplici installare e importare. Per altre informazioni, vedere [come creare uno Snap-in PowerShell di Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importazione di un modulo con Import-Module (PowerShell 2.0)

PowerShell 2.0 viene utilizzato l'oggetto denominato in modo appropriato [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) per importare i moduli. Quando si esegue questo cmdlet, Windows PowerShell cerca il modulo specificato all'interno delle directory specificate nel `PSModulePath` variabile. Quando viene trovata nella directory specificata, Windows PowerShell cerca i file nell'ordine seguente: i file manifesto del modulo (con estensione psd1), modulo i file script (psm1), file del modulo binario (DLL). Per altre informazioni sull'aggiunta di directory per la ricerca, vedere [modifica il percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md). Il codice seguente viene descritto come importare un modulo:

```powershell
Import-Module myModule
```

Supponendo che è accessibile da myModule il `PSModulePath`, PowerShell carica myModule nella memoria attiva. Se myModule non si trova su un `PSModulePath` percorso, si potrebbe comunque indicare in modo esplicito PowerShell dove si trovano:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

È anche possibile usare il parametro - verbose per identificare ciò che viene esportata all'esterno del modulo e cosa viene importato nella memoria attiva. Le esportazioni e importazioni limitano ciò che viene esposto all'utente: la differenza è che controlla la visibilità. In pratica, le esportazioni sono controllate dal codice all'interno del modulo. Al contrario, le importazioni sono controllate dal `Import-Module` chiamare. Per altre informazioni, vedere **limitando i membri che vengono importati**riportato di seguito.

## <a name="implicitly-importing-a-module-powershell-30"></a>In modo implicito l'importazione di un modulo (PowerShell 3.0)

A partire da Windows PowerShell 3.0, moduli vengono importati automaticamente quando qualsiasi cmdlet o funzione nel modulo viene usato in un comando. Questa funzionalità funziona in tutti i moduli in una directory inclusi nel valore della **PSModulePath** variabile di ambiente. Se non si salva un modulo in un percorso UNC valido, tuttavia, è comunque possibile caricare tramite l'impostazione esplicita [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) opzione, descritto in precedenza.

Le azioni seguenti attivano l'importazione automatica di un modulo, noto anche come "modulo auto-caricamento."

- Usare un cmdlet in un comando. Ad esempio, se si digita `Get-ExecutionPolicy` Importa il modulo Security che contiene il `Get-ExecutionPolicy` cmdlet.

- Usando il [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) per ottenere il comando.  Ad esempio, se si digita `Get-Command Get-JobTrigger` Importa i **PSScheduledJob** modulo che contiene il `Get-JobTrigger` cmdlet. Oggetto `Get-Command` comando che include caratteri jolly è considerato individuazione e non attiva l'importazione di un modulo.

- Usando il [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet per ottenere assistenza per un cmdlet. Ad esempio, se si digita `Get-Help Get-WinEvent` Importa il modulo Microsoft.PowerShell.Diagnostics che contiene il `Get-WinEvent` cmdlet.

Per supportare l'importazione automatica dei moduli, i `Get-Command` cmdlet recupera tutti i cmdlet e funzioni in tutti i moduli installati, anche se il modulo non viene importato nella sessione. Per altre informazioni, vedere l'argomento della Guida per la [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.

## <a name="the-importing-process"></a>Il processo di importazione

Quando si importa un modulo, lo stato di una nuova sessione viene creato per il modulo e un [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) viene creato l'oggetto in memoria. Uno stato di sessione viene creato per ogni modulo importato (che include il modulo radice e tutti i moduli annidati). I membri esportati dal modulo radice, inclusi tutti i membri che sono stati esportati per il modulo radice per tutti i moduli annidati, vengono quindi importati nello stato sessione del chiamante.

I metadati dei membri che sono esportate da un modulo dispone di una proprietà ModuleName. Questa proprietà viene popolata con il nome del modulo che li esportato.

> [!WARNING]
> Se il nome di un membro esportato viene usato un verbo non approvato o se il nome del membro utilizza caratteri non consentiti, viene visualizzato un avviso quando la [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet viene eseguito.

Per impostazione predefinita, il [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet non restituisce tutti gli oggetti alla pipeline. Tuttavia, il cmdlet supporta una `PassThru` parametro che può essere usato per restituire un [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) oggetto per ogni modulo importato. Per inviare l'output all'host, gli utenti devono eseguire la [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Limitare i membri che vengono importati

Durante l'importazione di un modulo tramite il [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, per impostazione predefinita, tutti i moduli esportati i membri vengono importati nella sessione, inclusi tutti i comandi esportati per il modulo da un modulo annidato. Per impostazione predefinita, le variabili e alias non vengono esportate. Per limitare i membri esportati, usare una [manifesto del modulo](./how-to-write-a-powershell-module-manifest.md). Per limitare i membri che vengono importati, usare i parametri seguenti del `Import-Module` cmdlet.

- `Function`: Questo parametro consente di limitare le funzioni esportate. (Se si utilizza un manifesto del modulo, vedere la chiave FunctionsToExport).

- `Cmdlet`: Questo parametro limita i cmdlet esportati (se si è mediante un modulo manifesto, vedere la chiave CmdletsToExport.)

- `Variable`: Questo parametro limita le variabili esportate (se si è mediante un modulo manifesto, vedere la chiave VariablesToExport.)

- `Alias`: Questo parametro limita gli alias esportati (se si è mediante un modulo manifesto, vedere la chiave AliasesToExport.)

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
