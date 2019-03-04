---
title: Come assegnare un nome di un File CAB di Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861287"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Come assegnare un nome a un file CAB della Guida aggiornabile

Questo argomento viene illustrato il formato richiesto per il file della Guida aggiornabile CAB (. File CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Come assegnare un nome a un file CAB della Guida aggiornabile

Aggiornabile è un file CAB (. File CAB) deve avere un nome con il formato seguente.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Gli elementi del nome sono come indicato di seguito.

ModuleName il valore del **nome** proprietà delle **ModuleInfo** oggetto a cui il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet restituisce.
Il valore della **nome** proprietà del **ModuleInfo** oggetto a cui il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet restituisce.

ModuleGUID il valore della **GUID** chiave nel manifesto del modulo.

Impostazioni cultura dell'interfaccia utente di UICulture dei file della Guida nel file CAB. Questo valore deve corrispondere al valore di uno dei **UICulture** elementi nel file XML HelpInfo per il modulo.

Ad esempio, se il nome del modulo è "TestModule", il GUID del modulo è 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 e le impostazioni cultura dell'interfaccia utente sono "en-US", il nome del file CAB potrebbe essere:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`