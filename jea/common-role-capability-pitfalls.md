---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "problemi comuni delle capacità del ruolo"
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="56beb-103">Problemi comuni delle capacità del ruolo</span><span class="sxs-lookup"><span data-stu-id="56beb-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="56beb-104">È possibile incorrere in alcuni inconvenienti durante il processo.</span><span class="sxs-lookup"><span data-stu-id="56beb-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="56beb-105">Questa guida rapida illustra come identificare e risolvere tali inconvenienti quando si modifica o si crea un nuovo endpoint:</span><span class="sxs-lookup"><span data-stu-id="56beb-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="56beb-106">Funzioni e Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56beb-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="56beb-107">I comandi di PowerShell scritti in PowerShell sono funzioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56beb-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="56beb-108">I comandi di PowerShell scritti come classi .NET specializzate sono cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56beb-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="56beb-109">È possibile verificare il tipo di comando eseguendo `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="56beb-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="56beb-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="56beb-110">VisibleProviders</span></span>
<span data-ttu-id="56beb-111">È necessario esporre qualsiasi provider richiesto dai comandi.</span><span class="sxs-lookup"><span data-stu-id="56beb-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="56beb-112">Il più comune è il provider FileSystem, ma potrebbe essere necessario esporne altri, ad esempio il provider Registry.</span><span class="sxs-lookup"><span data-stu-id="56beb-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="56beb-113">Per un'introduzione ai provider, vedere il [post del blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span><span class="sxs-lookup"><span data-stu-id="56beb-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="56beb-114">Prestare attenzione quando si espongono i provider: spesso è preferibile definire una propria funzione da usare con i provider sottostanti anziché esporre direttamente il provider in una sessione di JEA.</span><span class="sxs-lookup"><span data-stu-id="56beb-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="56beb-115">In questo modo è comunque possibile consentire agli utenti di lavorare con file, chiavi del Registro di sistema e così via, mantenendo tuttavia il controllo su **quali** file e chiavi del Registro di sistema possono essere usati con la logica di convalida personalizzata.</span><span class="sxs-lookup"><span data-stu-id="56beb-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

