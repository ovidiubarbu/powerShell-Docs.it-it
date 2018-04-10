---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="044ae-103">Logica per la preparazione di dipendenze dei moduli durante l'operazione di pubblicazione</span><span class="sxs-lookup"><span data-stu-id="044ae-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="044ae-104">I moduli elencati in RequiredModules vengono considerati dipendenze.</span><span class="sxs-lookup"><span data-stu-id="044ae-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="044ae-105">I moduli elencati in NestedModules e la cui base del modulo non è inclusa nella base del modulo specificata vengono considerati dipendenze.</span><span class="sxs-lookup"><span data-stu-id="044ae-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="044ae-106">Le dipendenze precedenti devono essere disponibili nello stesso repository di destinazione. In caso contrario l'operazione di pubblicazione ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="044ae-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="044ae-107">Ad esempio: se 'SnippetPx' non è disponibile nel repository, viene generato l'errore seguente.</span><span class="sxs-lookup"><span data-stu-id="044ae-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="044ae-108">Alcune dipendenze del modulo possono essere gestite esternamente. In tal caso devono essere aggiunte alla voce ExternalModuleDependencies nella sezione PSData del manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="044ae-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="044ae-109">Di seguito è riportata una parte del messaggio di errore precedente:</span><span class="sxs-lookup"><span data-stu-id="044ae-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="044ae-110">*Durante l'installazione del modulo, l'elenco di dipendenze preparato in precedenza viene usato per installare le dipendenze.*</span><span class="sxs-lookup"><span data-stu-id="044ae-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="044ae-111">*Verificare la disponibilità delle dipendenze del modulo in $env:PSModulePath nel sistema durante l'operazione di pubblicazione.*</span><span class="sxs-lookup"><span data-stu-id="044ae-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>