---
title: Parametri dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: c1d8984f4aad7bae6f9be66a2222e2c74c8afa3d
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022214"
---
# <a name="cmdlet-parameters"></a>Parametri dei cmdlet

I parametri del cmdlet forniscono il meccanismo che consente a un cmdlet di accettare l'input. I parametri possono accettare input direttamente dalla riga di comando o da oggetti passati al cmdlet tramite la pipeline, gli argomenti (noti anche come *valori*) di questi parametri possono specificare l'input accettato dal cmdlet, il modo in cui il cmdlet deve eseguire le proprie azioni e i dati restituiti dal cmdlet alla pipeline.

## <a name="in-this-section"></a>Contenuto della sezione

[Dichiarazione di proprietà come parametri](./declaring-properties-as-parameters.md) Fornisce informazioni di base che è necessario conoscere prima di dichiarare i parametri di un cmdlet.

[Tipi di parametri dei cmdlet](./types-of-cmdlet-parameters.md) Vengono descritti i diversi tipi di parametri che è possibile dichiarare nei cmdlet.

[Linee guida sul nome e la funzionalità del parametro del cmdlet](./standard-cmdlet-parameter-names-and-types.md) Vengono illustrati i nomi, il tipo di dati consigliato e la funzionalità dei parametri standard.

[Alias di parametro](./parameter-aliases.md) Vengono descritti gli alias che è possibile definire per i parametri.

[Nomi di parametro comuni](./common-parameter-names.md) In questo argomento vengono descritti i parametri aggiunti da Windows PowerShell ai cmdlet di.

[Set di parametri del cmdlet](./cmdlet-parameter-sets.md) Viene illustrato il modo in cui i set di parametri consentono di scrivere un singolo cmdlet in grado di eseguire diverse azioni per diversi scenari.

[Parametri dinamici cmdlet](./cmdlet-dynamic-parameters.md) Vengono illustrati i parametri disponibili per l'utente in condizioni particolari.

[Supporto di caratteri jolly nei parametri dei cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) Viene descritto come fornire supporto per i caratteri jolly quando si progetta un cmdlet che verrà eseguito su un gruppo di risorse.

[Convalida dell'input del parametro](./validating-parameter-input.md) Descrive in che modo Windows PowerShell convalida gli argomenti passati ai parametri del cmdlet.

[Parametri del filtro di input](./input-filter-parameters.md) Vengono illustrati i parametri `Filter`, `Include`e `Exclude` che filtrano il set di oggetti di input interessati dal cmdlet.

## <a name="related-sections"></a>Sezioni correlate

[Come convalidare l'input del parametro](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Vedere anche

[Dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md)

[Cmdlet di Windows PowerShell](./cmdlet-overview.md)
