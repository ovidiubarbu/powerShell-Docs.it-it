---
title: Dichiarazione di classe del cmdlet | Microsoft Docs
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
ms.openlocfilehash: 0de49d979c31b0e8d111323a2e1899d97868ec3f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978713"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="0ffb3-102">Dichiarazione della classe dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ffb3-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="0ffb3-103">Una classe Microsoft .NET Framework viene dichiarata come cmdlet specificando l'attributo del **cmdlet** come metadati per la classe.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="0ffb3-104">L'attributo del **cmdlet** è l'unico attributo obbligatorio per tutti i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span>
<span data-ttu-id="0ffb3-105">Quando si specifica l'attributo del **cmdlet** , è necessario specificare la coppia verbo-e-nome che identifica il cmdlet per l'utente.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="0ffb3-106">È necessario descrivere la funzionalità di Windows PowerShell supportata dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="0ffb3-107">Per ulteriori informazioni sulla sintassi di dichiarazione utilizzata per specificare l'attributo **cmdlet** , vedere Dichiarazione dell' [attributo del cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0ffb3-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0ffb3-108">L'attributo **cmdlet** viene definito dalla classe [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0ffb3-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="0ffb3-109">Le proprietà di questa classe corrispondono ai parametri di dichiarazione usati quando si dichiara l'attributo.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="0ffb3-110">Nomi</span><span class="sxs-lookup"><span data-stu-id="0ffb3-110">Nouns</span></span>

<span data-ttu-id="0ffb3-111">Il sostantivo del cmdlet specifica le risorse su cui agisce il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="0ffb3-112">Il sostantivo distingue i cmdlet da altri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="0ffb3-113">I sostantivi nei nomi dei cmdlet devono essere specifici e, nel caso di sostantivi generici, ad esempio *Server*, è preferibile aggiungere un prefisso breve che differenzi la risorsa da altre risorse simili.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="0ffb3-114">Ad esempio, un nome di cmdlet che include un sostantivo con un prefisso è `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="0ffb3-115">La combinazione di un sostantivo specifico con un verbo più generale consente all'utente di individuare rapidamente il cmdlet mediante la relativa azione e quindi di identificare il cmdlet mediante la relativa risorsa evitando la duplicazione del nome di cmdlet non necessaria.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="0ffb3-116">Per un elenco di caratteri speciali che non possono essere usati nei nomi di cmdlet, vedere le [linee guida per lo sviluppo necessarie](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="0ffb3-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="0ffb3-117">Verbi</span><span class="sxs-lookup"><span data-stu-id="0ffb3-117">Verbs</span></span>

<span data-ttu-id="0ffb3-118">Quando si specifica un verbo, le linee guida per lo sviluppo richiedono l'uso di uno dei verbi predefiniti forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="0ffb3-119">Utilizzando uno di questi verbi predefiniti, sarà garantita la coerenza tra i cmdlet scritti da e i cmdlet scritti da Microsoft e da altri.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="0ffb3-120">Il verbo "Get", ad esempio, viene usato per i cmdlet che recuperano i dati.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="0ffb3-121">Per ulteriori informazioni sulle linee guida per i verbi, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0ffb3-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="0ffb3-122">Per un elenco di caratteri speciali che non possono essere usati nei nomi di cmdlet, vedere le [linee guida per lo sviluppo necessarie](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="0ffb3-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="0ffb3-123">Supporto della funzionalità di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ffb3-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="0ffb3-124">L'attributo **cmdlet** consente inoltre di specificare che il cmdlet supporta alcune delle funzionalità comuni fornite da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="0ffb3-125">Questo include il supporto per le funzionalità comuni, ad esempio la conferma dei commenti e suggerimenti degli utenti, denominate supporto per la funzionalità ShouldProcess, e il supporto per le transazioni.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="0ffb3-126">(Il supporto per le transazioni è stato introdotto in Windows PowerShell 2,0).</span><span class="sxs-lookup"><span data-stu-id="0ffb3-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="0ffb3-127">Per ulteriori informazioni sulla sintassi di dichiarazione utilizzata per specificare l'attributo **cmdlet** , vedere Dichiarazione dell' [attributo del cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0ffb3-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="0ffb3-128">Definizione della classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ffb3-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="0ffb3-129">Il codice seguente è la definizione di una classe di cmdlet GetProc.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="0ffb3-130">Si noti che viene utilizzata la combinazione di maiuscole e minuscole Pascal e che il nome della classe include il verbo e il sostantivo del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a><span data-ttu-id="0ffb3-131">Maiuscole e minuscole Pascal</span><span class="sxs-lookup"><span data-stu-id="0ffb3-131">Pascal Casing</span></span>

<span data-ttu-id="0ffb3-132">Quando si denominano i cmdlet, utilizzare la convenzione Pascal.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="0ffb3-133">I cmdlet `Get-Item` e `Get-ItemProperty`, ad esempio, illustrano il modo corretto per usare le maiuscole durante la denominazione dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ffb3-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ffb3-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ffb3-134">See Also</span></span>

[<span data-ttu-id="0ffb3-135">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="0ffb3-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="0ffb3-136">Dichiarazione CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="0ffb3-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="0ffb3-137">Nomi dei verbi dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ffb3-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="0ffb3-138">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ffb3-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="0ffb3-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0ffb3-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
