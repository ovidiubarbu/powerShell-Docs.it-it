---
title: Visualizzazione estesa (di base) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367940"
---
# <a name="wide-view-basic"></a>Visualizzazione più ampia (base)

In questo esempio viene illustrato come implementare una visualizzazione di base estesa che visualizza [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet `Get-Service`. Per ulteriori informazioni sui componenti di una visualizzazione estesa, vedere [creazione di un'ampia visualizzazione](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Per caricare il file di formattazione

1. Copiare il codice XML dalla sezione esempio di questo argomento in un file di testo.

2. Salvare il file di testo. Assicurarsi di aggiungere l'estensione `format.ps1xml` al file per identificarla come un file di formattazione.

3. Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Questo file di formattazione definisce la visualizzazione di un oggetto già definito da un file di formattazione di Windows PowerShell. Quando si esegue il cmdlet, è necessario utilizzare il parametro `prependPath` e non è possibile caricare il file di formattazione come modulo.

## <a name="demonstrates"></a>Dimostra

In questo file di formattazione vengono illustrati gli elementi XML seguenti:

- Elemento del [nome](./name-element-for-view-format.md) per la visualizzazione.

- Elemento [ViewSelectedBy](./viewselectedby-element-format.md) che definisce quali oggetti vengono visualizzati dalla visualizzazione.

- Elemento [WideItem](./wideitem-element-for-widecontrol-format.md) che definisce la proprietà visualizzata dalla visualizzazione.

## <a name="example"></a>Esempio

Il codice XML seguente definisce una visualizzazione estesa che Visualizza il valore della proprietà [System. ServiceProcess. ServiceController. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) .

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>Vedere anche

[Esempi di file di formattazione](./examples-of-formatting-files.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
