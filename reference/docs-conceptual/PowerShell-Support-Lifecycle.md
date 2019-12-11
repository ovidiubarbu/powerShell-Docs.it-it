---
title: Ciclo di vita del supporto di PowerShell Core
description: Criteri che disciplinano il supporto per PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 27738514fc84105a0339eafcdbb540b7d3790052
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416292"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo di vita del supporto di PowerShell Core

PowerShell Core è un set distinto di strumenti e componenti che viene fornito, installato e configurato separatamente da Windows PowerShell. PowerShell Core non è pertanto incluso nei contratti di licenza di Windows 7/8.1/10 o Windows Server.

PowerShell Core è tuttavia supportato nei contratti di supporto Microsoft tradizionali, tra cui [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] e [Microsoft Software Assurance][assurance].
È anche possibile acquistare il [supporto assistito][] per PowerShell Core inviando una richiesta di supporto per il problema riscontrato.

## <a name="community-support"></a>Supporto della community

È inoltre disponibile il [supporto della community][] in GitHub dove è possibile segnalare un problema o un bug oppure inviare una richiesta di funzionalità.
È anche possibile ottenere assistenza da altri membri della community in Microsoft [PowerShell Tech Community][] o in uno dei forum elencati nella sezione community della pagina hub di [PowerShell][pshub]. Microsoft non offre garanzie che il problema verrà affrontato o risolto in modo tempestivo dalla community. Nel caso di un problema che richieda attenzione immediata è consigliabile usare le tradizionali opzioni di supporto a pagamento.

## <a name="lifecycle-of-powershell-core"></a>Ciclo di vita di PowerShell Core

PowerShell Core adotta i [Criteri moderni Microsoft relativi al ciclo di vita][modern]. Questo ciclo di vita del supporto è stato pensato per mantenere i clienti sempre aggiornati con le versioni più recenti.

Il ramo della versione 6.x di PowerShell Core verrà aggiornato approssimativamente ogni sei mesi (ad esempio, 6.0, 6.1, 6.2 e così via).

> [!IMPORTANT]
> Per continuare a ricevere il supporto è necessario eseguire l'aggiornamento entro sei mesi dal rilascio di ogni nuova versione secondaria.

Ad esempio, se PowerShell Core 6.1 viene rilasciato il 1° luglio 2018, sarà necessario eseguire l'aggiornamento a PowerShell Core 6.1 entro il 1° gennaio 1 2019 per mantenere il supporto.

> [!IMPORTANT]
> Per continuare a ricevere il supporto, è necessario eseguire l'aggiornamento entro 30 giorni dal rilascio di ogni nuova versione di patch.

Ad esempio, se si esegue PowerShell Core 6.1 e la versione 6.1.3 è stata rilasciata il 19 febbraio 2019, per mantenere il supporto occorre eseguire l'aggiornamento a PowerShell Core 6.1.3 entro il 21 marzo 2019, ovvero 30 giorni dopo il rilascio. Se vengono trovate correzioni richieste, queste verranno rilasciate nell'aggiornamento cumulativo successivo.

Nei Criteri moderni relativi al ciclo di vita viene anche indicato che Microsoft segnalerà ai clienti il termine del supporto per un prodotto (ad esempio, PowerShell Core) con un preavviso di 12 mesi.

Infine, è previsto che per PowerShell Core verrà adottato l'approccio di tipo LTS (Long Term Servicing), ovvero manutenzione a lungo termine. Con questo approccio, verranno inclusi nel supporto solo gli aggiornamenti di manutenzione e di sicurezza per un determinato ramo/versione di 6.x.

## <a name="supported-platforms"></a>Piattaforme supportate

Per verificare se la piattaforma e la versione di PowerShell Core sono ufficialmente supportate, vedere la tabella seguente.

La nostra community ha anche reso disponibili pacchetti per alcune piattaforme, ma non sono ufficialmente supportati. Questi pacchetti sono contrassegnati come `Community` nella tabella.

Le piattaforme elencate come `Experimental` non sono ufficialmente supportate, ma sono disponibili per la sperimentazione e per l'invio di commenti e suggerimenti.

| Piattaforma                                          |      6.2      |    7.0    |
|---------------------------------------------------|:-------------:|:---------:|
| Windows 7, 8.1 e 10                            |   Funzionalità supportata   | Funzionalità supportata |
| Windows Server 2008 R2, 2012 R2, 2016             |   Funzionalità supportata   | Funzionalità supportata |
| [Canale semestrale di Windows Server][semi-annual] |   Funzionalità supportata   | Funzionalità supportata |
| Ubuntu 16.04 e 18.04                            |   Funzionalità supportata   | Funzionalità supportata |
| Ubuntu 18.10 (tramite pacchetto Snap)                   |   Community   | Community |
| Ubuntu 19.04 (tramite pacchetto Snap)                   |   Community   | Community |
| Debian 9                                          |   Funzionalità supportata   | Funzionalità supportata |
| Debian 10                                         | Non Supportato | Funzionalità supportata |
| CentOS 7                                          |   Funzionalità supportata   | Funzionalità supportata |
| Red Hat Enterprise Linux 7                        |   Funzionalità supportata   | Funzionalità supportata |
| openSUSE 42.3                                     |   Funzionalità supportata   | Funzionalità supportata |
| Fedora 28                                         |   Funzionalità supportata   | Funzionalità supportata |
| Fedora 29, 30                                     | Non Supportato | Funzionalità supportata |
| Alpine 3.8                                        |   Vedere la nota    | Vedere la nota  |
| Alpine 3.9 e 3.10                               | Non Supportato | Vedere la nota  |
| macOS 10.12+                                      |   Funzionalità supportata   | Funzionalità supportata |
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

In base al [ciclo di vita di PowerShell Core](#lifecycle-of-powershell-core), la tabella seguente elenca le date in cui non saranno più supportate le varie versioni.

| Versione | Fine del ciclo di vita                   |
|---------|-------------------------------|
| 6.0     | 13 febbraio 2019             |
| 6.1     | 28 settembre 2019            |
| 6.2     | 6 mesi dopo le versioni 7     |

## <a name="unsupported-platforms"></a>Piattaforme non supportate

Quando una versione di una piattaforma raggiunge la fine del ciclo di vita come definito dal proprietario della piattaforma, anche PowerShell Core interromperà il supporto per tale versione. I pacchetti rilasciati in precedenza rimarranno disponibili per i clienti che devono accedervi, ma non verranno più forniti il supporto formale e gli aggiornamenti di qualsiasi tipo.

Pertanto, il supporto per le versioni seguenti è stato terminato dai proprietari della distribuzione e tali versioni non sono più supportate.

| Piattaforma | Versione | Fine vita                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Agosto 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Dicembre 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maggio 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Maggio 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Gennaio 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Luglio 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Gennaio 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Luglio 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Giugno 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Novembre 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Aprile 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Note sulla licenza

PowerShell Core viene rilasciato con la [licenza MIT][]. In base a questa licenza e in assenza di un contratto di supporto a pagamento, il supporto per gli utenti è limitato al [supporto della community][]. Con il supporto della community, Microsoft non garantisce velocità di risposta o correzioni.

## <a name="windows-powershell-module"></a>Modulo Windows PowerShell

Il supporto per PowerShell Core non include altri moduli del prodotto, a meno che questi non supportino in modo esplicito PowerShell Core. Ad esempio, l'uso del modulo `ActiveDirectory`, incluso in Windows Server, è uno scenario non supportato.

Tuttavia, i moduli che non supportano in modo esplicito PowerShell Core possono essere compatibili in alcuni casi. Installando il modulo [WindowsPSModulePath][] è possibile aggiungere `PSModulePath` di Windows PowerShell a `PSModulePath` di PowerShell Core.

Installare prima il modulo **WindowsPSModulePath** da PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Dopo l'installazione di questo modulo, eseguire il cmdlet `Add-WindowsPSModulePath` per aggiungere `PSModulePath` di Windows PowerShell a PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Funzionalità sperimentali

Le [funzionalità sperimentali][] sono limitate al [supporto della community](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[supporto della community]: https://github.com/powershell/powershell/issues
[pshub]: https://docs.microsoft.com/powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[supporto assistito]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licenza MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Funzionalità sperimentali]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
