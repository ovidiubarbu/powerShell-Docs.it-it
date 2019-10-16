---
title: Visualizzazione elenco (etichette) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362790"
---
# <a name="list-view-labels"></a>Visualizzazione elenco (etichette)

In questo esempio viene illustrato come implementare una visualizzazione elenco che visualizza un'etichetta personalizzata per ogni riga dell'elenco. In questa visualizzazione elenco sono elencate le proprietà di [System. ServiceProcess. ServiceController? DisplayProperty = oggetto FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituito dal cmdlet [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) . Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

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

- Elemento [ListControl](./listcontrol-element-format.md) che definisce la proprietà visualizzata dalla visualizzazione.

- Elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.

- Elemento [Label](./label-element-for-listitem-for-listcontrol-format.md) che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.

- Elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) che definisce la proprietà che viene visualizzata.

## <a name="example"></a>Esempio

Il codice XML seguente definisce una visualizzazione elenco che consente di visualizzare un'etichetta personalizzata in ogni riga. In questo caso, l'etichetta include il nome della proprietà con ogni lettera maiuscola e la parola "Property". In ogni riga il nome della proprietà viene visualizzato seguito dal valore della proprietà.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) dopo il caricamento del file di formato.

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>Vedere anche

[Esempi di file di formattazione](./examples-of-formatting-files.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
