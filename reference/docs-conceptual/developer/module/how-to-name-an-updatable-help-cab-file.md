---
title: Come assegnare un nome a un file CAB della Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367160"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="71fbb-102">Come assegnare un nome a un file CAB della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="71fbb-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="71fbb-103">In questo argomento viene illustrato il formato del nome richiesto per il file CAB della Guida aggiornabile (. File CAB).</span><span class="sxs-lookup"><span data-stu-id="71fbb-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="71fbb-104">Come assegnare un nome a un file CAB della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="71fbb-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="71fbb-105">Un file CAB aggiornabile (. File CAB) deve avere un nome con il formato seguente.</span><span class="sxs-lookup"><span data-stu-id="71fbb-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="71fbb-106">Gli elementi del nome sono i seguenti.</span><span class="sxs-lookup"><span data-stu-id="71fbb-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="71fbb-107">ModuleName valore della proprietà **Name** dell'oggetto **ModuleInfo** restituito dal cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .</span><span class="sxs-lookup"><span data-stu-id="71fbb-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="71fbb-108">ModuleGUID il valore della chiave **GUID** nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="71fbb-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="71fbb-109">UICulture le impostazioni cultura dell'interfaccia utente dei file della guida nel file CAB.</span><span class="sxs-lookup"><span data-stu-id="71fbb-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="71fbb-110">Questo valore deve corrispondere al valore di uno degli elementi **UICulture** nel file XML HELPINFO per il modulo.</span><span class="sxs-lookup"><span data-stu-id="71fbb-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="71fbb-111">Ad esempio, se il nome del modulo è "TestModule", il GUID del modulo è 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 e le impostazioni cultura dell'interfaccia utente sono "en-US", il nome del file CAB sarà:</span><span class="sxs-lookup"><span data-stu-id="71fbb-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`