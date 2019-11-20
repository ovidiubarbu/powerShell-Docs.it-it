---
title: Dichiarazione dell'attributo OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365340"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="116f6-102">Dichiarazione dell'attributo OutputType</span><span class="sxs-lookup"><span data-stu-id="116f6-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="116f6-103">L'attributo `OutputType` identifica i tipi di .NET Framework restituiti da un cmdlet, una funzione o uno script.</span><span class="sxs-lookup"><span data-stu-id="116f6-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="116f6-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="116f6-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="116f6-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="116f6-105">Parameters</span></span>

<span data-ttu-id="116f6-106">È necessario digitare (`string[]` o `Type[]`).</span><span class="sxs-lookup"><span data-stu-id="116f6-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="116f6-107">Specifica i tipi restituiti dalla funzione del cmdlet o dallo script.</span><span class="sxs-lookup"><span data-stu-id="116f6-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="116f6-108">ParameterSetName (String []) facoltativa.</span><span class="sxs-lookup"><span data-stu-id="116f6-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="116f6-109">Specifica i set di parametri che restituiscono i tipi specificati nel parametro `type`.</span><span class="sxs-lookup"><span data-stu-id="116f6-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="116f6-110">providerCmdlet facoltativo.</span><span class="sxs-lookup"><span data-stu-id="116f6-110">providerCmdlet Optional.</span></span> <span data-ttu-id="116f6-111">Specifica il cmdlet del provider che restituisce i tipi specificati nel parametro `type`.</span><span class="sxs-lookup"><span data-stu-id="116f6-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="116f6-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="116f6-112">See Also</span></span>

[<span data-ttu-id="116f6-113">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="116f6-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)