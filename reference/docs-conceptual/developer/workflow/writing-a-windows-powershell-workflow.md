---
title: Scrittura di un flusso di lavoro di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366010"
---
# <a name="writing-a-windows-powershell-workflow"></a>Come scrivere un flusso di lavoro di Windows PowerShell

È possibile creare un flusso di lavoro XAML aggiungendo le attività esposte dagli assembly di Windows PowerShell a Progettazione flussi di lavoro in Visual Studio. Gli assembly di Windows PowerShell seguenti espongono le attività abilitate per il flusso di lavoro.

> [!IMPORTANT]
> Un flusso di lavoro XAML deve essere incluso nel pacchetto come modulo se si desidera fornire la guida per il flusso di lavoro. Per informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft. PowerShell. Core. Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft. PowerShell. Diagnostics. Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft. PowerShell. Security. Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft. PowerShell. Utility. Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  Negli argomenti seguenti viene descritto come creare un flusso di lavoro utilizzando le attività di Windows PowerShell.

- [Aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Creazione di un flusso di lavoro con le attività di Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)

- [Creazione di un flusso di lavoro tramite uno script di Windows PowerShell](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importazione e richiamo di un flusso di lavoro di Windows PowerShell](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Creazione di un'attività del flusso di lavoro da un cmdlet di Windows PowerShell](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)