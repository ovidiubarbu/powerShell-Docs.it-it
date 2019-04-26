---
title: Esempio PowerShell02 Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082516"
---
# <a name="windows-powershell02-sample"></a>Esempio di Windows PowerShell02

Questo esempio viene illustrato come eseguire i comandi in modo asincrono utilizzando gli spazi di esecuzione di un pool di spazi di esecuzione. L'esempio genera un elenco di comandi e quindi esegue i comandi, mentre il motore di Windows PowerShell apre uno spazio di esecuzione dal pool quando è necessaria.

## <a name="requirements"></a>Requisiti

- Questo esempio richiede Windows PowerShell 2.0.

## <a name="demonstrates"></a>Di seguito viene illustrato

In questo esempio viene illustrato quanto segue:

- Creazione di un oggetto RunspacePool con un numero minimo e massimo di spazi di esecuzione possono essere aperte contemporaneamente.

- Creazione di un elenco dei comandi.

- Eseguire i comandi in modo asincrono.

- Chiama il [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) metodo per visualizzare il numero di spazi di esecuzione sono gratuiti.

- Acquisire l'output del comando con il [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (metodo).

## <a name="example"></a>Esempio

In questo esempio illustra come aprire gli spazi di esecuzione di un pool di spazi di esecuzione e come eseguire in modo asincrono i comandi in questi spazi di esecuzione.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Vedere anche

[Scrittura di un'applicazione Host di PowerShell di Windows](./writing-a-windows-powershell-host-application.md)