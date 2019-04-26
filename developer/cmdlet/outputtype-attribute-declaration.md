---
title: Dichiarazione di attributo OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067604"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="5f292-102">Dichiarazione dell'attributo OutputType</span><span class="sxs-lookup"><span data-stu-id="5f292-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="5f292-103">Il `OutputType` attributo identifica i tipi di .NET Framework restituiti da un cmdlet, funzione o script.</span><span class="sxs-lookup"><span data-stu-id="5f292-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f292-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5f292-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="5f292-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="5f292-105">Parameters</span></span>

<span data-ttu-id="5f292-106">Tipo (`string[]` o `Type[]`) richiesto.</span><span class="sxs-lookup"><span data-stu-id="5f292-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="5f292-107">Specifica i tipi restituiti dalla funzione di cmdlet o script.</span><span class="sxs-lookup"><span data-stu-id="5f292-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="5f292-108">ParameterSetName (string[]) facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5f292-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="5f292-109">Specifica il set di parametri che restituiscono i tipi specificati nel `type` parametro.</span><span class="sxs-lookup"><span data-stu-id="5f292-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="5f292-110">providerCmdlet facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5f292-110">providerCmdlet Optional.</span></span> <span data-ttu-id="5f292-111">Specifica i cmdlet del provider che restituisce i tipi specificati nel `type` parametro.</span><span class="sxs-lookup"><span data-stu-id="5f292-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f292-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5f292-112">See Also</span></span>

[<span data-ttu-id="5f292-113">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f292-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
