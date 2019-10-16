---
title: Richiamo di cmdlet e script all'interno di un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364290"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Richiamo di cmdlet e script all'interno di un cmdlet

Un cmdlet può richiamare altri cmdlet e script dall'interno del metodo di elaborazione dell'input del cmdlet. In questo modo è possibile aggiungere al cmdlet la funzionalità di cmdlet e script esistenti senza dover riscrivere il codice.

## <a name="the-invoke-method"></a>Metodo Invoke

Tutti i cmdlet possono richiamare un cmdlet esistente chiamando il metodo [System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) dall'interno di un metodo di elaborazione dell'input, ad esempio [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), sottoposto a override da cmdlet. Tuttavia, è possibile richiamare solo i cmdlet che derivano direttamente dalla classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Non è possibile richiamare un cmdlet che deriva dalla classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

Il metodo [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) presenta le varianti seguenti.

[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto cmdlet e restituisce una raccolta di oggetti di tipo "T".

[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto cmdlet e restituisce un emumerator fortemente tipizzato. Questa variante consente all'utente di usare gli oggetti nella raccolta per eseguire operazioni personalizzate.

## <a name="examples"></a>Esempi

|Esempio|Description|
|-------------|-----------------|
|[Richiamo di cmdlet all'interno di un cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|In questo esempio viene illustrato come richiamare un cmdlet da un altro cmdlet.|
|[Richiamo di script all'interno di un cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|In questo esempio viene illustrato come richiamare uno script fornito al cmdlet da un altro cmdlet.|

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
