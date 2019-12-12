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
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="3ed3a-102">Come impostare i numeri di versione di XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="3ed3a-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="3ed3a-103">In questo argomento viene illustrato come impostare e aumentare i numeri di versione in un file di informazioni della Guida aggiornabile, comunemente noto come "file XML HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="3ed3a-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="3ed3a-104">Come impostare i numeri di versione di XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="3ed3a-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="3ed3a-105">I numeri di versione in un file XML HelpInfo sono fondamentali per il funzionamento della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="3ed3a-106">I cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) scaricano i nuovi file della guida solo quando il numero di versione per le impostazioni cultura dell'interfaccia utente nel file XML HELPINFO remoto è maggiore del numero di versione per le impostazioni cultura dell'interfaccia utente nel codice XML HELPINFO locale oppure non è presente alcun file XML HELPINFO locale.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="3ed3a-107">Il file XML HelpInfo usa il numero di versione in 4 parti definito nella classe **System. Version** del Framework Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="3ed3a-108">Il formato è `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="3ed3a-109">Gli autori di moduli possono usare qualsiasi schema di numerazione della versione consentito dalla classe **System. Version** .</span><span class="sxs-lookup"><span data-stu-id="3ed3a-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="3ed3a-110">La guida aggiornabile richiede solo che il numero di versione per le impostazioni cultura dell'interfaccia utente aumenti quando una nuova versione del file CAB per le impostazioni cultura dell'interfaccia utente viene caricata nel percorso specificato dall'elemento **HelpContentURI** nel file XML HELPINFO.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="3ed3a-111">Nell'esempio seguente vengono illustrati gli elementi del file XML HelpInfo per le impostazioni cultura dell'interfaccia utente tedesche (de-DE) quando la versione è 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="3ed3a-112">Il numero di versione per le impostazioni cultura dell'interfaccia utente riflette la versione del file CAB per le impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="3ed3a-113">Il numero di versione viene applicato all'intero file CAB.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="3ed3a-114">Non è possibile impostare numeri di versione diversi per file diversi nel file CAB.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="3ed3a-115">Il numero di versione per ogni lingua dell'interfaccia utente viene valutato in modo indipendente e non deve essere correlato ai numeri di versione per altre impostazioni cultura dell'interfaccia utente supportate dal modulo.</span><span class="sxs-lookup"><span data-stu-id="3ed3a-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>