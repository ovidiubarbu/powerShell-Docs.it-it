---
title: Alias di parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369590"
---
# <a name="parameter-aliases"></a><span data-ttu-id="5f583-102">Alias dei parametri</span><span class="sxs-lookup"><span data-stu-id="5f583-102">Parameter Aliases</span></span>

<span data-ttu-id="5f583-103">I parametri cmdlet possono avere anche degli alias.</span><span class="sxs-lookup"><span data-stu-id="5f583-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="5f583-104">È possibile utilizzare gli alias anziché i nomi dei parametri quando si digita o si specifica il parametro in un comando.</span><span class="sxs-lookup"><span data-stu-id="5f583-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="5f583-105">Vantaggi dell'utilizzo degli alias</span><span class="sxs-lookup"><span data-stu-id="5f583-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="5f583-106">L'aggiunta di alias ai parametri offre i vantaggi seguenti.</span><span class="sxs-lookup"><span data-stu-id="5f583-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="5f583-107">È possibile fornire un collegamento in modo che l'utente non debba usare il nome del parametro completo quando viene chiamato il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f583-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="5f583-108">Ad esempio, è possibile usare l'alias "CN" anziché il nome del parametro "computername".</span><span class="sxs-lookup"><span data-stu-id="5f583-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="5f583-109">È possibile definire più alias se si desidera fornire nomi diversi per lo stesso parametro.</span><span class="sxs-lookup"><span data-stu-id="5f583-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="5f583-110">Se è necessario utilizzare più gruppi di utenti che fanno riferimento agli stessi dati in modi diversi, potrebbe essere necessario definire più alias.</span><span class="sxs-lookup"><span data-stu-id="5f583-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="5f583-111">È possibile fornire la compatibilità con le versioni precedenti per gli script esistenti se il nome di un parametro viene modificato.</span><span class="sxs-lookup"><span data-stu-id="5f583-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="5f583-112">Utilizzando l'attributo alias insieme all'attributo ValueFromPipelineByName, è possibile definire un parametro che consente al cmdlet di eseguire l'associazione a tipi di oggetti diversi.</span><span class="sxs-lookup"><span data-stu-id="5f583-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="5f583-113">Si immagini, ad esempio, di avere due oggetti di tipi diversi e che il primo oggetto disponga di una proprietà Writer e che il secondo oggetto disponga di una proprietà Editor.</span><span class="sxs-lookup"><span data-stu-id="5f583-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="5f583-114">Se il cmdlet dispone di un parametro con alias di writer e di editor e il cmdlet accetta input della pipeline in base ai nomi di proprietà, il cmdlet può essere associato a entrambi gli oggetti usando i due alias di parametro.</span><span class="sxs-lookup"><span data-stu-id="5f583-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="5f583-115">Per altre informazioni sugli alias che possono essere usati con parametri specifici, vedere [nomi di parametri comuni](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="5f583-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="5f583-116">Definizione degli alias di parametro</span><span class="sxs-lookup"><span data-stu-id="5f583-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="5f583-117">Per definire un alias per un parametro, dichiarare l'attributo alias, come illustrato nella dichiarazione di parametro seguente.</span><span class="sxs-lookup"><span data-stu-id="5f583-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="5f583-118">In questo esempio vengono definiti più alias per lo stesso parametro.</span><span class="sxs-lookup"><span data-stu-id="5f583-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="5f583-119">Per ulteriori informazioni, vedere[come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5f583-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5f583-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5f583-120">See Also</span></span>

[<span data-ttu-id="5f583-121">Nomi di parametro comuni</span><span class="sxs-lookup"><span data-stu-id="5f583-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="5f583-122">Come dichiarare i parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f583-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="5f583-123">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f583-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
