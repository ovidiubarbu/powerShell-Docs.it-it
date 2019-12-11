---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Creazione del secondo hop nella comunicazione remota di PowerShell
ms.openlocfilehash: 567d75009f7d53e9e95e5480b275ec3991cfb9f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417621"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="66e87-103">Creazione del secondo hop nella comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="66e87-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="66e87-104">Il "problema relativo al secondo hop" si riferisce a una situazione simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="66e87-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="66e87-105">Si è connessi al _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="66e87-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="66e87-106">Dal _ServerA_, si avvia una sessione remota di PowerShell per connettersi al _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="66e87-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="66e87-107">Un comando eseguito nel _ServerB_ tramite la sessione di comunicazione remota di PowerShell prova ad accedere a una risorsa nel _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="66e87-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="66e87-108">L'accesso alla risorsa nel _ServerC_ viene negata, perché le credenziali usate per creare la sessione di comunicazione remota di PowerShell non vengono passate dal _ServerB_ al _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="66e87-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="66e87-109">Ci sono diversi modi per risolvere questo problema.</span><span class="sxs-lookup"><span data-stu-id="66e87-109">There are several ways to address this problem.</span></span> <span data-ttu-id="66e87-110">In questo argomento vengono esaminate alcune delle soluzioni più comuni per il problema del secondo hop.</span><span class="sxs-lookup"><span data-stu-id="66e87-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="66e87-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="66e87-111">CredSSP</span></span>

<span data-ttu-id="66e87-112">È possibile usare [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) per l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="66e87-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span></span> <span data-ttu-id="66e87-113">CredSSP memorizza le credenziali nel server remoto (_ServerB_), quindi il suo uso potrebbe facilitare il furto di credenziali.</span><span class="sxs-lookup"><span data-stu-id="66e87-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="66e87-114">Se il computer remoto viene compromesso, l'utente malintenzionato ha accesso alle credenziali dell'utente.</span><span class="sxs-lookup"><span data-stu-id="66e87-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="66e87-115">Per impostazione predefinita, CredSSP è disabilitato sia nei computer client che nei computer server.</span><span class="sxs-lookup"><span data-stu-id="66e87-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="66e87-116">È opportuno abilitare CredSSP solo negli ambienti più attendibili.</span><span class="sxs-lookup"><span data-stu-id="66e87-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="66e87-117">Ad esempio, quando un amministratore di dominio si connette a un controller di dominio perché il controller di dominio è estremamente attendibile.</span><span class="sxs-lookup"><span data-stu-id="66e87-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="66e87-118">Per altre informazioni sui problemi di sicurezza relativi all'uso di CredSSP per la comunicazione remota di PowerShell, vedere [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (Sabotaggio accidentale: attenzione a CredSSP).</span><span class="sxs-lookup"><span data-stu-id="66e87-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="66e87-119">Per altre informazioni sugli attacchi con furto di credenziali, vedere [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036) (Mitigazione degli attacchi Pass-the-Hash (PtH) e di altre tecniche per il furto delle credenziali).</span><span class="sxs-lookup"><span data-stu-id="66e87-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="66e87-120">Per un esempio su come abilitare e usare CredSSP per la comunicazione remota di PowerShell, vedere [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/) (Uso di CredSSP per risolvere il problema relativo al secondo hop).</span><span class="sxs-lookup"><span data-stu-id="66e87-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="66e87-121">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-121">Pros</span></span>

- <span data-ttu-id="66e87-122">Funziona per tutti i server con Windows Server 2008 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="66e87-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="66e87-123">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-123">Cons</span></span>

- <span data-ttu-id="66e87-124">Presenta vulnerabilità di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="66e87-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="66e87-125">Richiede la configurazione dei ruoli client e server.</span><span class="sxs-lookup"><span data-stu-id="66e87-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="66e87-126">Delega Kerberos (non vincolata)</span><span class="sxs-lookup"><span data-stu-id="66e87-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="66e87-127">È anche possibile usare la delega non vincolata Kerberos per creare il secondo hop.</span><span class="sxs-lookup"><span data-stu-id="66e87-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="66e87-128">Tuttavia, questo metodo non offre alcun controllo su dove vengono usate le credenziali delegate.</span><span class="sxs-lookup"><span data-stu-id="66e87-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="66e87-129">**Nota:** gli account di Active Directory che hanno il set di proprietà **L'account è sensibile e non può essere delegato** non possono essere delegati.</span><span class="sxs-lookup"><span data-stu-id="66e87-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="66e87-130">Per altre informazioni, vedere [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Considerazione sulla sicurezza: analisi del set di proprietà 'L'account è sensibile e non può essere delegato' per gli account privilegiati) e [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Strumenti e impostazioni dell'autenticazione Kerberos).</span><span class="sxs-lookup"><span data-stu-id="66e87-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="66e87-131">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-131">Pros</span></span>

- <span data-ttu-id="66e87-132">Non richiede codice speciale.</span><span class="sxs-lookup"><span data-stu-id="66e87-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="66e87-133">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-133">Cons</span></span>

- <span data-ttu-id="66e87-134">Non supporta il secondo hop per WinRM.</span><span class="sxs-lookup"><span data-stu-id="66e87-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="66e87-135">Non offre alcun controllo su dove vengono usate le credenziali e crea una vulnerabilità della sicurezza.</span><span class="sxs-lookup"><span data-stu-id="66e87-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="66e87-136">Delega vincolata Kerberos</span><span class="sxs-lookup"><span data-stu-id="66e87-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="66e87-137">È possibile usare la delega vincolata legacy (non basata sulle risorse) per creare il secondo hop.</span><span class="sxs-lookup"><span data-stu-id="66e87-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="66e87-138">Configurare la delega vincolata Kerberos con l'opzione "Usa un qualsiasi protocollo di autenticazione" per consentire la transizione di protocollo.</span><span class="sxs-lookup"><span data-stu-id="66e87-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="66e87-139">gli account di Active Directory che hanno il set di proprietà **L'account è sensibile e non può essere delegato** non possono essere delegati.</span><span class="sxs-lookup"><span data-stu-id="66e87-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="66e87-140">Per altre informazioni, vedere [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Considerazione sulla sicurezza: analisi del set di proprietà 'L'account è sensibile e non può essere delegato' per gli account privilegiati) e [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Strumenti e impostazioni dell'autenticazione Kerberos).</span><span class="sxs-lookup"><span data-stu-id="66e87-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="66e87-141">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-141">Pros</span></span>

- <span data-ttu-id="66e87-142">Non richiede codice speciale</span><span class="sxs-lookup"><span data-stu-id="66e87-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="66e87-143">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-143">Cons</span></span>

- <span data-ttu-id="66e87-144">Non supporta il secondo hop per WinRM.</span><span class="sxs-lookup"><span data-stu-id="66e87-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="66e87-145">Deve essere configurato nell'oggetto di Active Directory del server remoto (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="66e87-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="66e87-146">Limitato a un solo dominio.</span><span class="sxs-lookup"><span data-stu-id="66e87-146">Limited to one domain.</span></span> <span data-ttu-id="66e87-147">Non funziona attraverso domini o foreste.</span><span class="sxs-lookup"><span data-stu-id="66e87-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="66e87-148">Richiede diritti per aggiornare gli oggetti e i nomi dell'entità servizio (SPN).</span><span class="sxs-lookup"><span data-stu-id="66e87-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="66e87-149">Delega vincolata Kerberos basata sulle risorse</span><span class="sxs-lookup"><span data-stu-id="66e87-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="66e87-150">Co l'uso della delega vincolata Kerberos basata sulle risorse (introdotta in Windows Server 2012), si configura la delega delle credenziali nell'oggetto del server dove si trovano le risorse.</span><span class="sxs-lookup"><span data-stu-id="66e87-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="66e87-151">Nello scenario del secondo hop illustrato in precedenza, si configura il _ServerC_ per specificare da dove verranno accettate le credenziali delegate.</span><span class="sxs-lookup"><span data-stu-id="66e87-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="66e87-152">**Nota:** gli account di Active Directory che hanno il set di proprietà **L'account è sensibile e non può essere delegato** non possono essere delegati.</span><span class="sxs-lookup"><span data-stu-id="66e87-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="66e87-153">Per altre informazioni, vedere [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Considerazione sulla sicurezza: analisi del set di proprietà 'L'account è sensibile e non può essere delegato' per gli account privilegiati) e [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Strumenti e impostazioni dell'autenticazione Kerberos).</span><span class="sxs-lookup"><span data-stu-id="66e87-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="66e87-154">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-154">Pros</span></span>

- <span data-ttu-id="66e87-155">Le credenziali non vengono archiviate.</span><span class="sxs-lookup"><span data-stu-id="66e87-155">Credentials are not stored.</span></span>
- <span data-ttu-id="66e87-156">È relativamente semplice da configurare con i cmdlet di PowerShell, non è necessario alcun codice speciale.</span><span class="sxs-lookup"><span data-stu-id="66e87-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="66e87-157">Non è necessario alcun accesso particolare al dominio.</span><span class="sxs-lookup"><span data-stu-id="66e87-157">No special domain access is required.</span></span>
- <span data-ttu-id="66e87-158">Funziona attraverso domini e foreste.</span><span class="sxs-lookup"><span data-stu-id="66e87-158">Works across domains and forests.</span></span>
- <span data-ttu-id="66e87-159">Codice di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66e87-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="66e87-160">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-160">Cons</span></span>

- <span data-ttu-id="66e87-161">Richiede Windows Server 2012 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="66e87-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="66e87-162">Non supporta il secondo hop per WinRM.</span><span class="sxs-lookup"><span data-stu-id="66e87-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="66e87-163">Richiede diritti per aggiornare gli oggetti e i nomi dell'entità servizio (SPN).</span><span class="sxs-lookup"><span data-stu-id="66e87-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="66e87-164">Esempio</span><span class="sxs-lookup"><span data-stu-id="66e87-164">Example</span></span>

<span data-ttu-id="66e87-165">Di seguito viene illustrato un esempio di PowerShell che configura una delega vincolata basata sulle risorse nel _ServerC_ per consentire le credenziali delegate dal _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="66e87-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="66e87-166">In questo esempio si presuppone che tutti i server eseguano Windows Server 2012 o versione successiva, e che ci sia almeno un controller di dominio di Windows Server 2012 a cui appartenga uno dei server.</span><span class="sxs-lookup"><span data-stu-id="66e87-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="66e87-167">Prima di poter configurare la delega vincolata, è necessario aggiungere la funzionalità `RSAT-AD-PowerShell` per installare il modulo di PowerShell per Active Directory e importare il modulo nella sessione:</span><span class="sxs-lookup"><span data-stu-id="66e87-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="66e87-168">Molti cmdlet disponibili hanno ora un parametro **PrincipalsAllowedToDelegateToAccount**:</span><span class="sxs-lookup"><span data-stu-id="66e87-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="66e87-169">Il parametro **PrincipalsAllowedToDelegateToAccount** imposta l'attributo dell'oggetto di Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, che contiene un elenco di controllo di accesso (ACL). Questo elenco specifica gli account che hanno l'autorizzazione per delegare le credenziali all'account associato (in questo esempio, sarà l'account computer per il _Server_).</span><span class="sxs-lookup"><span data-stu-id="66e87-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="66e87-170">A questo punto vengono impostate le variabili da usare per rappresentare i server:</span><span class="sxs-lookup"><span data-stu-id="66e87-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="66e87-171">WinRM (e di conseguenza la comunicazione remota di PowerShell) viene eseguito come account del computer per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="66e87-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="66e87-172">È possibile verificarlo esaminando la proprietà **StartName** del servizio `winrm`:</span><span class="sxs-lookup"><span data-stu-id="66e87-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="66e87-173">Per il _ServerC_ per consentire la delega da una sessione di comunicazione remota di PowerShell nel _ServerB_, viene consentito l'accesso impostando il parametro **PrincipalsAllowedToDelegateToAccount** nel _ServerC_ all'oggetto computer del _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="66e87-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="66e87-174">Le cache del [Centro distribuzione chiavi (KDC)](/windows/win32/secauthn/key-distribution-center) Kerberos ha negato i tentativi di accesso (cache negativa) per 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="66e87-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="66e87-175">Se il _ServerB_ ha tentato in precedenza di accedere al _ServerC_, sarà necessario cancellare la cache nel _ServerB_ chiamando il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="66e87-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="66e87-176">È anche possibile riavviare il computer o attendere almeno 15 minuti per cancellare la cache.</span><span class="sxs-lookup"><span data-stu-id="66e87-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="66e87-177">Dopo la cancellazione della cache, è possibile eseguire codice dal _ServerA_ attraverso il _ServerB_ al _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="66e87-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="66e87-178">In questo esempio, la variabile `$using` viene usata per rendere visibile la variabile `$ServerC` al _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="66e87-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="66e87-179">Per altre informazioni sulla variabile `$using`, vedere [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="66e87-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="66e87-180">Per consentire a più server di delegare le credenziali al _ServerC_, impostare il valore del parametro **PrincipalsAllowedToDelegateToAccount** nel _ServerC_ a una matrice:</span><span class="sxs-lookup"><span data-stu-id="66e87-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="66e87-181">Se si vuole creare il secondo hop tra domini, aggiungere un nome di dominio completo (FQDN) del controller di dominio del dominio a cui appartiene il _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="66e87-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="66e87-182">Per rimuovere l'abilità di delegare le credenziali al ServerC, impostare il valore del parametro **PrincipalsAllowedToDelegateToAccount** nel _ServerC_ to `$null`:</span><span class="sxs-lookup"><span data-stu-id="66e87-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="66e87-183">Informazioni sulla delega vincolata Kerberos basata sulle risorse</span><span class="sxs-lookup"><span data-stu-id="66e87-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="66e87-184">Novità nell'autenticazione Kerberos</span><span class="sxs-lookup"><span data-stu-id="66e87-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- <span data-ttu-id="66e87-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1) (Come Windows Server 2012 semplifica i problemi della delega vincolata Kerberos, parte 1)</span><span class="sxs-lookup"><span data-stu-id="66e87-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)</span></span>
- <span data-ttu-id="66e87-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2) (Come Windows Server 2012 semplifica i problemi della delega vincolata Kerberos, parte 2)</span><span class="sxs-lookup"><span data-stu-id="66e87-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)</span></span>
- <span data-ttu-id="66e87-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper) (Informazioni sulla delega vincolata Kerberos per le distribuzioni proxy dell'applicazione Azure Active Directory con l'Autenticazione integrata di Windows)</span><span class="sxs-lookup"><span data-stu-id="66e87-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper)</span></span>
- <span data-ttu-id="66e87-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405) ([MS-ADA2]: attributi dello schema di Active Directory M2.210 Attributo msDS-AllowedToActOnBehalfOfOtherIdentity)</span><span class="sxs-lookup"><span data-stu-id="66e87-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span></span>
- <span data-ttu-id="66e87-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a) ([MS-SFU]: estensioni del protocollo Kerberos: servizio per utenti e protocollo di delega vincolata 1.3.2 S4U2proxy)</span><span class="sxs-lookup"><span data-stu-id="66e87-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span></span>
- [<span data-ttu-id="66e87-190">Delega vincolata Kerberos basata sulle risorse</span><span class="sxs-lookup"><span data-stu-id="66e87-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- <span data-ttu-id="66e87-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/) (Amministrazione remota senza delega vincolata tramite PrincipalsAllowedToDelegateToAccount)</span><span class="sxs-lookup"><span data-stu-id="66e87-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="66e87-192">PSSessionConfiguration tramite RunAs</span><span class="sxs-lookup"><span data-stu-id="66e87-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="66e87-193">È possibile creare una configurazione sessione nel _ServerB_ e impostare il parametro **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="66e87-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="66e87-194">Per informazioni sull'uso di PSSessionConfiguration e RunAs per risolvere il problema del secondo hop, vedere [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/) (Un'altra soluzione per creare più hop nella comunicazione remota di PowerShell)</span><span class="sxs-lookup"><span data-stu-id="66e87-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="66e87-195">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-195">Pros</span></span>

- <span data-ttu-id="66e87-196">Funziona con qualsiasi server che esegue WMF 3.0 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="66e87-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="66e87-197">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-197">Cons</span></span>

- <span data-ttu-id="66e87-198">Richiede la configurazione di **PSSessionConfiguration** e **RunAs** in ogni server intermedio (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="66e87-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="66e87-199">Richiede la manutenzione delle password quando si usa un account **RunAs** di dominio</span><span class="sxs-lookup"><span data-stu-id="66e87-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="66e87-200">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="66e87-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="66e87-201">JEA consente di limitare i comandi che un amministratore può eseguire durante una sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66e87-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="66e87-202">Può essere usato per risolvere il problema del secondo hop.</span><span class="sxs-lookup"><span data-stu-id="66e87-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="66e87-203">Per informazioni su JEA, vedere [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="66e87-203">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="66e87-204">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-204">Pros</span></span>

- <span data-ttu-id="66e87-205">Non richiede nessuna manutenzione delle password quando si usa un account virtuale.</span><span class="sxs-lookup"><span data-stu-id="66e87-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="66e87-206">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-206">Cons</span></span>

- <span data-ttu-id="66e87-207">Richiede WMF 5.0 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="66e87-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="66e87-208">Richiede la configurazione in ogni server intermedio (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="66e87-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="66e87-209">Passare le credenziali all'interno di un blocco di script Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="66e87-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="66e87-210">È possibile passare le credenziali all'interno del parametro **ScriptBlock** di una chiamata al cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="66e87-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="66e87-211">Vantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-211">Pros</span></span>

- <span data-ttu-id="66e87-212">Non richiede una configurazione di server speciale.</span><span class="sxs-lookup"><span data-stu-id="66e87-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="66e87-213">Funziona in qualsiasi server che esegue WMF 2.0 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="66e87-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="66e87-214">Svantaggi</span><span class="sxs-lookup"><span data-stu-id="66e87-214">Cons</span></span>

- <span data-ttu-id="66e87-215">Richiede una tecnica di codice complicata.</span><span class="sxs-lookup"><span data-stu-id="66e87-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="66e87-216">Se si esegue WMF 2.0, richiede una sintassi diversa per passare gli argomenti a una sessione remota.</span><span class="sxs-lookup"><span data-stu-id="66e87-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="66e87-217">Esempio</span><span class="sxs-lookup"><span data-stu-id="66e87-217">Example</span></span>

<span data-ttu-id="66e87-218">L'esempio seguente illustra come passare le credenziali in un blocco di script **Invoke-Command**:</span><span class="sxs-lookup"><span data-stu-id="66e87-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="66e87-219">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="66e87-219">See also</span></span>

[<span data-ttu-id="66e87-220">Considerazioni sulla sicurezza della comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="66e87-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
