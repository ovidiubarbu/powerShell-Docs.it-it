---
title: Gli alias dei parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067587"
---
# <a name="parameter-aliases"></a><span data-ttu-id="8877a-102">Alias dei parametri</span><span class="sxs-lookup"><span data-stu-id="8877a-102">Parameter Aliases</span></span>

<span data-ttu-id="8877a-103">Parametri del cmdlet possono avere anche degli alias.</span><span class="sxs-lookup"><span data-stu-id="8877a-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="8877a-104">È possibile usare gli alias anziché i nomi dei parametri quando si immette o specifica il parametro in un comando.</span><span class="sxs-lookup"><span data-stu-id="8877a-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="8877a-105">Vantaggi dell'uso di alias</span><span class="sxs-lookup"><span data-stu-id="8877a-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="8877a-106">Aggiunta di alias per i parametri offre i vantaggi seguenti.</span><span class="sxs-lookup"><span data-stu-id="8877a-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="8877a-107">È possibile fornire un collegamento in modo che l'utente non dovrà usare il nome del parametro completo quando viene chiamato il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8877a-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="8877a-108">Ad esempio, è possibile usare l'alias "CN" anziché il nome del parametro "Nomecomputer".</span><span class="sxs-lookup"><span data-stu-id="8877a-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="8877a-109">Se si desidera fornire nomi diversi per lo stesso parametro, è possibile definire più alias.</span><span class="sxs-lookup"><span data-stu-id="8877a-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="8877a-110">È possibile definire più alias, se si lavora con più gruppi di utenti che fanno riferimento agli stessi dati in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="8877a-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="8877a-111">È possibile garantire la compatibilità per gli script esistenti se il nome di un parametro viene modificato.</span><span class="sxs-lookup"><span data-stu-id="8877a-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="8877a-112">Usando l'Alias (attributo) con l'attributo ValueFromPipelineByName, è possibile definire un parametro che consente di cmdlet per l'associazione a diversi tipi di oggetto.</span><span class="sxs-lookup"><span data-stu-id="8877a-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="8877a-113">Ad esempio, si dispone di due oggetti di tipi diversi e il primo oggetto disponeva di una proprietà di writer e il secondo oggetto ha una proprietà dell'editor.</span><span class="sxs-lookup"><span data-stu-id="8877a-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="8877a-114">Se il cmdlet ha un parametro che ha alias writer e l'editor e il cmdlet accepted input della pipeline basati su nei nomi di proprietà, il cmdlet è stato possibile associare a entrambi gli oggetti usando i due alias di parametro.</span><span class="sxs-lookup"><span data-stu-id="8877a-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="8877a-115">Per altre informazioni sugli alias che può essere utilizzato con parametri specifici, vedere [i nomi dei parametri comuni](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="8877a-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="8877a-116">Definizione di alias di parametro</span><span class="sxs-lookup"><span data-stu-id="8877a-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="8877a-117">Per definire un alias per un parametro, dichiarare l'attributo di Alias, come illustrato nella seguente dichiarazione di parametro.</span><span class="sxs-lookup"><span data-stu-id="8877a-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="8877a-118">In questo esempio, sono definiti più alias per il parametro stesso.</span><span class="sxs-lookup"><span data-stu-id="8877a-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="8877a-119">(Per altre informazioni, vedere[come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="8877a-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="8877a-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8877a-120">See Also</span></span>

[<span data-ttu-id="8877a-121">Nomi dei parametri comuni</span><span class="sxs-lookup"><span data-stu-id="8877a-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="8877a-122">Come dichiarare i parametri del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8877a-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="8877a-123">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8877a-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
