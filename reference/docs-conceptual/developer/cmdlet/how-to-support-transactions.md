---
title: Come supportare le transazioni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365540"
---
# <a name="how-to-support-transactions"></a>Come supportare le transazioni

Questo esempio Mostra gli elementi di codice di base che aggiungono il supporto per le transazioni a un cmdlet.

> [!IMPORTANT]
> Per ulteriori informazioni sul modo in cui Windows PowerShell gestisce le transazioni, vedere [informazioni sulle transazioni][about_Transactions].

## <a name="to-support-transactions"></a>Per supportare le transazioni

1. Quando si dichiara l'attributo del cmdlet, specificare che il cmdlet supporta le transazioni.
   Quando il cmdlet supporta le transazioni, Windows PowerShell aggiunge il parametro `UseTransaction` al cmdlet quando viene eseguito.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. All'interno di uno dei metodi di elaborazione dell'input, aggiungere un blocco `if` per determinare se una transazione è disponibile.
   Se l'istruzione `if` viene risolta in `true`, le azioni all'interno di questa istruzione possono essere eseguite nel contesto della transazione corrente.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
