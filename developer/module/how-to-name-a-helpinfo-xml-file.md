---
title: Come assegnare un nome di un File XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082397"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Come assegnare un nome a un file XML HelpInfo

Questo argomento viene illustrato il formato richiesto per i file di informazioni della Guida aggiornabile, comunemente noti come file XML HelpInfo.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Come assegnare un nome a un file XML HelpInfo

Un file XML HelpInfo deve avere un nome con il formato seguente.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Gli elementi del nome sono come indicato di seguito.

ModuleName il valore del **nome** proprietà delle **ModuleInfo** oggetto a cui il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet restituisce.

ModuleGUID il valore della **GUID** chiave nel manifesto del modulo.

Ad esempio, se il nome del modulo è "TestModule" e il GUID del modulo è 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, il nome del file XML HelpInfo per il modulo sarà:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`