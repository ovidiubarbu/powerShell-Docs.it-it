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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Come richiamare gli script all'interno di un cmdlet

In questo esempio viene illustrato come richiamare uno script che viene fornito a un cmdlet. Lo script viene eseguito dal cmdlet e i relativi risultati vengono restituiti al cmdlet come una raccolta di [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) oggetti.

## <a name="to-invoke-a-script-block"></a>Per richiamare un blocco di script

1. Il comando verifica che sia stato specificato un blocco di script al cmdlet. Se è stato fornito un blocco di script, il comando richiama il blocco di script con i relativi parametri necessari.

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

2. Quindi, lo script esegue l'iterazione attraverso la raccolta restituita di [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) oggetti ed eseguire le operazioni necessarie.

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

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
