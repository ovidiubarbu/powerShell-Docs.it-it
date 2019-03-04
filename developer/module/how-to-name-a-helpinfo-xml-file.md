---
title: Come assegnare un nome di un File XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857827"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="c203a-102">Come assegnare un nome a un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="c203a-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="c203a-103">Questo argomento viene illustrato il formato richiesto per i file di informazioni della Guida aggiornabile, comunemente noti come file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="c203a-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="c203a-104">Come assegnare un nome a un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="c203a-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="c203a-105">Un file XML HelpInfo deve avere un nome con il formato seguente.</span><span class="sxs-lookup"><span data-stu-id="c203a-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="c203a-106">Gli elementi del nome sono come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="c203a-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="c203a-107">ModuleName il valore del **nome** proprietà delle **ModuleInfo** oggetto a cui il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet restituisce.</span><span class="sxs-lookup"><span data-stu-id="c203a-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="c203a-108">Il valore della **nome** proprietà del **ModuleInfo** oggetto a cui il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet restituisce.</span><span class="sxs-lookup"><span data-stu-id="c203a-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="c203a-109">ModuleGUID il valore della **GUID** chiave nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="c203a-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="c203a-110">Ad esempio, se il nome del modulo è "TestModule" e il GUID del modulo è 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, il nome del file XML HelpInfo per il modulo sarà:</span><span class="sxs-lookup"><span data-stu-id="c203a-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`