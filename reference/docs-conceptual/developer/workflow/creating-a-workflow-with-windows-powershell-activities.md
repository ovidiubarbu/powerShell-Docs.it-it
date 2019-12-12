---
title: Creazione di un flusso di lavoro con le attività di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359630"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Creazione di un flusso di lavoro con le attività di Windows PowerShell

È possibile creare un flusso di lavoro di Windows PowerShell selezionando attività dalla casella degli strumenti di Visual Studio e trascinandoli nella finestra Progettazione flussi di lavoro. Per informazioni sull'aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio, vedere [aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Nelle procedure riportate di seguito viene descritto come creare un flusso di lavoro che controlla lo stato del dominio di un gruppo di computer specificati dall'utente, li aggiunge a un dominio se non sono già stati aggiunti, quindi controlla di nuovo lo stato.

### <a name="setting-up-the-project"></a>Configurazione del progetto

1. Per creare un progetto flusso di lavoro e aggiungere le attività dagli assembly [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) e [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) alla casella degli strumenti, seguire la procedura descritta in [aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) .

2. Aggiungere System. Management. Automation, Microsoft. PowerShell. Activities, System. Management, Microsoft. PowerShell. Management. Activities e Microsoft. PowerShell. Commands. Management come al progetto come assembly di riferimento.

### <a name="adding-activities-to-the-workflow"></a>Aggiunta di attività al flusso di lavoro

1. Aggiungere un'attività **Sequence** al flusso di lavoro.

2. Creare un argomento denominato `ComputerName` con un tipo di argomento `String[]`. Questo argomento rappresenta i nomi dei computer da controllare e unire.

3. Creare un argomento denominato `DomainCred` di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Questo argomento rappresenta le credenziali di dominio di un account di dominio autorizzato per l'aggiunta di un computer al dominio.

4. Creare un argomento denominato `MachineCred` di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Questo argomento rappresenta le credenziali di un amministratore nei computer da controllare e unire.

5. Aggiungere un'attività **ActivityDesigner ParallelForEach** all'interno dell'attività **Sequence** . Immettere `comp` e `ComputerName` nelle caselle di testo in modo che il ciclo scorre gli elementi della matrice `ComputerName`.

6. Aggiungere un'attività **Sequence** al corpo dell'attività **ActivityDesigner ParallelForEach** . Impostare la proprietà **DisplayName** della sequenza su `JoinDomain`.

7. Aggiungere un'attività **GetWmiObject** alla sequenza **JoinDomain** .

8. Modificare le proprietà dell'attività **GetWmiObject** come indicato di seguito.

   |Proprietà|Value|
   |--------------|-----------|
   |**Classe**|"Win32_ComputerSystem"|
   |**PSComputerName**|comp|
   |**PSCredential**|MachineCred|

9. Aggiungere un'attività **AddComputer** alla sequenza **JoinDomain** dopo l'attività **GetWmiObject** .

10. Modificare le proprietà dell'attività **AddComputer** come indicato di seguito.

    |Proprietà|Value|
    |--------------|-----------|
    |**NomeComputer**|comp|
    |**DomainCredential**|DomainCred|

11. Aggiungere un'attività **RestartComputer** alla sequenza **JoinDomain** dopo l'attività **AddComputer** .

12. Modificare le proprietà dell'attività **RestartComputer** come indicato di seguito.

    |Proprietà|Value|
    |--------------|-----------|
    |**NomeComputer**|comp|
    |**Credenziali**|MachineCred|
    |**Per**|Microsoft. PowerShell. Commands. WaitForServiceTypes. PowerShell|
    |**Forzare**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. Aggiungere un'attività **GetWmiObject** alla sequenza **JoinDomain** dopo l'attività **RestartComputer** . Modificare le proprietà in modo che corrispondano a quelle dell'attività **GetWmiObject** precedente.

    Una volta completate le procedure, la finestra di progettazione del flusso di lavoro avrà un aspetto simile al seguente.

    ![XAML JoinDomain in Progettazione flussi di lavoro](../media/joindomainworkflow.png)
    ![XAML di JoinDomain in Progettazione flussi di lavoro](../media/joindomainworkflow.png "JoinDomainWorkflow")