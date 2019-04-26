---
title: Esempio di codice AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081989"
---
# <a name="accessdbprovidersample01-code-sample"></a>Codice di esempio di AccessDbProviderSample01

Il codice seguente viene illustrata l'implementazione del provider di Windows PowerShell descritto nella [creazione di un PowerShell Provider di Windows base](./creating-a-basic-windows-powershell-provider.md). Questa implementazione fornisce metodi per avviare e arrestare il provider, e sebbene non fornisce un mezzo per accedere a un archivio dati o per ottenere o impostare i dati nell'archivio dati, è fornire la funzionalità di base necessarie per tutti i provider.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider01.cs) per il provider utilizzando il Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.
>
> Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)