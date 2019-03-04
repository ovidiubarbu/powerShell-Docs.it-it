---
title: Richiesta di conferma dal cmdlet | Microsoft Docs
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
ms.openlocfilehash: ec441831f5e3231a44c9875d1b6d2bf6280a6965
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853397"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Richiesta di conferma dai cmdlet

I cmdlet devono richiedere conferma quando si sta tentando di apportare una modifica al sistema di fuori dell'ambiente di Windows PowerShell. Ad esempio, se un cmdlet sta per aggiungere un account utente o arrestare un processo, il cmdlet richiede conferma da parte dell'utente prima di procedere. Al contrario, se un cmdlet sta per essere modificata una variabile di Windows PowerShell, il cmdlet non dovrà richiedere la conferma.

Per poter effettuare una richiesta di conferma, il cmdlet deve indicare che supporta le richieste di conferma e deve chiamare il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi (facoltativi) per visualizzare un messaggio di richiesta di conferma.

## <a name="supporting-confirmation-requests"></a>Supporta le richieste di conferma

Per supportare le richieste di conferma, è necessario impostare il cmdlet di `SupportsShouldProcess` parametro dell'attributo Cmdlet `true`. In questo modo, il `Confirm` e `WhatIf` parametri del cmdlet forniti da Windows PowerShell. Il `Confirm` parametro consente all'utente di controllare se viene visualizzata la richiesta di conferma. Il `WhatIf` parametro consente all'utente determinare se il cmdlet deve visualizzare un messaggio o eseguire l'azione corrispondente. Non aggiungere manualmente il `Confirm` e `WhatIf` parametri a un cmdlet.

Nell'esempio seguente mostra una dichiarazione di attributo Cmdlet che supporta le richieste di conferma.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Chiamare i metodi di richiesta di conferma

Nel codice di cmdlet, chiamare il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo prima di eseguita l'operazione che modifica il sistema. Progettare il cmdlet in modo che se la chiamata restituisce un valore di `false`, non viene eseguita l'operazione e il cmdlet elabora l'operazione successiva.

## <a name="calling-the-shouldcontinue-method"></a>La chiamata al metodo ShouldContinue

La maggior parte dei cmdlet di richiedere conferma usando solo il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (metodo). Alcuni casi potrebbero tuttavia richiedere conferma aggiuntiva. In questi casi, integrare il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamata con una chiamata ai [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (metodo). In questo modo il cmdlet o il provider l'ambito di un controllo più più preciso il **Sì a tutto** risposta alla richiesta di conferma.

Se un cmdlet chiama il [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo, il cmdlet necessario fornire anche un `Force` parametro opzionale. Se l'utente specifica `Force` quando l'utente richiama il cmdlet, il cmdlet deve comunque chiamare [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), ma deve ignorare la chiamata a [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) genererà un'eccezione quando viene chiamato da un ambiente interattivo in cui non è possibile richiedere all'utente. Aggiunta di un `Force` parametro assicura che il comando può comunque essere eseguito quando viene richiamato in un ambiente interattivo.

Nell'esempio seguente viene illustrato come chiamare [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Il comportamento di un [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamata può variare a seconda dell'ambiente in cui viene richiamato il cmdlet. Usando le linee guida precedenti contribuirà a garantire che il cmdlet si comporti in modo coerente con altri cmdlet, indipendentemente dall'ambiente host.

Per un esempio della chiamata al metodo il [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo, vedere [come richiedere conferme](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Specificare il livello di impatto

Quando si crea il cmdlet, specificare il livello di impatto (gravità) della modifica. A tale scopo, impostare il valore della `ConfirmImpact` parametro dell'attributo Cmdlet alta, Media o bassa. È possibile specificare un valore per `ConfirmImpact` solo quando è specificare anche il `SupportsShouldProcess` parametro del cmdlet.

Per la maggior parte dei cmdlet, non è necessario specificare in modo esplicito `ConfirmImpact`.  In alternativa, usare l'impostazione predefinita del parametro, ovvero Medium. Se si imposta `ConfirmImpact` sul livello più alto, l'operazione verrà confermata per impostazione predefinita. Riservare questa impostazione per le azioni altamente arresto improvviso, ad esempio la riformattazione di un volume di disco rigido.

## <a name="calling-non-confirmation-methods"></a>Chiamata di metodi Non conferma

Se il cmdlet o il provider deve inviare un messaggio ma non richiedere conferma, può chiamare i tre metodi seguenti. Evitare di usare la [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metodo per inviare messaggi di questi tipi, poiché [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) output è mescolato con l'output normale del cmdlet o del provider, difficile la scrittura di script.

- Per l'utente di attenzione e continuare con l'operazione, è possibile chiamare il cmdlet o il provider di [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) (metodo).

- Per fornire informazioni aggiuntive che l'utente potrà recuperarlo usando il `Verbose` parametro, il cmdlet o il provider può chiamare le [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (metodo).

- Per fornire dettagli a livello di debug per gli altri sviluppatori o per il supporto tecnico, è possibile chiamare il cmdlet o il provider di [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) (metodo). L'utente può recuperare queste informazioni usando il `Debug` parametro.

Cmdlet e provider prima chiamata dei metodi seguenti per richiedere conferma prima di tentare di eseguire un'operazione che modifica un sistema all'esterno di Windows PowerShell:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

A tale scopo, chiamare il [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo, che richiede all'utente di confermare l'operazione di base sul modo in cui l'utente ha richiamato il comando.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
