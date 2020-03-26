---
title: Ciclo di vita del supporto di PowerShell Core
description: Criteri che disciplinano il supporto per PowerShell Core
ms.date: 03/09/2020
ms.openlocfilehash: c1e91aa193dd4a6353098e16ae18301c0753ea85
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082401"
---
# <a name="powershell-support-lifecycle"></a>Ciclo di vita del supporto di PowerShell

PowerShell è un set distinto di strumenti e componenti che viene offerto, installato e configurato separatamente da Windows PowerShell. PowerShell non è incluso nei contratti di licenza di Windows.

PowerShell Core è supportato nei contratti di supporto Microsoft tradizionali, tra cui [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].
È anche possibile acquistare il [supporto assistito][] per PowerShell inviando una richiesta di supporto per il problema riscontrato.

## <a name="community-support"></a>Supporto della community

È inoltre disponibile il [supporto della community][] in GitHub dove è possibile segnalare un problema o un bug oppure inviare una richiesta di funzionalità.
È anche possibile ottenere assistenza da altri membri della community in Microsoft [PowerShell Tech Community][] o in uno dei forum elencati nella sezione community della pagina hub di [PowerShell][pshub]. Microsoft non offre garanzie che il problema verrà affrontato o risolto in modo tempestivo dalla community. Nel caso di un problema che richieda attenzione immediata è consigliabile usare le tradizionali opzioni di supporto a pagamento.

## <a name="lifecycle-of-powershell-7"></a>Ciclo di vita di PowerShell 7

Con il rilascio di PowerShell 7, PowerShell continua a essere supportato in base ai [nuovi criteri per il ciclo di vita Microsoft][modern], ma le date di supporto sono collegate al [ciclo di vita del supporto di .NET Core][Long-Term]. In questo approccio di manutenzione, i clienti possono scegliere tra versioni con supporto a lungo termine (LTS, Long Term Support) e versioni correnti. PowerShell 7.0 è una versione con supporto a lungo termine (LTS). Il supporto termina con il supporto di .NET Core 3.1. La versione LTS successiva seguirà i termini della versione LTS successiva di .NET Core. Per le date di fine supporto correnti, vedere la [tabella di fine del ciclo di vita delle versioni di PowerShell](#powershell-releases-end-of-life). Gli aggiornamenti delle versioni LTS includono solo correzioni e aggiornamenti critici per la sicurezza e la manutenzione, progettati per evitare o ridurre al minimo l'effetto sui carichi di lavoro esistenti.

Una versione corrente è una versione che viene introdotta tra una versione LTS e la successiva. Le versioni correnti possono contenere correzioni critiche, innovazioni e nuove funzionalità. Le versioni correnti sono supportate per tre mesi dopo la versione corrente o LTS successiva.

> [!IMPORTANT]
> Per disporre del supporto è necessario avere installato l'aggiornamento patch più recente. Se ad esempio si esegue PowerShell 7.0 ed è stata rilasciata la versione 7.0.1, è necessario eseguire l'aggiornamento a 7.0.1 per ottenere il supporto.

## <a name="lifecycle-of-powershell-core-6x"></a>Ciclo di vita di PowerShell Core 6.x

PowerShell Core usava i [Criteri moderni Microsoft relativi al ciclo di vita][modern]. Questo ciclo di vita del supporto è stato pensato per mantenere i clienti sempre aggiornati con le versioni più recenti.

Il ramo della versione 6.x di PowerShell Core veniva aggiornato approssimativamente ogni sei mesi (ad esempio, 6.0, 6.1, 6.2 e così via). Tuttavia, con il rilascio di PowerShell 7 non saranno più rilasciate versioni secondarie di 6.x. PowerShell 6.2.x continuerà a ricevere aggiornamenti del servizio mentre è ancora supportato.

> [!IMPORTANT]
> Per continuare a ricevere il supporto è necessario eseguire l'aggiornamento entro sei mesi dal rilascio di ogni nuova versione secondaria.

Ad esempio, se PowerShell Core 6.1 viene rilasciato il 1° luglio 2018, sarà necessario eseguire l'aggiornamento a PowerShell Core 6.1 entro il 1° gennaio 1 2019 per mantenere il supporto.

> [!IMPORTANT]
> Per continuare a ricevere il supporto, è necessario eseguire l'aggiornamento entro 30 giorni dal rilascio di ogni nuova versione di patch.

Ad esempio, se si esegue PowerShell Core 6.1 e la versione 6.1.3 è stata rilasciata il 19 febbraio 2019, per mantenere il supporto occorre eseguire l'aggiornamento a PowerShell Core 6.1.3 entro il 21 marzo 2019, ovvero 30 giorni dopo il rilascio. Se vengono trovate correzioni richieste, queste verranno rilasciate nell'aggiornamento cumulativo successivo.

Nei Criteri moderni relativi al ciclo di vita viene anche indicato che Microsoft segnalerà ai clienti il termine del supporto per un prodotto (ad esempio, PowerShell Core) con un preavviso di 12 mesi.

## <a name="supported-platforms"></a>Piattaforme supportate

Per verificare se la piattaforma e la versione di PowerShell Core sono ufficialmente supportate, vedere la tabella seguente.

La nostra community ha anche reso disponibili pacchetti per alcune piattaforme, ma non sono ufficialmente supportati. Questi pacchetti sono contrassegnati come `Community` nella tabella.

Le piattaforme elencate come `Experimental` non sono ufficialmente supportate, ma sono disponibili per la sperimentazione e per l'invio di commenti e suggerimenti.

| Piattaforma                                          |      6.2      |    7.0    |
| ------------------------------------------------- | :-----------: | :-------: |
| Windows 8.1 e 10                               |   Supportato   | Supportato |
| Windows Server 2012 R2, 2016                      |   Supportato   | Supportato |
| [Canale semestrale di Windows Server][semi-annual] |   Supportato   | Supportato |
| Ubuntu 16.04 e 18.04                            |   Supportato   | Supportato |
| Ubuntu 19.10 (tramite pacchetto Snap)                   |   Community   | Community |
| Ubuntu 20.04 (tramite pacchetto Snap)                   |   Community   | Community |
| Debian 9                                          |   Supportato   | Supportato |
| Debian 10                                         | Non supportato | Supportato |
| CentOS 7                                          |   Supportato   | Supportato |
| CentOS 8                                          | Non supportato | Supportato |
| Red Hat Enterprise Linux 7                        |   Supportato   | Supportato |
| Red Hat Enterprise Linux 8                        | Non supportato | Supportato |
| Fedora 30                                         | Non supportato | Supportato |
| Alpine 3.8                                        |   Vedere la nota    | Vedere la nota  |
| Alpine 3.9 e 3.10                               | Non supportato | Vedere la nota  |
| macOS 10.12+                                      |   Supportato   | Supportato |
| Arch                                              |   Community   | Community |
| Raspbian                                          |   Community   | Community |
| Kali                                              |   Community   | Community |
| AppImage (funziona su più piattaforme Linux)      |   Community   | Community |
| [Pacchetto Snap](https://snapcraft.io/powershell)   |   Vedere la nota    | Vedere la nota  |

> [!NOTE]
> I pacchetti Snap sono supportati come la distribuzione su cui si esegue il pacchetto.

> [!NOTE]
> CIM, la comunicazione remota di PowerShell e DSC non sono supportati in Alpine.

## <a name="powershell-releases-end-of-life"></a>Fine del ciclo di vita per le versioni di PowerShell

In base al [ciclo di vita di PowerShell](#lifecycle-of-powershell-7), la tabella seguente elenca le date in cui non saranno più supportate le varie versioni.

| Versione |    Fine del ciclo di vita     |
| :-----: | ------------------ |
|   7.0   | 3 dicembre 2022   |
|   6.2   | 4 settembre 2020  |
|   6.1   | 28 settembre 2019 |
|   6.0   | 13 febbraio 2019  |

## <a name="unsupported-platforms"></a>Piattaforme non supportate

Quando una versione di una piattaforma raggiunge la fine del ciclo di vita come definito dal proprietario della piattaforma, anche PowerShell Core interromperà il supporto per tale versione. I pacchetti rilasciati in precedenza rimarranno disponibili per i clienti che devono accedervi, ma non verranno più forniti il supporto formale e gli aggiornamenti di qualsiasi tipo.

Pertanto, il supporto per le versioni seguenti è stato terminato dai proprietari della distribuzione e tali versioni non sono più supportate.

|    Piattaforma    | Versione |                                                         Fine vita                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [Giugno 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [Agosto 2017](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [Dicembre 2017](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [Maggio 2018](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [Novembre 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [Maggio 2019](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42.1   | [Maggio 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42.2   | [Gennaio 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42.3   | [Luglio 2019](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14.04  | [Aprile 2019](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16.10  | [Luglio 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17.04  | [Gennaio 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17.10  | [Luglio 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [Gennaio 2020](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [Gennaio 2020](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>Note sulla licenza

PowerShell Core viene rilasciato con la [licenza MIT][]. In base a questa licenza e in assenza di un contratto di supporto a pagamento, il supporto per gli utenti è limitato al [supporto della community][]. Con il supporto della community, Microsoft non garantisce velocità di risposta o correzioni.

## <a name="windows-powershell-compatibility"></a>Compatibilità di Windows PowerShell

Il ciclo di vita del supporto per PowerShell non include i moduli disponibili all'esterno del pacchetto della versione PowerShell 7. Ad esempio l'uso del modulo `ActiveDirectory`, incluso in Windows Server, è supportato nel quadro del [Ciclo di vita del supporto di Windows][].

PowerShell 7 migliora la compatibilità con i moduli di PowerShell esistenti scritti per Windows PowerShell.
Per altre informazioni, vedere l'articolo [Informazioni sulla compatibilità di Windows][] e l'[elenco di compatibilità dei moduli][].

> [!NOTE]
> Il modulo [**WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) non è più necessario in PowerShell 7 e non è supportato.

## <a name="experimental-features"></a>Funzionalità sperimentali

Le [funzionalità sperimentali][] sono limitate al [supporto della community](#community-support).

## <a name="release-history"></a>Cronologia delle versioni

La tabella seguente contiene una sequenza temporale delle versioni principali di PowerShell, da usare come riferimento cronologico. Non è destinata all'uso per la determinazione del ciclo di vita del supporto.

|       Versione        | Data di rilascio |                                                                     Note                                                                      |
| -------------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| PowerShell 7.0 (LTS) |   Marzo 2020   | Basata su .NET Core 3.1 (LTS)                                                                                                                  |
| PowerShell 6.0       |   Gennaio 2018   | Prima versione, basata su .NET Core 2.1. Può essere installata su Windows, Linux e macOS.                                                              |
| PowerShell 5.1       |   Agosto 2016   | Rilasciata nell'aggiornamento dell'anniversario di Windows 10 e in Windows Server 2016                                                                             |
| PowerShell 5.0       |   Febbraio 2016   | Rilasciata in Windows Management Framework (WMF) 5.0                                                                                            |
| PowerShell 4.0       |   Ottobre 2013   | Integrata in Windows 8.1 e con Windows Server 2012 R2. Può essere installata su Windows Server 7 SP1, Windows Server 2008 R2 SP1 e Windows Server 2012. |
| PowerShell 3.0       |   Ottobre 2012   | Integrata in Windows 8 e con Windows Server 2012. Può essere installata su Windows 7 SP1, Windows Server 2008 SP1 e Windows Server 2008 R2 SP1.  |
| PowerShell 2.0       |   Luglio 2009   | Integrata in Windows 7 e con Windows Server 2008 R2. Può essere installata su Windows XP SP3, Windows Server 2003 SP2 e Windows Vista SP1.            |
| PowerShell 1.0       |   Novembre 2006   | Può essere installata su Windows XP SP2, Windows Server 2003 SP1 e Windows Vista. Componente facoltativo di Windows Server 2008.                          |

<!-- hyperlink references -->
[Premier]: https://www.microsoft.com/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[supporto della community]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[supporto assistito]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[licenza MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[Informazioni sulla compatibilità di Windows]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Ciclo di vita del supporto di Windows]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Elenco di compatibilità dei moduli]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Funzionalità sperimentali]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures
