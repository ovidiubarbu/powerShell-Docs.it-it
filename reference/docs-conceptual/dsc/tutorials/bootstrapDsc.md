---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurare una macchina virtuale all'avvio iniziale tramite DSC
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954608"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="3fbf9-103">Configurare una macchina virtuale all'avvio iniziale tramite DSC</span><span class="sxs-lookup"><span data-stu-id="3fbf9-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fbf9-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3fbf9-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="3fbf9-105">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3fbf9-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="3fbf9-106">La chiave del Registro di sistema **DSCAutomationHostEnabled** descritta in questo argomento non è disponibile in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="3fbf9-107">Per informazioni su come configurare nuove macchine virtuali all'avvio iniziale di PowerShell 4.0, vedere [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/) (Configurare automaticamente le macchine virtuali usando DSC all'avvio iniziale)</span><span class="sxs-lookup"><span data-stu-id="3fbf9-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="3fbf9-108">Per eseguire questi esempi, è necessario:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="3fbf9-109">Un disco rigido virtuale di avvio.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-109">A bootable VHD to work with.</span></span> <span data-ttu-id="3fbf9-110">È possibile scaricare un'immagine ISO con una copia di valutazione di Windows Server 2016 in [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="3fbf9-111">È possibile trovare istruzioni su come creare un disco rigido virtuale da un'immagine ISO in [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)) (Creazione di dischi rigidi virtuali di avvio).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="3fbf9-112">Un computer host con Hyper-V abilitato.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="3fbf9-113">Per altre informazioni, vedere [Panoramica di Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="3fbf9-114">Tramite DSC, è possibile automatizzare l'installazione del software e la configurazione di un computer all'avvio iniziale.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="3fbf9-115">A tale scopo, inserire un documento di configurazione MOF o una metaconfigurazione nei supporti di avvio (ad esempio, un disco rigido Virtuale) in modo che vengano eseguiti durante il processo di avvio iniziale.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="3fbf9-116">Questo comportamento viene specificato dalla chiave del Registro di sistema [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="3fbf9-117">Per impostazione predefinita, il valore di questa chiave è 2, che consente l'esecuzione di DSC all'avvio.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="3fbf9-118">Se si preferisce che DSC non venga eseguito all'avvio, impostare il valore della [chiave del Registro di sistema DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) su 0.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="3fbf9-119">Inserire un documento MOF in un disco rigido virtuale</span><span class="sxs-lookup"><span data-stu-id="3fbf9-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="3fbf9-120">Inserire una metaconfigurazione DSC in un disco rigido virtuale</span><span class="sxs-lookup"><span data-stu-id="3fbf9-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="3fbf9-121">Disabilitare DSC in fase di avvio</span><span class="sxs-lookup"><span data-stu-id="3fbf9-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="3fbf9-122">È possibile inserire `Pending.mof` e `MetaConfig.mof` in un computer contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="3fbf9-123">Se entrambi i file sono presenti, le impostazioni specificate in `MetaConfig.mof` hanno la precedenza.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="3fbf9-124">Inserire un documento MOF in un disco rigido virtuale</span><span class="sxs-lookup"><span data-stu-id="3fbf9-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="3fbf9-125">Per applicare una configurazione all'avvio iniziale, è possibile inserire un documento di configurazione MOF compilato nel disco rigido virtuale come file `Pending.mof`.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="3fbf9-126">Se la chiave del Registro di sistema **DSCAutomationHostEnabled** è impostata su 2 (valore predefinito), DSC applicherà la configurazione definita da `Pending.mof` quando il computer viene avviato per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="3fbf9-127">Per questo esempio, verrà usata la configurazione seguente, che consente di installare IIS nel nuovo computer:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="3fbf9-128">Per inserire il documento di configurazione MOF nel disco rigido virtuale</span><span class="sxs-lookup"><span data-stu-id="3fbf9-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="3fbf9-129">Montare il disco rigido virtuale in cui si vuole inserire la configurazione mediante la chiamata al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="3fbf9-130">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="3fbf9-131">In un computer che esegue PowerShell 5.0 o versione successiva salvare la configurazione precedente (**SampleIISInstall**) come file di script PowerShell (con estensione ps1).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="3fbf9-132">Nella console di PowerShell passare alla cartella in cui è stato salvato il file con estensione ps1.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="3fbf9-133">Eseguire i comandi PowerShell seguenti per compilare il documento MOF. Per informazioni sulla compilazione delle configurazioni DSC, vedere [Configurazioni DSC](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="3fbf9-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="3fbf9-134">Verrà creato un file `localhost.mof` in una nuova cartella denominata `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="3fbf9-135">Spostare il file nella posizione corretta del disco rigido virtuale e rinominarlo come `Pending.mof` usando il cmdlet [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="3fbf9-136">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="3fbf9-137">Smontare il disco rigido virtuale tramite la chiamata al cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="3fbf9-138">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="3fbf9-139">Creare una macchina virtuale usando il disco rigido virtuale in cui è installato il documento MOF di DSC.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="3fbf9-140">Dopo l'avvio iniziale e l'installazione del sistema operativo, verrà installato IIS.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-140">After initial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="3fbf9-141">È possibile verificare questo aspetto chiamando il cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="3fbf9-142">Inserire una metaconfigurazione DSC in un disco rigido virtuale</span><span class="sxs-lookup"><span data-stu-id="3fbf9-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="3fbf9-143">È anche possibile configurare un computer per eseguire il pull di una configurazione all'avvio iniziale inserendo una metaconfigurazione (vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md)) nel disco rigido virtuale come file `MetaConfig.mof`.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-143">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="3fbf9-144">Se la chiave del Registro di sistema **DSCAutomationHostEnabled** è impostata su 2 (valore predefinito), DSC applicherà la metaconfigurazione definita da `MetaConfig.mof` a Gestione configurazione locale quando il computer viene avviato per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="3fbf9-145">Se la metaconfigurazione specifica che la Gestione configurazione locale deve eseguire il pull delle configurazioni da un server di pull, il computer tenterà di eseguire il pull di una configurazione da tale server di pull all'avvio iniziale.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span>
<span data-ttu-id="3fbf9-146">Per informazioni sulla configurazione di un server di pull DSC, vedere [Configurazione di un server di pull Web DSC](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="3fbf9-147">Per questo esempio, verranno usate la configurazione descritta nella sezione precedente (**SampleIISInstall**) e la metaconfigurazione seguente:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="3fbf9-148">Per inserire il documento di metaconfigurazione MOF nel disco rigido virtuale</span><span class="sxs-lookup"><span data-stu-id="3fbf9-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="3fbf9-149">Montare il disco rigido virtuale in cui si vuole inserire la metaconfigurazione mediante la chiamata al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="3fbf9-150">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="3fbf9-151">[Configurare un server di pull Web DSC](../pull-server/pullServer.md) e salvare la configurazione **SampleIISInstall** nella cartella appropriata.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="3fbf9-152">In un computer che esegue PowerShell 5.0 o versione successiva salvare la metaconfigurazione precedente (**PullClientBootstrap**) come file di script PowerShell (con estensione ps1).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="3fbf9-153">Nella console di PowerShell passare alla cartella in cui è stato salvato il file con estensione ps1.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="3fbf9-154">Eseguire i comandi PowerShell seguenti per compilare il documento di metaconfigurazione MOF. Per informazioni sulla compilazione delle configurazioni DSC, vedere [Configurazioni DSC](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="3fbf9-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="3fbf9-155">Verrà creato un file `localhost.meta.mof` in una nuova cartella denominata `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="3fbf9-156">Spostare il file nella posizione corretta del disco rigido virtuale e rinominarlo come `MetaConfig.mof` usando il cmdlet [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="3fbf9-157">Smontare il disco rigido virtuale tramite la chiamata al cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="3fbf9-158">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="3fbf9-159">Creare una macchina virtuale usando il disco rigido virtuale in cui è installato il documento MOF di DSC.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="3fbf9-160">Dopo l'avvio iniziale e l'installazione del sistema operativo, DSC eseguirà il pull della configurazione dal server di pull e verrà installato IIS.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-160">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="3fbf9-161">È possibile verificare questo aspetto chiamando il cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="3fbf9-162">Disabilitare DSC in fase di avvio</span><span class="sxs-lookup"><span data-stu-id="3fbf9-162">Disable DSC at boot time</span></span>

<span data-ttu-id="3fbf9-163">Per impostazione predefinita, il valore della chiave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` è impostato su 2, che consente l'esecuzione di una configurazione DSC se il computer è in stato in sospeso o aggiornato.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="3fbf9-164">Se non si vuole far eseguire una configurazione all'avvio iniziale, è necessario impostare il valore di questa chiave su 0:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="3fbf9-165">Montare il disco rigido virtuale tramite la chiamata al cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd).</span><span class="sxs-lookup"><span data-stu-id="3fbf9-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="3fbf9-166">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="3fbf9-167">Caricare la sottochiave del Registro di sistema `HKLM\Software` dal disco rigido virtuale chiamando `reg load`.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="3fbf9-168">Passare a `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` tramite il provider del Registro di sistema di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="3fbf9-169">Modificare il valore di `DSCAutomationHostEnabled` in 0.</span><span class="sxs-lookup"><span data-stu-id="3fbf9-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="3fbf9-170">Scaricare il Registro di sistema eseguendo i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="3fbf9-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="3fbf9-171">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3fbf9-171">See Also</span></span>

[<span data-ttu-id="3fbf9-172">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="3fbf9-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="3fbf9-173">Chiave del Registro di sistema DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="3fbf9-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="3fbf9-174">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="3fbf9-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="3fbf9-175">Configurazione di un server di pull Web DSC</span><span class="sxs-lookup"><span data-stu-id="3fbf9-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
