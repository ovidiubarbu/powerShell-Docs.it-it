---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: Miglioramenti del motore di PowerShell in WMF 5.1
ms.openlocfilehash: 3c69c4e13f64683f743eb78b0c9e177ff5b3a771
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
#<a name="powershell-engine-improvements"></a>Miglioramenti apportati al motore di PowerShell

I miglioramenti seguenti apportati al motore di PowerShell principale sono stati implementati in WMF 5.1:


## <a name="performance"></a>Prestazioni ##

Le prestazioni sono migliorate in alcune aree importanti:

- Avvio
- Pipelining ai cmdlet quali ForEach-Object e Where-Object più veloce del 50% circa

Alcuni miglioramenti di esempio (i risultati possono variare in base all'hardware):

| Scenario | 5.0 - Tempo (ms) | 5.1 - Tempo (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Prima esecuzione di PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Cache di analisi del comando integrata: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> Nota: una modifica correlata all'avvio può avere impatto su alcuni scenari non supportati.
> PowerShell non legge i file `$pshome\*.ps1xml`: questi file sono stati convertiti in C# per evitare il sovraccarico dell'elaborazione di file XML da parte di alcuni file e della CPU.
I file supportano ancora V2 side-by-side, pertanto se si modifica il contenuto del file, la modifica non avrà alcun impatto su V5, ma solo su V2.
Si noti che la modifica dei contenuti di questi file non ha mai costituito uno scenario supportato.

Un'altra modifica evidente riguarda la modalità di memorizzazione nella cache dei comandi esportati e di altre informazioni relative ai moduli installati in un sistema da parte di PowerShell.
In precedenza, la cache veniva archiviata nella directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
In WMF 5.1, la cache è un singolo file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Per altre informazioni dettagliate, vedere [Modulo Analysis Cache](scenarios-features.md#module-analysis-cache).