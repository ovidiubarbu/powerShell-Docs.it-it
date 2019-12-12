---
title: Visualizzazione estesa (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367950"
---
# <a name="wide-view-groupby"></a>Visualizzazione più ampia (GroupBy)

Questo esempio illustra come implementare una visualizzazione estesa che Visualizza i gruppi di [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet `Get-Service`. Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Per caricare il file di formattazione

1. Copiare il codice XML dalla sezione esempio di questo argomento in un file di testo.

2. Salvare il file di testo. Assicurarsi di aggiungere l'estensione `format.ps1xml` al file per identificarla come un file di formattazione.

3. Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Questo file di formattazione definisce la visualizzazione di un oggetto già definito da un file di formattazione di Windows PowerShell. Quando si esegue il cmdlet, è necessario utilizzare il parametro `prependPath` e non è possibile caricare il file di formattazione come modulo.

## <a name="demonstrates"></a>Illustra

In questo file di formattazione vengono illustrati gli elementi XML seguenti:

- Elemento del [nome](./name-element-for-view-format.md) per la visualizzazione.

- Elemento [ViewSelectedBy](./viewselectedby-element-format.md) che definisce quali oggetti vengono visualizzati dalla visualizzazione.

- Elemento [GroupBy](./groupby-element-for-view-format.md) che definisce quando viene visualizzato un nuovo gruppo.

- Elemento [WideItem](./wideitem-element-for-widecontrol-format.md) che definisce la proprietà visualizzata dalla visualizzazione.

## <a name="example"></a>Esempio

Nel codice XML seguente viene definita un'ampia visualizzazione che consente di visualizzare gruppi di oggetti. Ogni nuovo gruppo viene avviato quando viene modificato il valore della proprietà [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) dopo il caricamento del file di formato.

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>Vedere anche

[Esempi di file di formattazione](./examples-of-formatting-files.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
