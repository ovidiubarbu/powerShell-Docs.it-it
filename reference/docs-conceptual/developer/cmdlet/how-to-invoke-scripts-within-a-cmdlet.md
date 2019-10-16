---
title: Come richiamare gli script all'interno di un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364410"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Come richiamare gli script all'interno di un cmdlet

In questo esempio viene illustrato come richiamare uno script fornito a un cmdlet. Lo script viene eseguito dal cmdlet e i risultati vengono restituiti al cmdlet come raccolta di oggetti [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .

## <a name="to-invoke-a-script-block"></a>Per richiamare un blocco di script

1. Il comando verifica che sia stato fornito un blocco di script al cmdlet. Se è stato fornito un blocco di script, il comando richiama il blocco di script con i parametri obbligatori.

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

2. Quindi, lo script scorre la raccolta restituita di oggetti [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) ed esegue le operazioni necessarie.

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
