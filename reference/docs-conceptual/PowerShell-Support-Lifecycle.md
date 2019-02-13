---
title: Ciclo di vita del supporto di PowerShell Core
description: Criteri che disciplinano il supporto per PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: cb1daf953b11ffba8f39bcc05a8b122350c497eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682959"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo di vita del supporto di PowerShell Core

PowerShell Core è un set distinto di strumenti e componenti che viene fornito, installato e configurato separatamente da Windows PowerShell.
Pertanto, PowerShell Core non è incluso in Windows 7/8.1/10 o Windows Server al contratto di licenza.

PowerShell Core è tuttavia supportato nei contratti di supporto Microsoft tradizionali, tra cui [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].
È anche possibile acquistare il [supporto assistito][] per PowerShell Core inviando una richiesta di supporto per il problema riscontrato.

È inoltre disponibile il [supporto della community][] in GitHub dove è possibile segnalare un problema o un bug oppure inviare una richiesta di funzionalità.
Inoltre, è possibile ricevere assistenza da altri membri della community nella pagina Generale [Microsoft Community][] o il Microsoft [PowerShell Tech Community][].
Microsoft non ci sono garanzie che la community verrà indirizzo o di risolvere il problema in modo tempestivo.
Nel caso di un problema che richieda attenzione immediata è consigliabile usare le tradizionali opzioni di supporto a pagamento.

## <a name="lifecycle-of-powershell-core"></a>Ciclo di vita di PowerShell Core

PowerShell Core adotta i [Criteri moderni Microsoft relativi al ciclo di vita][modern].
Questo ciclo di vita del supporto è stato pensato per mantenere i clienti sempre aggiornati con le versioni più recenti.

Il ramo della versione 6.x di PowerShell Core verrà aggiornato approssimativamente ogni sei mesi (esempi: 6.0, 6.1, 6.2, ecc.)

> [!IMPORTANT]
> Per continuare a ricevere il supporto è necessario eseguire l'aggiornamento entro sei mesi dal rilascio di ogni nuova versione secondaria.

Ad esempio, se PowerShell Core 6.1 viene rilasciato il 1 ° luglio 2018, dovrebbe eseguire l'aggiornamento a PowerShell Core 6.1 dal 1 ° gennaio 2019 per mantenere il supporto tecnico.

![Ciclo di vita del ramo PowerShell Core][lifecycle-chart]

I criteri del ciclo di vita moderni richiede inoltre che Microsoft offrire ai clienti preavviso di 12 mesi prima di sospendere il supporto per un prodotto (vale a dire, PowerShell Core).

Infine, prevediamo di PowerShell Core verrà adottato il "Long Term servicing" approccio.
Questo approccio per la manutenzione, richiede solo per la manutenzione e aggiornamenti della protezione al supporto per una determinato ramo/versione di 6.x.

## <a name="supported-platforms"></a>Piattaforme supportate

Nella tabella seguente per visualizzare la versione di PowerShell Core si usa la piattaforma è ufficialmente supportata.

La nostra community ha anche reso disponibili pacchetti per alcune piattaforme, ma non sono ufficialmente supportati.
Questi pacchetti sono contrassegnati come `Community` nella tabella.

Le piattaforme elencate come `Experimental` non sono ufficialmente supportate, ma sono disponibili per la sperimentazione e per l'invio di commenti e suggerimenti.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 e 10                            | Funzionalità supportata   | Funzionalità supportata   |
| Windows Server 2008 R2, 2012 R2, 2016             | Funzionalità supportata   | Funzionalità supportata   |
| [Canale semestrale di Windows Server][semi-annual] | Funzionalità supportata   | Funzionalità supportata   |
| Ubuntu 14.04 e 16.04                           | Funzionalità supportata   | Funzionalità supportata   |
| Ubuntu 18.04                                      |             | Funzionalità supportata   |
| Ubuntu 18.10 (tramite pacchetto Snap)                   |             | Community   |
| Debian 9                                          | Funzionalità supportata   | Funzionalità supportata   |
| CentOS 7                                          | Funzionalità supportata   | Funzionalità supportata   |
| Red Hat Enterprise Linux 7                        | Funzionalità supportata   | Funzionalità supportata   |
| openSUSE 42.3                                     | Funzionalità supportata   | Funzionalità supportata   |
| Fedora 28                                         |             | Funzionalità supportata   |
| macOS 10.12+                                      | Funzionalità supportata   | Funzionalità supportata   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Sperimentale| Community   |
| Kali                                              | Community   | Community   |
| AppImage (funziona su più piattaforme Linux)     | Community   | Community   |
| [Pacchetto Snap](https://snapcraft.io/powershell)   | Vedere la nota    | Vedere la nota    |

> [!NOTE]
> I pacchetti Snap saranno sperimentali per un determinato periodo di tempo.
> Successivamente, se come previsto Snap non introdurrà nuovi problemi di supporto, il supporto seguirà la distribuzione in cui è in esecuzione il pacchetto.

## <a name="powershell-release-end-of-life"></a>PowerShell versione finale del ciclo di vita

In base [ciclo di vita di PowerShell Core](#lifecycle-of-powershell-core), la tabella seguente elenca le date quando vari versione verrà non più supportato.

| Versione | Fine vita                   |
|---------|-------------------------------|
| 6.0     | 13 febbraio 2019             |
| 6.1     | 6 mesi dopo la 6.2 Release   |

## <a name="platforms-which-are-out-of-support"></a>Piattaforme, non supportati

Quando una versione della piattaforma raggiunge la fine del ciclo di vita come definito dal proprietario della piattaforma, PowerShell Core cesserà anche supportare tale versione della piattaforma.
I pacchetti rilasciati in precedenza rimarranno disponibili per i clienti che devono accedervi, ma non verranno più forniti il supporto formale e gli aggiornamenti di qualsiasi tipo.

Pertanto, i proprietari di distribuzione è terminato il supporto per le seguenti versioni e non sono supportati.

| Sistema operativo       | Versione | Fine vita                                                                                 |
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

## <a name="notes-on-licensing"></a>Note sulla licenza

PowerShell Core viene rilasciato con la [licenza MIT][].
Condizioni della presente licenza e senza un contratto di supporto a pagamento, gli utenti non possono superare [supporto della community][].
Con il supporto della community, Microsoft non garantisce velocità di risposta o correzioni.

## <a name="windows-powershell-module"></a>Modulo Windows PowerShell

Supporto per PowerShell Core non include i moduli di prodotto, a meno che tali moduli supportano in modo esplicito PowerShell Core.
Ad esempio, l'uso del modulo `ActiveDirectory`, incluso in Windows Server, è uno scenario non supportato.

Tuttavia, i moduli che non supportano in modo esplicito PowerShell Core possono essere compatibili in alcuni casi.
Installando i [ `WindowsPSModulePath` ][] modulo, è possibile aggiungere il comando di Windows PowerShell `PSModulePath` a di PowerShell Core `PSModulePath`.

Installare prima il modulo `WindowsPSModulePath` da PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Dopo l'installazione di questo modulo, eseguire il cmdlet `Add-WindowsPSModulePath` per aggiungere `PSModulePath` di Windows PowerShell a PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[supporto della community]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[supporto assistito]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licenza MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
