---
title: Denominazione dei file della Guida | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367010"
---
# <a name="naming-help-files"></a>Denominazione dei file della Guida

In questo argomento viene illustrato come assegnare un nome a un file della guida basato su XML in modo che il cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) possa trovarlo. I requisiti del nome variano a seconda del tipo di comando.

## <a name="cmdlet-help-files"></a>File della Guida dei cmdlet

Il nome del file della C# guida per un cmdlet deve essere relativo all'assembly in cui è definito il cmdlet. Usare il formato del nome file seguente:

```
<AssemblyName>.dll-help.xml
```

Il formato del nome dell'assembly è obbligatorio anche quando l'assembly è un modulo annidato.

Ad esempio, [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) il cmdlet è definito nell'assembly Microsoft. PowerShell. Diagnostics. dll. Il cmdlet `Get-Help` Cerca un argomento della Guida per il cmdlet `Get-WinEvent` solo nel file Microsoft. PowerShell. Diagnostics. dll-help. XML nella directory del modulo.

## <a name="provider-help-files"></a>File della guida del provider

Il file della Guida per un provider di Windows PowerShell deve essere denominato per l'assembly in cui è definito il provider. Usare il formato del nome file seguente:

```
<AssemblyName>.dll-help.xml
```

Il formato del nome dell'assembly è obbligatorio anche quando l'assembly è un modulo annidato.

Ad esempio, il provider di certificati viene definito nell'assembly Microsoft. PowerShell. Security. dll. Il cmdlet `Get-Help` Cerca un argomento della Guida per il provider di certificati solo nel file Microsoft. PowerShell. Security. dll-help. XML nella directory del modulo.

## <a name="function-help-files"></a>File della Guida per le funzioni

Per documentare le funzioni, è possibile usare la [Guida basata su Commenti](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentata in un file della Guida XML. Quando la funzione è documentata in un file XML, la funzione deve avere una parola chiave `.ExternalHelp` commento che associa la funzione al file XML. In caso contrario, il cmdlet `Get-Help` non riesce a trovare il file della guida.

Non sono previsti requisiti tecnici per il nome di un file della Guida per le funzioni. Tuttavia, una procedura consigliata consiste nel denominare il file della Guida per il modulo di script in cui la funzione è definita. Ad esempio, la funzione seguente viene definita nel file con estensione psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>File della guida del comando CIM

Il file della Guida per un comando CIM deve essere denominato per il file CDXML in cui è definito il comando CIM. Usare il formato del nome file seguente:

```
<FileName>.cdxml-help.xml
```

I comandi CIM sono definiti nei file CDXML che possono essere inclusi nei moduli come moduli annidati. Quando il comando CIM viene importato nella sessione come funzione, Windows PowerShell aggiunge una parola chiave `.ExternalHelp` comment alla definizione di funzione che associa la funzione a un file della Guida XML denominato per il file CDXML in cui è definito il comando CIM.

## <a name="script-workflow-help-files"></a>File della guida del flusso di lavoro script

I flussi di lavoro di script inclusi nei moduli possono essere documentati in file della Guida basati su XML. Non sono previsti requisiti tecnici per il nome del file della guida. Tuttavia, una procedura consigliata consiste nel denominare il file della Guida per il modulo di script in cui viene definito il flusso di lavoro di script. Ad esempio:

```
<ScriptModule>.psm1-help.xml
```

A differenza di altri comandi con script, i flussi di lavoro di script non richiedono una parola chiave di commento `.ExternalHelp` per associarli a un file della guida. Windows PowerShell cerca invece le sottodirectory specifiche delle impostazioni cultura dell'interfaccia utente della directory dei moduli per i file della Guida basati su XML e cerca la guida per il flusso di lavoro di script in tutti i file. `.ExternalHelp` parola chiave comment viene ignorata.

Poiché la parola chiave `.ExternalHelp` comment viene ignorata, il cmdlet `Get-Help` può trovare la guida per i flussi di lavoro di script solo quando sono inclusi nei moduli.