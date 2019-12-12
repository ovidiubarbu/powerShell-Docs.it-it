---
title: Informazioni di riferimento su Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 48b2b2b9ab2a39cf185ed54bcfa99d46562e13b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366280"
---
# <a name="windows-powershell-reference"></a>Guida di riferimento di Windows PowerShell

Windows PowerShell è un ambiente Microsoft .NET connesso al Framework progettato per l'automazione amministrativa. Windows PowerShell offre un nuovo approccio alla creazione di comandi, alla composizione di soluzioni e alla creazione di strumenti di gestione grafici basati sull'interfaccia utente.

Windows PowerShell consente a un amministratore di sistema di automatizzare l'amministrazione delle risorse di sistema mediante l'esecuzione di comandi direttamente o tramite script.

## <a name="developer-audience"></a>Sviluppatori

Il Software Development Kit (SDK) di Windows PowerShell viene scritto per gli sviluppatori di comandi che richiedono informazioni di riferimento sulle API fornite da Windows PowerShell. Gli sviluppatori di comandi usano Windows PowerShell per creare sia i comandi che i provider che estendono le attività che possono essere eseguite da Windows PowerShell.

## <a name="windows-powershell-resources"></a>Risorse di Windows PowerShell

Oltre a Windows PowerShell SDK, le risorse seguenti forniscono altre informazioni.

[Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Viene fornita un'introduzione a Windows PowerShell: il linguaggio, i cmdlet, i provider e l'utilizzo di oggetti.

[Scrittura di un modulo di Windows PowerShell](./module/writing-a-windows-powershell-module.md) Fornisce informazioni ed esempi per gli amministratori, gli sviluppatori di script e gli sviluppatori di cmdlet che devono creare pacchetti e distribuire le soluzioni di Windows PowerShell usando i moduli di Windows PowerShell.

[Scrittura di un cmdlet di Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) Fornisce esempi di codice e informazioni per i responsabili del programma che progettano i cmdlet e per gli sviluppatori che implementano il codice del cmdlet.

[Blog del team di Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) La risorsa migliore per imparare e collaborare con altri utenti di Windows PowerShell. Leggere il Blog del team di Windows PowerShell e quindi aggiungere il forum degli utenti di Windows PowerShell (Microsoft. public. Windows. PowerShell). Utilizzare Windows Live Search per trovare altre risorse e Blog di Windows PowerShell. Quando si sviluppano le proprie competenze, è quindi possibile contribuire liberamente alle proprie idee.

[Browser modulo di PowerShell](/powershell/module/) Fornisce le versioni più recenti degli argomenti della guida della riga di comando.

## <a name="class-libraries"></a>Librerie di classi

[System. Management. Automation](/dotnet/api/System.Management.Automation) questo spazio dei nomi è lo spazio dei nomi radice per Windows PowerShell. Contiene le classi, le enumerazioni e le interfacce necessarie per implementare i cmdlet personalizzati. In particolare, la classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) è la classe di base dalla quale devono essere derivate tutte le classi di cmdlet. Per ulteriori informazioni sui cmdlet di, vedere.

[System. Management. Automation. provider](/dotnet/api/System.Management.Automation.Provider) questo spazio dei nomi contiene le classi, le enumerazioni e le interfacce necessarie per implementare un provider di Windows PowerShell. In particolare, la classe [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) è la classe di base dalla quale devono essere derivate tutte le classi del provider di Windows PowerShell.

[Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) questo spazio dei nomi contiene le classi per i cmdlet e i provider implementati da Windows PowerShell. Analogamente, si *consiglia di creare un oggetto*. Spazio dei nomi dei comandi per i cmdlet implementati.

[System. Management. Automation. host](/dotnet/api/System.Management.Automation.Host) questo spazio dei nomi contiene le classi, le enumerazioni e le interfacce utilizzate dal cmdlet per definire l'interazione tra l'utente e Windows PowerShell.

[System. Management. Automation. Internal](/dotnet/api/System.Management.Automation.Internal) questo spazio dei nomi contiene le classi di base utilizzate da altre classi dello spazio dei nomi. Ad esempio, la classe [System. Management. Automation. Internal. Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) è la classe base per la classe [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .

[System. Management. Automation. Runspaces](/dotnet/api/System.Management.Automation.Runspaces) questo spazio dei nomi contiene le classi, le enumerazioni e le interfacce usate per creare un spazio di Windows PowerShell. In questo contesto, spazio di Windows PowerShell è il contesto in cui una o più pipeline di Windows PowerShell richiamano i cmdlet. Ovvero i cmdlet funzionano nel contesto di un spazio di Windows PowerShell. Per altre informazioni su aboutWindows PowerShell Runspaces, vedere la pagina relativa a [Windows PowerShell Runspaces](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
