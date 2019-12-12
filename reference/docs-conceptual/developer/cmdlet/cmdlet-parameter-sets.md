---
title: Set di parametri del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: dfe747893b4aef6376ea3b12dd79b7c144455ed0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415695"
---
# <a name="cmdlet-parameter-sets"></a>Set di parametri del cmdlet

PowerShell usa i set di parametri per consentire la scrittura di un singolo cmdlet che può eseguire diverse azioni per diversi scenari. I set di parametri consentono di esporre parametri diversi all'utente. Per restituire informazioni diverse in base ai parametri specificati dall'utente.

## <a name="examples-of-parameter-sets"></a>Esempi di set di parametri

Ad esempio, il cmdlet `Get-EventLog` di PowerShell restituisce informazioni diverse a seconda che l'utente specifichi il parametro **List** o **logName** . Se viene specificato il parametro **List** , il cmdlet restituisce le informazioni sui file di log, ma non le informazioni sull'evento contenute. Se viene specificato il parametro **logName** , il cmdlet restituisce informazioni sugli eventi in un registro eventi specifico. I parametri **List** e **logName** identificano due set di parametri distinti.

## <a name="unique-parameter"></a>Parametro univoco

Ogni set di parametri deve avere un parametro univoco usato dal runtime di PowerShell per esporre il set di parametri appropriato. Se possibile, il parametro Unique deve essere un parametro obbligatorio. Quando un parametro è obbligatorio, l'utente deve specificare il parametro e il runtime di PowerShell usa tale parametro per identificare il set di parametri. Il parametro Unique non può essere obbligatorio se il cmdlet è progettato per essere eseguito senza specificare alcun parametro.

## <a name="multiple-parameter-sets"></a>Set di parametri multipli

Nella figura seguente la colonna sinistra mostra tre set di parametri validi. Il **parametro a** è univoco per il primo set di parametri, il **parametro B** è univoco per il secondo set di parametri e il **parametro C** è univoco per il terzo set di parametri. Nella colonna a destra i set di parametri non hanno un parametro univoco.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Requisiti per i set di parametri

I requisiti seguenti si applicano a tutti i set di parametri.

- Ogni set di parametri deve avere almeno un parametro univoco. Se possibile, rendere questo parametro un parametro obbligatorio.

- Un set di parametri che contiene più parametri posizionali deve definire posizioni univoche per ogni parametro. Non è possibile specificare la stessa posizione per due parametri posizionali.

- Solo un parametro in un set può dichiarare la parola chiave `ValueFromPipeline` con un valore di `true`.
  Più parametri possono definire la parola chiave `ValueFromPipelineByPropertyName` con un valore di `true`.

- Se per un parametro non è specificato alcun set di parametri, il parametro appartiene a tutti i set di parametri.

> [!NOTE]
> Per un cmdlet o una funzione, è previsto un limite di 32 set di parametri.

## <a name="default-parameter-sets"></a>Set di parametri predefiniti

Quando vengono definiti più set di parametri, è possibile usare la parola chiave `DefaultParameterSetName` dell'attributo **cmdlet** per specificare il set di parametri predefinito. PowerShell usa il set di parametri predefinito se non è in grado di determinare il set di parametri da usare in base alle informazioni fornite dal comando. Per ulteriori informazioni sull'attributo **cmdlet** , vedere [dichiarazione dell'attributo del cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Dichiarazione di set di parametri

Per creare un set di parametri, è necessario specificare la parola chiave `ParameterSetName` quando si dichiara l'attributo del **parametro** per ogni parametro nel set di parametri. Per i parametri che appartengono a più set di parametri, aggiungere un attributo di **parametro** per ogni set di parametri. Questo attributo consente di definire il parametro in modo diverso per ogni set di parametri. È ad esempio possibile definire un parametro come obbligatorio in un unico set e facoltativo in un altro. Tuttavia, ogni set di parametri deve contenere un parametro univoco. Per altre informazioni, vedere [dichiarazione dell'attributo Parameter](parameter-attribute-declaration.md).

Nell'esempio seguente il parametro **username** è il parametro Unique del set di parametri `Test01` e il parametro **ComputerName** è il parametro Unique del set di parametri `Test02`. Il parametro **SharedParam** appartiene a entrambi i set ed è obbligatorio per il set di parametri `Test01` ma facoltativo per il set di parametri `Test02`.

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
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
private string sharedParam;
```
