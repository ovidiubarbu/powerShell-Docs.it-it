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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360700"
---
# <a name="importing-a-powershell-module"></a>Importazione di un modulo di PowerShell

Una volta installato un modulo in un sistema, è probabile che si desideri importare il modulo. L'importazione è il processo che carica il modulo nella memoria attiva, in modo che un utente possa accedere al modulo nella sessione di PowerShell. In PowerShell 2,0 è possibile importare un modulo di PowerShell appena installato con una chiamata al cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) . In PowerShell 3,0 PowerShell è in grado di importare in modo implicito un modulo quando una delle funzioni o dei cmdlet del modulo viene chiamata da un utente. Si noti che in entrambe le versioni si presuppone che il modulo venga installato in un percorso in cui PowerShell è in grado di trovarlo. per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md). È possibile utilizzare un manifesto del modulo per limitare le parti del modulo esportate ed è possibile utilizzare i parametri della chiamata `Import-Module` per limitare le parti importate.

## <a name="importing-a-snap-in-powershell-10"></a>Importazione di uno snap-in (PowerShell 1,0)

I moduli non esistono in PowerShell 1,0: è necessario registrare e usare gli snap-in. Tuttavia, non è consigliabile usare questa tecnologia a questo punto, perché i moduli sono in genere più facili da installare e importare. Per ulteriori informazioni, vedere [la pagina relativa alla creazione di uno snap-in di Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importazione di un modulo con Import-Module (PowerShell 2,0)

PowerShell 2,0 usa il cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) con nome appropriato per importare i moduli. Quando si esegue questo cmdlet, Windows PowerShell cerca il modulo specificato nelle directory specificate nella variabile `PSModulePath`. Quando viene trovata la directory specificata, Windows PowerShell cerca i file nell'ordine seguente: file manifesto del modulo (con estensione psd1), file del modulo di script (con estensione psm1), file dei moduli binari (. dll). Per ulteriori informazioni sull'aggiunta di directory alla ricerca, vedere [modifica del percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md). Il codice seguente descrive come importare un modulo:

```powershell
Import-Module myModule
```

Supponendo che il modulo si trovasse nel `PSModulePath`, PowerShell caricherà il modulo nella memoria attiva. Se il modulo non si trovava in un percorso `PSModulePath`, era comunque possibile indicare in modo esplicito a PowerShell dove trovarlo:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

È anche possibile usare il parametro-Verbose per identificare ciò che viene esportato dal modulo e cosa viene importato nella memoria attiva. Sia le esportazioni che le importazioni limitano gli elementi esposti all'utente: la differenza consiste nel controllare la visibilità. Essenzialmente, le esportazioni sono controllate dal codice all'interno del modulo. Al contrario, le importazioni vengono controllate dalla chiamata `Import-Module`. Per ulteriori informazioni, vedere la sezione relativa alla **restrizione dei membri importati**di seguito.

## <a name="implicitly-importing-a-module-powershell-30"></a>Importazione implicita di un modulo (PowerShell 3,0)

A partire da Windows PowerShell 3,0, i moduli vengono importati automaticamente quando si usa un cmdlet o una funzione nel modulo in un comando. Questa funzionalità funziona in qualsiasi modulo di una directory inclusa nel valore della variabile di ambiente **PSModulePath** . Se il modulo non viene salvato in un percorso valido, è comunque possibile caricarli usando l'opzione di [Importazione-modulo](/powershell/module/Microsoft.PowerShell.Core/Import-Module) esplicita descritta in precedenza.

Le azioni seguenti attivano l'importazione automatica di un modulo, noto anche come "caricamento automatico del modulo".

- Utilizzando un cmdlet in un comando. Ad esempio, digitando `Get-ExecutionPolicy` viene importato il modulo Microsoft. PowerShell. Security che contiene il cmdlet `Get-ExecutionPolicy`.

- Usare il cmdlet [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) per ottenere il comando.  Ad esempio, digitando `Get-Command Get-JobTrigger` viene importato il modulo **PSScheduledJob** che contiene il cmdlet `Get-JobTrigger`. Un comando `Get-Command` che include caratteri jolly viene considerato l'individuazione e non attiva l'importazione di un modulo.

- Usare il cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) per ottenere la guida per un cmdlet. Ad esempio, digitando `Get-Help Get-WinEvent` viene importato il modulo Microsoft. PowerShell. Diagnostics che contiene il cmdlet `Get-WinEvent`.

Per supportare l'importazione automatica dei moduli, il cmdlet `Get-Command` Ottiene tutti i cmdlet e le funzioni in tutti i moduli installati, anche se il modulo non viene importato nella sessione. Per ulteriori informazioni, vedere l'argomento della Guida relativo al cmdlet [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) .

## <a name="the-importing-process"></a>Processo di importazione

Quando viene importato un modulo, viene creato un nuovo stato della sessione per il modulo e un oggetto [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) viene creato in memoria. Viene creato uno stato sessione per ogni modulo importato (inclusi il modulo radice e tutti i moduli nidificati). I membri esportati dal modulo radice, inclusi i membri che sono stati esportati nel modulo radice da tutti i moduli annidati, vengono quindi importati nello stato sessione del chiamante.

I metadati dei membri esportati da un modulo hanno una proprietà ModuleName. Questa proprietà viene popolata con il nome del modulo che ha esportato.

> [!WARNING]
> Se il nome di un membro esportato usa un verbo non approvato o se il nome del membro usa caratteri limitati, viene visualizzato un avviso quando viene eseguito il cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Per impostazione predefinita, il cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) non restituisce alcun oggetto alla pipeline. Tuttavia, il cmdlet supporta un parametro `PassThru` che può essere usato per restituire un oggetto [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) per ogni modulo importato. Per inviare l'output all'host, gli utenti devono eseguire il cmdlet [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) .

## <a name="restricting--the-members-that-are-imported"></a>Limitazione dei membri importati

Quando un modulo viene importato usando il cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) , per impostazione predefinita tutti i membri del modulo esportati vengono importati nella sessione, inclusi tutti i comandi esportati nel modulo da un modulo annidato. Per impostazione predefinita, le variabili e gli alias non vengono esportati. Per limitare i membri esportati, utilizzare un [manifesto del modulo](./how-to-write-a-powershell-module-manifest.md). Per limitare i membri importati, utilizzare i seguenti parametri del cmdlet `Import-Module`.

- `Function`: questo parametro limita le funzioni esportate. Se si usa un manifesto del modulo, vedere la chiave FunctionsToExport.

- `Cmdlet`: questo parametro limita i cmdlet esportati. Se si usa un manifesto del modulo, vedere la chiave CmdletsToExport.

- `Variable`: questo parametro limita le variabili esportate. Se si usa un manifesto del modulo, vedere la chiave VariablesToExport.

- `Alias`: questo parametro limita gli alias esportati. Se si usa un manifesto del modulo, vedere la chiave AliasesToExport.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
