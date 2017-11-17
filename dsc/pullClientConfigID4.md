---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0
ms.openlocfilehash: 19328018d276cddd0877869b0ec69c14c51e4b85
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="b9427-103">Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="b9427-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="b9427-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b9427-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b9427-105">Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL per contattare il server di pull da cui ottenere le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="b9427-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="b9427-106">A tale scopo, è necessario configurare Gestione configurazione locale con le informazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="b9427-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="b9427-107">Per configurare Gestione configurazione locale, è necessario creare un tipo speciale di configurazione detto "metaconfigurazione".</span><span class="sxs-lookup"><span data-stu-id="b9427-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="b9427-108">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Gestione configurazione locale di Windows PowerShell 4.0 DSC (Desired State Configuration)](metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="b9427-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="b9427-109">Lo script seguente configura Gestione configurazione locale per il pull delle configurazioni da un server denominato "PullServer":</span><span class="sxs-lookup"><span data-stu-id="b9427-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="b9427-110">Nello script, **DownloadManagerCustomData** passa l'URL del server di pull e (per questo esempio) consente una connessione non protetta.</span><span class="sxs-lookup"><span data-stu-id="b9427-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span> 

<span data-ttu-id="b9427-111">Dopo essere stato eseguito, questo script crea una nuova cartella di output denominata **SimpleMetaConfigurationForPull** e inserisce in questa cartella un file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="b9427-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="b9427-112">Per applicare la configurazione, usare **Set-DscLocalConfigurationManager** con i parametri per **ComputerName** (usare "localhost") e **Path** (percorso del file localhost.meta.mof nel nodo di destinazione).</span><span class="sxs-lookup"><span data-stu-id="b9427-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="b9427-113">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b9427-113">For example:</span></span> 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="b9427-114">ID configurazione</span><span class="sxs-lookup"><span data-stu-id="b9427-114">Configuration ID</span></span>
<span data-ttu-id="b9427-115">Lo script imposta la proprietà **ConfigurationID** di Gestione configurazione locale su un GUID creato in precedenza per questo scopo (è possibile creare un GUID usando il cmdlet **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="b9427-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="b9427-116">Il valore di **ConfigurationID** viene usato da Gestione configurazione locale per trovare la configurazione appropriata nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="b9427-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="b9427-117">Il file MOF di configurazione nel server di pull deve essere denominato `ConfigurationID.mof`, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b9427-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="b9427-118">Pull da un server SMB</span><span class="sxs-lookup"><span data-stu-id="b9427-118">Pulling from an SMB server</span></span>

<span data-ttu-id="b9427-119">Se il server di pull viene configurato come condivisione file SMB, piuttosto che come servizio Web, specificare **DscFileDownloadManager** invece di **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="b9427-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="b9427-120">**DscFileDownloadManager** accetta una proprietà **SourcePath** invece di **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="b9427-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="b9427-121">Lo script seguente configura Gestione configurazione locale per il pull da una condivisione SMB denominata "SmbDscShare" su un server chiamato "CONTOSO-SERVER":</span><span class="sxs-lookup"><span data-stu-id="b9427-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="b9427-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b9427-122">See Also</span></span>

- [<span data-ttu-id="b9427-123">Configurazione di un server di pull Web DSC</span><span class="sxs-lookup"><span data-stu-id="b9427-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="b9427-124">Configurazione di un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="b9427-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)

