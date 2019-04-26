---
title: Esempi di PowerShell, API di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082584"
---
# <a name="windows-powershell-api-samples"></a>Esempi di API di Windows PowerShell

In questa sezione include il codice di esempio che illustra come creare spazi di esecuzione che limitano l'utilizzo di funzionalità e come eseguire in modo asincrono i comandi utilizzando un pool di spazi di esecuzione per specificare gli spazi di esecuzione. È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti di questa sezione nell'applicazione host.

## <a name="in-this-section"></a>Contenuto della sezione

[Esempio PowerShell01](./windows-powershell01-sample.md) in questo esempio viene illustrato come utilizzare un' [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto per limitare le funzionalità di uno spazio di esecuzione. L'output di questo esempio viene illustrato come limitare la modalità del linguaggio dello spazio di esecuzione, come contrassegnare un cmdlet come privato, come aggiungere e remove cmdlet e provider, come aggiungere un comando proxy e altro ancora.

[Esempio PowerShell02](./windows-powershell02-sample.md) questo esempio viene illustrato come eseguire i comandi in modo asincrono utilizzando gli spazi di esecuzione di un pool di spazi di esecuzione. L'esempio genera un elenco di comandi e quindi esegue i comandi, mentre il motore di Windows PowerShell apre uno spazio di esecuzione dal pool quando è necessaria.