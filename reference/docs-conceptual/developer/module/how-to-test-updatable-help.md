---
title: Come testare la guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367150"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="75255-102">Come testare una Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="75255-102">How to Test Updatable Help</span></span>

<span data-ttu-id="75255-103">Questo argomento descrive gli approcci per testare la guida aggiornabile per un modulo.</span><span class="sxs-lookup"><span data-stu-id="75255-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="75255-104">Uso di Verbose per rilevare gli errori</span><span class="sxs-lookup"><span data-stu-id="75255-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="75255-105">Dopo aver caricato il file XML HelpInfo e i file CAB per il modulo, testare i file eseguendo un comando [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) con il parametro **verbose** .</span><span class="sxs-lookup"><span data-stu-id="75255-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="75255-106">Il parametro **verbose** indica `Update-Help` per segnalare i passaggi critici nelle azioni, dalla lettura della chiave **HelpInfoUri** nel manifesto del modulo per la convalida dei tipi di file nel file CAB decompresso e l'inserimento dei file nel file CAB specifico della lingua Directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="75255-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="75255-107">Quando tutti i messaggi dettagliati vengono risolti, eseguire un comando `Update-Help` con il parametro **debug** .</span><span class="sxs-lookup"><span data-stu-id="75255-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="75255-108">Questo parametro deve rilevare eventuali problemi rimanenti con i file della Guida aggiornabili.</span><span class="sxs-lookup"><span data-stu-id="75255-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>