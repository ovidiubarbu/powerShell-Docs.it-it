---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Flusso di informazioni
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147611"
---
# <a name="information-stream"></a><span data-ttu-id="7b39d-103">Flusso di informazioni</span><span class="sxs-lookup"><span data-stu-id="7b39d-103">Information Stream</span></span>

<span data-ttu-id="7b39d-104">In PowerShell 5.0 è stato aggiunto un nuovo flusso di **informazioni** strutturate per trasmettere dati strutturati tra uno script e il relativo host.</span><span class="sxs-lookup"><span data-stu-id="7b39d-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="7b39d-105">`Write-Host` è stato inoltre aggiornato per generare l'output nel flusso di **informazioni** in cui è ora possibile acquisirlo o disattivarlo.</span><span class="sxs-lookup"><span data-stu-id="7b39d-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="7b39d-106">Il nuovo cmdlet `Write-Information` usato con i parametri comuni **InformationVariable** e **InformationAction** consente miglioramenti a livello di flessibilità e funzionalità.</span><span class="sxs-lookup"><span data-stu-id="7b39d-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="7b39d-107">La funzione seguente usa i cmdlet che sfruttano il nuovo flusso di **informazioni**.</span><span class="sxs-lookup"><span data-stu-id="7b39d-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="7b39d-108">Gli esempi seguenti mostrano i risultati dell'esecuzione di questa funzione.</span><span class="sxs-lookup"><span data-stu-id="7b39d-108">The following examples show the results of running this function.</span></span>

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

<span data-ttu-id="7b39d-109">La variabile `$r` ha acquisito le informazioni sul processo nella variabile script `$p`.</span><span class="sxs-lookup"><span data-stu-id="7b39d-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="7b39d-110">A differenza del cmdlet `Write-Host`, l'uso del parametro **InformationVariable** di `Write-Information` consente di acquisire l'output in una variabile.</span><span class="sxs-lookup"><span data-stu-id="7b39d-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="7b39d-111">Usando **Tag** è possibile creare canali separati per i messaggi inviati al flusso di **informazioni**.</span><span class="sxs-lookup"><span data-stu-id="7b39d-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="7b39d-112">Quando si invia un messaggio al flusso di **informazioni** con un tag, tale messaggio non viene visualizzato nell'applicazione host, ma può essere recuperato tramite il nome del tag.</span><span class="sxs-lookup"><span data-stu-id="7b39d-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="7b39d-113">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="7b39d-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```