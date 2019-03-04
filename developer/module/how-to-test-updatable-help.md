---
title: Come testare una Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854737"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="ad042-102">Come testare una Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="ad042-102">How to Test Updatable Help</span></span>

<span data-ttu-id="ad042-103">Questo argomento descrive gli approcci all'esecuzione di test per la Guida aggiornabile per un modulo.</span><span class="sxs-lookup"><span data-stu-id="ad042-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="ad042-104">Uso dettagliato per rilevare gli errori</span><span class="sxs-lookup"><span data-stu-id="ad042-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="ad042-105">Dopo aver caricato il file XML HelpInfo e un file CAB per un modulo, i file di test tramite l'esecuzione di un' [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) con il **Verbose** parametro.</span><span class="sxs-lookup"><span data-stu-id="ad042-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="ad042-106">Il **Verbose** parametro indica `Update-Help` per segnalare i passaggi essenziali relative azioni, di leggere il **HelpInfoUri** chiave nel manifesto del modulo per la convalida i tipi di file nel file CAB decompresso e il posizionamento dei file nella directory del modulo specifico della lingua.</span><span class="sxs-lookup"><span data-stu-id="ad042-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>
<span data-ttu-id="ad042-107">Dopo aver caricato il file XML HelpInfo e un file CAB per un modulo, i file di test tramite l'esecuzione di un' [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) con il **Verbose** parametro.</span><span class="sxs-lookup"><span data-stu-id="ad042-107">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="ad042-108">Il **Verbose** parametro indica `Update-Help` per segnalare i passaggi essenziali relative azioni, di leggere il **HelpInfoUri** chiave nel manifesto del modulo per la convalida i tipi di file nel file CAB decompresso e il posizionamento dei file nella directory del modulo specifico della lingua.</span><span class="sxs-lookup"><span data-stu-id="ad042-108">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="ad042-109">Quando vengono risolti tutti i messaggi dettagliati, eseguire un' `Update-Help` comando con il **Debug** parametro.</span><span class="sxs-lookup"><span data-stu-id="ad042-109">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="ad042-110">Questo parametro deve rilevare eventuali problemi rimanenti con i file della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="ad042-110">This parameter should detect any remaining problems with the Updatable Help files.</span></span>