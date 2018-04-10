---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorse DSC (Desired State Configuration) predefinite per Linux
ms.openlocfilehash: 77617b72584f39c46fc4b9eb67235378bbfc19aa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="511b4-103">Risorse DSC (Desired State Configuration) predefinite per Linux</span><span class="sxs-lookup"><span data-stu-id="511b4-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="511b4-104">Le risorse sono blocchi predefiniti che è possibile usare per scrivere uno script di PowerShell DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="511b4-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="511b4-105">DSC per Linux include un set di funzionalità predefinite per la configurazione di risorse come file e cartelle, pacchetti, variabili di ambiente e servizi e processi.</span><span class="sxs-lookup"><span data-stu-id="511b4-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="511b4-106">Risorse predefinite</span><span class="sxs-lookup"><span data-stu-id="511b4-106">Built-in resources</span></span>

<span data-ttu-id="511b4-107">La tabella seguente contiene un elenco di queste risorse, insieme ai collegamenti agli argomenti che le descrivono dettagliatamente.</span><span class="sxs-lookup"><span data-stu-id="511b4-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="511b4-108">[Risorsa nxArchive](lnxArchiveResource.md): fornisce un meccanismo per decomprimere file di archivio (ZIP) in un percorso specifico.</span><span class="sxs-lookup"><span data-stu-id="511b4-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="511b4-109">[Risorsa nxEnvironment](lnxEnvironmentResource.md): gestisce le variabili di ambiente nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="511b4-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="511b4-110">[Risorsa nxFile](lnxFileResource.md): gestisce i file e le directory di Linux.</span><span class="sxs-lookup"><span data-stu-id="511b4-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="511b4-111">[Risorsa nxFileLine](lnxFileLineResource.md): gestisce singole righe in un file di Linux.</span><span class="sxs-lookup"><span data-stu-id="511b4-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="511b4-112">[Risorsa nxGroup](lnxGroupResource.md): gestisce i gruppi locali di Linux.</span><span class="sxs-lookup"><span data-stu-id="511b4-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="511b4-113">[Risorsa nxPackage](lnxPackageResource.md): gestisce i pacchetti in nodi di Linux.</span><span class="sxs-lookup"><span data-stu-id="511b4-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="511b4-114">[Risorsa nxScript](lnxScriptResource.md): esegue gli script nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="511b4-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="511b4-115">[Risorsa nxService](lnxServiceResource.md): gestisce i servizi Linux (daemon).</span><span class="sxs-lookup"><span data-stu-id="511b4-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="511b4-116">[Risorsa nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md): gestisce le chiavi ssh pubbliche per un utente di Linux.</span><span class="sxs-lookup"><span data-stu-id="511b4-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="511b4-117">[Risorsa nxUser](lnxUserResource.md): gestisce gli utenti locali di Linux.</span><span class="sxs-lookup"><span data-stu-id="511b4-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>