---
title: Aggiunta di Windows PowerShell attività alla casella degli strumenti di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863567"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Aggiunta di attività di Windows PowerShell nella casella degli strumenti di Visual Studio

Prima di creare un flusso di lavoro di PowerShell usando Progettazione flussi di lavoro, è innanzitutto necessario aggiungere le attività di PowerShell nella casella degli strumenti in un progetto di applicazione console flusso di lavoro di Visual Studio. La procedura seguente viene illustrato come aggiungere le attività dall'assembly Microsoft.PowerShell.Core.Activities alla casella degli strumenti di Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Aggiunta di attività di Windows PowerShell nella casella degli strumenti

1. Creare un nuovo progetto di applicazione console flusso di lavoro in Visual Studio.

2. Nel **View** menu, fare clic su **della casella degli strumenti**.

3. Aggiungere una nuova scheda della casella degli strumenti facendo clic all'interno della casella degli strumenti e scegliendo **Aggiungi scheda**e assegnare un nome, ad esempio "Attività di PowerShell" la nuova scheda.

   Aggiunta di una scheda consente di raggruppare le attività di PowerShell separata dagli altri strumenti della casella degli strumenti.

4. Nella nuova scheda della casella degli strumenti, fare clic su **Scegli elementi...** . Il **Scegli elementi della casella degli strumenti** viene visualizzata la finestra.

5. Nel **Scegli elementi della casella degli strumenti** finestra di dialogo, fare clic sui **System. Activities** scheda.

6. Fare clic su **esplorare**.

7. Passare alla cartella %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e e fare doppio clic su Microsoft.PowerShell.Core.Activities.dll.

8. Fare clic su **OK**. Le attività definite dall'assembly Microsoft.PowerShell.Core.Activities sono ora disponibili nella casella degli strumenti.

## <a name="see-also"></a>Vedere anche

[Come scrivere un flusso di lavoro di Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Creazione di un flusso di lavoro con attività di Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)