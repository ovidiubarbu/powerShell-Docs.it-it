---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: blacklist
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
### <a name="on-blacklisting"></a><span data-ttu-id="e1864-103">Blacklist</span><span class="sxs-lookup"><span data-stu-id="e1864-103">On Blacklisting</span></span>
<span data-ttu-id="e1864-104">Dopo essersi esercitati con JEA, ci si potrebbe chiedere se è possibile disattivare i comandi.</span><span class="sxs-lookup"><span data-stu-id="e1864-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="e1864-105">Si tratta di una domanda legittima, ma l'operazione non è attualmente prevista per JEA per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="e1864-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="e1864-106">JEA è stato progettato per limitare gli operatori solo alle azioni che devono svolgere.</span><span class="sxs-lookup"><span data-stu-id="e1864-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="e1864-107">La blacklist è un concetto opposto.</span><span class="sxs-lookup"><span data-stu-id="e1864-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="e1864-108">Gli autori dei comandi di PowerShell non hanno progettato i comandi di PowerShell prendendo in considerazione JEA.</span><span class="sxs-lookup"><span data-stu-id="e1864-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="e1864-109">In una nuova installazione di Windows Server 2016 sono immediatamente disponibili circa 1520 comandi.</span><span class="sxs-lookup"><span data-stu-id="e1864-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="e1864-110">I modelli di rischio per questi comandi non includono la possibilità che un utente esegua i comandi come account con più privilegi.</span><span class="sxs-lookup"><span data-stu-id="e1864-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="e1864-111">Ad esempio, alcuni comandi consentono l'inserimento di codice a livello di progettazione (Add-Type e Invoke-Command nel modulo core di PowerShell).</span><span class="sxs-lookup"><span data-stu-id="e1864-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="e1864-112">JEA visualizza un avviso quando si espongono i comandi visti in precedenza, ma tutti gli altri comandi di Windows non sono stati nuovamente valutati in base al nuovo modello di rischio.</span><span class="sxs-lookup"><span data-stu-id="e1864-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="e1864-113">È necessario comprendere le capacità dei comandi che si espongono con JEA.</span><span class="sxs-lookup"><span data-stu-id="e1864-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="e1864-114">E anche se JEA blocca tutti i comandi con vulnerabilità tipo "code injection", non vi sono garanzie che un utente malintenzionato non sia in grado di eseguire un'azione inserita nella blacklist con un altro comando correlato.</span><span class="sxs-lookup"><span data-stu-id="e1864-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="e1864-115">Se non si comprendono tutti i comandi che si intende esporre, non è possibile garantire che una determinata operazione non venga eseguita.</span><span class="sxs-lookup"><span data-stu-id="e1864-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="e1864-116">L'impegno consiste nel comprendere i comandi esposti e se tali comandi usano una whitelist o una blacklist.</span><span class="sxs-lookup"><span data-stu-id="e1864-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="e1864-117">Il numero di comandi che possono essere esposti in base a una blacklist è da gestire, quindi JEA viene implementato usando invece delle whitelist.</span><span class="sxs-lookup"><span data-stu-id="e1864-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

