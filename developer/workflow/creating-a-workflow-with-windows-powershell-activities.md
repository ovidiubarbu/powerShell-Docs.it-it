---
title: Creazione di un flusso di lavoro con attività di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055428"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Creazione di un flusso di lavoro con le attività di Windows PowerShell

È possibile creare un flusso di lavoro di Windows PowerShell selezionando le attività dalla casella degli strumenti di Visual Studio e trascinarli nella finestra di progettazione del flusso di lavoro. Per informazioni sull'aggiunta di attività di Windows PowerShell per Visual Studio Toolbox, vedere [aggiunta di attività di Windows PowerShell per Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Le procedure seguenti descrivono come creare un flusso di lavoro che controlla lo stato del dominio di un gruppo di computer specificato dall'utente, li aggiunge a un dominio se non sono già unite in join e quindi controlla di nuovo lo stato.

### <a name="setting-up-the-project"></a>Impostazione del progetto

1. Seguire la procedura descritta in [aggiunta di attività di Windows PowerShell per Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) per creare un progetto di flusso di lavoro e aggiungere le attività dalle [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) e[ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) gli assembly nella casella degli strumenti.

2. Aggiungere Automation, Microsoft.PowerShell.Activities, System. Management, Microsoft.PowerShell.Management.Activities e Microsoft.PowerShell.Commands.Management per quanto riguarda il progetto come assembly di riferimento.

### <a name="adding-activities-to-the-workflow"></a>Aggiunta di attività al flusso di lavoro

1. Aggiungere un **sequenza** attività al flusso di lavoro.

2. Creare un argomento denominato `ComputerName` con un argomento di tipo `String[]`. Questo argomento rappresenta i nomi dei computer per controllare e creare un join.

3. Creare un argomento denominato `DomainCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Questo argomento rappresenta le credenziali di dominio di un account di dominio che è autorizzato ad aggiungere un computer al dominio.

4. Creare un argomento denominato `MachineCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Questo argomento rappresenta le credenziali di amministratore sui computer per controllare e creare un join.

5. Aggiungere un **ParallelForEach** attività all'interno di **sequenza** attività. Immettere `comp` e `ComputerName` nelle caselle di testo in modo che il ciclo scorre gli elementi del `ComputerName` matrice.

6. Aggiungere un **sequenza** il corpo dell'attività la **ParallelForEach** attività. Impostare il **DisplayName** proprietà della sequenza `JoinDomain`.

7. Aggiungere un **GetWmiObject** attività per il **JoinDomain** sequenza.

8. Modificare le proprietà del **GetWmiObject** attività come indicato di seguito.

   |Proprietà|Value|
   |--------------|-----------|
   |**Classe**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Aggiungere un **AddComputer** attività per il **JoinDomain** sequenza dopo il **GetWmiObject** attività.

10. Modificare le proprietà del **AddComputer** attività come indicato di seguito.

    |Proprietà|Value|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. Aggiungere un **RestartComputer** attività per il **JoinDomain** sequenza dopo il **AddComputer** attività.

12. Modificare le proprietà del **RestartComputer** attività come indicato di seguito.

    |Proprietà|Value|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**Credenziali**|MachineCred|
    |**per**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. Aggiungere un **GetWmiObject** attività per il **JoinDomain** sequenza dopo il **RestartComputer** attività. Modificare le proprietà per poter essere lo stesso come il precedente **GetWmiObject** attività.

    Dopo avere completato le procedure, la finestra di progettazione del flusso di lavoro dovrebbe essere simile al seguente.

    ![JoinDomain XAML nella finestra di progettazione del flusso di lavoro](../media/joindomainworkflow.png)
    ![JoinDomain XAML nella finestra di progettazione del flusso di lavoro](../media/joindomainworkflow.png "JoinDomainWorkflow")