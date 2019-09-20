---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Flusso di informazioni
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147611"
---
# <a name="information-stream"></a>Flusso di informazioni

In PowerShell 5.0 è stato aggiunto un nuovo flusso di **informazioni** strutturate per trasmettere dati strutturati tra uno script e il relativo host. `Write-Host` è stato inoltre aggiornato per generare l'output nel flusso di **informazioni** in cui è ora possibile acquisirlo o disattivarlo. Il nuovo cmdlet `Write-Information` usato con i parametri comuni **InformationVariable** e **InformationAction** consente miglioramenti a livello di flessibilità e funzionalità.

La funzione seguente usa i cmdlet che sfruttano il nuovo flusso di **informazioni**.

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

Gli esempi seguenti mostrano i risultati dell'esecuzione di questa funzione.

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

La variabile `$r` ha acquisito le informazioni sul processo nella variabile script `$p`.

```powershell
$r.Id
4008
```

A differenza del cmdlet `Write-Host`, l'uso del parametro **InformationVariable** di `Write-Information` consente di acquisire l'output in una variabile. Usando **Tag** è possibile creare canali separati per i messaggi inviati al flusso di **informazioni**.

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

Quando si invia un messaggio al flusso di **informazioni** con un tag, tale messaggio non viene visualizzato nell'applicazione host, ma può essere recuperato tramite il nome del tag. Ad esempio:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```