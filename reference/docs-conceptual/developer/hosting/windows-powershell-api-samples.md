---
title: Esempi di API di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360840"
---
# <a name="windows-powershell-api-samples"></a>Esempi di API di Windows PowerShell

Questa sezione include codice di esempio che illustra come creare Runspaces che limitano le funzionalità e come eseguire i comandi in modo asincrono usando un pool spazio per fornire Runspaces. È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti in questa sezione nell'applicazione host.

## <a name="in-this-section"></a>Contenuto della sezione

[Esempio PowerShell01](./windows-powershell01-sample.md) Questo esempio illustra come usare un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) per limitare la funzionalità di un spazio. Nell'output di questo esempio viene illustrato come limitare la modalità del linguaggio di spazio, come contrassegnare un cmdlet come privato, come aggiungere e rimuovere cmdlet e provider, come aggiungere un comando proxy e altro ancora.

[Esempio PowerShell02](./windows-powershell02-sample.md) Questo esempio illustra come eseguire i comandi in modo asincrono usando il Runspaces di un pool di spazio. L'esempio genera un elenco di comandi, quindi esegue i comandi mentre il motore di Windows PowerShell apre un spazio dal pool quando necessario.