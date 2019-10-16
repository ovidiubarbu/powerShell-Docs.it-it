---
title: Esercitazione getproc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364440"
---
# <a name="getproc-tutorial"></a>Esercitazione su GetProc

Questa sezione fornisce un'esercitazione per la creazione di un cmdlet Get-proc molto simile al cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) fornito da Windows PowerShell. Questa esercitazione fornisce frammenti di codice che illustrano come vengono implementati i cmdlet e una spiegazione del codice.

## <a name="topics-in-this-tutorial"></a>Argomenti in questa esercitazione

Gli argomenti di questa esercitazione sono progettati per essere letti in sequenza, con ogni argomento che si basa su ciò che è stato discusso nell'argomento precedente.

[Creazione di un cmdlet senza parametri](./creating-a-cmdlet-without-parameters.md) In questa sezione viene descritto come creare un cmdlet che recupera le informazioni dal computer locale senza l'utilizzo di parametri e quindi scrive le informazioni nella pipeline.

[Aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md) Questa sezione descrive come aggiungere un parametro al cmdlet Get-proc in modo che il cmdlet possa elaborare l'input in base a oggetti espliciti passati al cmdlet. L'implementazione descritta qui recupera i processi in base al nome e quindi scrive le informazioni nella pipeline.

[Aggiunta di parametri che elaborano l'input della pipeline](./adding-parameters-that-process-pipeline-input.md) Questa sezione descrive come aggiungere un parametro al cmdlet Get-proc, in modo che il cmdlet possa elaborare gli oggetti passati tramite la pipeline. Il cmdlet di implementazione descritto di seguito recupera i processi in base agli oggetti passati al cmdlet e quindi scrive le informazioni nella pipeline.

[Aggiunta della segnalazione errori non fatale al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) In questa sezione viene descritto come aggiungere una segnalazione errori non fatale a un cmdlet. L'implementazione descritta qui rileva gli errori non fatali che si verificano durante l'elaborazione dell'input e scrive un record di errore nel flusso di errori.

## <a name="see-also"></a>Vedere anche

[Creazione di un cmdlet senza parametri](./creating-a-cmdlet-without-parameters.md)

[Aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Aggiunta di parametri che elaborano l'input della pipeline](./adding-parameters-that-process-pipeline-input.md)

[Aggiunta della segnalazione errori non fatale al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
