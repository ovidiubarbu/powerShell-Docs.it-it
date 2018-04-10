---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: Oggetto ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="bbfc8-103">Oggetto ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="bbfc8-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="bbfc8-104">L'oggetto **$psISE**, ovvero l'oggetto radice principale in Windows PowerShell® Integrated Scripting Environment (ISE), è un'istanza della classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="bbfc8-105">Questo argomento descrive le proprietà dell'oggetto **ObjectModelRoot**.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="bbfc8-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="bbfc8-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="bbfc8-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="bbfc8-107">CurrentFile</span></span>

> <span data-ttu-id="bbfc8-108">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bbfc8-109">Proprietà di sola lettura che ottiene il file, il quale è associato a tale oggetto host con stato attivo.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="bbfc8-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="bbfc8-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="bbfc8-111">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bbfc8-112">Proprietà di sola lettura che ottiene la scheda di PowerShell con stato attivo.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="bbfc8-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="bbfc8-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="bbfc8-114">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bbfc8-115">Proprietà di sola lettura che ottiene lo strumento aggiuntivo di Windows PowerShell ISE attualmente visibile che si trova nel riquadro strumenti orizzontale nella parte inferiore dell'editor.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="bbfc8-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="bbfc8-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="bbfc8-117">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bbfc8-118">Proprietà di sola lettura che ottiene lo strumento aggiuntivo di Windows PowerShell ISE attualmente visibile che si trova nel riquadro strumenti verticale nella parte destra dell'editor.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="bbfc8-119">Options</span><span class="sxs-lookup"><span data-stu-id="bbfc8-119">Options</span></span>

> <span data-ttu-id="bbfc8-120">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bbfc8-121">Proprietà di sola lettura che ottiene le varie opzioni che possono modificare le impostazioni in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="bbfc8-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="bbfc8-122">PowerShellTabs</span></span>

> <span data-ttu-id="bbfc8-123">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bbfc8-124">Proprietà di sola lettura che ottiene la raccolta di schede di PowerShell, che sono aperte in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="bbfc8-125">Per impostazione predefinita, questo oggetto contiene una sola scheda di PowerShell. Tuttavia, è possibile aggiungere altre schede di PowerShell a questo oggetto usando gli script o i menu di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbfc8-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bbfc8-126">See Also</span></span>

- [<span data-ttu-id="bbfc8-127">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bbfc8-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="bbfc8-128">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="bbfc8-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)