---
title: Richiamare i cmdlet e script all'interno di un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855187"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Richiamo di cmdlet e script all'interno di un cmdlet

Un cmdlet può richiamare altri cmdlet e script da entro il metodo del cmdlet di elaborazione dell'input. In questo modo è possibile aggiungere la funzionalità di script e i cmdlet esistenti per il cmdlet senza dover riscrivere il codice.

## <a name="the-invoke-method"></a>Il metodo Invoke

Tutti i cmdlet possono richiamare un cmdlet esistente chiamando il [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metodo all'interno di un metodo di elaborazione, ad esempio dell'input [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), che viene viene sottoposto a override dal cmdlet. Tuttavia, è possibile richiamare solo i cmdlet che derivano direttamente dai [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Non è possibile richiamare un cmdlet da cui deriva il [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

Il [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metodo presenta le seguenti varianti.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto di cmdlet e restituisce una raccolta di oggetti di tipo "T".

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto di cmdlet e restituisce un emumerator fortemente tipizzato. Questa variante consente all'utente di usare gli oggetti nella raccolta per eseguire operazioni personalizzate.

## <a name="examples"></a>Esempi

|Esempio|Description|
|-------------|-----------------|
|[Richiamare i cmdlet all'interno di un Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|In questo esempio viene illustrato come richiamare un cmdlet all'interno di un altro cmdlet.|
|[Richiamo degli script all'interno di un Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|In questo esempio viene illustrato come richiamare uno script che viene fornito per il cmdlet impedisce all'interno di un altro cmdlet.|

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
