---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,sicurezza
title: Prerequisiti di JEA
ms.openlocfilehash: e6ee16e34eb9f1f0b2f3601c1aa9e90ab4f785f1
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites"></a><span data-ttu-id="bcf3f-103">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="bcf3f-103">Prerequisites</span></span>

> <span data-ttu-id="bcf3f-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bcf3f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bcf3f-105">Just Enough Administration (JEA) è una funzionalità inclusa in Windows PowerShell 5.0 e versione successiva.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="bcf3f-106">Questo argomento illustra i prerequisiti che devono essere soddisfatti per poter usare JEA.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="bcf3f-107">Installare JEA</span><span class="sxs-lookup"><span data-stu-id="bcf3f-107">Install JEA</span></span>

<span data-ttu-id="bcf3f-108">JEA è disponibile in Windows PowerShell 5.0 e versione successiva, ma per una funzionalità completa, è consigliabile installare la versione più recente di PowerShell disponibile per il sistema.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="bcf3f-109">La tabella seguente illustra la disponibilità di JEA in Windows Server:</span><span class="sxs-lookup"><span data-stu-id="bcf3f-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="bcf3f-110">Sistema operativo server</span><span class="sxs-lookup"><span data-stu-id="bcf3f-110">Server Operating System</span></span>   | <span data-ttu-id="bcf3f-111">Disponibilità di JEA</span><span class="sxs-lookup"><span data-stu-id="bcf3f-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="bcf3f-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="bcf3f-112">Windows Server 2016</span></span>       | <span data-ttu-id="bcf3f-113">Preinstallato</span><span class="sxs-lookup"><span data-stu-id="bcf3f-113">Preinstalled</span></span>
<span data-ttu-id="bcf3f-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bcf3f-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="bcf3f-115">Funzionalità completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bcf3f-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="bcf3f-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="bcf3f-116">Windows Server 2012</span></span>       | <span data-ttu-id="bcf3f-117">Funzionalità completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bcf3f-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="bcf3f-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="bcf3f-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="bcf3f-119">Funzionalità limitata<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bcf3f-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="bcf3f-120">È anche possibile usare JEA nel computer di casa o di lavoro:</span><span class="sxs-lookup"><span data-stu-id="bcf3f-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="bcf3f-121">Sistema operativo client</span><span class="sxs-lookup"><span data-stu-id="bcf3f-121">Client Operating System</span></span>   | <span data-ttu-id="bcf3f-122">Disponibilità di JEA</span><span class="sxs-lookup"><span data-stu-id="bcf3f-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="bcf3f-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="bcf3f-123">Windows 10 1607+</span></span>          | <span data-ttu-id="bcf3f-124">Preinstallato</span><span class="sxs-lookup"><span data-stu-id="bcf3f-124">Preinstalled</span></span>
<span data-ttu-id="bcf3f-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="bcf3f-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="bcf3f-126">Preinstallato, con funzionalità limitata<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bcf3f-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="bcf3f-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="bcf3f-127">Windows 10 1507</span></span>           | <span data-ttu-id="bcf3f-128">Non disponibile</span><span class="sxs-lookup"><span data-stu-id="bcf3f-128">Not available</span></span>
<span data-ttu-id="bcf3f-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="bcf3f-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="bcf3f-130">Funzionalità completa con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bcf3f-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="bcf3f-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="bcf3f-131">Windows 7</span></span>                 | <span data-ttu-id="bcf3f-132">Funzionalità limitata<sup>1</sup> con WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bcf3f-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="bcf3f-133"><sup>1</sup> JEA non può essere configurato per l'uso dell'account del servizio gestito del gruppo in Windows Server 2008 R2 o Windows 7.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="bcf3f-134">*Sono* supportati gli account virtuali e le altre funzionalità JEA.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="bcf3f-135"><sup>2</sup> Le versioni 1511 e 1603 di Windows 10 non supportano le funzionalità JEA seguenti: esecuzione come account del servizio gestito del gruppo, regole di accesso condizionale in configurazioni di sessione, unità utente e concessione dell'accesso agli account utente locali.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="bcf3f-136">Per ottenere supporto per queste funzionalità, aggiornare Windows alla versione 1607 (Aggiornamento dell'anniversario) o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="bcf3f-137">Controllare quale versione di PowerShell è installata</span><span class="sxs-lookup"><span data-stu-id="bcf3f-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="bcf3f-138">Per controllare quale versione di PowerShell è installata nel sistema, verificare la variabile `$PSVersionTable` in un prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="bcf3f-139">È possibile usare JEA se la versione *principale* è uguale o maggiore di **5**.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="bcf3f-140">Per prestazioni ottimali e per l'accesso a tutte le funzionalità più recenti, è consigliabile eseguire l'aggiornamento alla versione di PowerShell **5.1**, quando possibile.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="bcf3f-141">Installare Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="bcf3f-141">Install Windows Management Framework</span></span>

<span data-ttu-id="bcf3f-142">Se si esegue una versione precedente di PowerShell, è necessario aggiornare il sistema con la versione più recente di Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="bcf3f-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="bcf3f-143">Nell'[Area download Microsoft](https://aka.ms/WMF5) sono disponibili i pacchetti di aggiornamento e un collegamento alle note sulla versione più recente di WMF.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="bcf3f-144">È consigliabile testare la compatibilità del carico di lavoro con WMF prima di aggiornare tutti i server.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="bcf3f-145">Gli utenti di Windows 10 devono installare gli aggiornamenti delle funzionalità più recenti per ottenere la versione corrente di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="bcf3f-146">Comunicazione remota di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcf3f-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="bcf3f-147">La comunicazione remota di PowerShell costituisce la base su cui viene compilato JEA.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="bcf3f-148">È quindi necessario assicurarsi che la comunicazione remota di PowerShell sia abilitata e [adeguatamente protetta](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) nel sistema prima di poter usare JEA.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="bcf3f-149">La comunicazione remota di PowerShell è abilitata per impostazione predefinita su Windows Server 2012, 2012 R2 e 2016.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="bcf3f-150">È possibile abilitare la comunicazione remota di PowerShell eseguendo il comando seguente in una finestra di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="bcf3f-151">Abilitare la registrazione del blocco di script e del modulo di PowerShell (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="bcf3f-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="bcf3f-152">La procedura seguente consente di registrare tutte le azioni di PowerShell nel sistema.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="bcf3f-153">Non è necessaria la registrazione del modulo di PowerShell per JEA, tuttavia è consigliabile che sia attivata per assicurarsi che i comandi eseguiti dagli utenti siano registrati in una posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="bcf3f-154">È possibile configurare i criteri di registrazione del modulo di PowerShell tramite i criteri di gruppo.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="bcf3f-155">Aprire l'Editor Criteri di gruppo locali in una workstation o un oggetto Criteri di gruppo nella Console Gestione Criteri di gruppo in un Controller di dominio Active Directory</span><span class="sxs-lookup"><span data-stu-id="bcf3f-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="bcf3f-156">Passare a **Configurazione computer\\Modelli amministrativi\\Componenti di Windows\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="bcf3f-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="bcf3f-157">Fare doppio clic su **Attiva registrazione moduli**</span><span class="sxs-lookup"><span data-stu-id="bcf3f-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="bcf3f-158">Fare clic su **Abilitato**</span><span class="sxs-lookup"><span data-stu-id="bcf3f-158">Click **Enabled**</span></span>
5. <span data-ttu-id="bcf3f-159">Nella sezione Opzioni fare clic su **Mostra** accanto a Nomi moduli</span><span class="sxs-lookup"><span data-stu-id="bcf3f-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="bcf3f-160">Digitare "**\***" nella finestra popup.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="bcf3f-161">Questa operazione indica a PowerShell di registrare i comandi da tutti i moduli.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="bcf3f-162">Fare clic su **OK** per impostare i criteri</span><span class="sxs-lookup"><span data-stu-id="bcf3f-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="bcf3f-163">Fare doppio clic su **Attiva registrazione blocco script di PowerShell**</span><span class="sxs-lookup"><span data-stu-id="bcf3f-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="bcf3f-164">Fare clic su **Abilitato**</span><span class="sxs-lookup"><span data-stu-id="bcf3f-164">Click **Enabled**</span></span>
10. <span data-ttu-id="bcf3f-165">Fare clic su **OK** per impostare i criteri</span><span class="sxs-lookup"><span data-stu-id="bcf3f-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="bcf3f-166">(Solo in computer uniti in dominio) Eseguire **gpupdate** o attendere che i criteri di gruppo elaborino i criteri aggiornati e applichino le impostazioni</span><span class="sxs-lookup"><span data-stu-id="bcf3f-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="bcf3f-167">È anche possibile abilitare la trascrizione di PowerShell a livello di sistema con i criteri di gruppo.</span><span class="sxs-lookup"><span data-stu-id="bcf3f-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bcf3f-168">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="bcf3f-168">Next steps</span></span>

- [<span data-ttu-id="bcf3f-169">Creare un file delle funzionalità del ruolo</span><span class="sxs-lookup"><span data-stu-id="bcf3f-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="bcf3f-170">Creare un file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="bcf3f-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="bcf3f-171">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bcf3f-171">See also</span></span>

- <span data-ttu-id="bcf3f-172">[Additional information about PowerShell Remoting and WinRM security](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) (Altre informazioni sulla comunicazione remota di PowerShell e sulla sicurezza di WinRM)</span><span class="sxs-lookup"><span data-stu-id="bcf3f-172">[Additional information about PowerShell Remoting and WinRM security](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)</span></span>
- [<span data-ttu-id="bcf3f-173">Post di blog sulla sicurezza di *PowerShell ♥ the Blue Team*</span><span class="sxs-lookup"><span data-stu-id="bcf3f-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

