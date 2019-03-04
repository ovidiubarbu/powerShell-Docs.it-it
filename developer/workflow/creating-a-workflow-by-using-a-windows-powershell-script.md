---
title: Creazione di un flusso di lavoro usando uno Script di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853047"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Creazione di un flusso di lavoro usando uno script di Windows PowerShell

È possibile creare un flusso di lavoro scrivendo uno script di Windows PowerShell. Per creare un flusso di lavoro, usare la parola chiave del flusso di lavoro seguita da un nome per il flusso di lavoro prima del corpo dello script. Ad esempio:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Si trova il flusso di lavoro nello stesso modo che si trattasse di qualsiasi altro comando Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implementazione di Parallel e Sequence

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supporta l'esecuzione di attività in parallelo. Per implementare questa funzionalità in uno script di Windows PowerShell, usare il `parallel` (parola chiave) davanti a un blocco di script. È anche possibile usare il `foreach -parallel` costruzione per scorrere una raccolta di oggetti in parallelo. Per eseguire un gruppo di attività in ordine sequenziale in un blocco parallel, racchiudere il gruppo di attività in un blocco di script e prima del blocco con la parola chiave di sequenza.

## <a name="joining-computers-to-a-domain"></a>Aggiunta di computer a un dominio

Lo script seguente crea un flusso di lavoro che controlla lo stato del dominio di un gruppo di computer specificato dall'utente, li aggiunge a un dominio se non sono già unite in join e quindi controlla di nuovo lo stato. Si tratta di una versione dello script del flusso di lavoro XAML illustrato nella [creazione di un flusso di lavoro con attività di Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```