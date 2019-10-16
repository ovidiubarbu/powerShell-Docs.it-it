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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365880"
---
# <a name="cmdlet-samples"></a>Esempi di cmdlet

Questa sezione descrive il codice di esempio fornito in Windows PowerShell 2,0 SDK. È possibile copiare il codice dagli argomenti in questa sezione o aprire i file di origine installati con l'SDK. Il [Software Development Kit (SDK) di Windows PowerShell 2,0](https://www.microsoft.com/en-us/download/details.aspx?id=2560) fornisce i file Leggimi, i file di origine e i file di progetto di Visual Studio per ogni esempio. Con l'SDK installato, è possibile trovare gli esempi nella cartella `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

## <a name="in-this-section"></a>Contenuto della sezione

[Esempio GetProcessSample01](./getprocesssample01-sample.md) In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale.

[Esempio GetProcessSample02](./getprocesssample02-sample.md) In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Fornisce un parametro del nome che può essere usato per specificare i processi da recuperare.

[Esempio GetProcessSample03](./getprocesssample03-sample.md) In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Fornisce un parametro Name che può accettare un oggetto dalla pipeline o un valore di una proprietà di un oggetto il cui nome di proprietà corrisponde al nome del parametro.

[Esempio GetProcessSample04](./getprocesssample04-sample.md) In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Genera un errore non fatale se si verifica un errore durante il recupero di un processo.

[Esempio GetProcessSample05](./getprocesssample05-sample.md) Questo esempio mostra una versione completa del cmdlet Get-proc.

[Esempio StopProcessSample01](./stopprocesssample01-sample.md) In questo esempio viene illustrato come scrivere un cmdlet che richiede feedback da parte dell'utente prima di tentare di arrestare un processo e come implementare un parametro `PassThru` che indica che l'utente desidera che il cmdlet restituisca un oggetto.

[Esempio StopProcessSample02](./stopprocesssample02-sample.md) In questo esempio viene illustrato come scrivere un cmdlet che scrive messaggi di debug, dettagliati e di avviso durante l'arresto dei processi nel computer locale.

[Esempio StopProcessSample03](./stopprocesssample03-sample.md) In questo esempio viene illustrato come scrivere un cmdlet i cui parametri hanno alias e che supportano caratteri jolly.

[Esempio StopProcessSample04](./stopprocesssample04-sample.md) In questo esempio viene illustrato come scrivere un cmdlet che dichiara set di parametri, specifica il set di parametri predefinito e può accettare un oggetto di input.

[Esempio Events01](./events01-sample.md) In questo esempio viene illustrato come creare un cmdlet che consente all'utente di eseguire la registrazione per gli eventi generati da [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Con questo cmdlet, ad esempio, gli utenti possono registrare un'azione da eseguire quando viene creato un file in una directory specifica. Questo esempio deriva dalla classe di base [Microsoft. PowerShell. Commands. Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
