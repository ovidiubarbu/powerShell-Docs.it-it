---
title: Richiesta di conferma dai cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369530"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Richiesta di conferma dai cmdlet

I cmdlet devono richiedere una conferma quando stanno per apportare una modifica al sistema che si trova al di fuori dell'ambiente di Windows PowerShell. Se, ad esempio, un cmdlet sta per aggiungere un account utente o arrestare un processo, il cmdlet deve richiedere una conferma da parte dell'utente prima di procedere. Al contrario, se un cmdlet sta per modificare una variabile di Windows PowerShell, non è necessario che il cmdlet richieda la conferma.

Per eseguire una richiesta di conferma, il cmdlet deve indicare che supporta le richieste di conferma ed è necessario chiamare i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (facoltativo) per visualizzare un messaggio di richiesta di conferma.

## <a name="supporting-confirmation-requests"></a>Supporto delle richieste di conferma

Per supportare le richieste di conferma, il cmdlet deve impostare il parametro `SupportsShouldProcess` dell'attributo cmdlet su `true`. In questo modo vengono abilitati i parametri del cmdlet `Confirm` e `WhatIf` forniti da Windows PowerShell. Il `Confirm` parametro consente all'utente di controllare se la richiesta di conferma viene visualizzata. Il `WhatIf` parametro consente all'utente di determinare se il cmdlet deve visualizzare un messaggio o eseguire l'azione. Non aggiungere manualmente i parametri `Confirm` e `WhatIf` a un cmdlet.

Nell'esempio seguente viene illustrata una dichiarazione di attributo cmdlet che supporta le richieste di conferma.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Chiamata dei metodi di richiesta di conferma

Nel codice del cmdlet chiamare il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) prima che venga eseguita l'operazione che modifica il sistema. Progettare il cmdlet in modo che se la chiamata restituisce un valore di `false`, l'operazione non viene eseguita e il cmdlet elabora l'operazione successiva.

## <a name="calling-the-shouldcontinue-method"></a>Chiamata al metodo ShouldContinue

La maggior parte dei cmdlet richiede la conferma usando solo il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Tuttavia, alcuni casi potrebbero richiedere una conferma aggiuntiva. In questi casi, integrare la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) con una chiamata al metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Ciò consente al cmdlet o al provider di controllare in modo più accurato l'ambito della risposta **Sì** alla richiesta di conferma.

Se un cmdlet chiama il metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , il cmdlet deve fornire anche un parametro `Force` switch. Se l'utente specifica `Force` quando l'utente richiama il cmdlet, il cmdlet deve comunque chiamare [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), ma deve ignorare la chiamata a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) genererà un'eccezione quando viene chiamata da un ambiente non interattivo in cui l'utente non può essere richiesto. L'aggiunta di un parametro di `Force` garantisce che il comando possa essere ancora eseguito quando viene richiamato in un ambiente non interattivo.

Nell'esempio seguente viene illustrato come chiamare [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Il comportamento di una chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) può variare a seconda dell'ambiente in cui viene richiamato il cmdlet. Utilizzando le linee guida precedenti, è possibile garantire che il cmdlet si comporterà in modo coerente con altri cmdlet, indipendentemente dall'ambiente host.

Per un esempio di chiamata al metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , vedere [come richiedere le conferme](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Specificare il livello di effetto

Quando si crea il cmdlet, specificare il livello di effetto (gravità) della modifica. A tale scopo, impostare il valore del parametro `ConfirmImpact` dell'attributo cmdlet su High, medium o low. È possibile specificare un valore per `ConfirmImpact` solo quando si specifica anche il parametro `SupportsShouldProcess` per il cmdlet.

Per la maggior parte dei cmdlet, non è necessario specificare in modo esplicito `ConfirmImpact`.  Usare invece l'impostazione predefinita del parametro, che è medio. Se si imposta `ConfirmImpact` su High, l'operazione verrà confermata per impostazione predefinita. Riservare questa impostazione per le azioni estremamente problematiche, ad esempio la riformattazione di un volume del disco rigido.

## <a name="calling-non-confirmation-methods"></a>Chiamata di metodi non di conferma

Se il cmdlet o il provider deve inviare un messaggio ma non richiedere la conferma, può chiamare i tre metodi seguenti. Evitare di usare il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) per inviare messaggi di questi tipi perché l'output [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) è mescolato al normale output del cmdlet o del provider, rendendo difficile la scrittura di script.

- Per prestare attenzione all'utente e continuare con l'operazione, il cmdlet o il provider può chiamare il metodo [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

- Per fornire informazioni aggiuntive che l'utente può recuperare utilizzando il `Verbose` parametro, il cmdlet o il provider può chiamare il metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

- Per fornire dettagli a livello di debug per altri sviluppatori o per il supporto del prodotto, il cmdlet o il provider può chiamare il metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . L'utente può recuperare queste informazioni usando il parametro `Debug`.

I cmdlet e i provider chiamano prima di tutto i metodi seguenti per richiedere la conferma prima di provare a eseguire un'operazione che modifica un sistema all'esterno di Windows PowerShell:

- [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

A tale scopo, chiama il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , che richiede all'utente di confermare l'operazione in base alla modalità con cui l'utente ha richiamato il comando.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
