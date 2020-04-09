---
title: Esempio di Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978645"
---
# <a name="windows-powershell02-sample"></a>Esempio di Windows PowerShell02

Questo esempio illustra come eseguire i comandi in modo asincrono usando il Runspaces di un pool di spazio. L'esempio genera un elenco di comandi, quindi esegue i comandi mentre il motore di Windows PowerShell apre un spazio dal pool quando necessario.

## <a name="requirements"></a>Requisiti

- Questo esempio richiede Windows PowerShell 2,0.

## <a name="demonstrates"></a>Dimostra

In questo esempio viene illustrato quanto segue:

- Creazione di un oggetto RunspacePool con un numero minimo e massimo di Runspaces consentiti per l'apertura nello stesso momento.
- Creazione di un elenco di comandi.
- Esecuzione dei comandi in modo asincrono.
- Chiamata del metodo [System. Management. Automation. Runspaces. Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) per verificare il numero di Runspaces disponibili.
- Acquisizione dell'output del comando con il metodo [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

## <a name="example"></a>Esempio

Questo esempio illustra come aprire il Runspaces di un pool spazio e come eseguire i comandi in modo asincrono in tali Runspaces.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a>Vedere anche

[Scrittura di un'applicazione host di Windows PowerShell](./writing-a-windows-powershell-host-application.md)
