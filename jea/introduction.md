---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: introduzione
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="introduction"></a><span data-ttu-id="eb0cd-103">Introduzione</span><span class="sxs-lookup"><span data-stu-id="eb0cd-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="eb0cd-104">**Motivazione**</span><span class="sxs-lookup"><span data-stu-id="eb0cd-104">**Motivation**</span></span>  
<span data-ttu-id="eb0cd-105">Quando si concede a un utente l'accesso con privilegi ai propri sistemi, si estende il limite di trust a tale utente.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="eb0cd-106">Questo è un rischio: gli amministratori sono una superficie di attacco.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="eb0cd-107">Gli attacchi interni e le credenziali rubate sono sia reali che comuni.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="eb0cd-108">**Non è un problema nuovo**</span><span class="sxs-lookup"><span data-stu-id="eb0cd-108">**Not a new problem**</span></span>  
<span data-ttu-id="eb0cd-109">Probabilmente si ha familiarità con il principio di privilegio minimo e si può usare una forma di controllo degli accessi in base al ruolo (RBAC) con le applicazioni che la gestiscono.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="eb0cd-110">Tuttavia, l'efficacia e la gestibilità di queste soluzioni spesso sono limitate a causa della vastità dell'ambito dall'imprecisione.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="eb0cd-111">E la copertura RBAC presenta anche delle lacune.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="eb0cd-112">In Windows, ad esempio, l'accesso con privilegi è sostanzialmente un commutatore binario, che forza la concessione di autorizzazioni non necessarie quando si aggiungono utenti al gruppo Administrators.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="eb0cd-113">**JEA (Just Enough Administration)**</span><span class="sxs-lookup"><span data-stu-id="eb0cd-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="eb0cd-114">Offre una piattaforma di controllo degli accessi in base al ruolo (RBAC) tramite Comunicazione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="eb0cd-115">*Consente a utenti specifici di eseguire attività amministrative specifiche sui server senza concedere loro diritti di amministratore.*</span><span class="sxs-lookup"><span data-stu-id="eb0cd-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="eb0cd-116">Ciò consente di colmare le lacune tra le soluzioni RBAC esistenti e semplifica la gestione delle impostazioni.</span><span class="sxs-lookup"><span data-stu-id="eb0cd-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

