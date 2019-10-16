---
title: Visualizzazione elenco (di base) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362810"
---
# <a name="list-view-basic"></a>Visualizzazione elenco (base)

Questo esempio illustra come implementare una visualizzazione elenco di base in cui viene visualizzato [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) restituiti dal cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) . Per ulteriori informazioni sui componenti di una visualizzazione elenco, vedere [creazione di una visualizzazione elenco](./creating-a-list-view.md).

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

- Elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) che definisce la proprietà che viene visualizzata.

## <a name="example"></a>Esempio

Il codice XML seguente definisce una visualizzazione elenco che visualizza quattro proprietà di [System. ServiceProcess. ServiceController? Oggetto DisplayProperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) . In ogni riga il nome della proprietà viene visualizzato seguito dal valore della proprietà.

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

Nell'esempio seguente viene illustrato come Windows PowerShell visualizzi [System. ServiceProcess. ServiceController? DisplayProperty = oggetti FullName](/dotnet/api/System.ServiceProcess.ServiceController) dopo il caricamento del file di formato.

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

[Scrittura di un file di formattazione di PowerShell](./writing-a-powershell-formatting-file.md)
