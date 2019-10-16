---
title: Dichiarazione dell'attributo del cmdlet | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363540"
---
# <a name="cmdlet-attribute-declaration"></a>Dichiarazione dell'attributo Cmdlet

L'attributo cmdlet identifica una classe Microsoft .NET Framework come cmdlet e specifica il verbo e il sostantivo utilizzati per richiamare il cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parametri

`VerbName` ([System. String](/dotnet/api/System.String)) obbligatorio. Specifica il verbo del cmdlet. Questo verbo specifica l'azione eseguita dal cmdlet. Per altre informazioni sui verbi dei cmdlet approvati, vedere [nomi di verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md) e [linee guida per lo sviluppo necessarie](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) obbligatorio. Specifica il nome del cmdlet. Questo sostantivo specifica la risorsa su cui agisce il cmdlet. Per altre informazioni sui sostantivi dei cmdlet, vedere [dichiarazione di cmdlet](./cmdlet-class-declaration.md) e [linee guida per lo sviluppo fortemente consigliate](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il cmdlet supporta le chiamate al metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , che fornisce al cmdlet un modo per richiedere all'utente prima che venga eseguita un'azione che modifica il sistema. `False`, il valore predefinito, indica che il cmdlet non supporta le chiamate al metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Per ulteriori informazioni sulle richieste di conferma, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) parametro denominato facoltativo. Specifica quando l'azione del cmdlet deve essere confermata da una chiamata al metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) verrà chiamato solo quando il valore ConfirmImpact del cmdlet (per impostazione predefinita, Medium) è uguale o maggiore del valore della variabile `$ConfirmPreference`. Questo parametro deve essere specificato solo quando viene specificato il parametro `SupportsShouldProcess`.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) parametro denominato facoltativo. Specifica il set di parametri predefinito che il runtime di Windows PowerShell tenta di utilizzare quando non è in grado di determinare il set di parametri da utilizzare. Si noti che questa situazione può essere eliminata impostando il parametro Unique di ogni parametro come parametro obbligatorio.

Un caso in cui Windows PowerShell non è in grado di utilizzare il set di parametri predefinito anche se viene specificato un nome predefinito del set di parametri. Il runtime di Windows PowerShell non è in grado di distinguere tra set di parametri basati esclusivamente sul tipo di oggetto. Se, ad esempio, si dispone di un set di parametri che accetta una stringa come percorso del file e un altro set che accetta direttamente un oggetto **FileInfo** , Windows PowerShell non è in grado di determinare quale set di parametri utilizzare in base ai valori passati al cmdlet, né di utilizzare il cmdlet set di parametri predefinito. In questo caso, anche se si specifica un nome predefinito per il set di parametri, Windows PowerShell genera un messaggio di errore di set di parametri ambiguo.

`SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. `True` indica che il cmdlet può essere utilizzato all'interno di una transazione. Quando si specifica `True`, il runtime di Windows PowerShell aggiunge il parametro `UseTransaction` all'elenco di parametri del cmdlet. `False`, il valore predefinito, indica che non è possibile utilizzare il cmdlet all'interno di una transazione.

## <a name="remarks"></a>Osservazioni

- Insieme, il verbo e il sostantivo vengono usati per identificare il cmdlet registrato e per richiamare il cmdlet all'interno di uno script.

- Quando il cmdlet viene richiamato dalla console di Windows PowerShell, il comando è simile al seguente:

**Verboname-NounName**

- Tutti i cmdlet che modificano le risorse all'esterno di Windows PowerShell devono includere la parola chiave `SupportsShouldProcess` quando viene dichiarato l'attributo del cmdlet, che consente al cmdlet di chiamare il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) prima di consente di eseguire l'azione. Se la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) restituisce `false`, l'azione non deve essere eseguita. Per ulteriori informazioni sulle richieste di conferma generate dalla chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

I parametri del cmdlet `Confirm` e `WhatIf` sono disponibili solo per i cmdlet che supportano le chiamate a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .

## <a name="example"></a>Esempio

La definizione di classe seguente usa l'attributo cmdlet per identificare la classe .NET Framework per un cmdlet **Get-proc** che recupera le informazioni sui processi in esecuzione nel computer locale.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Per altre informazioni sul cmdlet **Get-proc** , vedere [esercitazione GetProc](./getproc-tutorial.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
