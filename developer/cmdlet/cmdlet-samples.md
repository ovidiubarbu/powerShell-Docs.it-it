---
title: Esempi di cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058046"
---
# <a name="cmdlet-samples"></a>Esempi di cmdlet

In questa sezione viene descritto il codice di esempio fornito in Windows PowerShell 2.0 SDK. È possibile copiare codice da negli argomenti di questa sezione o aprire i file di origine installati con il SDK. Il [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) fornisce i file Leggimi, i file di origine e file di progetto di Visual Studio per ogni esempio. Con il SDK installato, è possibile trovare gli esempi nel `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` cartella.

## <a name="in-this-section"></a>Contenuto della sezione

[Esempio GetProcessSample01](./getprocesssample01-sample.md) in questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale.

[Esempio GetProcessSample02](./getprocesssample02-sample.md) in questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Fornisce un parametro di nome che può essere utilizzato per specificare i processi da recuperare.

[Esempio GetProcessSample03](./getprocesssample03-sample.md) in questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Fornisce un parametro del nome che può accettare un oggetto dalla pipeline o un valore da una proprietà di un oggetto il cui nome di proprietà è identico al nome del parametro.

[Esempio GetProcessSample04](./getprocesssample04-sample.md) in questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Se si verifica un errore durante il recupero di un processo, viene generato un errore non fatali.

[Esempio GetProcessSample05](./getprocesssample05-sample.md) in questo esempio viene illustrata una versione completa del cmdlet Get-Process.

[Esempio StopProcessSample01](./stopprocesssample01-sample.md) in questo esempio viene illustrato come scrivere un cmdlet che richiede il feedback all'utente prima di tentare di arrestare un processo e come implementare un `PassThru` parametro che indica che l'utente vuole che il cmdlet per restituire un oggetto.

[Esempio StopProcessSample02](./stopprocesssample02-sample.md) in questo esempio viene illustrato come scrivere un cmdlet che scrive messaggi di avviso e di debug, verbose, durante l'arresto dei processi nel computer locale.

[Esempio StopProcessSample03](./stopprocesssample03-sample.md) in questo esempio viene illustrato come scrivere un cmdlet i cui parametri sono gli alias e che supportano i caratteri jolly.

[Esempio StopProcessSample04](./stopprocesssample04-sample.md) questo esempio viene illustrato come scrivere un cmdlet che dichiara i set di parametri, specifica il parametro predefinito impostato e può accettare un oggetto di input.

[Esempio Events01](./events01-sample.md) in questo esempio viene illustrato come creare un cmdlet che consente all'utente di registrare gli eventi generati da [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Con questo cmdlet gli utenti possono, ad esempio, registrare un'azione da eseguire quando viene creato un file in una directory specifica. In questo esempio deriva dal [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe di base.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
