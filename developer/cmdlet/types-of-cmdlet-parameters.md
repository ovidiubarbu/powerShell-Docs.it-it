---
title: Tipi di parametri del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067196"
---
# <a name="types-of-cmdlet-parameters"></a>Tipi di parametri del cmdlet

Questo argomento descrive i diversi tipi di parametri che è possibile dichiarare nei cmdlet. Parametri del cmdlet possono essere posizionali, denominati, obbligatorio, facoltativo o parametri opzionali.

## <a name="positional-and-named-parameters"></a>Parametri posizionali e denominati

Tutti i parametri del cmdlet sono parametri posizionali o denominati. Un parametro denominato richiede che si digita il nome del parametro e l'argomento quando si chiama il cmdlet. Un parametro posizionale richiede solo che si digitano gli argomenti nell'ordine relativo. Il sistema esegue il mapping quindi il primo argomento senza nome per il primo parametro posizionale. Il sistema esegue il mapping il secondo argomento senza nome per il secondo parametro senza nome e così via. Per impostazione predefinita, tutti i parametri del cmdlet sono parametri denominati.

Per definire un parametro denominato, omettere il `Position` parola chiave nel **parametro** attributo di dichiarazione, come illustrato nella seguente dichiarazione di parametro.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Per definire un parametro posizionale, aggiungere il `Position` dichiarazione dell'attributo, parola chiave nel parametro e quindi specificare una posizione. Nell'esempio seguente il `UserName` parametro viene dichiarato come un parametro posizionale con posizione 0. Ciò significa che il primo argomento della chiamata verrà associato automaticamente a questo parametro.

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
> Progettazione dei cmdlet buona consiglia che i parametri utilizzati più di essere dichiarati come parametri posizionali in modo che l'utente non dovrà immettere il nome del parametro quando si esegue il cmdlet.

Parametri posizionali e denominati accettano argomenti singoli o più argomenti separati da virgole. Solo se il parametro accetta una raccolta, ad esempio una matrice di stringhe, sono consentiti più argomenti. È possibile combinare parametri posizionali e denominati nel cmdlet stesso. In questo caso, il sistema deve recuperare prima di tutto gli argomenti denominati e quindi tenta di eseguire il mapping le rimanenti senza nome argomenti ai parametri posizionali.

I comandi seguenti mostrano i diversi modi in cui è possibile specificare singolo e più argomenti per i parametri del `Get-Command` cmdlet. Si noti che negli ultimi due esempi **-name** non dovrà essere specificato perché il `Name` parametro viene definito come un parametro posizionale.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Parametri obbligatori e facoltativi

È anche possibile definire i parametri del cmdlet come parametri obbligatori o facoltativi. (Un parametro obbligatorio deve essere specificato prima che il runtime di Windows PowerShell richiama il cmdlet.)  Per impostazione predefinita, i parametri vengono definiti come facoltativi.

Per definire un parametro obbligatorio, aggiungere il `Mandatory` dichiarazione dell'attributo, parola chiave nel parametro e impostarlo su `true`, come illustrato nella seguente dichiarazione di parametro.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Per definire un parametro facoltativo, omettere il `Mandatory` parola chiave nel **parametro** attributo di dichiarazione, come illustrato nella seguente dichiarazione di parametro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Parametri opzionali

Windows PowerShell fornisce un' [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tipo che consente di definire un parametro il cui valore viene impostato automaticamente su `false` se il parametro non viene specificato quando è il cmdlet viene chiamato. Se possibile, usare parametri di opzione anziché i parametri booleani.

Si consideri l'esempio seguente. Per impostazione predefinita, alcuni cmdlet di Windows PowerShell non passare un oggetto di output alla pipeline. Tuttavia, questi cmdlet hanno un `PassThru` passare parametri che esegue l'override del comportamento predefinito. Se il `PassThru` viene specificato quando vengono chiamati questi cmdlet, il cmdlet restituisce un oggetto di output alla pipeline.

Se è necessario il parametro venga specificato un valore predefinito di `true` quando il parametro non viene specificato nella chiamata, provare a invertire il senso di parametro. Per esempio, anziché impostare l'attributo di parametro da un valore booleano `true`, dichiarare la proprietà come il [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) digitare e quindi impostare il valore predefinito del parametro da `false`.

Per definire un parametro opzionale, dichiarare la proprietà come il [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) digitare, come illustrato nell'esempio seguente.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Per rendere il cmdlet agire sul parametro quando viene specificato, usare la struttura seguente all'interno di uno degli input metodi di elaborazione.

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
