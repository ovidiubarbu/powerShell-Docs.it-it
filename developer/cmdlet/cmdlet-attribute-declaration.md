---
title: Dichiarazione di attributo cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058029"
---
# <a name="cmdlet-attribute-declaration"></a>Dichiarazione dell'attributo Cmdlet

L'attributo Cmdlet identifica una classe di Microsoft .NET Framework come un cmdlet e specifica il verbo e sostantivo utilizzato per richiamare il cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parametri

`VerbName` ([System. String](/dotnet/api/System.String)) richiesto. Specifica il verbo di cmdlet. Questo verbo specifica l'azione eseguita dal cmdlet. Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi di Cmdlet Verb](./approved-verbs-for-windows-powershell-commands.md) e [necessarie linee guida sullo sviluppo](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) richiesto. Specifica il nome di cmdlet. Il sostantivo specifica la risorsa che interviene il cmdlet. Per altre informazioni sui nomi di cmdlet, vedere [Cmdlet dichiarazione](./cmdlet-class-declaration.md) e [fortemente consigliabile linee guida sullo sviluppo](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il cmdlet supporta le chiamate per il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo, che offre un modo per richiedere all'utente prima di un'azione che modifica il sistema viene eseguita il cmdlet. `False`, il valore predefinito, indica che il cmdlet non supporta le chiamate per il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (metodo). Per altre informazioni sulle richieste di conferma, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) parametro denominato facoltativo. Specifica quando è necessario confermare l'azione del cmdlet da una chiamata per il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (metodo). [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) verrà chiamato solo quando il valore ConfirmImpact del cmdlet (impostazione predefinita è Medium) è uguale o maggiore del valore della `$ConfirmPreference` variabile. Questo parametro deve essere specificato solo quando il `SupportsShouldProcess` parametro è specificato.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) parametro denominato facoltativo. Specifica che il parametro predefinito impostato che il runtime di Windows PowerShell tenta di usare quando non è possibile determinare quale serie di parametri da usare. Si noti che questa situazione può essere eliminata, rendendo il parametro unique di ogni parametro di impostare un parametro obbligatorio.

C'è un caso in cui Windows PowerShell non è possibile usare il parametro di predefinito impostato anche se viene specificato il nome di un set di parametri predefinito. Il runtime di Windows PowerShell non è possibile distinguere tra set di parametri basato esclusivamente sul tipo di oggetto. Ad esempio, se si dispone di un set di parametri che accetta una stringa come il percorso del file e impostare un altro che accetta un **FileInfo** direttamente l'oggetto, Windows PowerShell non è possibile determinare quale parametro impostato per l'utilizzo in base ai valori passati per il cmdlet, né per l'uso di set di parametri predefinito. In questo caso, anche se si specifica che un parametro predefinito set name, Windows PowerShell genera un messaggio di errore ambiguo parametro set.

`SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il cmdlet può essere usato all'interno di una transazione. Quando `True` viene specificato, il runtime di Windows PowerShell aggiunge il `UseTransaction` parametro all'elenco di parametri del cmdlet. `False`, il valore predefinito, indica che il cmdlet può essere usato all'interno di una transazione.

## <a name="remarks"></a>Osservazioni

- Insieme, il verbo e sostantivo vengono usati per identificare i cmdlet registrato e richiamare i cmdlet in uno script.

- Quando il cmdlet viene richiamato dalla console di Windows PowerShell, il comando è simile al comando seguente:

**VerbName-NounName**

- Devono includere tutti i cmdlet che modificano le risorse all'esterno di Windows PowerShell il `SupportsShouldProcess` parola chiave quando viene dichiarato l'attributo Cmdlet, che consente al cmdlet di chiamare il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo prima che il cmdlet esegue l'azione corrispondente. Se il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamata restituisce `false`, l'azione non deve essere assunta. Per altre informazioni sulle richieste di conferma generato dal [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamare, vedere [conferma che richiede](./requesting-confirmation-from-cmdlets.md).

Il `Confirm` e `WhatIf` i parametri del cmdlet sono disponibili solo per i cmdlet che supportano [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamate.

## <a name="example"></a>Esempio

La definizione di classe seguente usa l'attributo Cmdlet per identificare la classe di .NET Framework per un **Get-Proc** cmdlet che recupera le informazioni sui processi in esecuzione nel computer locale.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Per altre informazioni sul **Get-Proc** cmdlet, vedere [esercitazione GetProc](./getproc-tutorial.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
