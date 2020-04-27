---
ms.date: 04/15/2020
keywords: powershell,cmdlet
title: Creazione del secondo hop nella comunicazione remota di PowerShell
ms.openlocfilehash: 7819058bd8118ba44e66ec658017f536076609b5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81527623"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Creazione del secondo hop nella comunicazione remota di PowerShell

Il "problema relativo al secondo hop" si riferisce a una situazione simile alla seguente:

1. Si è connessi al _ServerA_.
2. Dal _ServerA_, si avvia una sessione remota di PowerShell per connettersi al _ServerB_.
3. Un comando eseguito nel _ServerB_ tramite la sessione di comunicazione remota di PowerShell prova ad accedere a una risorsa nel _ServerC_.
4. L'accesso alla risorsa nel _ServerC_ viene negata, perché le credenziali usate per creare la sessione di comunicazione remota di PowerShell non vengono passate dal _ServerB_ al _ServerC_.

Ci sono diversi modi per risolvere questo problema. In questo argomento vengono esaminate alcune delle soluzioni più comuni per il problema del secondo hop.

## <a name="credssp"></a>CredSSP

È possibile usare [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) per l'autenticazione. CredSSP memorizza le credenziali nel server remoto (_ServerB_), quindi il suo uso potrebbe facilitare il furto di credenziali. Se il computer remoto viene compromesso, l'utente malintenzionato ha accesso alle credenziali dell'utente. Per impostazione predefinita, CredSSP è disabilitato sia nei computer client che nei computer server. È opportuno abilitare CredSSP solo negli ambienti più attendibili. Ad esempio, quando un amministratore di dominio si connette a un controller di dominio perché il controller di dominio è estremamente attendibile.

Per altre informazioni sui problemi di sicurezza relativi all'uso di CredSSP per la comunicazione remota di PowerShell, vedere [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (Sabotaggio accidentale: attenzione a CredSSP).

Per altre informazioni sugli attacchi con furto di credenziali, vedere [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036) (Mitigazione degli attacchi Pass-the-Hash (PtH) e di altre tecniche per il furto delle credenziali).

Per un esempio di come abilitare e usare CredSSP per la comunicazione remota di PowerShell, vedere [Abilitare la funzionalità "secondo hop" di PowerShell con CredSSP](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Vantaggi

- Funziona per tutti i server con Windows Server 2008 o versione successiva.

### <a name="cons"></a>Svantaggi

- Presenta vulnerabilità di sicurezza.
- Richiede la configurazione dei ruoli client e server.

## <a name="kerberos-delegation-unconstrained"></a>Delega Kerberos (non vincolata)

È anche possibile usare la delega non vincolata Kerberos per creare il secondo hop. Tuttavia, questo metodo non offre alcun controllo su dove vengono usate le credenziali delegate.

> [!NOTE]
> gli account di Active Directory che hanno il set di proprietà **L'account è sensibile e non può essere delegato** non possono essere delegati. Per altre informazioni, vedere [Security Focus: Analisi del set di proprietà 'L'account è sensibile e non può essere delegato' per gli account privilegiati](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) e [Strumenti e impostazioni dell'autenticazione Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx).

### <a name="pros"></a>Vantaggi

- Non richiede codice speciale.

### <a name="cons"></a>Svantaggi

- Non supporta il secondo hop per WinRM.
- Non offre alcun controllo su dove vengono usate le credenziali e crea una vulnerabilità della sicurezza.

## <a name="kerberos-constrained-delegation"></a>Delega vincolata Kerberos

È possibile usare la delega vincolata legacy (non basata sulle risorse) per creare il secondo hop. Configurare la delega vincolata Kerberos con l'opzione "Usa un qualsiasi protocollo di autenticazione" per consentire la transizione di protocollo.

> [!NOTE]
> gli account di Active Directory che hanno il set di proprietà **L'account è sensibile e non può essere delegato** non possono essere delegati. Per altre informazioni, vedere [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) (Considerazione sulla sicurezza: analisi del set di proprietà 'L'account è sensibile e non può essere delegato' per gli account privilegiati) e [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Strumenti e impostazioni dell'autenticazione Kerberos).

### <a name="pros"></a>Vantaggi

- Non richiede codice speciale

### <a name="cons"></a>Svantaggi

- Non supporta il secondo hop per WinRM.
- Deve essere configurato nell'oggetto di Active Directory del server remoto (_ServerB_).
- Limitato a un solo dominio. Non funziona attraverso domini o foreste.
- Richiede diritti per aggiornare gli oggetti e i nomi dell'entità servizio (SPN).

## <a name="resource-based-kerberos-constrained-delegation"></a>Delega vincolata Kerberos basata sulle risorse

Co l'uso della delega vincolata Kerberos basata sulle risorse (introdotta in Windows Server 2012), si configura la delega delle credenziali nell'oggetto del server dove si trovano le risorse. Nello scenario del secondo hop illustrato in precedenza, si configura il _ServerC_ per specificare da dove verranno accettate le credenziali delegate.

> [!NOTE]
> gli account di Active Directory che hanno il set di proprietà **L'account è sensibile e non può essere delegato** non possono essere delegati. Per altre informazioni, vedere [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) (Considerazione sulla sicurezza: analisi del set di proprietà 'L'account è sensibile e non può essere delegato' per gli account privilegiati) e [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Strumenti e impostazioni dell'autenticazione Kerberos).

### <a name="pros"></a>Vantaggi

- Le credenziali non vengono archiviate.
- È relativamente semplice da configurare con i cmdlet di PowerShell, non è necessario alcun codice speciale.
- Non è necessario alcun accesso particolare al dominio.
- Funziona attraverso domini e foreste.
- Codice di PowerShell.

### <a name="cons"></a>Svantaggi

- Richiede Windows Server 2012 o versione successiva.
- Non supporta il secondo hop per WinRM.
- Richiede diritti per aggiornare gli oggetti e i nomi dell'entità servizio (SPN).

### <a name="example"></a>Esempio

Di seguito viene illustrato un esempio di PowerShell che configura una delega vincolata basata sulle risorse nel _ServerC_ per consentire le credenziali delegate dal _ServerB_. In questo esempio si presuppone che tutti i server eseguano Windows Server 2012 o versione successiva, e che ci sia almeno un controller di dominio di Windows Server 2012 a cui appartenga uno dei server.

Prima di poter configurare la delega vincolata, è necessario aggiungere la funzionalità `RSAT-AD-PowerShell` per installare il modulo di PowerShell per Active Directory e importare il modulo nella sessione:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell
PS C:\> Import-Module ActiveDirectory
```

Molti cmdlet disponibili hanno ora un parametro **PrincipalsAllowedToDelegateToAccount**:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

Il parametro **PrincipalsAllowedToDelegateToAccount** imposta l'attributo dell'oggetto di Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, che contiene un elenco di controllo di accesso (ACL). Questo elenco specifica gli account che hanno l'autorizzazione per delegare le credenziali all'account associato (in questo esempio, sarà l'account computer per il _Server_).

A questo punto vengono impostate le variabili da usare per rappresentare i server:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (e di conseguenza la comunicazione remota di PowerShell) viene eseguito come account del computer per impostazione predefinita. È possibile verificarlo esaminando la proprietà **StartName** del servizio `winrm`:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Per il _ServerC_ per consentire la delega da una sessione di comunicazione remota di PowerShell nel _ServerB_, viene consentito l'accesso impostando il parametro **PrincipalsAllowedToDelegateToAccount** nel _ServerC_ all'oggetto computer del _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Le cache del [Centro distribuzione chiavi (KDC)](/windows/win32/secauthn/key-distribution-center) Kerberos ha negato i tentativi di accesso (cache negativa) per 15 minuti. Se il _ServerB_ ha tentato in precedenza di accedere al _ServerC_, sarà necessario cancellare la cache nel _ServerB_ chiamando il comando seguente:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

È anche possibile riavviare il computer o attendere almeno 15 minuti per cancellare la cache.

Dopo la cancellazione della cache, è possibile eseguire codice dal _ServerA_ attraverso il _ServerB_ al _ServerC_:

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

In questo esempio, la variabile `$using` viene usata per rendere visibile la variabile `$ServerC` al _ServerB_.
Per altre informazioni sulla variabile `$using`, vedere [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Per consentire a più server di delegare le credenziali al _ServerC_, impostare il valore del parametro **PrincipalsAllowedToDelegateToAccount** nel _ServerC_ a una matrice:

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Se si vuole creare il secondo hop tra domini, aggiungere un nome di dominio completo (FQDN) del controller di dominio del dominio a cui appartiene il _ServerB_:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Per rimuovere l'abilità di delegare le credenziali al ServerC, impostare il valore del parametro **PrincipalsAllowedToDelegateToAccount** nel _ServerC_ to `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informazioni sulla delega vincolata Kerberos basata sulle risorse

- [Novità nell'autenticazione Kerberos](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11))
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1) (Come Windows Server 2012 semplifica i problemi della delega vincolata Kerberos, parte 1)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2) (Come Windows Server 2012 semplifica i problemi della delega vincolata Kerberos, parte 2)
- [Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper) (Informazioni sulla delega vincolata Kerberos per le distribuzioni proxy dell'applicazione Azure Active Directory con l'Autenticazione integrata di Windows)
- [[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405) ([MS-ADA2]: attributi dello schema di Active Directory M2.210 Attributo msDS-AllowedToActOnBehalfOfOtherIdentity)
- [[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a) ([MS-SFU]: estensioni del protocollo Kerberos: servizio per utenti e protocollo di delega vincolata 1.3.2 S4U2proxy)
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](/archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount) (Amministrazione remota senza delega vincolata tramite PrincipalsAllowedToDelegateToAccount)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration tramite RunAs

È possibile creare una configurazione sessione nel _ServerB_ e impostare il parametro **RunAsCredential**.

Per informazioni sull'uso di PSSessionConfiguration e RunAs per risolvere il problema del secondo hop, vedere [Another solution to multi-hop PowerShell remoting](/archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting) (Un'altra soluzione per creare più hop nella comunicazione remota di PowerShell)

### <a name="pros"></a>Vantaggi

- Funziona con qualsiasi server che esegue WMF 3.0 o versione successiva.

### <a name="cons"></a>Svantaggi

- Richiede la configurazione di **PSSessionConfiguration** e **RunAs** in ogni server intermedio (_ServerB_).
- Richiede la manutenzione delle password quando si usa un account **RunAs** di dominio

## <a name="just-enough-administration-jea"></a>JEA (Just Enough Administration)

JEA consente di limitare i comandi che un amministratore può eseguire durante una sessione di PowerShell. Può essere usato per risolvere il problema del secondo hop.

Per informazioni su JEA, vedere [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).

### <a name="pros"></a>Vantaggi

- Non richiede nessuna manutenzione delle password quando si usa un account virtuale.

### <a name="cons"></a>Svantaggi

- Richiede WMF 5.0 o versione successiva.
- Richiede la configurazione in ogni server intermedio (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Passare le credenziali all'interno di un blocco di script Invoke-Command

È possibile passare le credenziali all'interno del parametro **ScriptBlock** di una chiamata al cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).

### <a name="pros"></a>Vantaggi

- Non richiede una configurazione di server speciale.
- Funziona in qualsiasi server che esegue WMF 2.0 o versione successiva.

### <a name="cons"></a>Svantaggi

- Richiede una tecnica di codice complicata.
- Se si esegue WMF 2.0, richiede una sintassi diversa per passare gli argomenti a una sessione remota.

### <a name="example"></a>Esempio

L'esempio seguente illustra come passare le credenziali in un blocco di script **Invoke-Command**:

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Vedere anche

[Considerazioni sulla sicurezza della comunicazione remota di PowerShell](WinRMSecurity.md)
