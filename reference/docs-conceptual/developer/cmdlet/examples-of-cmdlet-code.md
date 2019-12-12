---
title: Esempi di codice cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364500"
---
# <a name="examples-of-cmdlet-code"></a>Esempi di codice dei cmdlet

Questa sezione contiene esempi di codice cmdlet che è possibile usare per iniziare a scrivere cmdlet personalizzati.

> [!IMPORTANT]
> Per istruzioni dettagliate per la scrittura di cmdlet, vedere [esercitazioni per la scrittura di cmdlet](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>Contenuto della sezione

[Come scrivere un semplice cmdlet](./how-to-write-a-simple-cmdlet.md) In questo esempio viene illustrata la struttura di base del codice del cmdlet.

[Come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md) Questo esempio illustra come dichiarare i diversi tipi di parametri.

[Come dichiarare i set di parametri](./how-to-declare-parameter-sets.md) In questo esempio viene illustrato come dichiarare set di parametri che possono modificare l'azione eseguita da un cmdlet.

[Come convalidare l'input del parametro](./how-to-validate-parameter-input.md) In questi esempi viene illustrato come convalidare l'input dei parametri.

[Come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md) Questo esempio illustra come dichiarare un parametro aggiunto in fase di esecuzione.

[Come richiamare gli script all'interno di un cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) In questo esempio viene illustrato come richiamare uno script fornito a un cmdlet.

[Come eseguire l'override dei metodi di elaborazione dell'input](./how-to-override-input-processing-methods.md) In questi esempi viene illustrata la struttura di base utilizzata per eseguire l'override dei metodi BeginProcessing, ProcessRecord e EndProcessing.

[Come supportare le chiamate ShouldProcess](./how-to-request-confirmations.md) Questo esempio illustra il modo in cui i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) devono essere chiamati dall'interno di un cmdlet.

[Come supportare le transazioni](./how-to-support-transactions.md) In questo esempio viene illustrato come indicare che il cmdlet supporta le transazioni e come implementare l'azione eseguita quando il cmdlet viene utilizzato all'interno di una transazione.

[Come supportare i processi](./how-to-support-jobs.md) Questo esempio illustra come supportare i processi quando si scrivono i cmdlet.

[Come richiamare un cmdlet all'interno di un cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) In questo esempio viene illustrato come richiamare un cmdlet da un altro cmdlet, che consente di aggiungere la funzionalità del cmdlet richiamato al cmdlet che si sta sviluppando.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
