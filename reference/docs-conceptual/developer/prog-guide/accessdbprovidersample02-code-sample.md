---
title: Esempio di codice AccessDbProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 33cdebd7f2f5ae21ec7aff559382362025d12e47
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416257"
---
# <a name="accessdbprovidersample02-code-sample"></a>Codice di esempio di AccessDbProviderSample02

Il codice seguente illustra l'implementazione del provider di Windows PowerShell descritto in [creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md). Questa implementazione crea un percorso, effettua una connessione a un database di Access e quindi rimuove l'unità.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider02.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .
>
> Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
