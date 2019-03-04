---
title: Creazione di un servizio Web OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856627"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="34106-102">Creazione di un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="34106-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="34106-103">Estensione IIS ODATA gestione è un'infrastruttura per la creazione di un endpoint web ASP.NET del servizio che espone i dati di gestione, che si accede tramite i cmdlet di Windows PowerShell e gli script, come entità di servizio OData Web.</span><span class="sxs-lookup"><span data-stu-id="34106-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="34106-104">Che esegue l'elaborazione delle richieste OData e convertendoli in una chiamata di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34106-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="34106-105">I team dei prodotti possono basarsi su questa infrastruttura per creare endpoint che espongono set di dati di gestione specifici.</span><span class="sxs-lookup"><span data-stu-id="34106-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="34106-106">Scaricare e installare il [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) esempio.</span><span class="sxs-lookup"><span data-stu-id="34106-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="34106-107">Seguire le istruzioni per distribuire il servizio web.</span><span class="sxs-lookup"><span data-stu-id="34106-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="34106-108">Il servizio web espone i servizi e processi tramite le operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD).</span><span class="sxs-lookup"><span data-stu-id="34106-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="34106-109">Le richieste CRUD effettuate al servizio web di richiamano i comandi di Windows PowerShell che eseguono le operazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="34106-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="34106-110">Un mapping tra le operazioni CRUD e i comandi di Windows PowerShell sottostanti viene implementato dal file schema. XML, MOF e due file di schema.</span><span class="sxs-lookup"><span data-stu-id="34106-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="34106-111">Il file MOF Usa la [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="34106-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="34106-112">Il file di schema. XML viene utilizzato un XML schema descritto in [Schema di Mapping della risorsa](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="34106-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34106-113">Prima di abilitare estensione IIS ODATA gestione in Windows Server 2008 R2 SP1, è necessario abilitare le funzionalità seguenti.</span><span class="sxs-lookup"><span data-stu-id="34106-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="34106-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="34106-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="34106-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="34106-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="34106-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="34106-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="34106-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="34106-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="34106-118">Passaggi per la creazione di un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="34106-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="34106-119">Gli argomenti seguenti descrivono come creare e distribuire un servizio web OData di gestione.</span><span class="sxs-lookup"><span data-stu-id="34106-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="34106-120">Aggiunta di risorse a un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="34106-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="34106-121">Implementare l'autorizzazione personalizzata per un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="34106-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="34106-122">Implementazione SessionConfiguration per un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="34106-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="34106-123">Creazione del file di schema MOF per un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="34106-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="34106-124">Creazione del file di schema XML per un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="34106-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="34106-125">Creazione del file Web. config per un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="34106-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="34106-126">Distribuzione di un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="34106-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="34106-127">Associare le entità OData di gestione</span><span class="sxs-lookup"><span data-stu-id="34106-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="34106-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="34106-128">See Also</span></span>

[<span data-ttu-id="34106-129">File di Schema di estensione IIS ODATA gestione</span><span class="sxs-lookup"><span data-stu-id="34106-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
