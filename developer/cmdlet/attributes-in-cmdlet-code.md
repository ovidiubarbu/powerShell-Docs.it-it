---
title: Gli attributi nel codice del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853787"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="7e9bf-102">Attributi nel codice dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e9bf-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="7e9bf-103">Per usare la funzionalità comune fornita da Windows PowerShell, le classi e proprietà pubbliche definite nel codice cmdlet sono decorate con attributi.</span><span class="sxs-lookup"><span data-stu-id="7e9bf-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="7e9bf-104">Ad esempio, la definizione di classe seguente usa l'attributo Cmdlet per identificare la classe di Microsoft .NET Framework in cui il **Get-Proc** cmdlet viene implementato.</span><span class="sxs-lookup"><span data-stu-id="7e9bf-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="7e9bf-105">(Questo cmdlet viene usato come esempio in questo documento ed è simile al `Get-Process` cmdlet forniti da Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="7e9bf-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="7e9bf-106">Questi attributi vengono considerati i metadati perché l'implementazione è separata rispetto all'implementazione del codice di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7e9bf-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="7e9bf-107">Quando il runtime di Windows PowerShell viene eseguito il cmdlet, riconosce gli attributi e quindi esegue l'azione appropriata per ogni attributo.</span><span class="sxs-lookup"><span data-stu-id="7e9bf-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="7e9bf-108">Anche se è possibile implementare la propria versione delle funzionalità fornite da questi attributi, una progettazione ottimale cmdlet Usa queste funzionalità comuni.</span><span class="sxs-lookup"><span data-stu-id="7e9bf-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="7e9bf-109">Per altre informazioni sugli attributi diversi che possono essere dichiarati in dei cmdlet, vedere [tipi di attributo](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="7e9bf-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e9bf-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7e9bf-110">See Also</span></span>

[<span data-ttu-id="7e9bf-111">Tipi di attributo</span><span class="sxs-lookup"><span data-stu-id="7e9bf-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="7e9bf-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e9bf-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
