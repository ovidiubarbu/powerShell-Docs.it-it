---
title: Attributi nel codice del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370000"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="5f2b0-102">Attributi nel codice dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f2b0-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="5f2b0-103">Per utilizzare la funzionalità comune fornita da Windows PowerShell, le classi e le proprietà pubbliche definite nel codice del cmdlet sono decorate con attributi.</span><span class="sxs-lookup"><span data-stu-id="5f2b0-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="5f2b0-104">La definizione di classe seguente, ad esempio, usa l'attributo cmdlet per identificare la classe Microsoft .NET Framework in cui viene implementato il cmdlet **Get-proc** .</span><span class="sxs-lookup"><span data-stu-id="5f2b0-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="5f2b0-105">Questo cmdlet viene usato come esempio in questo documento ed è simile al cmdlet `Get-Process` fornito da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f2b0-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="5f2b0-106">Questi attributi sono considerati metadati perché la loro implementazione è separata dall'implementazione del codice del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f2b0-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="5f2b0-107">Quando il runtime di Windows PowerShell esegue il cmdlet, riconosce gli attributi e quindi esegue l'azione appropriata per ogni attributo.</span><span class="sxs-lookup"><span data-stu-id="5f2b0-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="5f2b0-108">Sebbene sia necessario implementare una versione personalizzata della funzionalità fornita da questi attributi, una progettazione di cmdlet efficace utilizza queste funzionalità comuni.</span><span class="sxs-lookup"><span data-stu-id="5f2b0-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="5f2b0-109">Per ulteriori informazioni sui diversi attributi che possono essere dichiarati nei cmdlet, vedere [tipi](./attribute-types.md)di attributi.</span><span class="sxs-lookup"><span data-stu-id="5f2b0-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f2b0-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5f2b0-110">See Also</span></span>

[<span data-ttu-id="5f2b0-111">Tipi di attributi</span><span class="sxs-lookup"><span data-stu-id="5f2b0-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="5f2b0-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f2b0-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
