---
title: Dichiarazione dell'attributo Parameter | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365360"
---
# <a name="parameter-attribute-declaration"></a>Dichiarazione dell'attributo Parameter

L'attributo Parameter identifica una proprietà pubblica della classe cmdlet come parametro del cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parametri

`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro del cmdlet è obbligatorio. Se non viene fornito un parametro obbligatorio quando viene richiamato il cmdlet, Windows PowerShell richiede all'utente un valore di parametro. Il valore predefinito è `false`.

parametro denominato facoltativo `ParameterSetName` ([System. String](/dotnet/api/System.String)). Specifica il set di parametri a cui appartiene il parametro del cmdlet. Se non viene specificato alcun set di parametri, il parametro appartiene a tutti i set di parametri.

`Position` ([System. Int32](/dotnet/api/System.Int32)) parametro denominato facoltativo. Specifica la posizione del parametro all'interno di un comando di Windows PowerShell.

`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro del cmdlet prende il valore da un oggetto pipeline. Specificare questa parola chiave se il cmdlet accede all'oggetto completo, non solo a una proprietà dell'oggetto. Il valore predefinito è `false`.

`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro del cmdlet prende il valore da una proprietà di un oggetto pipeline con lo stesso nome o lo stesso alias di questo parametro. Se, ad esempio, il cmdlet dispone di un parametro `Name` e l'oggetto pipeline dispone anche di una proprietà `Name`, il valore della proprietà `Name` viene assegnato al parametro `Name` del cmdlet. Il valore predefinito è `false`.

`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il parametro del cmdlet accetta tutti gli argomenti rimanenti passati al cmdlet. Il valore predefinito è `false`.

`HelpMessage` parametro denominato facoltativo. Specifica una breve descrizione del parametro. Windows PowerShell Visualizza questo messaggio quando viene eseguito un cmdlet e non viene specificato un parametro obbligatorio.

`HelpMessageBaseName` parametro denominato facoltativo. Specifica la posizione in cui risiedono gli identificatori di risorsa. Questo parametro, ad esempio, può specificare un assembly di risorse che contiene i messaggi della guida che si desidera localizzare.

`HelpMessageResourceId` parametro denominato facoltativo. Specifica l'identificatore di risorsa per un messaggio della guida.

## <a name="remarks"></a>Osservazioni

- Per ulteriori informazioni su come dichiarare questo attributo, vedere [come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md).

- Un cmdlet può avere un numero qualsiasi di parametri. Tuttavia, per un'esperienza utente migliore, limitare il numero di parametri.

- I parametri devono essere dichiarati in proprietà o campi non statici pubblici. I parametri devono essere dichiarati in proprietà. La proprietà deve disporre di una funzione di accesso set pubblica. Se si specifica la parola chiave `ValueFromPipeline` o `ValueFromPipelineByPropertyName`, la proprietà deve disporre di una funzione di accesso get pubblica.

- Quando si specificano parametri posizionali, limitare il numero di parametri posizionali in un parametro impostato su un valore minore di 5. E, i parametri posizionali non devono essere contigui. Le posizioni 5, 100 e 250 funzionano allo stesso modo delle posizioni 0, 1 e 2.

- Quando la parola chiave `Position` non è specificata, il relativo nome deve essere usato come riferimento al parametro del cmdlet.

- Quando si usano i set di parametri, tenere presente quanto segue:

    - Ogni set di parametri deve avere almeno un parametro univoco. Una progettazione di cmdlet efficace indica che questo parametro univoco deve essere obbligatorio, se possibile. Se il cmdlet è progettato per l'esecuzione senza parametri, il parametro Unique non può essere obbligatorio.

    - Nessun set di parametri deve contenere più di un parametro posizionale con la stessa posizione.

    - Solo un parametro in un set di parametri deve dichiarare `ValueFromPipeline = true`. Più parametri possono definire `ValueFromPipelineByPropertyName = true`.

    - Più parametri possono definire `ValueFromPipelineByPropertyName = true`.

- Per ulteriori informazioni sulle linee guida per i nomi dei parametri, vedere [cmdlet parameter names](standard-cmdlet-parameter-names-and-types.md).

- L'attributo Parameter è definito dalla classe [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Nomi dei parametri del cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
