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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363380"
---
# <a name="creating-custom-controls"></a>Creazione dei controlli personalizzati

I controlli personalizzati sono i componenti più flessibili di un file di formattazione. Diversamente dalla tabella, dall'elenco e dalle viste estese che definiscono una struttura formale di dati, ad esempio una tabella di dati, i controlli personalizzati consentono di definire la modalità di visualizzazione di un singolo elemento di dati. È possibile definire un set comune di controlli personalizzati disponibili per tutte le visualizzazioni del file di formattazione, è possibile definire controlli personalizzati disponibili per una visualizzazione specifica oppure è possibile definire un set di controlli disponibili per un gruppo di oggetti.

## <a name="custom-control-example"></a>Esempio di controllo personalizzato

Nell'esempio seguente viene illustrato un controllo personalizzato definito nel file Certificates. Format. ps1xml. Questo controllo personalizzato viene utilizzato per separare gli oggetti [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) visualizzati in una visualizzazione tabella.

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

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
