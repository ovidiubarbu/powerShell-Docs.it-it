---
title: Come richiamare gli script all'interno di un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855837"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="29077-102">Come richiamare gli script all'interno di un cmdlet</span><span class="sxs-lookup"><span data-stu-id="29077-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="29077-103">In questo esempio viene illustrato come richiamare uno script che viene fornito a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29077-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="29077-104">Lo script viene eseguito dal cmdlet e i relativi risultati vengono restituiti al cmdlet come una raccolta di [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) oggetti.</span><span class="sxs-lookup"><span data-stu-id="29077-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="29077-105">Per richiamare un blocco di script</span><span class="sxs-lookup"><span data-stu-id="29077-105">To invoke a script block</span></span>

1. <span data-ttu-id="29077-106">Il comando verifica che sia stato specificato un blocco di script al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29077-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="29077-107">Se è stato fornito un blocco di script, il comando richiama il blocco di script con i relativi parametri necessari.</span><span class="sxs-lookup"><span data-stu-id="29077-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="29077-108">Quindi, lo script esegue l'iterazione attraverso la raccolta restituita di [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) oggetti ed eseguire le operazioni necessarie.</span><span class="sxs-lookup"><span data-stu-id="29077-108">Then, the script iterates through the returned collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="29077-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="29077-109">See Also</span></span>

[<span data-ttu-id="29077-110">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="29077-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
