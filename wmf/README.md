---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="windows-management-framework"></a><span data-ttu-id="7ff6a-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="7ff6a-103">Windows Management Framework</span></span>

<span data-ttu-id="7ff6a-104">Windows Management Framework (WMF) è un meccanismo di distribuzione che offre un'interfaccia di gestione coerente delle varie caratteristiche di Windows e Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="7ff6a-105">Con l'installazione di WMF, i clienti ottengono un modo semplice per l'interazione tra diversi sistemi operativi nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="7ff6a-106">WMF rende disponibili gli aggiornamenti alle funzionalità di gestione, in una determinata versione di Windows e Windows Server, disponibile per l'installazione nelle versioni precedenti (in genere 2 versioni precedenti) di Windows e Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="7ff6a-107">L'installazione di WMF aggiunge e/o aggiorna le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="7ff6a-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ff6a-108">Windows PowerShell</span></span>
- <span data-ttu-id="7ff6a-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="7ff6a-110">Windows PowerShell Integrated Script Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="7ff6a-111">Gestione remota Windows (WinRM)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="7ff6a-112">Strumentazione gestione Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="7ff6a-113">Servizi Web di Windows PowerShell (estensione IIS OData di gestione)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="7ff6a-114">Registrazione inventario software (SIL)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="7ff6a-115">Provider CIM di gestione del server</span><span class="sxs-lookup"><span data-stu-id="7ff6a-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="7ff6a-116">Note sulla versione di WMF</span><span class="sxs-lookup"><span data-stu-id="7ff6a-116">WMF Release Notes</span></span>
<span data-ttu-id="7ff6a-117">Per informazioni sui vari miglioramenti in PowerShell e altri componenti di una determinata versione di WMF, consultare i collegamenti seguenti per rivedere le note sulla versione:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>


- [<span data-ttu-id="7ff6a-118">WMF 5.1 (Preview)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-118">WMF 5.1 (Preview)</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="7ff6a-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="7ff6a-119">WMF 5.0</span></span>](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="7ff6a-120">Disponibilità di WMF tra i sistemi operativi Windows</span><span class="sxs-lookup"><span data-stu-id="7ff6a-120">WMF Availability Across Windows Operating Systems</span></span>

><span data-ttu-id="7ff6a-121">TODO: Aggiungere collegamenti a WMF DLC nell'intestazione di colonna</span><span class="sxs-lookup"><span data-stu-id="7ff6a-121">TODO: Add links to specific WMF DLC on the column header</span></span>

| <span data-ttu-id="7ff6a-122">Versione del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="7ff6a-122">Operating System Version</span></span> | [<span data-ttu-id="7ff6a-123">WMF 5.1 Preview*</span><span class="sxs-lookup"><span data-stu-id="7ff6a-123">WMF 5.1 Preview*</span></span>]() | [<span data-ttu-id="7ff6a-124">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="7ff6a-124">WMF 5.0</span></span>]() | [<span data-ttu-id="7ff6a-125">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="7ff6a-125">WMF 4.0</span></span>]() |  [<span data-ttu-id="7ff6a-126">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="7ff6a-126">WMF 3.0</span></span>]() | [<span data-ttu-id="7ff6a-127">WMF (2.0)</span><span class="sxs-lookup"><span data-stu-id="7ff6a-127">WMF (2.0)</span></span>]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="7ff6a-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="7ff6a-128">Windows Server 2016</span></span> | <span data-ttu-id="7ff6a-129">Incluso*</span><span class="sxs-lookup"><span data-stu-id="7ff6a-129">Ships in-box*</span></span> | <span data-ttu-id="7ff6a-130">Incluso*</span><span class="sxs-lookup"><span data-stu-id="7ff6a-130">Ships in-box*</span></span> |  |  |  |
| <span data-ttu-id="7ff6a-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="7ff6a-131">Windows 10</span></span> | <span data-ttu-id="7ff6a-132">Incluso*</span><span class="sxs-lookup"><span data-stu-id="7ff6a-132">Ships in-box*</span></span> | <span data-ttu-id="7ff6a-133">Incluso*</span><span class="sxs-lookup"><span data-stu-id="7ff6a-133">Ships in-box*</span></span>  | | | |  
| <span data-ttu-id="7ff6a-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7ff6a-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="7ff6a-135">??</span><span class="sxs-lookup"><span data-stu-id="7ff6a-135">??</span></span> | <span data-ttu-id="7ff6a-136">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-136">Yes</span></span> | <span data-ttu-id="7ff6a-137">Incluso</span><span class="sxs-lookup"><span data-stu-id="7ff6a-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="7ff6a-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7ff6a-138">Windows 8.1</span></span> | <span data-ttu-id="7ff6a-139">??</span><span class="sxs-lookup"><span data-stu-id="7ff6a-139">??</span></span> | <span data-ttu-id="7ff6a-140">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-140">Yes</span></span> |  <span data-ttu-id="7ff6a-141">Incluso</span><span class="sxs-lookup"><span data-stu-id="7ff6a-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="7ff6a-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7ff6a-142">Windows Server 2012</span></span> | <span data-ttu-id="7ff6a-143">??</span><span class="sxs-lookup"><span data-stu-id="7ff6a-143">??</span></span> | <span data-ttu-id="7ff6a-144">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-144">Yes</span></span> | <span data-ttu-id="7ff6a-145">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-145">Yes</span></span> |  <span data-ttu-id="7ff6a-146">Incluso</span><span class="sxs-lookup"><span data-stu-id="7ff6a-146">Ships in-box</span></span> | |
| <span data-ttu-id="7ff6a-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="7ff6a-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="7ff6a-148">Incluso</span><span class="sxs-lookup"><span data-stu-id="7ff6a-148">Ships in-box</span></span> | |
| <span data-ttu-id="7ff6a-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="7ff6a-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="7ff6a-150">??</span><span class="sxs-lookup"><span data-stu-id="7ff6a-150">??</span></span> | <span data-ttu-id="7ff6a-151">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-151">Yes</span></span> | <span data-ttu-id="7ff6a-152">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-152">Yes</span></span> |  <span data-ttu-id="7ff6a-153">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-153">Yes</span></span>| <span data-ttu-id="7ff6a-154">Incluso</span><span class="sxs-lookup"><span data-stu-id="7ff6a-154">Ships in-box</span></span> |
| <span data-ttu-id="7ff6a-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="7ff6a-155">Windows 7 SP1</span></span>  | <span data-ttu-id="7ff6a-156">??</span><span class="sxs-lookup"><span data-stu-id="7ff6a-156">??</span></span> | <span data-ttu-id="7ff6a-157">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-157">Yes</span></span> | <span data-ttu-id="7ff6a-158">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-158">Yes</span></span> | <span data-ttu-id="7ff6a-159">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-159">Yes</span></span> | <span data-ttu-id="7ff6a-160">Incluso</span><span class="sxs-lookup"><span data-stu-id="7ff6a-160">Ships in-box</span></span> |
| <span data-ttu-id="7ff6a-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="7ff6a-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="7ff6a-162">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-162">Yes</span></span> | <span data-ttu-id="7ff6a-163">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-163">Yes</span></span> |
| <span data-ttu-id="7ff6a-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="7ff6a-164">Windows Vista</span></span> | | | | | <span data-ttu-id="7ff6a-165">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-165">Yes</span></span> |
| <span data-ttu-id="7ff6a-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="7ff6a-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="7ff6a-167">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-167">Yes</span></span> |
| <span data-ttu-id="7ff6a-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="7ff6a-168">Windows XP</span></span> | | | |  | <span data-ttu-id="7ff6a-169">Sì</span><span class="sxs-lookup"><span data-stu-id="7ff6a-169">Yes</span></span> |

><span data-ttu-id="7ff6a-170">TODO: Spiegare * nella tabella precedente</span><span class="sxs-lookup"><span data-stu-id="7ff6a-170">TODO: Explain * in the above table</span></span>
