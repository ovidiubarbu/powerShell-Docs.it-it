---
title: Creazione di un flusso di lavoro tramite uno script di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5720200ce32f114cd4965d961b9e2804bd154b2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870847"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Creazione di un flusso di lavoro usando uno script di Windows PowerShell

È possibile creare un flusso di lavoro scrivendo uno script di Windows PowerShell. Per creare un flusso di lavoro, usare la parola chiave Workflow seguita da un nome per il flusso di lavoro prima del corpo dello script. Ad esempio:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Il flusso di lavoro viene trovato in modo analogo a qualsiasi altro comando di Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implementazione di Parallel e Sequence

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) supporta l'esecuzione di attività in parallelo. Per implementare questa funzionalità in uno script di Windows PowerShell, usare la parola chiave `parallel` davanti a un blocco di script. È anche possibile usare la costruzione `foreach -parallel` per scorrere una raccolta di oggetti in parallelo. Per eseguire un gruppo di attività in ordine sequenziale all'interno di un blocco parallelo, racchiudere il gruppo di attività in un blocco di script e precedere il blocco con la parola chiave Sequence.

## <a name="joining-computers-to-a-domain"></a>Aggiunta di computer a un dominio

Lo script seguente crea un flusso di lavoro che controlla lo stato del dominio di un gruppo di computer specificati dall'utente, li aggiunge a un dominio se non sono già stati aggiunti, quindi controlla di nuovo lo stato.
Si tratta di una versione script del flusso di lavoro XAML illustrata in [creazione di un flusso di lavoro con le attività di Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).

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