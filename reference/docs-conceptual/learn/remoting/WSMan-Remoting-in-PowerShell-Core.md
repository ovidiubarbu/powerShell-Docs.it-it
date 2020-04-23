---
title: Comunicazione remota di WS-Management (WS-Management) in PowerShell Core
description: Comunicazione remota in PowerShell Core tramite WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "62058880"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="9313b-103">Comunicazione remota di WS-Management (WS-Management) in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9313b-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="9313b-104">Istruzioni per creare un endpoint di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="9313b-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="9313b-105">Il pacchetto PowerShell Core per Windows include un plug-in WinRM (`pwrshplugin.dll`) e uno script di installazione (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="9313b-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="9313b-106">Questi file consentono a PowerShell di accettare le connessioni remote PowerShell in ingresso quando viene specificato l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="9313b-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="9313b-107">Motivazione</span><span class="sxs-lookup"><span data-stu-id="9313b-107">Motivation</span></span>

<span data-ttu-id="9313b-108">Un'installazione di PowerShell può stabilire sessioni di PowerShell con i computer remoti usando `New-PSSession` e `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="9313b-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="9313b-109">Per abilitarla ad accettare le connessioni remote PowerShell in ingresso, l'utente deve creare un endpoint di comunicazione remota WinRM.</span><span class="sxs-lookup"><span data-stu-id="9313b-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="9313b-110">Si tratta di uno scenario di consenso esplicito in cui l'utente esegue Install-PowerShellRemoting.ps1 per creare l'endpoint WinRM.</span><span class="sxs-lookup"><span data-stu-id="9313b-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="9313b-111">Lo script di installazione è una soluzione provvisoria fino a quando non verranno aggiunte altre funzionalità a `Enable-PSRemoting` per eseguire la stessa azione.</span><span class="sxs-lookup"><span data-stu-id="9313b-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="9313b-112">Per altri dettagli, vedere il problema [n. 1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="9313b-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="9313b-113">Azioni script</span><span class="sxs-lookup"><span data-stu-id="9313b-113">Script Actions</span></span>

<span data-ttu-id="9313b-114">Lo script</span><span class="sxs-lookup"><span data-stu-id="9313b-114">The script</span></span>

1. <span data-ttu-id="9313b-115">Crea una directory per il plug-in all'interno di `$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="9313b-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="9313b-116">Copia pwrshplugin.dll in questo percorso</span><span class="sxs-lookup"><span data-stu-id="9313b-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="9313b-117">Genera un file di configurazione</span><span class="sxs-lookup"><span data-stu-id="9313b-117">Generates a configuration file</span></span>
1. <span data-ttu-id="9313b-118">Registra il plug-in in WinRM</span><span class="sxs-lookup"><span data-stu-id="9313b-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="9313b-119">Registrazione</span><span class="sxs-lookup"><span data-stu-id="9313b-119">Registration</span></span>

<span data-ttu-id="9313b-120">Lo script deve essere eseguito all'interno di una sessione di PowerShell a livello di amministratore e viene eseguito in due modalità.</span><span class="sxs-lookup"><span data-stu-id="9313b-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="9313b-121">Eseguito dall'istanza di PowerShell che verrà registrata</span><span class="sxs-lookup"><span data-stu-id="9313b-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="9313b-122">Eseguito da un'altra istanza di PowerShell per conto dell'istanza che verrà registrata</span><span class="sxs-lookup"><span data-stu-id="9313b-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="9313b-123">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9313b-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="9313b-124">**NOTA:** lo script di registrazione della comunicazione remota riavvierà WinRM, in modo che tutte le sessioni PSRP esistenti verranno terminate subito dopo l'esecuzione dello script.</span><span class="sxs-lookup"><span data-stu-id="9313b-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="9313b-125">Se eseguito durante una sessione remota, la connessione viene interrotta.</span><span class="sxs-lookup"><span data-stu-id="9313b-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="9313b-126">Come connettersi al nuovo endpoint</span><span class="sxs-lookup"><span data-stu-id="9313b-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="9313b-127">Stabilire una sessione di PowerShell con il nuovo endpoint PowerShell specificando `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="9313b-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="9313b-128">Per connettersi all'istanza di PowerShell dall'esempio precedente, usare una delle chiamate seguenti:</span><span class="sxs-lookup"><span data-stu-id="9313b-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="9313b-129">Si noti che le chiamate `New-PSSession` e `Enter-PSSession` in cui non viene specificato `-ConfigurationName` avranno come destinazione l'endpoint PowerShell predefinito, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="9313b-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>