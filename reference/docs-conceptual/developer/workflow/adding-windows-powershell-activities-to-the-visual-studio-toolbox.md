---
title: Aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359650"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Aggiunta di attività di Windows PowerShell nella casella degli strumenti di Visual Studio

Prima di creare un flusso di lavoro di PowerShell usando Progettazione flussi di lavoro, è necessario innanzitutto aggiungere le attività di PowerShell alla casella degli strumenti in un progetto di applicazione console del flusso di lavoro di Visual Studio. La procedura seguente illustra come aggiungere le attività dall'assembly Microsoft. PowerShell. Core. Activities alla casella degli strumenti di Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Aggiunta di attività di Windows PowerShell alla casella degli strumenti

1. Creare un nuovo progetto di applicazione console del flusso di lavoro in Visual Studio.

2. Scegliere **Casella degli strumenti** dal menu **Visualizza**.

3. Aggiungere una nuova scheda nella casella degli strumenti facendo clic con il pulsante destro del mouse all'interno della casella degli strumenti e scegliendo **Aggiungi scheda**e assegnare un nome alla nuova scheda come "attività di PowerShell".

   L'aggiunta di una scheda consente di raggruppare le attività di PowerShell separate da altri strumenti nella casella degli strumenti.

4. Nella scheda nuovo casella degli strumenti fare clic su **Scegli elementi.** Verrà visualizzata la finestra di dialogo **Scegli elementi casella degli strumenti** .

5. Nella finestra di dialogo **Scegli elementi della casella degli strumenti** fare clic sulla scheda **System. Activities** .

6. Fai clic su **Browse**.

7. Passare alla cartella%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e e fare doppio clic su Microsoft. PowerShell. Core. Activities. dll.

8. Fare clic su **OK**. Le attività definite dall'assembly Microsoft. PowerShell. Core. Activities sono ora disponibili nella casella degli strumenti.

## <a name="see-also"></a>Vedere anche

[Come scrivere un flusso di lavoro di Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Creazione di un flusso di lavoro con le attività di Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)