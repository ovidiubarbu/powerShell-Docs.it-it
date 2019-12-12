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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359720"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="bf61d-102">Creazione di un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="bf61d-103">Estensione IIS ODATA di gestione è un'infrastruttura per la creazione di un endpoint del servizio Web ASP.NET che espone i dati di gestione, a cui si accede tramite cmdlet e script di Windows PowerShell come entità del servizio Web OData.</span><span class="sxs-lookup"><span data-stu-id="bf61d-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="bf61d-104">A tale scopo, elabora le richieste OData e le converte in una chiamata di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf61d-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="bf61d-105">I team di prodotto possono basarsi su questa infrastruttura per creare endpoint che espongono set di dati di gestione specifici.</span><span class="sxs-lookup"><span data-stu-id="bf61d-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="bf61d-106">Scaricare e installare l'esempio [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) .</span><span class="sxs-lookup"><span data-stu-id="bf61d-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="bf61d-107">Seguire le istruzioni per distribuire il servizio Web.</span><span class="sxs-lookup"><span data-stu-id="bf61d-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="bf61d-108">Questo servizio Web espone i servizi e i processi mediante operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD).</span><span class="sxs-lookup"><span data-stu-id="bf61d-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="bf61d-109">Le richieste CRUD effettuate al servizio Web richiamano i comandi di Windows PowerShell che eseguono le operazioni richieste.</span><span class="sxs-lookup"><span data-stu-id="bf61d-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="bf61d-110">Un mapping tra le operazioni CRUD e i comandi di Windows PowerShell sottostanti viene implementato da due file di schema, schema. mof e schema. XML.</span><span class="sxs-lookup"><span data-stu-id="bf61d-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="bf61d-111">Il file schema. MOF utilizza lo standard MOF ( [Distributed Management Task Force](https://www.dmtf.org/) ) (DMTF).</span><span class="sxs-lookup"><span data-stu-id="bf61d-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="bf61d-112">Nel file schema. XML viene utilizzato un XML Schema descritto in [schema di mapping delle risorse](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="bf61d-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf61d-113">Prima di abilitare l'estensione IIS ODATA di gestione in Windows Server 2008 R2 SP1, è necessario abilitare le funzionalità seguenti.</span><span class="sxs-lookup"><span data-stu-id="bf61d-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="bf61d-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="bf61d-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="bf61d-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="bf61d-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="bf61d-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="bf61d-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="bf61d-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="bf61d-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="bf61d-118">Passaggi per la creazione di un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="bf61d-119">Negli argomenti seguenti viene descritto come creare e distribuire un servizio Web OData di gestione.</span><span class="sxs-lookup"><span data-stu-id="bf61d-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="bf61d-120">Aggiunta di risorse a un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="bf61d-121">Implementazione dell'autorizzazione personalizzata per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="bf61d-122">Implementazione di SessionConfiguration per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="bf61d-123">Creazione del file di schema MOF per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="bf61d-124">Creazione del file di XML Schema per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="bf61d-125">Creazione del file Web. config per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="bf61d-126">Distribuzione di un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="bf61d-127">Associazione di entità OData di gestione</span><span class="sxs-lookup"><span data-stu-id="bf61d-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="bf61d-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bf61d-128">See Also</span></span>

[<span data-ttu-id="bf61d-129">Gestione dei file di schema dell'estensione IIS ODATA</span><span class="sxs-lookup"><span data-stu-id="bf61d-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
