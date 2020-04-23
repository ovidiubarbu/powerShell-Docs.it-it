---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Miglioramenti apportati a JEA (Just Enough Administration)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147601"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="03f25-103">Miglioramenti apportati a JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="03f25-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="03f25-104">JEA (Just Enough Administration) è una nuova funzionalità di WMF 5.0 che consente l'amministrazione basata su ruoli tramite la comunicazione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03f25-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="03f25-105">Questa funzionalità estende l'infrastruttura esistente di endpoint vincolati, consentendo a utenti non amministratori di eseguire comandi, script e file eseguibili specifici come amministratore.</span><span class="sxs-lookup"><span data-stu-id="03f25-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="03f25-106">In questo modo è possibile ridurre il numero di amministratori con diritti completi nel proprio ambiente e migliorare la sicurezza.</span><span class="sxs-lookup"><span data-stu-id="03f25-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="03f25-107">Copia di file vincolata in/da endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="03f25-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="03f25-108">È ora possibile copiare in remoto file in/da un endpoint JEA e avere la certezza che l'utente che si connette non potrà copiare *nessun* file nel sistema.</span><span class="sxs-lookup"><span data-stu-id="03f25-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="03f25-109">A questo scopo, è necessario configurare il file PSSC in modo da consentire il montaggio di un'unità utente per la connessione degli utenti.</span><span class="sxs-lookup"><span data-stu-id="03f25-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="03f25-110">L'unità utente è un nuovo dispositivo PSDrive che è esclusivo per ogni utente che si connette e che viene mantenuto da una sessione all'altra.</span><span class="sxs-lookup"><span data-stu-id="03f25-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="03f25-111">Quando si usa `Copy-Item` per copiare file in o da una sessione JEA, esiste un vincolo in base al quale l'accesso è consentito solo all'unità utente.</span><span class="sxs-lookup"><span data-stu-id="03f25-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="03f25-112">I tentativi di copiare i file in altre unità PSDrive avranno esito negativo.</span><span class="sxs-lookup"><span data-stu-id="03f25-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="03f25-113">Per configurare l'unità utente nel file di configurazione della sessione JEA, usare i nuovi campi seguenti:</span><span class="sxs-lookup"><span data-stu-id="03f25-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="03f25-114">La cartella che supporta l'unità utente verrà creata in `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="03f25-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="03f25-115">Per utilizzare l'unità utente e copiare i file in/da un endpoint JEA configurato per esporre l'unità utente, usare i parametri `-ToSession` e `-FromSession` su `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="03f25-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="03f25-116">È quindi possibile scrivere funzioni personalizzate per elaborare i dati archiviati nell'unità utente e rendere disponibili tali dati agli utenti nel file di capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="03f25-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="03f25-117">Supporto per gli account del servizio gestiti del gruppo</span><span class="sxs-lookup"><span data-stu-id="03f25-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="03f25-118">In alcuni casi, per un'attività che un utente deve eseguire in una sessione JEA potrebbe essere necessario accedere a risorse che non si trovano nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="03f25-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="03f25-119">Quando una sessione JEA è configurata per l'uso di un account virtuale, qualsiasi tentativo di accedere a tali risorse risulterà proveniente dall'identità del computer locale, non dall'account virtuale o dall'utente connesso.</span><span class="sxs-lookup"><span data-stu-id="03f25-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="03f25-120">In TP5 è stato abilitato il supporto per l'esecuzione di JEA nel contesto di un [account del servizio gestito del gruppo](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)). In tal modo, risulta molto più semplice accedere alle risorse di rete usando un'identità di dominio.</span><span class="sxs-lookup"><span data-stu-id="03f25-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="03f25-121">Per configurare una sessione JEA per l'esecuzione con un account del servizio gestito del gruppo, usare la nuova chiave seguente nel file PSSC:</span><span class="sxs-lookup"><span data-stu-id="03f25-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="03f25-122">Gli account del servizio gestiti del gruppo non garantiscono l'isolamento o la limitazione dell'ambito degli account virtuali.</span><span class="sxs-lookup"><span data-stu-id="03f25-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="03f25-123">Ogni utente che si connette condividerà la stessa identità degli account del servizio gestiti del gruppo, che può avere le autorizzazioni necessarie per accedere all'intera azienda.</span><span class="sxs-lookup"><span data-stu-id="03f25-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="03f25-124">Prestare molta attenzione quando si sceglie di usare un account del servizio gestito del gruppo e, quando possibile, dare sempre la preferenza agli account virtuali limitati al computer locale.</span><span class="sxs-lookup"><span data-stu-id="03f25-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="03f25-125">Criteri di accesso condizionale</span><span class="sxs-lookup"><span data-stu-id="03f25-125">Conditional access policies</span></span>

<span data-ttu-id="03f25-126">JEA è ideale per limitare le operazioni che un utente può eseguire quando si connette a un sistema per gestirlo. Il problema si pone, tuttavia, quando si vuole limitare il *periodo di tempo* in cui un utente può utilizzare JEA.</span><span class="sxs-lookup"><span data-stu-id="03f25-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="03f25-127">Sono state aggiunte opzioni di configurazione nei file di configurazione della sessione (con estensione pssc) per consentire di specificare gruppi di sicurezza a cui un utente deve appartenere per stabilire una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="03f25-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="03f25-128">Questo meccanismo è particolarmente utile se l'ambiente in uso è dotato di un sistema JIT (Just In Time) e si vuole consentire agli utenti di elevare i propri privilegi prima di accedere a un endpoint JEA con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="03f25-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="03f25-129">Il nuovo campo *RequiredGroups* del file PSSC consente di specificare la logica per determinare se un utente può connettersi a JEA.</span><span class="sxs-lookup"><span data-stu-id="03f25-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="03f25-130">Si tratta di specificare una tabella hash (opzionalmente nidificata) che usi le chiavi 'And' e 'Or' per costruire le regole.</span><span class="sxs-lookup"><span data-stu-id="03f25-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="03f25-131">Di seguito sono riportati alcuni esempi di come usare questo campo:</span><span class="sxs-lookup"><span data-stu-id="03f25-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="03f25-132">Correzione: gli account virtuali sono ora supportati in Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="03f25-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="03f25-133">In WMF 5.1 è ora possibile usare account virtuali in Windows Server 2008 R2, abilitando configurazioni coerenti e parità di funzionalità in Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="03f25-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="03f25-134">Gli account virtuali continuano a non essere supportati quando si usa JEA in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="03f25-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>