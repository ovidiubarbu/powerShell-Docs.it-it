---
ms.openlocfilehash: 034d75a84e39cb0cf88a272ca58b5ccc229c5d9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540453"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Codice di condotta Microsoft Open Source

Per questo progetto è stato adottato [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) (Codice di condotta Microsoft Open Source). Per altre informazioni, vedere [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) (Domande frequenti sul codice di condotta) oppure contattare [opencode@microsoft.com](mailto:opencode@microsoft.com) per eventuali domande o commenti.

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a>Stato della compilazione

| Ramo attivo | Ramo di staging |
|:------------|:---------------|
| [![live-badge][]][live-badge] | [![staging-badge][]][staging-badge]

## <a name="powershell-documentation"></a>Documentazione di PowerShell

Questo è il repository PowerShell-Docs, che contiene la documentazione ufficiale di PowerShell.

## <a name="repository-structure"></a>Struttura del repository

Ognuna delle cartelle di primo livello seguenti in questo repository contiene un set di documenti pubblicato in [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/reference/](https://docs.microsoft.com/powershell/scripting/) per argomenti concettuali relativi a PowerShell e informazioni di riferimento sui moduli per le versioni 5.1, 6.0 e 7.0. Questo contenuto è anche l'origine del contenuto della Guida recuperato tramite il cmdlet `Get-Help`.
  - [docs-Conceptual/](https://docs.microsoft.com/powershell): questa cartella contiene la documentazione concettuale e i docset seguenti:
    - [developer/](https://docs.microsoft.com/powershell/scripting/developer/) è la documentazione di PowerShell SDK (migrata da MSDN)
    - [dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) per la funzionalità Configurazione dello stato desiderato (DSC, Desired State Configuration)
    - [gallery/](https://docs.microsoft.com/powershell/scripting/gallery) per [PowerShell Gallery](https://www.powershellgallery.com/)
    - [jea/](https://docs.microsoft.com/powershell/scripting/jea/) per la funzionalità JEA (Just Enough Administration)
    - [wmf/](https://docs.microsoft.com/powershell/scripting/wmf/overview) contiene le note sulla versione per Windows Management Framework, il pacchetto usato per distribuire le nuove versioni di PowerShell nelle versioni precedenti di Windows.

## <a name="contributing"></a>Contributi

I contributi vengono aggiunti attivamente a questo repository tramite [richiesta pull](https://help.github.com/articles/using-pull-requests/) nel ramo di *staging*.
Si noti che prima di inviare una richiesta pull è necessario [firmare un contratto di licenza per i contributi](https://cla.microsoft.com/) in modo che la community possa liberamente usare i contributi inviati.

Per altre informazioni sui contributi, leggere la [guida per i collaboratori](https://docs.microsoft.com/contribute/powershell/powershell-contribute). La guida per i collaboratori contiene informazioni dettagliate su come contribuire alla documentazione, sugli strumenti suggeriti, nonché sui requisiti di stile e di formattazione. Usare i modelli per i problemi e le richieste di pull per garantire la coerenza della documentazione tra le varie versioni.

## <a name="licenses"></a>Licenze

Sono disponibili due file di licenza per questo progetto. La licenza MIT si applica al codice contenuto in questo repository. La licenza Creative Commons si applica alla documentazione.