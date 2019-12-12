---
title: Come importare i cmdlet mediante i moduli | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364460"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Come importare i cmdlet usando i moduli

Questo articolo descrive come importare i cmdlet in una sessione di PowerShell usando un modulo binario.

> [!NOTE]
> I membri dei moduli possono includere cmdlet, provider, funzioni, variabili, alias e molto altro ancora. Gli snap-in possono contenere solo cmdlet e provider.

## <a name="how-to-load-cmdlets-using-a-module"></a>Come caricare i cmdlet usando un modulo

1. Creare una cartella del modulo con lo stesso nome del file di assembly in cui sono implementati i cmdlet. In questa procedura viene creata la cartella del modulo nella cartella Windows `system32`.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. Verificare che la variabile di ambiente `PSModulePath` includa il percorso della nuova cartella del modulo. Per impostazione predefinita, la cartella di sistema è già stata aggiunta alla variabile di ambiente `PSModulePath`. Per visualizzare il `PSModulePath`, digitare: `$env:PSModulePath`.

1. Copiare l'assembly del cmdlet nella cartella del modulo.

1. Aggiungere un file manifesto del modulo (`.psd1`) nella cartella radice del modulo. PowerShell usa il manifesto del modulo per importare il modulo. Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](../module/how-to-write-a-powershell-module-manifest.md).

1. Eseguire il comando seguente per aggiungere i cmdlet alla sessione:

   `Import-Module [Module_Name]`

   Questa procedura può essere utilizzata per testare i cmdlet. Aggiunge tutti i cmdlet nell'assembly alla sessione. Per ulteriori informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Vedere anche

[Come scrivere un manifesto del modulo PowerShell](../module/how-to-write-a-powershell-module-manifest.md)

[Importazione di un modulo di PowerShell](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Installazione di moduli](../module/installing-a-powershell-module.md)

[Modifica del percorso di installazione di PSModulePath](../module/modifying-the-psmodulepath-installation-path.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
