---
title: Informazioni di riferimento di Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: dfda6cb68b089a30a156760345420ee80d1d3ae9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862107"
---
# <a name="windows-powershell-reference"></a>Guida di riferimento di Windows PowerShell

Windows PowerShell è un ambiente di connesse a .NET Framework di Microsoft progettato per l'automazione dell'amministrazoine. Windows PowerShell fornisce un nuovo approccio alla creazione di comandi, composizione di soluzioni e la creazione di strumenti di gestione basato su interfaccia utente grafica.

Windows PowerShell consente agli amministratori di sistema automatizzare l'amministrazione delle risorse di sistema per l'esecuzione di comandi direttamente o tramite script.

## <a name="developer-audience"></a>Sviluppatori

Il Software Development Kit (SDK) di Windows PowerShell è destinato agli sviluppatori di comandi che richiedono informazioni di riferimento sulle API fornite da Windows PowerShell. Gli sviluppatori di comando usano Windows PowerShell per creare i comandi e i provider che estendono le attività che possono essere eseguite da Windows PowerShell.

## <a name="windows-powershell-resources"></a>Risorse di Windows PowerShell

Oltre a SDK di Windows PowerShell, le risorse seguenti forniscono altre informazioni.

[Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) fornisce un'introduzione a Windows PowerShell: la lingua, i cmdlet, i provider e l'uso di oggetti.

[Scrittura di un modulo di Windows PowerShell](./module/writing-a-windows-powershell-module.md) fornisce informazioni ed esempi per gli amministratori, sviluppatori di script e gli sviluppatori di cmdlet che hanno bisogno per creare un pacchetto e distribuire le proprie soluzioni di Windows PowerShell usando i moduli di Windows PowerShell.

[Scrittura di un Cmdlet di Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) fornisce informazioni ed esempi di codice per i responsabili del programma che intendono progettare i cmdlet e per gli sviluppatori che intendono implementare codice del cmdlet.

[Blog del Team di Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) la risorsa ottimale per ottenere informazioni e collaborare con altri utenti di Windows PowerShell. Leggi il blog del Team di Windows PowerShell e quindi aggiungere i Forum di utenti di Windows PowerShell (in lingua inglese). Usare Windows Live Search per trovare altri blog su Windows PowerShell e le risorse. Quindi, quando si sviluppano le tue competenze, liberamente Esponi le tue idee.

[Browser moduli PowerShell](/powershell/module/) fornisce le versioni più recenti degli argomenti della Guida della riga di comando.

## <a name="class-libraries"></a>Librerie di classi

[Automation](/dotnet/api/System.Management.Automation) questo spazio dei nomi è lo spazio dei nomi radice per Windows PowerShell. Contiene le classi, enumerazioni e le interfacce necessarie per implementare cmdlet personalizzati. In particolare, il [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe è la classe base da cui tutti i cmdlet devono essere derivate le classi. Per altre informazioni sui cmdlet, vedere.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) questo spazio dei nomi contiene le classi, enumerazioni e le interfacce necessarie per implementare un provider di Windows PowerShell. In particolare, il [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe è la classe base da cui tutti di Windows PowerShell devono essere derivate le classi di provider.

[Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) questo spazio dei nomi contiene le classi per i cmdlet e i provider implementati da Windows PowerShell. Analogamente, è consigliabile creare un *YourName*. I comandi dello spazio dei nomi per i cmdlet implementati dallo sviluppatore.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) questo spazio dei nomi contiene le classi, enumerazioni e le interfacce che il cmdlet viene utilizzato per definire l'interazione tra il nome utente e Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) questo spazio dei nomi contiene le classi di base utilizzate da altre classi dello spazio dei nomi. Ad esempio, il [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) classe è la classe base per il [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) questo spazio dei nomi contiene le classi, enumerazioni e le interfacce utilizzate per creare uno spazio di esecuzione di Windows PowerShell. In questo contesto, lo spazio di esecuzione di Windows PowerShell è il contesto in cui una o più pipeline di Windows PowerShell richiamano i cmdlet. Vale a dire, i cmdlet funzionano all'interno del contesto di uno spazio di esecuzione di Windows PowerShell. Per altre informazioni aboutWindows spazi di esecuzione di PowerShell, vedere [spazi di esecuzione di Windows PowerShell](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
