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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066686"
---
# <a name="creating-custom-controls"></a>Creazione dei controlli personalizzati

Controlli personalizzati sono i componenti più flessibili di un file di formattazione. A differenza di tabella, elenco e visualizzazioni ampie che definiscono una struttura formale di dati, ad esempio una tabella di dati, i controlli personalizzati consentono di definire la modalità di visualizzazione di un singolo dato inserito. È possibile definire un set comune di controlli personalizzati che sono disponibili per tutte le visualizzazioni del file di formattazione, è possibile definire controlli personalizzati che sono disponibili per una visualizzazione specifica oppure è possibile definire un set di controlli disponibili per un gruppo di oggetti.

## <a name="custom-control-example"></a>Esempio di controllo personalizzato

Nell'esempio seguente mostra un controllo personalizzato che viene definito nel file Certificates.Format.ps1xml. Questo controllo personalizzato viene usato per separare le [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) oggetti visualizzati in una visualizzazione tabella.

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

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
