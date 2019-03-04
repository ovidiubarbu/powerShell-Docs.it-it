---
title: Filtro parametri di input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854467"
---
# <a name="input-filter-parameters"></a>Parametri di filtro degli input

Un cmdlet è possibile definire `Filter`, `Include`, e `Exclude` parametri che filtrano l'insieme di oggetti di input che interessa il cmdlet.

In genere, il set di oggetti di input è specificato da un `InputObject`, `Path`, o `Name` parametro. Ad esempio, un cmdlet può avere un `Path` parametro che accetta più percorsi con caratteri jolly e ogni percorso punta a un oggetto di input. Usati insieme, il `Filter`, `Include`, e `Exclude` parametri ulteriormente qualificare i percorsi di cmdlet funziona su ogni volta che viene richiamato.

## <a name="include-and-exclude-parameters"></a>Includere ed escludere i parametri

Il `Include` e `Exclude` parametri identificano gli oggetti che sono inclusi o esclusi dal set di oggetti di input passati al cmdlet. Usare questi parametri quando il filtro può essere espresso nel linguaggio con caratteri jolly standard. (Per altre informazioni sui caratteri jolly, vedere [che supportano i caratteri jolly in parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Il `Include` parametro include tutti gli oggetti i cui nomi corrispondono al filtro di inclusione. Il `Exclude` parametro esclude tutti gli oggetti i cui nomi corrispondono al filtro.

## <a name="filter-parameter"></a>Parametro di filtro

Il `Filter` parametro specifica un filtro che non è espressa nel linguaggio con caratteri jolly standard. Ad esempio, i filtri di Active Directory Service Interfaces (ADSI) o SQL potrebbero essere passati al cmdlet tramite relativo `Filter` parametro. Nei cmdlet di Windows PowerShell, questi filtri vengono specificati dai provider di Windows PowerShell mediante il cmdlet per accedere a un archivio dati. In genere, ogni provider definisce un filtro.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Applicazione di filtri se non è specificato alcun Set di oggetti di Input

Se non viene specificato alcun set di oggetti di input, ciò significa in genere filtrare i dati di tutti gli oggetti. Per altre informazioni, vedere[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)