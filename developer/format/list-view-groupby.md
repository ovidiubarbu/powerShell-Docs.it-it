---
title: Visualizzazione (GroupBy) elenco | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794443"
---
# <a name="list-view-groupby"></a>Visualizzazione elenco (GroupBy)

In questo esempio viene illustrato come implementare una visualizzazione elenco che separa le righe dell'elenco in gruppi. Questa vista elenco vengono visualizzate le proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet. Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Per caricare questo file di formattazione

1. Copiare il codice XML della sezione di questo argomento in un file di testo.

2. Salvare il file di testo. Assicurarsi di aggiungere il `format.ps1xml` estensione del file per identificarla come un file di formattazione.

3. Aprire Windows PowerShell ed eseguire il comando seguente per caricare il file di formattazione nella sessione corrente: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Questo file di formattazione definita la visualizzazione di un oggetto che è già definita da un file di formattazione di Windows PowerShell. È necessario usare il `prependPath` parametro quando si esegue il cmdlet, e non è possibile caricare questo tipo di formattazione del file come modulo.

## <a name="demonstrates"></a>Illustra

Questo file di formattazione illustra gli elementi XML seguenti:

- Il [nome](./name-element-for-view-format.md) (elemento) per la visualizzazione.

- Il [ViewSelectedBy](./viewselectedby-element-format.md) elemento che definisce quali oggetti vengono visualizzati nella visualizzazione.

- Il [GroupBy](./viewselectedby-element-format.md) elemento che definisce come viene visualizzato un nuovo gruppo di oggetti.

- Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento che definisce quale proprietà viene visualizzata nella visualizzazione.

- Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.

- Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento che definisce la proprietà da visualizzare.

## <a name="example"></a>Esempio

Il codice XML seguente definisce una visualizzazione elenco che inizia un nuovo gruppo ogni volta che il valore della [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) le modifiche alle proprietà. Quando viene avviata ogni gruppo, viene visualizzata un'etichetta personalizzata che include il nuovo valore della proprietà.

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

Nell'esempio seguente viene illustrato come Windows PowerShell Visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetti dopo il caricamento di questo file di formato. Le righe vuote aggiunte prima e dopo l'etichetta di gruppo vengono aggiunti automaticamente da Windows PowerShell.

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

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
