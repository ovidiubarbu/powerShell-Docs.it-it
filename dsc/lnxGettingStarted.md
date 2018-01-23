---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Introduzione a DSC (Desired State Configuration) per Linux
ms.openlocfilehash: 4fd8460bc5d2564cab291904b60a1a0c26c3e5a7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="59563-103">Introduzione a DSC (Desired State Configuration) per Linux</span><span class="sxs-lookup"><span data-stu-id="59563-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="59563-104">Questo argomento illustra come iniziare a usare PowerShell DSC (Desired State Configuration) per Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="59563-105">Per informazioni generali su DSC, vedere [Introduzione a Windows PowerShell DSC (Desired State Configuration)](overview.md).</span><span class="sxs-lookup"><span data-stu-id="59563-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="59563-106">Versioni del sistema operativo Linux supportate</span><span class="sxs-lookup"><span data-stu-id="59563-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="59563-107">DSC per Linux supporta le versioni seguenti del sistema operativo Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="59563-108">CentOS 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="59563-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="59563-109">Debian GNU/Linux 6, 7 e 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="59563-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="59563-110">Oracle Linux 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="59563-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="59563-111">Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="59563-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="59563-112">SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="59563-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="59563-113">Ubuntu Server 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="59563-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="59563-114">La tabella seguente descrive le dipendenze dei pacchetti necessarie per DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="59563-115">Pacchetto necessario</span><span class="sxs-lookup"><span data-stu-id="59563-115">Required package</span></span> |  <span data-ttu-id="59563-116">Description</span><span class="sxs-lookup"><span data-stu-id="59563-116">Description</span></span> |  <span data-ttu-id="59563-117">Versione minima</span><span class="sxs-lookup"><span data-stu-id="59563-117">Minimum version</span></span> | 
|---|---|---|
| <span data-ttu-id="59563-118">glibc</span><span class="sxs-lookup"><span data-stu-id="59563-118">glibc</span></span>| <span data-ttu-id="59563-119">Libreria GNU</span><span class="sxs-lookup"><span data-stu-id="59563-119">GNU Library</span></span>| <span data-ttu-id="59563-120">2…4 - 31.30</span><span class="sxs-lookup"><span data-stu-id="59563-120">2…4 – 31.30</span></span>| 
| <span data-ttu-id="59563-121">python</span><span class="sxs-lookup"><span data-stu-id="59563-121">python</span></span>| <span data-ttu-id="59563-122">Python</span><span class="sxs-lookup"><span data-stu-id="59563-122">Python</span></span>| <span data-ttu-id="59563-123">2.4 - 3.4</span><span class="sxs-lookup"><span data-stu-id="59563-123">2.4 – 3.4</span></span>| 
| <span data-ttu-id="59563-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="59563-124">omiserver</span></span>| <span data-ttu-id="59563-125">OMI (Open Management Infrastructure)</span><span class="sxs-lookup"><span data-stu-id="59563-125">Open Management Infrastructure</span></span>| <span data-ttu-id="59563-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="59563-126">1.0.8.1</span></span>| 
| <span data-ttu-id="59563-127">openssl</span><span class="sxs-lookup"><span data-stu-id="59563-127">openssl</span></span>| <span data-ttu-id="59563-128">Librerie OpenSSL</span><span class="sxs-lookup"><span data-stu-id="59563-128">OpenSSL Libraries</span></span>| <span data-ttu-id="59563-129">0.9.8 o 1.0</span><span class="sxs-lookup"><span data-stu-id="59563-129">0.9.8 or 1.0</span></span>| 
| <span data-ttu-id="59563-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="59563-130">ctypes</span></span>| <span data-ttu-id="59563-131">Libreria Python CTypes</span><span class="sxs-lookup"><span data-stu-id="59563-131">Python CTypes library</span></span>| <span data-ttu-id="59563-132">La versione deve corrispondere a quella di Python</span><span class="sxs-lookup"><span data-stu-id="59563-132">Must match Python version</span></span>| 
| <span data-ttu-id="59563-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="59563-133">libcurl</span></span>| <span data-ttu-id="59563-134">Libreria client HTTP cURL</span><span class="sxs-lookup"><span data-stu-id="59563-134">cURL http client library</span></span>| <span data-ttu-id="59563-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="59563-135">7.15.1</span></span>| 

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="59563-136">Installazione di DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="59563-136">Installing DSC for Linux</span></span>

<span data-ttu-id="59563-137">Prima di installare DSC per Linux, è necessario installare [OMI (Open Management Infrastructure)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="59563-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="59563-138">Installazione di OMI</span><span class="sxs-lookup"><span data-stu-id="59563-138">Installing OMI</span></span>

<span data-ttu-id="59563-139">DSC (Desired State Configuration) per Linux richiede il server CIM OMI (Open Management Infrastructure), versione 1.0.8.1 o successive.</span><span class="sxs-lookup"><span data-stu-id="59563-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="59563-140">È possibile scaricare OMI dal sito The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="59563-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="59563-141">Per installare OMI, installare il pacchetto appropriato per il sistema Linux (RPM o DEB), la versione OpenSSL (ssl_098 o ssl_100) e l'architettura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="59563-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="59563-142">I pacchetti RPM sono appropriati per CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="59563-143">I pacchetti DEB sono appropriati per Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="59563-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="59563-144">I pacchetti ssl_098 sono appropriati per i computer in cui è installato OpenSSL 0.9.8, mentre i pacchetti ssl_100 sono appropriati per i computer in cui è installato OpenSSL 1.0.</span><span class="sxs-lookup"><span data-stu-id="59563-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="59563-145">**Nota**: per determinare la versione di OpenSSL installata, eseguire il comando `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="59563-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="59563-146">Eseguire il comando seguente per installare OMI in un sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="59563-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="59563-147">Installazione di DSC</span><span class="sxs-lookup"><span data-stu-id="59563-147">Installing DSC</span></span>

<span data-ttu-id="59563-148">DSC per Linux è disponibile per il download [qui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="59563-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span> 

<span data-ttu-id="59563-149">Per installare DSC, installare il pacchetto appropriato per il sistema Linux (RPM o DEB), la versione OpenSSL (ssl_098 o ssl_100) e l'architettura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="59563-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="59563-150">I pacchetti RPM sono appropriati per CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="59563-151">I pacchetti DEB sono appropriati per Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="59563-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="59563-152">I pacchetti ssl_098 sono appropriati per i computer in cui è installato OpenSSL 0.9.8, mentre i pacchetti ssl_100 sono appropriati per i computer in cui è installato OpenSSL 1.0.</span><span class="sxs-lookup"><span data-stu-id="59563-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="59563-153">**Nota**: per determinare la versione di OpenSSL installata, eseguire il comando openssl version.</span><span class="sxs-lookup"><span data-stu-id="59563-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>
 
<span data-ttu-id="59563-154">Eseguire il comando seguente per installare DSC in un sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="59563-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="59563-155">Uso di DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="59563-155">Using DSC for Linux</span></span>

<span data-ttu-id="59563-156">Le sezioni seguenti illustrano come creare ed eseguire configurazioni DSC nei computer Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="59563-157">Creazione di un documento MOF di configurazione</span><span class="sxs-lookup"><span data-stu-id="59563-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="59563-158">La parola chiave Configuration di Windows PowerShell viene usata per creare una configurazione per i computer Linux, esattamente come per i computer Windows.</span><span class="sxs-lookup"><span data-stu-id="59563-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="59563-159">I passaggi seguenti descrivono la creazione di un documento di configurazione per un computer Linux con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59563-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="59563-160">Importare il modulo nx.</span><span class="sxs-lookup"><span data-stu-id="59563-160">Import the nx module.</span></span> <span data-ttu-id="59563-161">Il modulo nx di Windows PowerShell contiene lo schema per le risorse incorporate per DSC per Linux e deve essere installato nel computer locale e importato nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="59563-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="59563-162">- Per installare il modulo nx, copiare la directory del modulo nx in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` o `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="59563-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="59563-163">Il modulo nx è incluso nel pacchetto di installazione (MSI) di DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="59563-164">Per importare il modulo nx nella configurazione, usare il comando __Import-DSCResource__:</span><span class="sxs-lookup"><span data-stu-id="59563-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="59563-165">Definire una configurazione e generare il documento di configurazione:</span><span class="sxs-lookup"><span data-stu-id="59563-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="59563-166">Effettuare il push della configurazione nel computer Linux</span><span class="sxs-lookup"><span data-stu-id="59563-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="59563-167">È possibile effettuare il push dei documenti di configurazione (file MOF) nel computer Linux usando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="59563-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="59563-168">Per usare questo cmdlet, insieme ai cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) o [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx), in remoto in un computer Linux, è necessario usare una sessione CIMSession.</span><span class="sxs-lookup"><span data-stu-id="59563-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="59563-169">Il cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) viene usato per creare una sessione CIMSession nel computer Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="59563-170">Il codice seguente illustra come creare una sessione CIMSession per DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> <span data-ttu-id="59563-171">**Nota**:</span><span class="sxs-lookup"><span data-stu-id="59563-171">**Note**:</span></span>
* <span data-ttu-id="59563-172">Per la modalità "Push", le credenziali dell'utente devono corrispondere all'utente ROOT nel computer Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="59563-173">DSC per Linux supporta solo le connessioni SSL/TLS. Il cmdlet New-CimSession deve essere usato con il parametro –UseSSL impostato su $true.</span><span class="sxs-lookup"><span data-stu-id="59563-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="59563-174">Il certificato SSL usato da OMI (per DSC) è specificato nel file: `/opt/omi/etc/omiserver.conf` con le proprietà: pemfile e keyfile.</span><span class="sxs-lookup"><span data-stu-id="59563-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="59563-175">Se il certificato non è considerato attendibile dal computer Windows in cui si esegue il cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967), è possibile scegliere di ignorare la convalida del certificato con le opzioni di CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="59563-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="59563-176">Eseguire il comando seguente per effettuare il push della configurazione DSC nel nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="59563-177">Distribuire la configurazione con un server di pull</span><span class="sxs-lookup"><span data-stu-id="59563-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="59563-178">Le configurazioni possono essere distribuite in un computer Linux con un server di pull, esattamente come per i computer Windows.</span><span class="sxs-lookup"><span data-stu-id="59563-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="59563-179">Per informazioni sull'uso di un server di pull, vedere [Server di pull Windows PowerShell DSC (Desired Configuration Pull)](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="59563-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="59563-180">Per altre informazioni e per conoscere le limitazioni relative all'uso di computer Linux con un server di pull, vedere le note sulla versione per DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="59563-181">Uso di configurazioni in locale</span><span class="sxs-lookup"><span data-stu-id="59563-181">Working with configurations locally</span></span>

<span data-ttu-id="59563-182">DSC per Linux include gli script per usare la configurazione dal computer Linux locale.</span><span class="sxs-lookup"><span data-stu-id="59563-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="59563-183">Questi script si trovano in `/opt/microsoft/dsc/Scripts` e includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="59563-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="59563-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="59563-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="59563-185">Restituisce la configurazione corrente applicata al computer.</span><span class="sxs-lookup"><span data-stu-id="59563-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="59563-186">Simile al cmdlet Get-DscConfiguration di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59563-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="59563-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="59563-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="59563-188">Restituisce la metaconfigurazione corrente applicata al computer.</span><span class="sxs-lookup"><span data-stu-id="59563-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="59563-189">Simile al cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="59563-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="59563-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="59563-190">InstallModule.py</span></span>

 <span data-ttu-id="59563-191">Installa un modulo di risorse DSC personalizzato.</span><span class="sxs-lookup"><span data-stu-id="59563-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="59563-192">Richiede il percorso di un file ZIP contenente la libreria di oggetti condivisi del modulo e i file MOF dello schema.</span><span class="sxs-lookup"><span data-stu-id="59563-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="59563-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="59563-193">RemoveModule.py</span></span>

 <span data-ttu-id="59563-194">Rimuove un modulo di risorse DSC personalizzato.</span><span class="sxs-lookup"><span data-stu-id="59563-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="59563-195">Richiede il nome del modulo da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="59563-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="59563-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="59563-196">StartDscLocalConfigurationManager.py</span></span> 

 <span data-ttu-id="59563-197">Applica un file MOF di configurazione al computer.</span><span class="sxs-lookup"><span data-stu-id="59563-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="59563-198">Simile al cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="59563-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="59563-199">Richiede il percorso del file MOF di configurazione da applicare.</span><span class="sxs-lookup"><span data-stu-id="59563-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="59563-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="59563-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="59563-201">Applica un file MOF di metaconfigurazione al computer.</span><span class="sxs-lookup"><span data-stu-id="59563-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="59563-202">Simile al cmdlet [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx).</span><span class="sxs-lookup"><span data-stu-id="59563-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="59563-203">Richiede il percorso del file MOF di metaconfigurazione da applicare.</span><span class="sxs-lookup"><span data-stu-id="59563-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="59563-204">File di registro di PowerShell DSC (Desired State Configuration) per Linux</span><span class="sxs-lookup"><span data-stu-id="59563-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="59563-205">I file di registro seguenti vengono generati per i messaggi di DSC per Linux.</span><span class="sxs-lookup"><span data-stu-id="59563-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="59563-206">File di registro</span><span class="sxs-lookup"><span data-stu-id="59563-206">Log file</span></span>|<span data-ttu-id="59563-207">Directory</span><span class="sxs-lookup"><span data-stu-id="59563-207">Directory</span></span>|<span data-ttu-id="59563-208">Description</span><span class="sxs-lookup"><span data-stu-id="59563-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="59563-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="59563-209">omiserver.log</span></span>|<span data-ttu-id="59563-210">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="59563-210">/var/opt/omi/log</span></span>|<span data-ttu-id="59563-211">Messaggi relativi al funzionamento del server CIM OMI.</span><span class="sxs-lookup"><span data-stu-id="59563-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="59563-212">dsc.log</span><span class="sxs-lookup"><span data-stu-id="59563-212">dsc.log</span></span>|<span data-ttu-id="59563-213">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="59563-213">/var/opt/omi/log</span></span>|<span data-ttu-id="59563-214">Messaggi relativi al funzionamento delle operazioni delle risorse DSC e di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="59563-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|

