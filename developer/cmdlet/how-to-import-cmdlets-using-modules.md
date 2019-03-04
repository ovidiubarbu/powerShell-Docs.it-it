---
title: Come importare i cmdlet di uso di moduli | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859147"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Come importare i cmdlet usando i moduli

In questo argomento viene descritto come importare i cmdlet di una sessione di Windows PowerShell usando un modulo binario.

> [!NOTE]
> I membri dei moduli possono includere i cmdlet, provider, funzioni, variabili, alias e molto altro ancora. Gli snap-in può contenere solo i cmdlet e provider.

## <a name="how-to-load-cmdlets-using-a-module"></a>Come caricare i cmdlet di uso di un modulo

1. Creare una cartella del modulo che ha lo stesso nome del file di assembly in cui vengono implementati i cmdlet. In questa procedura, si crea la cartella del modulo nel `system32` cartella.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Assicurarsi che il `PSModulePath` variabile di ambiente include il percorso della cartella del nuovo modulo. Per impostazione predefinita, la cartella di sistema è già stato aggiunto per il `PSModulePath` variabile di ambiente.

3. Copiare l'assembly di cmdlet nella cartella del modulo.

4. Eseguire il comando seguente per aggiungere i cmdlet nella sessione:

   `import-module [Module_Name]`

   Questa procedura è utilizzabile per testare i cmdlet. Aggiunge tutti i cmdlet dell'assembly alla sessione. Per altre informazioni sui moduli, vedere i diversi tipi di moduli, i diversi modi per caricare i moduli e come limitare gli elementi di un modulo che vengono esportati [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Installazione dei moduli](../module/installing-a-powershell-module.md)