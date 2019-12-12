---
title: Come impostare i numeri di versione XML di HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360680"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Come impostare i numeri di versione di XML HelpInfo

In questo argomento viene illustrato come impostare e aumentare i numeri di versione in un file di informazioni della Guida aggiornabile, comunemente noto come "file XML HelpInfo".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Come impostare i numeri di versione di XML HelpInfo

I numeri di versione in un file XML HelpInfo sono fondamentali per il funzionamento della Guida aggiornabile.
I cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) scaricano i nuovi file della guida solo quando il numero di versione per le impostazioni cultura dell'interfaccia utente nel file XML HELPINFO remoto è maggiore del numero di versione per le impostazioni cultura dell'interfaccia utente nel codice XML HELPINFO locale oppure non è presente alcun file XML HELPINFO locale.

Il file XML HelpInfo usa il numero di versione in 4 parti definito nella classe **System. Version** del Framework Microsoft .NET. Il formato è `N1.N2.N3.N4`. Gli autori di moduli possono usare qualsiasi schema di numerazione della versione consentito dalla classe **System. Version** . La guida aggiornabile richiede solo che il numero di versione per le impostazioni cultura dell'interfaccia utente aumenti quando una nuova versione del file CAB per le impostazioni cultura dell'interfaccia utente viene caricata nel percorso specificato dall'elemento **HelpContentURI** nel file XML HELPINFO.

Nell'esempio seguente vengono illustrati gli elementi del file XML HelpInfo per le impostazioni cultura dell'interfaccia utente tedesche (de-DE) quando la versione è 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Il numero di versione per le impostazioni cultura dell'interfaccia utente riflette la versione del file CAB per le impostazioni cultura dell'interfaccia utente. Il numero di versione viene applicato all'intero file CAB. Non è possibile impostare numeri di versione diversi per file diversi nel file CAB. Il numero di versione per ogni lingua dell'interfaccia utente viene valutato in modo indipendente e non deve essere correlato ai numeri di versione per altre impostazioni cultura dell'interfaccia utente supportate dal modulo.