---
title: Visualizzazione elenco (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365140"
---
# <a name="list-view-groupby"></a>Visualizzazione elenco (GroupBy)

In questo esempio viene illustrato come implementare una visualizzazione elenco che separa le righe dell'elenco in gruppi. In questa visualizzazione elenco sono elencate le proprietà di [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) . Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

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

- Elemento [GroupBy](./viewselectedby-element-format.md) che definisce la modalità di visualizzazione di un nuovo gruppo di oggetti.

- Elemento [ListControl](./listcontrol-element-format.md) che definisce la proprietà visualizzata dalla visualizzazione.

- Elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.

- Elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) che definisce la proprietà che viene visualizzata.

## <a name="example"></a>Esempio

Il codice XML seguente definisce una visualizzazione elenco che avvia un nuovo gruppo ogni volta che viene modificato il valore della proprietà [System. ServiceProcess. ServiceController. status](/dotnet/api/System.ServiceProcess.ServiceController.Status) . Quando ogni gruppo viene avviato, viene visualizzata un'etichetta personalizzata che include il nuovo valore della proprietà.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
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

Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) dopo il caricamento del file di formato. Le righe vuote aggiunte prima e dopo l'etichetta del gruppo vengono aggiunte automaticamente da Windows PowerShell.

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>Vedere anche

[Esempi di file di formattazione](./examples-of-formatting-files.md)

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
