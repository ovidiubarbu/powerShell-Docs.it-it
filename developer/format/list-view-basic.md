---
title: Elenco di visualizzazione (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065309"
---
# <a name="list-view-basic"></a>Visualizzazione elenco (base)

In questo esempio viene illustrato come implementare una visualizzazione elenco di base che visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) gli oggetti restituiti dai [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Per altre informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

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

- Il [dell'oggetto ListControl](./listcontrol-element-format.md) elemento che definisce quale proprietà viene visualizzata nella visualizzazione.

- Il [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento che definisce ciò che viene visualizzato in una riga della visualizzazione elenco.

- Il [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento che definisce la proprietà da visualizzare.

## <a name="example"></a>Esempio

Il codice XML seguente definisce una visualizzazione elenco che mostra quattro proprietà del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetto. In ogni riga, il nome della proprietà viene visualizzato seguito dal valore della proprietà.

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

Nell'esempio seguente viene illustrato come Windows PowerShell Visualizza il [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) oggetti dopo il caricamento di questo file di formato.

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>Vedere anche

[Esempi di file di formattazione](./examples-of-formatting-files.md)

[La scrittura di un File di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
