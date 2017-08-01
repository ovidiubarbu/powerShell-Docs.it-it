---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: considerazioni per la limitazione dei comandi
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="5b68d-103">Considerazioni per la limitazione dei comandi</span><span class="sxs-lookup"><span data-stu-id="5b68d-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="5b68d-104">Questo passaggio richiede una puntualizzazione.</span><span class="sxs-lookup"><span data-stu-id="5b68d-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="5b68d-105">È essenziale che tutte le funzionalità esposte con JEA si trovino in aree con restrizioni di amministratore.</span><span class="sxs-lookup"><span data-stu-id="5b68d-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="5b68d-106">Gli utenti non amministratori non devono essere in grado di modificare gli script usati negli endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="5b68d-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="5b68d-107">Si noti che è fondamentale non concedere agli utenti di JEA la possibilità di sovrascrivere le configurazioni di JEA e gli script consentiti all'interno delle proprie sessioni di JEA.</span><span class="sxs-lookup"><span data-stu-id="5b68d-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="5b68d-108">Prestare particolare attenzione quando si espongono comandi come `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="5b68d-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

