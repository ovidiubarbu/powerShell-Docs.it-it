---
title: Novità di PowerShell Core 6.2
description: Nuove funzionalità e modifiche rilasciate in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750052"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="358a5-103">Novità di PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="358a5-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="358a5-104">Di seguito è riportata una selezione di alcune delle nuove funzionalità e modifiche più importanti introdotte in PowerShell Core 6.2.</span><span class="sxs-lookup"><span data-stu-id="358a5-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="358a5-105">Sono state introdotte anche **moltissime** "cose noiose" che rendono PowerShell più veloce e più stabile, oltre ad altrettante correzioni di bug.</span><span class="sxs-lookup"><span data-stu-id="358a5-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="358a5-106">Per un elenco completo delle modifiche, consultare il [log delle modifiche](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="358a5-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="358a5-107">Riportiamo alcuni nomi di seguito, ma vogliamo ringraziare [tutti i collaboratori della community](https://github.com/PowerShell/PowerShell/graphs/contributors) che hanno reso possibile questa versione.</span><span class="sxs-lookup"><span data-stu-id="358a5-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="358a5-108">Aggiornamenti e correzioni del motore</span><span class="sxs-lookup"><span data-stu-id="358a5-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="358a5-109">Aggiunta di messaggi di avviso per il cmdlet di abilitazione/disabilitazione della comunicazione remota di PowerShell ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="358a5-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="358a5-110">Correzione per la regressione della deserializzazione remota `FormatTable` ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="358a5-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="358a5-111">Aggiornamento delle API `async` basate su attività aggiunte a PowerShell per restituire direttamente un oggetto Task ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="358a5-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="358a5-112">Aggiunta di 5 overload `InvokeAsync` e `StopAsync` al tipo `PowerShell` ([#8056][]) (grazie @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="358a5-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="358a5-113">Aggiornamenti e correzioni generali dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="358a5-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="358a5-114">Abilitazione dei cmdlet `SecureString` per sistemi non Windows archiviando il testo normale ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="358a5-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="358a5-115">Aggiunta del messaggio di obsolescenza a `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="358a5-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="358a5-116">Correzione di `Restart-Computer` per utilizzare `localhost` quando WinRM non è presente ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="358a5-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="358a5-117">Impostazione di `Start-Job` per la generazione di un errore fatale quando PowerShell è ospitato ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="358a5-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="358a5-118">Aggiornamento della versione per `PowerShell.Native` e test di hosting ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="358a5-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="358a5-119">Modifiche che causano un'interruzione</span><span class="sxs-lookup"><span data-stu-id="358a5-119">Breaking Changes</span></span>

<span data-ttu-id="358a5-120">Correzione del comportamento NoEnumerate in Write-Output per coerenza con Windows PowerShell ([#9069][]) (grazie @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="358a5-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
