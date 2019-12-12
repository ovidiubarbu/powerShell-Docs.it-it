---
title: Parametri del filtro di input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364390"
---
# <a name="input-filter-parameters"></a>Parametri di filtro degli input

Un cmdlet può definire i parametri `Filter`, `Include`e `Exclude` che filtrano il set di oggetti di input interessati dal cmdlet.

In genere, il set di oggetti di input viene specificato da un parametro `InputObject`, `Path`o `Name`. Ad esempio, un cmdlet può avere un `Path` parametro che accetta più percorsi utilizzando caratteri jolly e ogni percorso punta a un oggetto di input. Insieme, i parametri `Filter`, `Include`e `Exclude` qualificano ulteriormente i percorsi utilizzati dal cmdlet ogni volta che viene richiamato.

## <a name="include-and-exclude-parameters"></a>Includi ed Escludi parametri

I parametri `Include` e `Exclude` identificano gli oggetti inclusi o esclusi dal set di oggetti di input passati al cmdlet. Usare questi parametri quando il filtro può essere espresso nel linguaggio con caratteri jolly standard. Per ulteriori informazioni sui caratteri jolly, vedere Supporto dei caratteri [jolly nei parametri dei cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md). Il parametro `Include` include tutti gli oggetti i cui nomi corrispondono al filtro di inclusione. Il parametro `Exclude` esclude tutti gli oggetti i cui nomi corrispondono al filtro.

## <a name="filter-parameter"></a>Parametro Filter

Il parametro `Filter` specifica un filtro non espresso nel linguaggio con caratteri jolly standard. È possibile, ad esempio, che i filtri ADSI (Active Directory Service Interfaces) o SQL vengano passati al cmdlet tramite il relativo parametro `Filter`. Nei cmdlet forniti da Windows PowerShell questi filtri sono specificati dai provider di Windows PowerShell che usano il cmdlet per accedere a un archivio dati. Ogni provider definisce in genere il proprio filtro.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtro se non è specificato alcun set di oggetti di input

Se non viene specificato alcun set di oggetti di input, questo significa in genere filtrare in base a tutti gli oggetti. Per ulteriori informazioni, vedere[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)