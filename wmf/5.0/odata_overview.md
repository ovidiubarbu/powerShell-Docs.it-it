---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 11891587f59dc8a38e4ce267018160f7f9a28178
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="64340-102">Generare cmdlet di PowerShell in base a un endpoint OData</span><span class="sxs-lookup"><span data-stu-id="64340-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="64340-103">Generare cmdlet di Windows PowerShell in base a un endpoint OData</span><span class="sxs-lookup"><span data-stu-id="64340-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>
--------------------------------------------------------------

<span data-ttu-id="64340-104">**Export-ODataEndpointProxy** è un cmdlet che genera un set di cmdlet di Windows PowerShell basati sulle funzionalità esposte da un determinato endpoint OData.</span><span class="sxs-lookup"><span data-stu-id="64340-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="64340-105">L'esempio seguente mostra come usare questo nuovo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="64340-105">The following example shows how to use this new cmdlet:</span></span>

<span data-ttu-id="64340-106">\# Caso d'uso di base di Export-ODataEndpointProxy</span><span class="sxs-lookup"><span data-stu-id="64340-106">\# Basic use case of Export-ODataEndpointProxy</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="64340-107">Parti dei principali casi d'uso per questa funzionalità sono ancora in fase di sviluppo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="64340-107">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="64340-108">Associazioni</span><span class="sxs-lookup"><span data-stu-id="64340-108">Associations</span></span>
-   <span data-ttu-id="64340-109">Passaggio di flussi</span><span class="sxs-lookup"><span data-stu-id="64340-109">Passing streams</span></span>

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="64340-110">Generare cmdlet di Windows PowerShell in base a un endpoint OData con ODataUtils</span><span class="sxs-lookup"><span data-stu-id="64340-110">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>
------------------------------------------------------------------------------
<span data-ttu-id="64340-111">Il modulo ODataUtils consente la generazione di cmdlet di Windows PowerShell da endpoint REST che supportano OData.</span><span class="sxs-lookup"><span data-stu-id="64340-111">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="64340-112">I seguenti miglioramenti incrementali sono disponibili nel modulo di Windows PowerShell Microsoft.PowerShell.ODataUtils.</span><span class="sxs-lookup"><span data-stu-id="64340-112">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="64340-113">Informazioni aggiuntive del canale dall'endpoint sul lato server al lato client.</span><span class="sxs-lookup"><span data-stu-id="64340-113">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="64340-114">Supporto del paging sul lato client</span><span class="sxs-lookup"><span data-stu-id="64340-114">Client-side paging support</span></span>
-   <span data-ttu-id="64340-115">Filtro sul lato server tramite il parametro -Select</span><span class="sxs-lookup"><span data-stu-id="64340-115">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="64340-116">Supporto delle intestazioni di richieste Web</span><span class="sxs-lookup"><span data-stu-id="64340-116">Support for web request headers</span></span>

<span data-ttu-id="64340-117">I cmdlet proxy generati dal cmdlet Export-ODataEndPointProxy forniscono informazioni aggiuntive (non indicate nei $metadata usati durante la generazione di proxy sul lato client) dall'endpoint OData sul lato server sul flusso di informazioni (una nuova funzionalità di Windows PowerShell 5.0).</span><span class="sxs-lookup"><span data-stu-id="64340-117">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="64340-118">Di seguito è riportato un esempio di come ottenere tali informazioni.</span><span class="sxs-lookup"><span data-stu-id="64340-118">Here is an example of how to get that information.</span></span>
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="64340-119">È possibile ottenere i record dal lato server in batch usando il supporto del paging sul lato client.</span><span class="sxs-lookup"><span data-stu-id="64340-119">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="64340-120">Ciò è utile quando è necessario ottenere una grande quantità di dati dal server tramite la rete.</span><span class="sxs-lookup"><span data-stu-id="64340-120">This is useful when you must get a large amount of data from the server over the network.</span></span>
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="64340-121">I cmdlet proxy generato supportano il parametro -Select che è possibile usare come filtro per ricevere solo le proprietà dei record necessarie per il client.</span><span class="sxs-lookup"><span data-stu-id="64340-121">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="64340-122">In questo modo si riduce la quantità di dati trasferiti in rete, perché il filtro viene applicato sul lato server.</span><span class="sxs-lookup"><span data-stu-id="64340-122">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="64340-123">Il cmdlet Export-ODataEndpointProxy e i cmdlet proxy generati da questo cmdlet supportano ora il parametro Headers (specificare i valori come tabella hash), che è possibile usare per canalizzare qualsiasi informazione aggiuntiva prevista dall'endpoint OData sul lato server.</span><span class="sxs-lookup"><span data-stu-id="64340-123">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="64340-124">Nell'esempio seguente, è possibile canalizzare una chiave della sottoscrizione tramite Headers per i servizi che prevedono una chiave della sottoscrizione per l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="64340-124">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```

