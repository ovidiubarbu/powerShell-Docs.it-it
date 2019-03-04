---
title: Imposta parametro di cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857267"
---
# <a name="cmdlet-parameter-sets"></a>Set di parametri dei cmdlet

Windows PowerShell Usa set di parametri per consentire la scrittura di un singolo cmdlet che possono eseguire azioni diverse per diversi scenari. Set di parametri consentono di esporre parametri diversi per l'utente e per restituire informazioni diverse in base ai parametri specificati dall'utente.

## <a name="examples-of-parameter-sets"></a>Esempi di set di parametri

Ad esempio, il `Get-EventLog` cmdlet (fornito da Windows PowerShell) restituisce informazioni diverse a seconda del fatto che l'utente specifichi il `List` o `LogName` parametro. Se il `List` viene specificato, il cmdlet restituisce informazioni sui file di log stessi, ma non le informazioni sugli eventi che contengono. Se il `LogName` parametro viene specificato, il cmdlet restituisce informazioni sugli eventi in un determinato registro eventi. Il `List` e `LogName` parametro identificano due set di parametri separato.

## <a name="unique-parameter"></a>Parametro univoco

Ogni set di parametri deve avere un parametro univoco che il runtime di Windows PowerShell è possibile usare per esporre il set di parametri appropriato. Se possibile, il parametro univoco deve essere un parametro obbligatorio. Quando un parametro è obbligatorio, l'utente è obbligato a specificare il parametro e il runtime di Windows PowerShell è possibile usare tale parametro per identificare il parametro impostato per l'utilizzo. Il parametro unique non può essere obbligatorio se il cmdlet è progettato per essere eseguito senza specificare alcun parametro.

## <a name="multiple-parameter-sets"></a>Più set di parametri

Nella figura seguente, la colonna a sinistra mostra tre set di parametri valido. Parametro oggetto è univoco per il primo set di parametri, parametro B è univoco per il secondo set di parametri e parametro C è univoco per il terzo set di parametri. Tuttavia, nella colonna destra, i set di parametri non è un parametro univoco.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Requisiti dei Set di parametri

I requisiti seguenti si applicano a tutti i set di parametri.

- Ogni set di parametri deve contenere almeno un parametro univoco. Se possibile, impostare questo parametro di un parametro obbligatorio.

- Un set di parametri che contiene più parametri posizionali debba definire le posizioni univoche per ogni parametro. Nessuna due parametri posizionali specificabile nella stessa posizione.

- Puoi dichiarare un solo parametro in un set di `ValueFromPipeline` parola chiave con il valore `true`. Possono definire più parametri di `ValueFromPipelineByPropertyName` parola chiave con il valore `true`.

- Se non viene specificato alcun set di parametri per un parametro, il parametro appartiene a tutti i set di parametri.

## <a name="default-parameter-sets"></a>Set di parametri predefiniti

Quando sono definiti più set di parametri, è possibile usare il `DefaultParameterSetName` (parola chiave) dell'attributo Cmdlet per specificare il set di parametri predefinito. Windows PowerShell Usa il parametro predefinito impostato se non è possibile determinare il parametro impostato per usare basato sulle informazioni fornite dal comando. Per altre informazioni sull'attributo Cmdlet, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>La dichiarazione di set di parametri

Per creare un set di parametri, è necessario specificare il `ParameterSetName` parola chiave quando si dichiara l'attributo di parametro per ogni parametro nel set di parametri. Per i parametri appartenenti a più set di parametri, aggiungere un attributo di parametro per ogni set di parametri. Ciò consente di definire il parametro in modo diverso per ogni set di parametri. Ad esempio, è possibile definire un parametro come obbligatori in un set e facoltativi in un altro. Tuttavia, ogni set di parametri deve contenere un solo parametro univoco.

Nell'esempio seguente, il `UserName` parametro è il parametro unique di set di parametri Test01 e il `ComputerName` parametro è il parametro unique di set di parametri Test02. Il `SharedParam` parametro appartiene a entrambi i set ed è obbligatorio per il parametro Test01 impostata ma facoltativo per il set di parametri Test02.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```