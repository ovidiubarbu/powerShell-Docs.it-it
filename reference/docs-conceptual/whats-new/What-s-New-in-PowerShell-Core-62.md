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
# <a name="whats-new-in-powershell-core-62"></a>Novità di PowerShell Core 6.2

Di seguito è riportata una selezione di alcune delle nuove funzionalità e modifiche più importanti introdotte in PowerShell Core 6.2.

Sono state introdotte anche **moltissime** "cose noiose" che rendono PowerShell più veloce e più stabile, oltre ad altrettante correzioni di bug.
Per un elenco completo delle modifiche, consultare il [log delle modifiche](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) su GitHub.

Riportiamo alcuni nomi di seguito, ma vogliamo ringraziare [tutti i collaboratori della community](https://github.com/PowerShell/PowerShell/graphs/contributors) che hanno reso possibile questa versione.

## <a name="engine-updates-and-fixes"></a>Aggiornamenti e correzioni del motore

- Aggiunta di messaggi di avviso per il cmdlet di abilitazione/disabilitazione della comunicazione remota di PowerShell ([#9203][])
- Correzione per la regressione della deserializzazione remota `FormatTable` ([#9116][])
- Aggiornamento delle API `async` basate su attività aggiunte a PowerShell per restituire direttamente un oggetto Task ([#9079][])
- Aggiunta di 5 overload `InvokeAsync` e `StopAsync` al tipo `PowerShell` ([#8056][]) (grazie @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Aggiornamenti e correzioni generali dei cmdlet

- Abilitazione dei cmdlet `SecureString` per sistemi non Windows archiviando il testo normale ([#9199][])
- Aggiunta del messaggio di obsolescenza a `Send-MailMessage` ([#9178][])
- Correzione di `Restart-Computer` per utilizzare `localhost` quando WinRM non è presente ([#9160][])
- Impostazione di `Start-Job` per la generazione di un errore fatale quando PowerShell è ospitato ([#9128][])
- Aggiornamento della versione per `PowerShell.Native` e test di hosting ([#8983][])

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

Correzione del comportamento NoEnumerate in Write-Output per coerenza con Windows PowerShell ([#9069][]) (grazie @vexx32!)

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
