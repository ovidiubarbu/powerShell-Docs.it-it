---
title: Visualizzazione più ampia (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083740"
---
# <a name="wide-view-basic"></a>Visualizzazione più ampia (base)

In questo esempio viene illustrato come implementare una visualizzazione più ampia base che visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai `Get-Service` cmdlet. Per altre informazioni sui componenti di una visualizzazione più ampia, vedere [creazione di una visualizzazione più ampia](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Per caricare questo file di formattazione

1. Copiare il codice XML della sezione di questo argomento in un file di testo.

2. Salvare il file di testo. Assicurarsi di aggiungere il `format.ps1xml` estensione del file per identificarla come un file di formattazione.

3. Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Questo file di formattazione definita la visualizzazione di un oggetto che è già definita da un file di formattazione di Windows PowerShell. È necessario usare il `prependPath` parametro quando si esegue il cmdlet, e non è possibile caricare questo tipo di formattazione del file come modulo.

## <a name="demonstrates"></a>Di seguito viene illustrato

Questo file di formattazione illustra gli elementi XML seguenti:

- Il [nome](./name-element-for-view-format.md) (elemento) per la visualizzazione.

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento che definisce quali oggetti vengono visualizzati nella visualizzazione.

- Il [WideItem](./wideitem-element-for-widecontrol-format.md) elemento che definisce quale proprietà viene visualizzata nella visualizzazione.

## <a name="example"></a>Esempio

Il codice XML seguente definisce una visualizzazione più ampia che visualizza il valore della [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) proprietà.

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

Nell'esempio seguente viene illustrato come Windows PowerShell Visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetti dopo il caricamento di questo file di formato.

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

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
