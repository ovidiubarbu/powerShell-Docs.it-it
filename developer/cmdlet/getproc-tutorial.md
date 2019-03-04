---
title: Esercitazione GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862457"
---
# <a name="getproc-tutorial"></a>Esercitazione su GetProc

In questa sezione fornisce un'esercitazione per la creazione di un cmdlet Get-Process che è molto simile al [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet forniti da Windows PowerShell. Questa esercitazione offre frammenti di codice che illustrano come vengono implementati i cmdlet e la descrizione del codice.

## <a name="topics-in-this-tutorial"></a>Negli argomenti di questa esercitazione

Negli argomenti di questa esercitazione sono progettati per essere letti in sequenza, con ogni argomento sulla base di quelle illustrate nell'argomento precedente.

[Creazione di un Cmdlet senza parametri](./creating-a-cmdlet-without-parameters.md) in questa sezione viene descritto come creare un cmdlet che recupera le informazioni dal computer locale senza l'utilizzo di parametri e quindi scrive le informazioni per la pipeline.

[Aggiunta di parametri di Input della riga di comando tale processo](./adding-parameters-that-process-command-line-input.md) in questa sezione viene descritto come aggiungere un parametro al cmdlet Get-Process in modo che il cmdlet può elaborare l'input in base agli oggetti espliciti passati al cmdlet. L'implementazione descritta qui recupera processi in base al nome e quindi scrive le informazioni per la pipeline.

[Aggiunta di parametri di Input della Pipeline di processo](./adding-parameters-that-process-pipeline-input.md) in questa sezione viene descritto come aggiungere un parametro al cmdlet Get-Process in modo che il cmdlet può elaborare gli oggetti passati a esso tramite la pipeline. Il cmdlet di implementazione descritto di seguito consente di recuperare i processi in base agli oggetti passati al cmdlet e quindi scrive le informazioni per la pipeline.

[Aggiunta di segnalazione degli errori non fatali al Cmdlet Your](./adding-non-terminating-error-reporting-to-your-cmdlet.md) in questa sezione viene descritto come aggiungere segnalazione a un cmdlet di errori non fatali. L'implementazione descritta qui rileva errori non fatali che si verificano durante l'elaborazione di input e scrive un record di errore nel flusso di errore.

## <a name="see-also"></a>Vedere anche

[Creazione di un Cmdlet senza parametri](./creating-a-cmdlet-without-parameters.md)

[Aggiunta di parametri che elaborano gli Input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Aggiunta di parametri di Input della Pipeline di processo](./adding-parameters-that-process-pipeline-input.md)

[Aggiunta di segnalazione errori non fatali al Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
