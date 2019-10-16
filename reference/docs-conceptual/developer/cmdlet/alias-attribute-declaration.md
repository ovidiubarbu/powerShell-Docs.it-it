---
title: Dichiarazione dell'attributo alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370020"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="0d03b-102">Dichiarazione dell'attributo Alias</span><span class="sxs-lookup"><span data-stu-id="0d03b-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="0d03b-103">L'attributo Alias consente all'utente di specificare nomi diversi per un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d03b-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="0d03b-104">Gli alias possono essere utilizzati per fornire collegamenti per un nome di parametro oppure possono fornire nomi diversi appropriati per scenari diversi.</span><span class="sxs-lookup"><span data-stu-id="0d03b-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d03b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0d03b-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="0d03b-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="0d03b-106">Parameters</span></span>

<span data-ttu-id="0d03b-107">`aliasName` (String []) required.</span><span class="sxs-lookup"><span data-stu-id="0d03b-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="0d03b-108">Specifica un set di nomi di alias delimitati da virgole per il parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d03b-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d03b-109">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0d03b-109">Remarks</span></span>

- <span data-ttu-id="0d03b-110">L'attributo alias viene usato con l'attributo Parameter quando si specifica un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d03b-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="0d03b-111">Per ulteriori informazioni su come dichiarare questi attributi, vedere [come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0d03b-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="0d03b-112">Ogni nome di alias deve essere univoco all'interno di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d03b-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="0d03b-113">Windows PowerShell non controlla la presenza di nomi di alias duplicati.</span><span class="sxs-lookup"><span data-stu-id="0d03b-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="0d03b-114">L'attributo alias viene usato una volta per ogni parametro in un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d03b-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="0d03b-115">L'attributo alias è definito dalla classe [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0d03b-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d03b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0d03b-116">See Also</span></span>

[<span data-ttu-id="0d03b-117">Alias di parametro</span><span class="sxs-lookup"><span data-stu-id="0d03b-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="0d03b-118">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d03b-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
