---
title: Creazione del file di schema XML per un servizio web OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857977"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="e243a-102">Creazione del file di schema XML per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e243a-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="e243a-103">Dopo aver definito le risorse esporrà il servizio web (vedere [la creazione del file di schema MOF per un servizio web IIS OData gestione](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), si esegue il mapping di tali risorse ai cmdlet di Windows PowerShell sottostanti che implementano supportati operazioni per ogni risorsa creando un file XML conforme al [Schema di Mapping della risorsa](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="e243a-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="e243a-104">Il file XML specifica anche gli URL utilizzati dal client per accedere alle risorse.</span><span class="sxs-lookup"><span data-stu-id="e243a-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="e243a-105">Risorse Mappng agli URL</span><span class="sxs-lookup"><span data-stu-id="e243a-105">Mappng resources to URLs</span></span>

<span data-ttu-id="e243a-106">La prima parte del file XML viene eseguito il mapping le risorse definite nel file di schema MOF agli URL che vengono utilizzati per accedervi.</span><span class="sxs-lookup"><span data-stu-id="e243a-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="e243a-107">L'esempio seguente illustra il mapping.</span><span class="sxs-lookup"><span data-stu-id="e243a-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="e243a-108">Cmdlet di mapping per le operazioni CRUD</span><span class="sxs-lookup"><span data-stu-id="e243a-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="e243a-109">Specificare quindi i cmdlet che corrispondono al CRUD (creare, leggere, aggiornare ed eliminare) le operazioni che supportano le risorse.</span><span class="sxs-lookup"><span data-stu-id="e243a-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="e243a-110">In OData di gestione [Schema di Mapping della risorsa](./resource-mapping-schema.md), le operazioni CRUD vengono eseguito il mapping come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="e243a-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="e243a-111">Comando CRUD</span><span class="sxs-lookup"><span data-stu-id="e243a-111">CRUD command</span></span>|<span data-ttu-id="e243a-112">Elemento XML</span><span class="sxs-lookup"><span data-stu-id="e243a-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="e243a-113">Creazione</span><span class="sxs-lookup"><span data-stu-id="e243a-113">Create</span></span>|<span data-ttu-id="e243a-114">Creazione</span><span class="sxs-lookup"><span data-stu-id="e243a-114">Create</span></span>|
|<span data-ttu-id="e243a-115">Lettura</span><span class="sxs-lookup"><span data-stu-id="e243a-115">Read</span></span>|<span data-ttu-id="e243a-116">Query</span><span class="sxs-lookup"><span data-stu-id="e243a-116">Query</span></span>|
|<span data-ttu-id="e243a-117">Aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="e243a-117">Update</span></span>|<span data-ttu-id="e243a-118">Aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="e243a-118">Update</span></span>|
|<span data-ttu-id="e243a-119">Elimina</span><span class="sxs-lookup"><span data-stu-id="e243a-119">Delete</span></span>|<span data-ttu-id="e243a-120">Elimina</span><span class="sxs-lookup"><span data-stu-id="e243a-120">Delete</span></span>|

<span data-ttu-id="e243a-121">L'esempio seguente illustra i mapping per le operazioni Create, Read e Update nel `Service` risorsa.</span><span class="sxs-lookup"><span data-stu-id="e243a-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="e243a-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e243a-122">See Also</span></span>

[<span data-ttu-id="e243a-123">Creazione del file di schema MOF per un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="e243a-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="e243a-124">Schema di Mapping delle risorse</span><span class="sxs-lookup"><span data-stu-id="e243a-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="e243a-125">Creazione di un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e243a-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)