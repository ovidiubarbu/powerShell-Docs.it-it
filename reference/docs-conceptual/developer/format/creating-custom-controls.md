---
title: Creazione di controlli personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363380"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="71ef1-102">Creazione dei controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="71ef1-102">Creating Custom Controls</span></span>

<span data-ttu-id="71ef1-103">I controlli personalizzati sono i componenti più flessibili di un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="71ef1-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="71ef1-104">Diversamente dalla tabella, dall'elenco e dalle viste estese che definiscono una struttura formale di dati, ad esempio una tabella di dati, i controlli personalizzati consentono di definire la modalità di visualizzazione di un singolo elemento di dati.</span><span class="sxs-lookup"><span data-stu-id="71ef1-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="71ef1-105">È possibile definire un set comune di controlli personalizzati disponibili per tutte le visualizzazioni del file di formattazione, è possibile definire controlli personalizzati disponibili per una visualizzazione specifica oppure è possibile definire un set di controlli disponibili per un gruppo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="71ef1-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="71ef1-106">Esempio di controllo personalizzato</span><span class="sxs-lookup"><span data-stu-id="71ef1-106">Custom Control Example</span></span>

<span data-ttu-id="71ef1-107">Nell'esempio seguente viene illustrato un controllo personalizzato definito nel file Certificates. Format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="71ef1-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="71ef1-108">Questo controllo personalizzato viene utilizzato per separare gli oggetti [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) visualizzati in una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="71ef1-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a><span data-ttu-id="71ef1-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="71ef1-109">See Also</span></span>

[<span data-ttu-id="71ef1-110">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="71ef1-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
