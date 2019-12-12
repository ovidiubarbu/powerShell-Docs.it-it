---
title: Come assegnare un nome a un file XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367200"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="990ed-102">Come assegnare un nome a un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="990ed-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="990ed-103">In questo argomento viene illustrato il formato del nome richiesto per i file di informazioni della Guida aggiornabili, comunemente noti come file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="990ed-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="990ed-104">Come assegnare un nome a un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="990ed-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="990ed-105">Un file XML HelpInfo deve avere un nome con il formato seguente.</span><span class="sxs-lookup"><span data-stu-id="990ed-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="990ed-106">Gli elementi del nome sono i seguenti.</span><span class="sxs-lookup"><span data-stu-id="990ed-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="990ed-107">ModuleName valore della proprietà **Name** dell'oggetto **ModuleInfo** restituito dal cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .</span><span class="sxs-lookup"><span data-stu-id="990ed-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="990ed-108">ModuleGUID il valore della chiave **GUID** nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="990ed-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="990ed-109">Ad esempio, se il nome del modulo è "TestModule" e il GUID del modulo è 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, il nome del file XML HelpInfo per il modulo sarà:</span><span class="sxs-lookup"><span data-stu-id="990ed-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`