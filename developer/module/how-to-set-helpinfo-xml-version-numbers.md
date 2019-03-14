---
title: Come impostare i numeri di versione XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: d69e8a734aa96ff9b7911815fb43b81103548b59
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794349"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Come impostare i numeri di versione di XML HelpInfo

In questo argomento viene illustrato come impostare e aumentare i numeri di versione in un file di informazioni della Guida aggiornabile, comunemente noto come "file XML HelpInfo".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Come impostare i numeri di versione di XML HelpInfo

I numeri di versione in un file XML HelpInfo sono fondamentali per il funzionamento di Guida aggiornabile. Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet scaricano nuovi file della Guida solo quando il numero di versione per impostazioni cultura dell'interfaccia utente nel file XML HelpInfo remoto è maggiore del numero di versione per le impostazioni cultura dell'interfaccia utente di XML HelpInfo locale, o è presente alcun file XML HelpInfo locale.

Il file XML HelpInfo utilizza il numero di versione in 4 parti definito nel **Version** classi di Microsoft .NET Framework. Il formato è `N1.N2.N3.N4`. Gli autori di moduli possono usare qualsiasi schema che è consentito di numerazione delle versioni di **Version** classe. La Guida aggiornabile richiede solo che il numero di versione per un aumento delle impostazioni cultura dell'interfaccia utente quando una nuova versione del file CAB per tali impostazioni cultura dell'interfaccia utente viene caricata nel percorso specificato dal **HelpContentURI** elemento nel file XML HelpInfo.

Nell'esempio seguente mostra gli elementi del file XML HelpInfo per il tedesco (de-DE) dell'interfaccia utente delle impostazioni cultura quando la versione è 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Il numero di versione per impostazioni cultura dell'interfaccia utente riflette la versione del file CAB per tali impostazioni cultura dell'interfaccia utente. Il numero di versione si applica all'intero file CAB. Nel file CAB non è possibile impostare i numeri di versione diversi per diversi file. Il numero di versione per ogni impostazione cultura dell'interfaccia utente viene valutato in modo indipendente e non devono avere in comune per i numeri di versione per altre impostazioni cultura dell'interfaccia utente supportate dal modulo.