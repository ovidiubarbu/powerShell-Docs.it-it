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
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055785"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="e6cf5-102">Come richiamare gli script all'interno di un cmdlet</span><span class="sxs-lookup"><span data-stu-id="e6cf5-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="e6cf5-103">In questo esempio viene illustrato come richiamare uno script che viene fornito a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="e6cf5-104">Lo script viene eseguito dal cmdlet e i relativi risultati vengono restituiti al cmdlet come una raccolta di [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) oggetti.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="e6cf5-105">Per richiamare un blocco di script</span><span class="sxs-lookup"><span data-stu-id="e6cf5-105">To invoke a script block</span></span>

1. <span data-ttu-id="e6cf5-106">Il comando verifica che sia stato specificato un blocco di script al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="e6cf5-107">Se è stato fornito un blocco di script, il comando richiama il blocco di script con i relativi parametri necessari.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="e6cf5-108">Quindi, lo script esegue l'iterazione attraverso la raccolta restituita di [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) oggetti ed eseguire le operazioni necessarie.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e6cf5-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e6cf5-109">See Also</span></span>

[<span data-ttu-id="e6cf5-110">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6cf5-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
