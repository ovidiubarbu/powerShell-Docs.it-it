---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Introduzione a DSC (Desired State Configuration) per Linux
ms.openlocfilehash: d5a4a17fbcffbbbd6df3dd902dbd104769b7d17e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893597"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="2488a-103">Introduzione a DSC (Desired State Configuration) per Linux</span><span class="sxs-lookup"><span data-stu-id="2488a-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="2488a-104">Questo argomento illustra come iniziare a usare PowerShell DSC (Desired State Configuration) per Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="2488a-105">Per informazioni generali su DSC, vedere [Introduzione a Windows PowerShell DSC (Desired State Configuration)](overview.md).</span><span class="sxs-lookup"><span data-stu-id="2488a-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="2488a-106">Versioni del sistema operativo Linux supportate</span><span class="sxs-lookup"><span data-stu-id="2488a-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="2488a-107">DSC per Linux supporta le versioni seguenti del sistema operativo Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="2488a-108">CentOS 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2488a-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="2488a-109">Debian GNU/Linux 6, 7 e 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2488a-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="2488a-110">Oracle Linux 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2488a-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="2488a-111">Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2488a-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="2488a-112">SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2488a-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="2488a-113">Ubuntu Server 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2488a-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="2488a-114">La tabella seguente descrive le dipendenze dei pacchetti necessarie per DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="2488a-115">Pacchetto necessario</span><span class="sxs-lookup"><span data-stu-id="2488a-115">Required package</span></span> |  <span data-ttu-id="2488a-116">Description</span><span class="sxs-lookup"><span data-stu-id="2488a-116">Description</span></span> |  <span data-ttu-id="2488a-117">Versione minima</span><span class="sxs-lookup"><span data-stu-id="2488a-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="2488a-118">glibc</span><span class="sxs-lookup"><span data-stu-id="2488a-118">glibc</span></span>| <span data-ttu-id="2488a-119">Libreria GNU</span><span class="sxs-lookup"><span data-stu-id="2488a-119">GNU Library</span></span>| <span data-ttu-id="2488a-120">2…4 - 31.30</span><span class="sxs-lookup"><span data-stu-id="2488a-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="2488a-121">python</span><span class="sxs-lookup"><span data-stu-id="2488a-121">python</span></span>| <span data-ttu-id="2488a-122">Python</span><span class="sxs-lookup"><span data-stu-id="2488a-122">Python</span></span>| <span data-ttu-id="2488a-123">2.4 - 3.4</span><span class="sxs-lookup"><span data-stu-id="2488a-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="2488a-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="2488a-124">omiserver</span></span>| <span data-ttu-id="2488a-125">OMI (Open Management Infrastructure)</span><span class="sxs-lookup"><span data-stu-id="2488a-125">Open Management Infrastructure</span></span>| <span data-ttu-id="2488a-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="2488a-126">1.0.8.1</span></span>|
| <span data-ttu-id="2488a-127">openssl</span><span class="sxs-lookup"><span data-stu-id="2488a-127">openssl</span></span>| <span data-ttu-id="2488a-128">Librerie OpenSSL</span><span class="sxs-lookup"><span data-stu-id="2488a-128">OpenSSL Libraries</span></span>| <span data-ttu-id="2488a-129">0.9.8 o 1.0</span><span class="sxs-lookup"><span data-stu-id="2488a-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="2488a-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="2488a-130">ctypes</span></span>| <span data-ttu-id="2488a-131">Libreria Python CTypes</span><span class="sxs-lookup"><span data-stu-id="2488a-131">Python CTypes library</span></span>| <span data-ttu-id="2488a-132">La versione deve corrispondere a quella di Python</span><span class="sxs-lookup"><span data-stu-id="2488a-132">Must match Python version</span></span>|
| <span data-ttu-id="2488a-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="2488a-133">libcurl</span></span>| <span data-ttu-id="2488a-134">Libreria client HTTP cURL</span><span class="sxs-lookup"><span data-stu-id="2488a-134">cURL http client library</span></span>| <span data-ttu-id="2488a-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="2488a-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="2488a-136">Installazione di DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="2488a-136">Installing DSC for Linux</span></span>

<span data-ttu-id="2488a-137">Prima di installare DSC per Linux, è necessario installare [OMI (Open Management Infrastructure)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="2488a-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="2488a-138">Installazione di OMI</span><span class="sxs-lookup"><span data-stu-id="2488a-138">Installing OMI</span></span>

<span data-ttu-id="2488a-139">DSC (Desired State Configuration) per Linux richiede il server CIM OMI (Open Management Infrastructure), versione 1.0.8.1 o successive.</span><span class="sxs-lookup"><span data-stu-id="2488a-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="2488a-140">È possibile scaricare OMI dal sito The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="2488a-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="2488a-141">Per installare OMI, installare il pacchetto appropriato per il sistema Linux (RPM o DEB), la versione OpenSSL (ssl_098 o ssl_100) e l'architettura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="2488a-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="2488a-142">I pacchetti RPM sono appropriati per CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="2488a-143">I pacchetti DEB sono appropriati per Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="2488a-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="2488a-144">I pacchetti ssl_098 sono appropriati per i computer in cui è installato OpenSSL 0.9.8, mentre i pacchetti ssl_100 sono appropriati per i computer in cui è installato OpenSSL 1.0.</span><span class="sxs-lookup"><span data-stu-id="2488a-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="2488a-145">Per determinare la versione di OpenSSL installata, eseguire il comando `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="2488a-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="2488a-146">Eseguire il comando seguente per installare OMI in un sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="2488a-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="2488a-147">Installazione di DSC</span><span class="sxs-lookup"><span data-stu-id="2488a-147">Installing DSC</span></span>

<span data-ttu-id="2488a-148">DSC per Linux è disponibile per il download [qui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="2488a-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="2488a-149">Per installare DSC, installare il pacchetto appropriato per il sistema Linux (RPM o DEB), la versione OpenSSL (ssl_098 o ssl_100) e l'architettura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="2488a-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="2488a-150">I pacchetti RPM sono appropriati per CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="2488a-151">I pacchetti DEB sono appropriati per Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="2488a-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="2488a-152">I pacchetti ssl_098 sono appropriati per i computer in cui è installato OpenSSL 0.9.8, mentre i pacchetti ssl_100 sono appropriati per i computer in cui è installato OpenSSL 1.0.</span><span class="sxs-lookup"><span data-stu-id="2488a-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="2488a-153">Per determinare la versione di OpenSSL installata, eseguire il comando openssl version.</span><span class="sxs-lookup"><span data-stu-id="2488a-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="2488a-154">Eseguire il comando seguente per installare DSC in un sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="2488a-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="2488a-155">Uso di DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="2488a-155">Using DSC for Linux</span></span>

<span data-ttu-id="2488a-156">Le sezioni seguenti illustrano come creare ed eseguire configurazioni DSC nei computer Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="2488a-157">Creazione di un documento MOF di configurazione</span><span class="sxs-lookup"><span data-stu-id="2488a-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="2488a-158">La parola chiave Configuration di Windows PowerShell viene usata per creare una configurazione per i computer Linux, esattamente come per i computer Windows.</span><span class="sxs-lookup"><span data-stu-id="2488a-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="2488a-159">I passaggi seguenti descrivono la creazione di un documento di configurazione per un computer Linux con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2488a-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="2488a-160">Importare il modulo nx.</span><span class="sxs-lookup"><span data-stu-id="2488a-160">Import the nx module.</span></span> <span data-ttu-id="2488a-161">Il modulo nx di Windows PowerShell contiene lo schema per le risorse incorporate per DSC per Linux e deve essere installato nel computer locale e importato nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="2488a-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="2488a-162">Per installare il modulo nx, copiare la directory del modulo nx in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` o `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="2488a-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="2488a-163">Il modulo nx è incluso nel pacchetto di installazione (MSI) di DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="2488a-164">Per importare il modulo nx nella configurazione, usare il comando `Import-DSCResource`:</span><span class="sxs-lookup"><span data-stu-id="2488a-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="2488a-165">Definire una configurazione e generare il documento di configurazione:</span><span class="sxs-lookup"><span data-stu-id="2488a-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="2488a-166">Effettuare il push della configurazione nel computer Linux</span><span class="sxs-lookup"><span data-stu-id="2488a-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="2488a-167">È possibile effettuare il push dei documenti di configurazione (file MOF) nel computer Linux usando il cmdlet [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="2488a-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span> <span data-ttu-id="2488a-168">Per usare questo cmdlet, insieme ai cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) o [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration), in remoto in un computer Linux, è necessario usare una sessione CIMSession.</span><span class="sxs-lookup"><span data-stu-id="2488a-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="2488a-169">Il cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) viene usato per creare una sessione CIMSession nel computer Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="2488a-170">Il codice seguente illustra come creare una sessione CIMSession per DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> <span data-ttu-id="2488a-171">Per la modalità "Push", le credenziali dell'utente devono corrispondere all'utente ROOT nel computer Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="2488a-172">DSC per Linux supporta solo le connessioni SSL/TLS. Il cmdlet `New-CimSession` deve essere usato con il parametro -UseSSL impostato su $true.</span><span class="sxs-lookup"><span data-stu-id="2488a-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="2488a-173">Il certificato SSL usato da OMI (per DSC) è specificato nel file: `/opt/omi/etc/omiserver.conf` con le proprietà: pemfile e keyfile.</span><span class="sxs-lookup"><span data-stu-id="2488a-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="2488a-174">Se il certificato non è considerato attendibile dal computer Windows in cui si esegue il cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967), è possibile scegliere di ignorare la convalida del certificato con le opzioni di CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="2488a-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="2488a-175">Eseguire il comando seguente per effettuare il push della configurazione DSC nel nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="2488a-176">Distribuire la configurazione con un server di pull</span><span class="sxs-lookup"><span data-stu-id="2488a-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="2488a-177">Le configurazioni possono essere distribuite in un computer Linux con un server di pull, esattamente come per i computer Windows.</span><span class="sxs-lookup"><span data-stu-id="2488a-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="2488a-178">Per informazioni sull'uso di un server di pull, vedere [Server di pull Windows PowerShell DSC (Desired Configuration Pull)](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="2488a-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="2488a-179">Per altre informazioni e per conoscere le limitazioni relative all'uso di computer Linux con un server di pull, vedere le note sulla versione per DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="2488a-180">Uso di configurazioni in locale</span><span class="sxs-lookup"><span data-stu-id="2488a-180">Working with configurations locally</span></span>

<span data-ttu-id="2488a-181">DSC per Linux include gli script per usare la configurazione dal computer Linux locale.</span><span class="sxs-lookup"><span data-stu-id="2488a-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="2488a-182">Questi script si trovano in `/opt/microsoft/dsc/Scripts` e includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="2488a-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="2488a-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="2488a-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="2488a-184">Restituisce la configurazione corrente applicata al computer.</span><span class="sxs-lookup"><span data-stu-id="2488a-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="2488a-185">Simile al cmdlet di Windows PowerShell `Get-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="2488a-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="2488a-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2488a-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="2488a-187">Restituisce la metaconfigurazione corrente applicata al computer.</span><span class="sxs-lookup"><span data-stu-id="2488a-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="2488a-188">Simile al cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="2488a-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="2488a-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="2488a-189">InstallModule.py</span></span>

<span data-ttu-id="2488a-190">Installa un modulo di risorse DSC personalizzato.</span><span class="sxs-lookup"><span data-stu-id="2488a-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="2488a-191">Richiede il percorso di un file ZIP contenente la libreria di oggetti condivisi del modulo e i file MOF dello schema.</span><span class="sxs-lookup"><span data-stu-id="2488a-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="2488a-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="2488a-192">RemoveModule.py</span></span>

<span data-ttu-id="2488a-193">Rimuove un modulo di risorse DSC personalizzato.</span><span class="sxs-lookup"><span data-stu-id="2488a-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="2488a-194">Richiede il nome del modulo da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="2488a-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="2488a-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2488a-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="2488a-196">Applica un file MOF di configurazione al computer.</span><span class="sxs-lookup"><span data-stu-id="2488a-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="2488a-197">Simile al cmdlet [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="2488a-197">Similar to the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span> <span data-ttu-id="2488a-198">Richiede il percorso del file MOF di configurazione da applicare.</span><span class="sxs-lookup"><span data-stu-id="2488a-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="2488a-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2488a-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="2488a-200">Applica un file MOF di metaconfigurazione al computer.</span><span class="sxs-lookup"><span data-stu-id="2488a-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="2488a-201">Simile al cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="2488a-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="2488a-202">Richiede il percorso del file MOF di metaconfigurazione da applicare.</span><span class="sxs-lookup"><span data-stu-id="2488a-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="2488a-203">File di registro di PowerShell DSC (Desired State Configuration) per Linux</span><span class="sxs-lookup"><span data-stu-id="2488a-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="2488a-204">I file di registro seguenti vengono generati per i messaggi di DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="2488a-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="2488a-205">File di registro</span><span class="sxs-lookup"><span data-stu-id="2488a-205">Log file</span></span>|<span data-ttu-id="2488a-206">Directory</span><span class="sxs-lookup"><span data-stu-id="2488a-206">Directory</span></span>|<span data-ttu-id="2488a-207">Description</span><span class="sxs-lookup"><span data-stu-id="2488a-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="2488a-208">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="2488a-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="2488a-209">Messaggi relativi al funzionamento del server CIM OMI.</span><span class="sxs-lookup"><span data-stu-id="2488a-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="2488a-210">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="2488a-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="2488a-211">Messaggi relativi al funzionamento delle operazioni delle risorse DSC e di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="2488a-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|