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
ms.openlocfilehash: 22cfbc63bd369ebcb2fd8a0d0e8d1995941bbb0f
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417996"
---
# <a name="accessdbprovidersample01-code-sample"></a>Codice di esempio di AccessDbProviderSample01

Il codice seguente illustra l'implementazione del provider di Windows PowerShell descritto in [creazione di un provider di base di Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). Questa implementazione fornisce metodi per l'avvio e l'arresto del provider e anche se non fornisce un mezzo per accedere a un archivio dati o per ottenere o impostare i dati nell'archivio dati, fornisce le funzionalità di base richieste da tutti i provider.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider01.cs) per questo provider utilizzando Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .
>
> Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
