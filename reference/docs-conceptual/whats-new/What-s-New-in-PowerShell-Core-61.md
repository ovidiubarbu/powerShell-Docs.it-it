---
title: Novità di PowerShell Core 6.1
description: Nuove funzionalità e modifiche rilasciate in PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086139"
---
# <a name="whats-new-in-powershell-core-61"></a>Novità di PowerShell Core 6.1

Di seguito è riportata una selezione di alcune delle nuove funzionalità e modifiche più importanti introdotte in PowerShell Core 6.1.

Sono state introdotte anche **moltissime** "cose noiose" che rendono PowerShell più veloce e più stabile, oltre ad altrettante correzioni di bug.
Per un elenco completo delle modifiche, consultare il [log delle modifiche](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) su GitHub.

Riportiamo alcuni nomi di seguito, ma vogliamo ringraziare [tutti i collaboratori della community](https://github.com/PowerShell/PowerShell/graphs/contributors) che hanno reso possibile questa versione.

## <a name="net-core-21"></a>.NET Core 2.1

PowerShell Core 6.1 è passato a .NET Core 2.1 dopo il [rilascio di maggio](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), con l'introduzione di una serie di miglioramenti in PowerShell, tra cui:

- miglioramenti delle prestazioni (vedere [di seguito](#performance-improvements))
- supporto per Alpine Linux (anteprima)
- [supporto globale per lo strumento di .NET](/dotnet/core/tools/global-tools), prossimamente in PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows Compatibility Pack per .NET Core

In Windows il team di .NET ha rilasciato il [Windows Compatibility Pack per .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), un set di assembly che ha aggiunto di nuovo diverse API rimosse a .NET Core in Windows.

Il Windows Compatibility Pack è stato aggiunto alla versione 6.1 di PowerShell Core in modo che tutti i moduli o script che usano tali API possano contare sulla disponibilità delle stesse.

Il Windows Compatibility Pack consente a PowerShell Core di usare **più di 1900 cmdlet accluse all'aggiornamento di ottobre 2018 di Windows 10 e a Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Supporto per l'inserimento delle applicazioni nell'elenco degli elementi consentiti

PowerShell Core 6.1 offre lo stesso supporto di Windows PowerShell 5.1 per l'inserimento delle applicazioni nell'elenco elementi consentiti con [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) e [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).
L'inserimento delle applicazioni nell'elenco degli elementi consentiti offre un controllo granulare dei file binari di cui è consentita l'esecuzione con la sono possono essere eseguiti usato con il [linguaggio vincolato](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) di PowerShell.

## <a name="performance-improvements"></a>Miglioramenti delle prestazioni

In PowerShell Core 6.0 sono stati apportati alcuni miglioramenti significativi delle prestazioni.
PowerShell Core 6.1 continua a migliorare la velocità di determinate operazioni.

Ad esempio, la velocità di `Group-Object` è aumentata del 66%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tempo (sec)   | 25,178                 | 19,653              | 6,641               |
| Accelerazione (%) | N/D                    | 21,9%               | 66,2%               |

Analogamente, gli scenari di ordinamento come questo sono stati migliorati di oltre il 15%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tempo (sec)   | 12,170                 | 8,493               | 7,08                |
| Accelerazione (%) | N/D                    | 30,2%               | 16,6%               |

`Import-Csv` è stato accelerato notevolmente anche dopo una regressione da Windows PowerShell.
L'esempio seguente usa un CSV di prova con 26.616 righe e sei colonne:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tempo (sec)   | 0,441                  | 1,069               | 0,268                  |
| Accelerazione (%) | N/D                    | -142,4%             | 74,9% (39,2% da WPS) |

Infine, la conversione da JSON in `PSObject` è stata accelerata di oltre il 50% dopo Windows PowerShell.
L'esempio seguente usa un file JSON di test di ~ 2MB:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tempo (sec)   | 0,259                  | 0,577               | 0,125                  |
| Accelerazione (%) | N/D                    | -122,8%             | 78,3% (51,7% da WPS) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Verificare in `system32` se sono inclusi moduli compatibili in Windows

Nell'aggiornamento 1809 di Windows 10 e in Windows Server 2019 sono stati aggiornati diversi moduli inclusi in PowerShell in modo da contrassegnarli come compatibili con PowerShell Core.

All'avvio, PowerShell Core 6.1 includerà automaticamente `$windir\System32` come parte della variabile di ambiente `PSModulePath`.
Tuttavia, espone solo i moduli a `Get-Module` e `Import-Module` se i relativi `CompatiblePSEdition` sono contrassegnati come compatibili con `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> È possibile che vengano visualizzati come disponibili moduli diversi, a seconda delle funzionalità e dei ruoli installati.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Si può eseguire l'override di questo comportamento con il parametro opzionale `-SkipEditionCheck` in modo da visualizzare tutti i moduli.
È stata anche aggiunta una proprietà `PSEdition` all'output della tabella.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Per altre informazioni su questo comportamento, vedere [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Cmdlet e rendering di markdown

Il markdown è uno standard per la creazione di documenti di testo normale leggibili con formattazione di base di cui si può eseguire il rendering in HTML.

Sono stati aggiunti alcuni cmdlet in 6.1 che consentono di convertire ed eseguire il rendering di documenti di markdown nella console, tra cui:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Ad esempio, `Show-Markdown` esegue il rendering di un file di markdown nella console:

![Esempio di visualizzazione di markdown](./images/markdown_example.png)

Per altre informazioni sul funzionamento di questi cmdlet, consultare [questo documento RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Flag di funzionalità sperimentali

È stato abilitato il supporto per le [funzionalità sperimentali][]. Ciò consente agli sviluppatori di PowerShell di offrire nuove funzionalità e ottenere commenti e suggerimenti prima di completare la progettazione. In questo modo si evita l'introduzione di modifiche che causano un'interruzione con l'evolversi della progettazione.

Usare `Get-ExperimentalFeature` per ottenere un elenco delle funzionalità sperimentali disponibili. È possibile abilitare o disabilitare queste funzionalità con `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature`.

Altre informazioni su questa funzionalità sono disponibili in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Miglioramenti dei cmdlet Web

Grazie a [@markekraus](https://github.com/markekraus), sono stati apportati numerosi miglioramenti ai cmdlet Web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
e [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - codifica predefinita impostata su UTF-8 per le risposte `application-json`
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - parametro `-SkipHeaderValidation` per consentire intestazioni `Content-Type` che non sono conformi agli standard
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - parametro `Form` per supportare il supporto `multipart/form-data` semplificato
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - gestione conforme e senza distinzione tra maiuscole e minuscole delle chiavi di relazione
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - aggiunta del parametro `-Resume` per i cmdlet Web

## <a name="remoting-improvements"></a>Miglioramenti della comunicazione remota

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>PowerShell Direct per i contenitori prova prima a usare PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) è una funzionalità di PowerShell e Hyper-V che consente di connettersi a una macchina virtuale Hyper-V o contenitore senza connettività di rete o altri servizi di gestione remota.

In passato, PowerShell Direct si collegava usando l'istanza di posta in arrivo inclusa in Windows PowerShell nel contenitore.
Ora PowerShell Direct per prima cosa tenta di connettersi usando qualsiasi variabile `pwsh.exe` nella variabile di ambiente `PATH`.
Se `pwsh.exe` non è disponibile, PowerShell Direct esegue il fallback per usare `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` ora crea endpoint di comunicazione remota separati per le versioni di anteprima

`Enable-PSRemoting` ora crea due configurazioni della sessione di comunicazione remota:

- Una per la versione principale di PowerShell. Ad esempio, `PowerShell.6` Questo endpoint può essere usato come base per gli aggiornamenti di versioni secondarie come configurazione di sessione di PowerShell 6 "a livello di sistema"
- Una configurazione di sessione specifica della versione, ad esempio: `PowerShell.6.1.0`

Questo comportamento è utile se si prevede di avere più versioni di PowerShell 6 installate e accessibili nello stesso computer.

Inoltre, le versioni di anteprima di PowerShell ora ottengono le proprie configurazioni di sessione remota dopo l'esecuzione del cmdlet `Enable-PSRemoting`:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

L'output può essere diverso se prima non è stato configurato WinRM.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Quindi è possibile visualizzare configurazioni di sessione di PowerShell separate per l'anteprima e le build stabili di PowerShell 6 e per ogni versione specifica.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>Sintassi di `user@host:port` supportata per SSH

I client SSH in genere supportano una stringa di connessione nel formato `user@host:port`.
Con l'aggiunta di SSH come protocollo per la comunicazione remota di PowerShell, è stato aggiunto il supporto per questo formato della stringa di connessione:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Opzione di MSI per l'aggiunta del menu di scelta rapida della shell di Esplora risorse in Windows

Grazie a [@bergmeister](https://github.com/bergmeister), ora è possibile attivare un menu di scelta rapida in Windows. È ora possibile aprire l'installazione a livello di sistema di PowerShell 6.1 da qualsiasi cartella in Esplora risorse:

![Menu di scelta rapida della shell per PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Novità

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>Opzione "Run as Administrator" (Esegui come amministratore) nel menu di scelta rapida di Windows

Grazie a [@bergmeister](https://github.com/bergmeister), il menu di scelta rapida di PowerShell Core ora include una voce che consente di eseguire PowerShell come amministratore:

!["Run as administrator" nel menu di scelta rapida di PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` consente di tornare alla directory precedente

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

O in Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Inoltre `cd` e `cd --` diventano `$HOME`.

### `Test-Connection`

Grazie a [@iSazonov](https://github.com/iSazonov), il cmdlet [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) è stato portato in PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` come non amministratore

A grande richiesta, `Update-Help` non deve più essere eseguito come amministratore.
`Update-Help` ora per impostazione predefinita salva la Guida in una cartella con ambito di utente.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nuovi metodi e proprietà per `PSCustomObject`

Grazie a [@iSazonov](https://github.com/iSazonov), sono stati aggiunti nuovi metodi e proprietà a `PSCustomObject`.
`PSCustomObject` include ora una proprietà `Count`/`Length` come altri oggetti.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

Questa attività include inoltre i metodi `ForEach` e `Where`, che consentono di usare e filtrare gli elementi `PSCustomObject`:

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

Grazie a @SimonWahlin, è stato aggiunto il parametro `-Not` a `Where-Object`.
Ora è possibile filtrare un oggetto in corrispondenza della pipeline per la non esistenza di una proprietà o un valore della proprietà null/vuoto.

Ad esempio, questo comando restituisce tutti i servizi per cui non sono definiti servizi dipendenti:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` crea un documento UTF-8 senza BOM

Con il passaggio a UTF-8 senza BOM in PowerShell 6.0, il cmdlet `New-ModuleManifest` è stato aggiornato per creare un documento UTF-8 senza BOM anziché un documento UTF-16.

### <a name="conversions-from-psmethod-to-delegate"></a>Conversioni da PSMethod in delegato

Grazie a [@powercode](https://github.com/powercode), è ora supportata la conversione di un `PSMethod` in un delegato.
Ciò consente di eseguire operazioni come il passaggio del `PSMethod` `[M]::DoubleStrLen` come valore delegato in `[M]::AggregateString`:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Per altre informazioni su questa modifica, consultare [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Deviazione standard in `Measure-Object`

Grazie a [@CloudyDino](https://github.com/CloudyDino), è stata aggiunta una proprietà `StandardDeviation` a `Measure-Object`:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Grazie a [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` include ora il parametro `Password`, che accetta un `SecureString`. In questo modo è possibile usarlo in modo non interattivo:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Rimozione della funzione `more`

In precedenza PowerShell rendeva disponibile in Windows la funzione `more` che eseguiva il wrapping di `more.com`.
Tale funzione è stata ora rimossa.

Inoltre, la funzione `help` ora usa `more.com` in Windows o il pager predefinito del sistema specificato da `$env:PAGER` nelle piattaforme non Windows.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` ora riporta gli utenti alla directory di lavoro corrente in quell'unità

In precedenza, usando `Set-Location` o `cd` per tornare a un PSDrive, gli utenti tornavano al percorso predefinito per tale unità.

Grazie a [@mcbobke](https://github.com/mcbobke), gli utenti ora vengono inviati all'ultima directory di lavoro corrente nota per tale sessione.

### <a name="windows-powershell-type-accelerators"></a>Acceleratori del tipo di Windows PowerShell

In Windows PowerShell sono inclusi i seguenti acceleratori del tipo, che semplificano il lavoro con i rispettivi tipi:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Questi acceleratori del tipo non erano inclusi in PowerShell 6, ma sono stati aggiunti a PowerShell 6.1 eseguito in Windows.

Questi tipi sono utili per costruire facilmente oggetti AD e WMI.

Ad esempio, è possibile eseguire una query con LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

Nell'esempio seguente viene creato un oggetto CIM Win32_OperatingSystem:

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

Questo esempio restituisce un oggetto ManagementClass per la classe Win32_OperatingSystem.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>Alias `-lp` per tutti i parametri `-LiteralPath`

Grazie a [@kvprasoon](https://github.com/kvprasoon), è ora disponibile un alias del parametro `-lp` per tutti i cmdlet predefiniti di PowerShell che hanno un parametro `-LiteralPath`.

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

### <a name="msi-based-installation-paths-on-windows"></a>Percorsi di installazione basati su MSI in Windows

In Windows il pacchetto MSI ora esegue l'installazione nel percorso seguente:

- `$env:ProgramFiles\PowerShell\6\` per l'installazione stabile di 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` per l'installazione di anteprima di 6.x

Questa modifica assicura che PowerShell Core possa essere aggiornato/gestito da Microsoft Update.

Per altre informazioni, consultare [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>La telemetria può essere disabilitata solo con una variabile di ambiente

PowerShell Core invia i dati di telemetria di base a Microsoft all'avvio. I dati includono il nome del sistema operativo, la versione del sistema operativo e la versione di PowerShell. Questi dati consentono di comprendere meglio gli ambienti in cui si usa PowerShell e di assegnare priorità alle nuove funzionalità e correzioni.

Per rifiutare esplicitamente questa telemetria, impostare la variabile di ambiente `POWERSHELL_TELEMETRY_OPTOUT` su `true`, `yes` o `1`. Non è più supportata l'eliminazione del file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` per disabilitare la telemetria.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Non è più consentita l'autenticazione di base via HTTP nella comunicazione remota di PowerShell sulle piattaforme Unix

Per evitare l'uso di traffico non crittografato, la comunicazione remota di PowerShell su piattaforme Unix richiede ora l'uso di NTLM/Negotiate o HTTPS.

Per altre informazioni su queste modifiche, vedere il [problema #6779](https://github.com/PowerShell/PowerShell/issues/6779).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Rimosso `VisualBasic` come linguaggio supportato in Add-Type

In passato era possibile compilare il codice Visual Basic usando il cmdlet `Add-Type`.
Visual Basic veniva usato raramente con `Add-Type`. Questa funzionalità è stata rimossa per ridurre le dimensioni di PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Pulizia di `CommandTypes.Workflow` e `WorkflowInfoCleaned`

Per altre informazioni su queste modifiche, vedere [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).

### <a name="group-object-now-sorts-the-groups"></a>Group-Object ordina ora i gruppi

Come parte del miglioramento delle prestazioni, `Group-Object` ora restituisce un elenco ordinato dei gruppi.
Anche se è consigliabile non fare affidamento sull'ordine, questa modifica potrebbe causare problemi se si volesse il primo gruppo. È stato deciso che valeva la pena introdurre questo miglioramento delle prestazioni perché l'impatto dell'eventuale dipendenza dal comportamento precedente è basso.

Per altre informazioni su questa modifica, vedere [Problema n. 7409](https://github.com/PowerShell/PowerShell/issues/7409).

<!-- URL references -->
[Funzionalità sperimentali]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
