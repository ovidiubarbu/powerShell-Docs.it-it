---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Prerequisiti di JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017812"
---
# <a name="prerequisites"></a><span data-ttu-id="65f6d-103">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="65f6d-103">Prerequisites</span></span>

<span data-ttu-id="65f6d-104">Just Enough Administration (JEA) è una funzionalità inclusa in PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="65f6d-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="65f6d-105">Questo articolo descrive i prerequisiti che devono essere soddisfatti per poter usare JEA.</span><span class="sxs-lookup"><span data-stu-id="65f6d-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="65f6d-106">Controllare quale versione di PowerShell è installata</span><span class="sxs-lookup"><span data-stu-id="65f6d-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="65f6d-107">Per controllare quale versione di PowerShell è installata nel sistema, verificare la variabile `$PSVersionTable` in un prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65f6d-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="65f6d-108">JEA è disponibile in PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="65f6d-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="65f6d-109">Per una funzionalità completa, è consigliabile installare la versione più recente di PowerShell disponibile per il sistema.</span><span class="sxs-lookup"><span data-stu-id="65f6d-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="65f6d-110">La tabella seguente illustra la disponibilità di JEA in Windows Server:</span><span class="sxs-lookup"><span data-stu-id="65f6d-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="65f6d-111">Sistema operativo server</span><span class="sxs-lookup"><span data-stu-id="65f6d-111">Server Operating System</span></span> |                <span data-ttu-id="65f6d-112">Disponibilità di JEA</span><span class="sxs-lookup"><span data-stu-id="65f6d-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="65f6d-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="65f6d-113">Windows Server 2016+</span></span>    | <span data-ttu-id="65f6d-114">Preinstallato</span><span class="sxs-lookup"><span data-stu-id="65f6d-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="65f6d-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="65f6d-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="65f6d-116">Funzionalità completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="65f6d-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="65f6d-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="65f6d-117">Windows Server 2012</span></span>     | <span data-ttu-id="65f6d-118">Funzionalità completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="65f6d-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="65f6d-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="65f6d-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="65f6d-120">Funzionalità limitata<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="65f6d-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="65f6d-121">È anche possibile usare JEA nel computer di casa o di lavoro:</span><span class="sxs-lookup"><span data-stu-id="65f6d-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="65f6d-122">Sistema operativo client</span><span class="sxs-lookup"><span data-stu-id="65f6d-122">Client Operating System</span></span> |                   <span data-ttu-id="65f6d-123">Disponibilità di JEA</span><span class="sxs-lookup"><span data-stu-id="65f6d-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="65f6d-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="65f6d-124">Windows 10 1607+</span></span>        | <span data-ttu-id="65f6d-125">Preinstallato</span><span class="sxs-lookup"><span data-stu-id="65f6d-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="65f6d-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="65f6d-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="65f6d-127">Preinstallato, con funzionalità limitata<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="65f6d-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="65f6d-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="65f6d-128">Windows 10 1507</span></span>         | <span data-ttu-id="65f6d-129">Non disponibile</span><span class="sxs-lookup"><span data-stu-id="65f6d-129">Not available</span></span>                                        |
| <span data-ttu-id="65f6d-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="65f6d-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="65f6d-131">Funzionalità completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="65f6d-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="65f6d-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="65f6d-132">Windows 7</span></span>               | <span data-ttu-id="65f6d-133">Funzionalità limitata<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="65f6d-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="65f6d-134"><sup>1</sup> JEA non può essere configurato per l'uso di account del servizio gestito del gruppo in Windows Server 2008 R2 o Windows 7.</span><span class="sxs-lookup"><span data-stu-id="65f6d-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="65f6d-135">*Sono* supportati gli account virtuali e le altre funzionalità JEA.</span><span class="sxs-lookup"><span data-stu-id="65f6d-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="65f6d-136"><sup>2</sup> Le funzionalità JEA seguenti non sono supportate nelle versioni di Windows 10 1511 e 1603:</span><span class="sxs-lookup"><span data-stu-id="65f6d-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="65f6d-137">Esecuzione di un account del servizio gestito del gruppo</span><span class="sxs-lookup"><span data-stu-id="65f6d-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="65f6d-138">Regole di accesso condizionale in configurazioni di sessione</span><span class="sxs-lookup"><span data-stu-id="65f6d-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="65f6d-139">Unità utente</span><span class="sxs-lookup"><span data-stu-id="65f6d-139">The user drive</span></span>
  - <span data-ttu-id="65f6d-140">Concessione dell'accesso agli account utente locali</span><span class="sxs-lookup"><span data-stu-id="65f6d-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="65f6d-141">Per ottenere supporto per queste funzionalità, aggiornare Windows alla versione 1607 (Aggiornamento dell'anniversario) o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="65f6d-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="65f6d-142">Installare Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="65f6d-142">Install Windows Management Framework</span></span>

<span data-ttu-id="65f6d-143">Se si esegue una versione precedente di PowerShell, può essere necessario aggiornare il sistema con la versione più recente di Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="65f6d-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="65f6d-144">Per altre informazioni, vedere la [documentazione di WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="65f6d-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="65f6d-145">È consigliabile testare la compatibilità del carico di lavoro con WMF prima di aggiornare tutti i server.</span><span class="sxs-lookup"><span data-stu-id="65f6d-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="65f6d-146">Gli utenti di Windows 10 devono installare gli aggiornamenti delle funzionalità più recenti per ottenere la versione corrente di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65f6d-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="65f6d-147">Comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="65f6d-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="65f6d-148">La comunicazione remota di PowerShell costituisce la base su cui viene compilato JEA.</span><span class="sxs-lookup"><span data-stu-id="65f6d-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="65f6d-149">È necessario assicurarsi che la comunicazione remota di PowerShell sia abilitata e adeguatamente protetta prima di usare JEA.</span><span class="sxs-lookup"><span data-stu-id="65f6d-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="65f6d-150">Per altre informazioni, vedere [Sicurezza di Gestione remota Windows](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="65f6d-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="65f6d-151">La comunicazione remota di PowerShell è abilitata per impostazione predefinita su Windows Server 2012, 2012 R2 e 2016.</span><span class="sxs-lookup"><span data-stu-id="65f6d-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="65f6d-152">È possibile abilitare la comunicazione remota di PowerShell eseguendo il comando seguente in una finestra di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="65f6d-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="65f6d-153">Abilitare la registrazione del blocco di script e del modulo di PowerShell (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="65f6d-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="65f6d-154">La procedura seguente consente di registrare tutte le azioni di PowerShell nel sistema.</span><span class="sxs-lookup"><span data-stu-id="65f6d-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="65f6d-155">Sebbene non sia necessaria la registrazione del modulo di PowerShell per JEA, è consigliabile attivare la registrazione per assicurarsi che i comandi eseguiti dagli utenti siano registrati in una posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="65f6d-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="65f6d-156">È possibile configurare i criteri di registrazione del modulo di PowerShell tramite i criteri di gruppo.</span><span class="sxs-lookup"><span data-stu-id="65f6d-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="65f6d-157">Aprire l'Editor Criteri di gruppo locali in una workstation o un oggetto Criteri di gruppo nella Console Gestione Criteri di gruppo in un Controller di dominio Active Directory</span><span class="sxs-lookup"><span data-stu-id="65f6d-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="65f6d-158">Passare a **Configurazione computer\\Modelli amministrativi\\Componenti di Windows\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="65f6d-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="65f6d-159">Fare doppio clic su **Attiva registrazione moduli**</span><span class="sxs-lookup"><span data-stu-id="65f6d-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="65f6d-160">Fare clic su **Abilitato**</span><span class="sxs-lookup"><span data-stu-id="65f6d-160">Click **Enabled**</span></span>
5. <span data-ttu-id="65f6d-161">Nella sezione Opzioni fare clic su **Mostra** accanto a Nomi moduli</span><span class="sxs-lookup"><span data-stu-id="65f6d-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="65f6d-162">Digitare `*` nella finestra popup per registrare i comandi di tutti i moduli.</span><span class="sxs-lookup"><span data-stu-id="65f6d-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="65f6d-163">Fare clic su **OK** per impostare i criteri</span><span class="sxs-lookup"><span data-stu-id="65f6d-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="65f6d-164">Fare doppio clic su **Attiva registrazione blocco script di PowerShell**</span><span class="sxs-lookup"><span data-stu-id="65f6d-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="65f6d-165">Fare clic su **Abilitato**</span><span class="sxs-lookup"><span data-stu-id="65f6d-165">Click **Enabled**</span></span>
10. <span data-ttu-id="65f6d-166">Fare clic su **OK** per impostare i criteri</span><span class="sxs-lookup"><span data-stu-id="65f6d-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="65f6d-167">(Solo in computer aggiunti a un dominio) Eseguire `gpupdate` o attendere che i Criteri di gruppo elaborino i criteri aggiornati e applichino le impostazioni</span><span class="sxs-lookup"><span data-stu-id="65f6d-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="65f6d-168">È anche possibile abilitare la trascrizione di PowerShell a livello di sistema con i criteri di gruppo.</span><span class="sxs-lookup"><span data-stu-id="65f6d-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="65f6d-169">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="65f6d-169">Next steps</span></span>

[<span data-ttu-id="65f6d-170">Creare un file delle funzionalità del ruolo</span><span class="sxs-lookup"><span data-stu-id="65f6d-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="65f6d-171">Creare un file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="65f6d-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="65f6d-172">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="65f6d-172">See also</span></span>

[<span data-ttu-id="65f6d-173">Sicurezza di Gestione remota Windows</span><span class="sxs-lookup"><span data-stu-id="65f6d-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="65f6d-174">PowerShell ♥ the Blue Team</span><span class="sxs-lookup"><span data-stu-id="65f6d-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
