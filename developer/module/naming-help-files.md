---
title: I file della Guida di denominazione | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856667"
---
# <a name="naming-help-files"></a>Denominazione dei file della Guida

Questo argomento illustra come assegnare un nome di un file della Guida basati su XML in modo che il [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet possibile trovarlo. I requisiti di nomi variano per ogni tipo di comando.
Questo argomento illustra come assegnare un nome di un file della Guida basati su XML in modo che il [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet possibile trovarlo. I requisiti di nomi variano per ogni tipo di comando.

## <a name="cmdlet-help-files"></a>File della Guida dei cmdlet

Il file della Guida per un C# cmdlet devono essere specificate per l'assembly in cui è definito il cmdlet. Usare il formato del nome file seguente:

```
<AssemblyName>.dll-help.xml
```

Il formato di nome di assembly è obbligatorio anche quando l'assembly è un modulo annidato.

Ad esempio, il [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet è definito nell'assembly Microsoft.PowerShell.Diagnostics.dll. Il `Get-Help` cmdlet Cerca un argomento della Guida per il `Get-WinEvent` cmdlet solo nel file Microsoft.PowerShell.Diagnostics.dll help.xml nella directory del modulo.
Ad esempio, il [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet è definito nell'assembly Microsoft.PowerShell.Diagnostics.dll. Il `Get-Help` cmdlet Cerca un argomento della Guida per il `Get-WinEvent` cmdlet solo nel file Microsoft.PowerShell.Diagnostics.dll help.xml nella directory del modulo.

## <a name="provider-help-files"></a>File della Guida di provider

File della Guida per un provider di Windows PowerShell deve essere denominato per l'assembly in cui è definito il provider. Usare il formato del nome file seguente:

```
<AssemblyName>.dll-help.xml
```

Il formato di nome di assembly è obbligatorio anche quando l'assembly è un modulo annidato.

Ad esempio, il provider Certificate è definito nell'assembly Microsoft.PowerShell.Security.dll. Il `Get-Help` cmdlet Cerca un argomento della Guida per il provider Certificate solo nel file Microsoft.PowerShell.Security.dll help.xml nella directory del modulo.

## <a name="function-help-files"></a>File della Guida (funzione)

Funzioni possono essere documentate con [della Guida basata sui commenti](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentati nel file XML della Guida. Quando la funzione è documentata in un file XML, la funzione deve avere un `.ExternalHelp` commento (parola chiave) che associa la funzione con il file XML. In caso contrario, il `Get-Help` cmdlet non è possibile trovare il file della Guida.
Funzioni possono essere documentate con [della Guida basata sui commenti](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentati nel file XML della Guida. Quando la funzione è documentata in un file XML, la funzione deve avere un `.ExternalHelp` commento (parola chiave) che associa la funzione con il file XML. In caso contrario, il `Get-Help` cmdlet non è possibile trovare il file della Guida.

Non sono previsti requisiti tecnici per il nome di un file della Guida funzione. Tuttavia, una procedura consigliata è assegnare un nome file della Guida per il modulo di script in cui la funzione è definita. Ad esempio, la funzione seguente è definita nel file MyModule.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>File della Guida comandi CIM

Il file della Guida per un comando CIM deve essere denominato per il file CDXML in cui è definito il comando CIM. Usare il formato del nome file seguente:

```
<FileName>.cdxml-help.xml
```

I comandi CIM sono definiti nel file CDXML che possono essere inclusi nei moduli come i moduli annidati. Quando il comando CIM viene importato nella sessione come una funzione, Windows PowerShell aggiunge un `.ExternalHelp` commento file di una parola chiave per la definizione di funzione che associa la funzione con un supporto XML è denominato per il file CDXML in cui è definito il comando CIM.

## <a name="script-workflow-help-files"></a>File della Guida del flusso di lavoro di script

I flussi di lavoro di script che sono inclusi nei moduli possono essere documentati nel file della Guida basati su XML. Non sono previsti requisiti tecnici per il nome del file della Guida. Tuttavia, una procedura consigliata è assegnare un nome file della Guida per il modulo di script in cui è definito il flusso di lavoro di script. Ad esempio:

```
<ScriptModule>.psm1-help.xml
```

A differenza di altri comandi script, i flussi di lavoro di script non richiedono un `.ExternalHelp` commento parola chiave per associarle a un file della Guida. Ma Windows PowerShell esegue la ricerca nelle sottodirectory specifiche di impostazioni cultura dell'interfaccia utente della directory del modulo per i file della Guida basati su XML e cerca la Guida per il flusso di lavoro di script in tutti i file. `.ExternalHelp` parola chiave di commento vengono ignorati.

Poiché il `.ExternalHelp` parola chiave di commento viene ignorato, il `Get-Help` cmdlet potranno richiedere assistenza per i flussi di lavoro di script solo quando vengono inclusi nei moduli.