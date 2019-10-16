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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367160"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Come assegnare un nome a un file CAB della Guida aggiornabile

In questo argomento viene illustrato il formato del nome richiesto per il file CAB della Guida aggiornabile (. File CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Come assegnare un nome a un file CAB della Guida aggiornabile

Un file CAB aggiornabile (. File CAB) deve avere un nome con il formato seguente.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Gli elementi del nome sono i seguenti.

ModuleName valore della proprietà **Name** dell'oggetto **ModuleInfo** restituito dal cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .

ModuleGUID il valore della chiave **GUID** nel manifesto del modulo.

UICulture le impostazioni cultura dell'interfaccia utente dei file della guida nel file CAB. Questo valore deve corrispondere al valore di uno degli elementi **UICulture** nel file XML HELPINFO per il modulo.

Ad esempio, se il nome del modulo è "TestModule", il GUID del modulo è 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 e le impostazioni cultura dell'interfaccia utente sono "en-US", il nome del file CAB sarà:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`