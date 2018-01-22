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

PowerShell Core è ufficialmente supportato sulle piattaforme seguenti:

* Windows 7, 8.1 e 10
* Windows Server 2008 R2, 2012 R2, 2016
* [Canale semestrale di Windows Server][semi-annual]
* Ubuntu 14.04, 16.04 e 17.04
* Debian 8.7+ e 9
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42.2
* Fedora 25, 26
* macOS 10.12+

La nostra community ha anche reso disponibili pacchetti per le piattaforme seguenti, ma non sono ufficialmente supportati:

* Arch Linux
* Kali Linux
* AppImage (funziona su più piattaforme Linux)

## <a name="notes-on-licensing"></a>Note sulla licenza

PowerShell Core viene rilasciato con la [licenza MIT][].
In base a questa licenza e in assenza di un contratto di supporto a pagamento, il supporto per gli utenti è limitato al [supporto della community][].
Con il supporto della community, Microsoft non garantisce velocità di risposta o correzioni.

## <a name="windows-powershell-module"></a>Modulo Windows PowerShell

Il supporto per PowerShell Core non si estende ad altri moduli del prodotto, a meno che questi non supportino in modo esplicito PowerShell Core.
Ad esempio, l'uso del modulo `ActiveDirectory`, incluso in Windows Server, è uno scenario non supportato.

Tuttavia, i moduli che non supportano in modo esplicito PowerShell Core possono essere compatibili in alcuni casi.
Installando il modulo [`WindowsPSModulePath`][], è possibile aggiungere `PSModulePath` di Windows PowerShell a `PSModulePath` di PowerShell Core.

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
