---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Funzione DSC per eseguire query delle informazioni sui nodi dal server di pull
ms.openlocfilehash: f97e1d62873fb9e23147ff137468a767455cd82c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="28f90-103">Funzione DSC per eseguire query delle informazioni sui nodi dal server di pull</span><span class="sxs-lookup"><span data-stu-id="28f90-103">DSC function to query node information from pull server.</span></span>

```powershell
function QueryNodeInformation
{
Param (      
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",                         
       [string] $ContentType = "application/json"           
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers 
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

<span data-ttu-id="28f90-104">Sostituire il parametro `Uri` con l'URI del server di pull.</span><span class="sxs-lookup"><span data-stu-id="28f90-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="28f90-105">Se le informazioni sui nodi ottenute devono essere in formato XML, impostare `ContentType` su `application/xml`.</span><span class="sxs-lookup"><span data-stu-id="28f90-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="28f90-106">Per recuperare le informazioni sui nodi dal parametro `$json`, usare lo script seguente:</span><span class="sxs-lookup"><span data-stu-id="28f90-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status 

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```

