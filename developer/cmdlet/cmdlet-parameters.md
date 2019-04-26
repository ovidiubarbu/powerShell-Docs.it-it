---
title: Parametri del cmdlet | Microsoft Docs
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
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068403"
---
# <a name="cmdlet-parameters"></a>Parametri dei cmdlet

Parametri del cmdlet forniscono il meccanismo che consente a un cmdlet accettare l'input. I parametri possono accettare l'input direttamente dalla riga di comando o da oggetti passati al cmdlet tramite la pipeline, gli argomenti (noto anche come *valori*) di questi parametri possono specificare l'input che il cmdlet accetta, come il cmdlet deve eseguire le azioni e i dati restituiti dal cmdlet per la pipeline.

## <a name="in-this-section"></a>Contenuto della sezione

[Dichiarazione di proprietà come parametri](./declaring-properties-as-parameters.md) fornisce informazioni di base è necessario comprendere prima di dichiarare i parametri di un cmdlet.

[Tipi di parametri del Cmdlet](./types-of-cmdlet-parameters.md) descrive i diversi tipi di parametri che è possibile dichiarare nei cmdlet.

[Nome del parametro di cmdlet e linee guida per la funzionalità](./standard-cmdlet-parameter-names-and-types.md) dischi i nomi, tipo di dati e funzionalità dei parametri standard consigliati.

[Gli alias dei parametri](./parameter-aliases.md) illustra gli alias che è possibile definire per i parametri.

[I nomi dei parametri comuni](./common-parameter-names.md) in questo argomento vengono descritti i parametri che Windows PowerShell aggiunge al cmdlet.

[Imposta parametro di cmdlet](./cmdlet-parameter-sets.md) viene illustrato come set di parametri consentono di scrivere un singolo cmdlet che possono eseguire azioni diverse per diversi scenari.

[I parametri dinamici cmdlet](./cmdlet-dynamic-parameters.md) vengono illustrati parametri disponibili per l'utente in condizioni speciali.

[Supporto di caratteri jolly in parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) viene descritto come fornire supporto per i caratteri jolly quando si progetta un cmdlet che verrà eseguito con un gruppo di risorse.

[Convalida Input parametro](./validating-parameter-input.md) illustra come la convalida di argomenti passati ai parametri del cmdlet Windows PowerShell.

[Filtro parametri di input](./input-filter-parameters.md) esamina i `Filter`, `Include`, e `Exclude` parametri che filtrano l'insieme di oggetti di input che interessa il cmdlet.

## <a name="related-sections"></a>Sezioni correlate

[Come convalidare l'Input del parametro](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Vedere anche

[Dichiarazione di attributo di parametro](./parameter-attribute-declaration.md)

[Cmdlet di Windows PowerShell](./cmdlet-overview.md)
