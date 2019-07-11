---
title: Dichiarazione di attributo parametro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735145"
---
# <a name="parameter-attribute-declaration"></a>Dichiarazione dell'attributo Parameter

L'attributo Parameter identifica una proprietà pubblica della classe cmdlet come un parametro del cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parametri

`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro di cmdlet è obbligatorio. Se un parametro obbligatorio non viene specificato quando viene richiamato il cmdlet, Windows PowerShell richiede all'utente un valore di parametro. Il valore predefinito è `false`.

`ParameterSetName` ([System. String](/dotnet/api/System.String)) parametro denominato facoltativo. Specifica che il parametro impostato che questo parametro di cmdlet appartiene. Se non viene specificato alcun set di parametri, il parametro appartiene a tutti i set di parametri.

`Position` ([System.Int32](/dotnet/api/System.Int32)) parametro denominato facoltativo. Specifica la posizione del parametro all'interno di un comando di Windows PowerShell.

`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro del cmdlet prende il valore da un oggetto della pipeline. Specificare questa parola chiave se il cmdlet accede completo dell'oggetto, non solo una proprietà dell'oggetto. Il valore predefinito è `false`.

`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro del cmdlet accetta il relativo valore da una proprietà di un oggetto della pipeline con lo stesso nome o lo stesso alias come parametro. Se, ad esempio, il cmdlet include un `Name` parametro e l'oggetto pipeline ha anche una `Name` proprietà, il valore della `Name` proprietà viene assegnata al `Name` parametro del cmdlet. Il valore predefinito è `false`.

`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro di cmdlet accetta tutti i restanti argomenti passati al cmdlet. Il valore predefinito è `false`.

`HelpMessage` Parametro denominato facoltativo. Specifica una breve descrizione del parametro. Windows PowerShell Visualizza questo messaggio quando viene eseguito un cmdlet e un parametro obbligatorio non è specificato.

`HelpMessageBaseName` Parametro denominato facoltativo. Specifica la posizione in cui si trovano gli identificatori di risorsa. Questo parametro, ad esempio, possibile specificare un assembly di risorse che contiene i messaggi della Guida che desideri localizzare.

`HelpMessageResourceId` Parametro denominato facoltativo. Specifica l'identificatore di risorsa per un messaggio della Guida.

## <a name="remarks"></a>Osservazioni

- Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Un cmdlet può avere qualsiasi numero di parametri. Tuttavia, per migliorare l'esperienza utente, limitare il numero di parametri.

- Parametri devono essere dichiarati nella proprietà o campi non statici pubblici. I parametri devono essere dichiarati nella proprietà. La proprietà deve avere una funzione di accesso set pubblica e se il `ValueFromPipeline` o `ValueFromPipelineByPropertyName` (parola chiave) viene specificato, la proprietà deve avere una funzione di accesso get pubblico.

- Quando si specificano i parametri posizionali, limitare il numero di parametri posizionali in un parametro impostato su meno di cinque. E, parametri posizionali non devono essere contigue. Le posizioni 5 e 100 250 funzionano come le posizioni 0, 1 e 2.

- Quando il `Position` parola chiave non è specificato, il parametro del cmdlet è necessario fare riferimento al nome.

- Quando si usano set di parametri, tenere presente quanto segue:

    - Ogni set di parametri deve contenere almeno un parametro univoco. Progettazione dei cmdlet buona indica che questo parametro univoco del failover sarà obbligatorio se possibile. Se il cmdlet è progettato per essere eseguito senza parametri, il parametro unique non può essere obbligatorio.

    - Nessun set di parametri deve contenere più di un parametro posizionale con la stessa posizione.

    - Un solo parametro in un set di parametri deve dichiarare `ValueFromPipeline = true`. Possono definire più parametri `ValueFromPipelineByPropertyName = true`.

    - Possono definire più parametri `ValueFromPipelineByPropertyName = true`.

- Per altre informazioni sulle linee guida per i nomi dei parametri, vedere [i nomi dei parametri di Cmdlet](standard-cmdlet-parameter-names-and-types.md).

- L'attributo di parametro è definito per il [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Nomi di parametro del cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
