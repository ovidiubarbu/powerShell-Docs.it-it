---
title: Ciclo di vita del supporto di PowerShell Core
description: Criteri che disciplinano il supporto per PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403498"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo di vita del supporto di PowerShell Core

PowerShell Core è un set distinto di strumenti e componenti che viene fornito, installato e configurato separatamente da Windows PowerShell.
PowerShell Core non è pertanto incluso nei contratti di licenza di Windows 7/8.1/10 o Windows Server.

PowerShell Core è tuttavia supportato nei contratti di supporto Microsoft tradizionali, tra cui [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].
È anche possibile acquistare il [supporto assistito][] per PowerShell Core inviando una richiesta di supporto per il problema riscontrato.

È inoltre disponibile il [supporto della community][] in GitHub dove è possibile segnalare un problema o un bug oppure inviare una richiesta di funzionalità.
In alternativa, è possibile ricevere assistenza da altri membri della community nella pagina generale di [Microsoft Community][] o in Microsoft [PowerShell Tech Community][].
Non ci sono garanzie che il problema verrà affrontato o risolto in modo tempestivo.
Nel caso di un problema che richieda attenzione immediata è consigliabile usare le tradizionali opzioni di supporto a pagamento.

## <a name="lifecycle-of-powershell-core"></a>Ciclo di vita di PowerShell Core

PowerShell Core adotta i [Criteri moderni Microsoft relativi al ciclo di vita][modern].
Questo ciclo di vita del supporto è stato pensato per mantenere i clienti sempre aggiornati con le versioni più recenti.

Il ramo della versione 6.x di PowerShell Core verrà aggiornato approssimativamente ogni sei mesi (ad esempio, 6.0, 6.1, 6.2 e così via).

> [!IMPORTANT]
> Per continuare a ricevere il supporto è necessario eseguire l'aggiornamento entro sei mesi dal rilascio di ogni nuova versione secondaria.

Se ad esempio PowerShell Core 6.1 viene rilasciato il 1° luglio 2018, sarà necessario eseguire l'aggiornamento a PowerShell Core 6.1 entro il 1° gennaio 2019 per mantenere il supporto.

![Ciclo di vita del ramo PowerShell Core][lifecycle-chart]

Nei Criteri moderni relativi al ciclo di vita viene anche indicato che Microsoft comunicherà ai clienti il termine del supporto per un prodotto (ad esempio, PowerShell Core) con un preavviso di 12 mesi.

È probabile che in futuro per PowerShell Core verrà adottato l'approccio di tipo "Long Term Servicing" in cui il mantenimento del supporto per un determinato ramo/versione di 6.x richiede solo gli aggiornamenti di manutenzione e sicurezza.

## <a name="supported-platforms"></a>Piattaforme supportate

Vedere la tabella seguente per scoprire in quale piattaforma è ufficialmente supportata la versione di PowerShell Core in uso.

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
| Debian 8.7+ e 9                                | Funzionalità supportata   | Funzionalità supportata   |
| CentOS 7                                          | Funzionalità supportata   | Funzionalità supportata   |
| Red Hat Enterprise Linux 7                        | Funzionalità supportata   | Funzionalità supportata   |
| OpenSUSE 42.3                                     | Funzionalità supportata   | Funzionalità supportata   |
| Fedora 27                                         | Funzionalità supportata   | Funzionalità supportata   |
| Fedora 28                                         |             | Funzionalità supportata   |
| macOS 10.12+                                      | Funzionalità supportata   | Funzionalità supportata   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Sperimentale| Community   |
| Kali                                              | Community   | Community   |
| AppImage (funziona su più piattaforme Linux)     | Community   | Community   |
| [Pacchetto Snap](https://snapcraft.io/powershell)   | Vedere la nota    | Vedere la nota    |

> [!NOTE]
> I pacchetti Snap saranno sperimentali per un determinato periodo di tempo.  Successivamente, se come previsto Snap non introdurrà nuovi problemi di supporto, il supporto seguirà la distribuzione in cui è in esecuzione il pacchetto.

## <a name="platform-which-are-out-of-support"></a>Piattaforme non più supportate

Quando una versione di una piattaforma raggiunge la fine del ciclo di vita come definito dal proprietario della piattaforma, anche PowerShell Core interromperà il supporto per tale versione. I pacchetti rilasciati in precedenza rimarranno disponibili per i clienti che devono accedervi, ma non verranno più forniti il supporto formale e gli aggiornamenti di qualsiasi tipo.

Pertanto, il supporto per le versioni seguenti è stato terminato dai proprietari della distribuzione e tali versioni non sono più supportate.

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

## <a name="notes-on-licensing"></a>Note sulla licenza

PowerShell Core viene rilasciato con la [licenza MIT][].
In base a questa licenza e in assenza di un contratto di supporto a pagamento, il supporto per gli utenti è limitato al [supporto della community][].
Con il supporto della community, Microsoft non garantisce velocità di risposta o correzioni.

## <a name="windows-powershell-module"></a>Modulo Windows PowerShell

Il supporto per PowerShell Core non si estende ad altri moduli del prodotto, a meno che questi non supportino in modo esplicito PowerShell Core.
Ad esempio, l'uso del modulo `ActiveDirectory`, incluso in Windows Server, è uno scenario non supportato.

Tuttavia, i moduli che non supportano in modo esplicito PowerShell Core possono essere compatibili in alcuni casi.
Installando il modulo [`WindowsPSModulePath`][] è possibile aggiungere `PSModulePath` di Windows PowerShell a `PSModulePath` di PowerShell Core.

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