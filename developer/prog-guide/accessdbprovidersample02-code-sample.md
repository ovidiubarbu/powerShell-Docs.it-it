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
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795488"
---
# <a name="accessdbprovidersample02-code-sample"></a>Codice di esempio di AccessDbProviderSample02

Il codice seguente viene illustrata l'implementazione del provider di Windows PowerShell descritto nella [creazione di un Provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md). Questa implementazione viene creato un percorso, stabilisce una connessione a un database di Access e quindi rimuove l'unità.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider02.cs) per questo provider tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.
>
> Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Esempio di codice

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)