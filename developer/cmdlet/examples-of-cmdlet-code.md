---
title: Esempi di codice per Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 39c0814faf72cdb4b24730acb2ae429a2f465b32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863127"
---
# <a name="examples-of-cmdlet-code"></a>Esempi di codice dei cmdlet

In questa sezione contiene esempi di codice del cmdlet che è possibile utilizzare per iniziare a scrivere cmdlet personalizzati.

> [!IMPORTANT]
> Per istruzioni dettagliate per la scrittura di cmdlet, vedere [esercitazioni per la scrittura di cmdlet](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>Contenuto della sezione

[Come scrivere un semplice Cmdlet](./how-to-write-a-simple-cmdlet.md) questo esempio illustra la struttura di base di codice del cmdlet.

[Come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md) in questo esempio viene illustrato come dichiarare i diversi tipi di parametri.

[Come dichiarare set di parametri](./how-to-declare-parameter-sets.md) in questo esempio viene illustrato come dichiarare set di parametri che è possono modificare l'azione esegue un cmdlet.

[Convalida Input parametro come](./how-to-validate-parameter-input.md) questi esempi illustrano come eseguire la convalida di input del parametro.

[Come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md) in questo esempio viene illustrato come dichiarare un parametro che viene aggiunto in fase di esecuzione.

[Come richiamare gli script all'interno di un Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) in questo esempio viene illustrato come richiamare uno script che viene fornito a un cmdlet.

[Come eseguire l'Override di metodi di elaborazione di Input](./how-to-override-input-processing-methods.md) questi esempi illustrano la struttura di base usata per eseguire l'override di metodi BeginProcessing, ProcessRecord ed EndProcessing.

[Come supporto per le chiamate ShouldProcess](./how-to-request-confirmations.md) in questo esempio viene illustrato come il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)metodi devono essere chiamati da all'interno di un cmdlet.

[Modalità di supporto delle transazioni](./how-to-support-transactions.md) in questo esempio viene illustrato come indicare che il cmdlet supporta le transazioni e come implementare l'azione da eseguita quando il cmdlet viene usato all'interno di una transazione.

[Come supportare processi](./how-to-support-jobs.md) in questo esempio viene illustrato come supportare i processi quando si scrivono i cmdlet.

[Come richiamare un Cmdlet da all'interno di un Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) in questo esempio viene illustrato come richiamare un cmdlet all'interno di un altro cmdlet, che consente di aggiungere la funzionalità del cmdlet richiamato al cmdlet si sta sviluppando.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
