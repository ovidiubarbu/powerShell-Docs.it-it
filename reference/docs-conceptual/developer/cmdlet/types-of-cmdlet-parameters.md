---
title: Tipi di parametri dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369310"
---
# <a name="types-of-cmdlet-parameters"></a>Tipi di parametri del cmdlet

In questo argomento vengono descritti i diversi tipi di parametri che è possibile dichiarare nei cmdlet. I parametri dei cmdlet possono essere posizionali, denominati, obbligatori, facoltativi o parametri di opzione.

## <a name="positional-and-named-parameters"></a>Parametri posizionali e denominati

Tutti i parametri del cmdlet sono denominati o parametri posizionali. Un parametro denominato richiede che si digitano il nome del parametro e l'argomento quando si chiama il cmdlet. Un parametro posizionale richiede solo che si digitano gli argomenti in ordine relativo. Il sistema esegue quindi il mapping del primo argomento senza nome al primo parametro posizionale. Il sistema esegue il mapping tra il secondo argomento senza nome e il secondo parametro senza nome e così via. Per impostazione predefinita, tutti i parametri del cmdlet sono parametri denominati.

Per definire un parametro denominato, omettere la parola chiave `Position` nella dichiarazione dell'attributo del **parametro** , come illustrato nella dichiarazione di parametro seguente.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Per definire un parametro posizionale, aggiungere la parola chiave `Position` nella dichiarazione dell'attributo Parameter, quindi specificare una posizione. Nell'esempio seguente il parametro `UserName` viene dichiarato come parametro posizionale con la posizione 0. Ciò significa che il primo argomento della chiamata verrà associato automaticamente a questo parametro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Una buona progettazione dei cmdlet consiglia di dichiarare i parametri più usati come parametri posizionali, in modo che l'utente non debba immettere il nome del parametro quando viene eseguito il cmdlet.

I parametri posizionali e denominati accettano argomenti singoli o più argomenti separati da virgole. Sono consentiti più argomenti solo se il parametro accetta una raccolta, ad esempio una matrice di stringhe. È possibile combinare parametri posizionali e denominati nello stesso cmdlet. In questo caso, il sistema recupera prima gli argomenti denominati, quindi tenta di eseguire il mapping degli argomenti senza nome rimanenti ai parametri posizionali.

I comandi seguenti illustrano i diversi modi in cui è possibile specificare argomenti singoli e multipli per i parametri del cmdlet `Get-Command`. Si noti che negli ultimi due esempi non è necessario specificare **-Name** perché il parametro `Name` è definito come parametro posizionale.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Parametri obbligatori e facoltativi

È anche possibile definire i parametri dei cmdlet come parametri obbligatori o facoltativi. È necessario specificare un parametro obbligatorio prima che il runtime di Windows PowerShell richiami il cmdlet.  Per impostazione predefinita, i parametri sono definiti come facoltativi.

Per definire un parametro obbligatorio, aggiungere la parola chiave `Mandatory` nella dichiarazione dell'attributo Parameter e impostarla su `true`, come illustrato nella dichiarazione di parametro seguente.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Per definire un parametro facoltativo, omettere la parola chiave `Mandatory` nella dichiarazione dell'attributo del **parametro** , come illustrato nella dichiarazione di parametro seguente.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Parametri di opzione

Windows PowerShell fornisce un tipo [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) che consente di definire un parametro il cui valore viene impostato automaticamente su `false` se il parametro non viene specificato quando viene chiamato il cmdlet. Quando possibile, usare parametri switch al posto di parametri booleani.

Si consideri l'esempio seguente. Per impostazione predefinita, diversi cmdlet di Windows PowerShell non passano un oggetto di output alla pipeline. Tuttavia, questi cmdlet hanno un `PassThru` parametro switch che sostituisce il comportamento predefinito. Se il parametro `PassThru` viene specificato al momento della chiamata di questi cmdlet, il cmdlet restituisce un oggetto di output alla pipeline.

Se è necessario che il parametro abbia un valore predefinito di `true` quando il parametro non è specificato nella chiamata, provare a invertire il senso del parametro. Per esempio, anziché impostare l'attributo del parametro su un valore booleano di `true`, dichiarare la proprietà come tipo [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) , quindi impostare il valore predefinito del parametro su `false`.

Per definire un parametro switch, dichiarare la proprietà come tipo [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) , come illustrato nell'esempio seguente.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Per fare in modo che il cmdlet agisca sul parametro quando viene specificato, utilizzare la struttura seguente in uno dei metodi di elaborazione dell'input.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
