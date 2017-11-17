---
ms.date: 2017-08-25
keywords: powershell,cmdlet
title: Oggetto ObjectModelRoot
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="c378e-103">Oggetto ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="c378e-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="c378e-104">L'oggetto **$psISE**, ovvero l'oggetto radice principale in Windows PowerShell® Integrated Scripting Environment (ISE), è un'istanza della classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="c378e-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="c378e-105">Questo argomento descrive le proprietà dell'oggetto **ObjectModelRoot**.</span><span class="sxs-lookup"><span data-stu-id="c378e-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="c378e-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c378e-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="c378e-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="c378e-107">CurrentFile</span></span>

> <span data-ttu-id="c378e-108">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c378e-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="c378e-109">Proprietà di sola lettura che ottiene il file, il quale è associato a tale oggetto host con stato attivo.</span><span class="sxs-lookup"><span data-stu-id="c378e-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="c378e-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="c378e-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="c378e-111">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c378e-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c378e-112">Proprietà di sola lettura che ottiene la scheda di PowerShell con stato attivo.</span><span class="sxs-lookup"><span data-stu-id="c378e-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="c378e-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="c378e-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="c378e-114">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c378e-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c378e-115">Proprietà di sola lettura che ottiene lo strumento aggiuntivo di Windows PowerShell ISE attualmente visibile che si trova nel riquadro strumenti orizzontale nella parte inferiore dell'editor.</span><span class="sxs-lookup"><span data-stu-id="c378e-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="c378e-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="c378e-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="c378e-117">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c378e-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="c378e-118">Proprietà di sola lettura che ottiene lo strumento aggiuntivo di Windows PowerShell ISE attualmente visibile che si trova nel riquadro strumenti verticale nella parte destra dell'editor.</span><span class="sxs-lookup"><span data-stu-id="c378e-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="c378e-119">Options</span><span class="sxs-lookup"><span data-stu-id="c378e-119">Options</span></span>

> <span data-ttu-id="c378e-120">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c378e-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="c378e-121">Proprietà di sola lettura che ottiene le varie opzioni che possono modificare le impostazioni in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c378e-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="c378e-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="c378e-122">PowerShellTabs</span></span>

> <span data-ttu-id="c378e-123">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c378e-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="c378e-124">Proprietà di sola lettura che ottiene la raccolta di schede di PowerShell, che sono aperte in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c378e-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="c378e-125">Per impostazione predefinita, questo oggetto contiene una sola scheda di PowerShell. Tuttavia, è possibile aggiungere altre schede di PowerShell a questo oggetto usando gli script o i menu di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c378e-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="c378e-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c378e-126">See Also</span></span>

- [<span data-ttu-id="c378e-127">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c378e-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c378e-128">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c378e-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="c378e-129">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="c378e-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
