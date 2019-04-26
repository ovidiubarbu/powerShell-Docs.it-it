---
title: Dichiarazione di classe cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068641"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="359db-102">Dichiarazione della classe dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="359db-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="359db-103">Una classe di Microsoft .NET Framework è dichiarata come un cmdlet, specificando il **Cmdlet** attributo sotto forma di metadati per la classe.</span><span class="sxs-lookup"><span data-stu-id="359db-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="359db-104">(Il **Cmdlet** attributo è l'unico attributo obbligatorio per tutti i cmdlet).</span><span class="sxs-lookup"><span data-stu-id="359db-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="359db-105">Quando si specifica la **Cmdlet** attributo, è necessario specificare la coppia di verbo e nome che identifica il cmdlet per l'utente.</span><span class="sxs-lookup"><span data-stu-id="359db-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="359db-106">E, è necessario descrivere le funzionalità di Windows PowerShell che supporta il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="359db-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="359db-107">Per altre informazioni sulla sintassi di dichiarazione che consente di specificare il **Cmdlet** dell'attributo, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="359db-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="359db-108">Il **Cmdlet** dipende dall'attributo le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="359db-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="359db-109">Le proprietà di questa classe corrispondono ai parametri utilizzati quando si dichiara l'attributo di dichiarazione.</span><span class="sxs-lookup"><span data-stu-id="359db-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="359db-110">Sostantivi</span><span class="sxs-lookup"><span data-stu-id="359db-110">Nouns</span></span>

<span data-ttu-id="359db-111">Il sostantivo del cmdlet consente di specificare le risorse su cui agisce il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="359db-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="359db-112">Il sostantivo riconosce la differenza dei cmdlet da altri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="359db-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="359db-113">Sostantivi nei nomi dei cmdlet devono essere specifico e, nel caso di sostantivi generici, ad esempio *server*, è consigliabile aggiungere un prefisso breve che consentono di distinguere le risorse da altre risorse simili.</span><span class="sxs-lookup"><span data-stu-id="359db-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="359db-114">Ad esempio, è un nome di cmdlet che include un sostantivo con un prefisso `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="359db-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="359db-115">La combinazione di un sostantivo specifico con un verbo più generale consente all'utente di individuare rapidamente i cmdlet per la relativa azione e quindi identificando il cmdlet per la propria risorsa evitando la duplicazione del nome cmdlet non necessari.</span><span class="sxs-lookup"><span data-stu-id="359db-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="359db-116">Per un elenco di caratteri speciali che non può essere usato nei nomi di cmdlet, vedere [linee guida sullo sviluppo necessari](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="359db-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="359db-117">Verbi</span><span class="sxs-lookup"><span data-stu-id="359db-117">Verbs</span></span>

<span data-ttu-id="359db-118">Quando si specifica un verbo, le linee guida sullo sviluppo richiedono di usare uno dei verbi predefiniti forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="359db-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="359db-119">Usando uno di questi verbi predefiniti, si garantisce la coerenza tra i cmdlet personalizzati e i cmdlet che vengono scritti da Microsoft e da altri utenti.</span><span class="sxs-lookup"><span data-stu-id="359db-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="359db-120">Ad esempio, il verbo "Get" viene usato per i cmdlet che recuperano i dati.</span><span class="sxs-lookup"><span data-stu-id="359db-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="359db-121">Per altre informazioni sulle linee guida per i verbi, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="359db-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="359db-122">Per un elenco di caratteri speciali che non può essere usato nei nomi di cmdlet, vedere [linee guida sullo sviluppo necessari](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="359db-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="359db-123">Supporto di funzionalità di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="359db-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="359db-124">Il **Cmdlet** attributo consente inoltre di specificare che il cmdlet supporta alcune delle funzionalità comune fornita da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="359db-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="359db-125">Ciò include il supporto per le funzionalità comuni, ad esempio conferma di commenti e suggerimenti utente (detto supporto per la funzionalità di ShouldProcess) e supporto per le transazioni.</span><span class="sxs-lookup"><span data-stu-id="359db-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="359db-126">(Supporto delle transazioni è stato introdotto in Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="359db-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="359db-127">Per altre informazioni sulla sintassi di dichiarazione che consente di specificare il **Cmdlet** dell'attributo, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="359db-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="359db-128">Definizione della classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="359db-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="359db-129">Il codice seguente è la definizione per una classe cmdlet GetProc.</span><span class="sxs-lookup"><span data-stu-id="359db-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="359db-130">Si noti che la convenzione Pascal maiuscole e minuscole viene utilizzata e che il nome della classe include il verbo e nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="359db-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="359db-131">La convenzione Pascal maiuscole e minuscole</span><span class="sxs-lookup"><span data-stu-id="359db-131">Pascal Casing</span></span>

<span data-ttu-id="359db-132">Quando si assegna un nome cmdlet, utilizzare la convenzione Pascal maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="359db-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="359db-133">Ad esempio, il `Get-Item` e `Get-ItemProperty` cmdlet mostrano il modo corretto da utilizzare per l'uso delle maiuscole denominazione cmdlet.</span><span class="sxs-lookup"><span data-stu-id="359db-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="359db-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="359db-134">See Also</span></span>

[<span data-ttu-id="359db-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="359db-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="359db-136">Dichiarazione CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="359db-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="359db-137">Nomi di verbi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="359db-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="359db-138">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="359db-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="359db-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="359db-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
