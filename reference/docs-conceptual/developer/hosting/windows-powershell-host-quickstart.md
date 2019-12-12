---
title: Guida introduttiva a Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360820"
---
# <a name="windows-powershell-host-quickstart"></a>Guida introduttiva dell'host di Windows PowerShell

Per ospitare Windows PowerShell nell'applicazione, usare la classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .
Questa classe fornisce metodi per la creazione di una pipeline di comandi, quindi l'esecuzione di tali comandi in un spazio.
Il modo più semplice per creare un'applicazione host consiste nell'usare il valore predefinito spazio.
Il valore predefinito di spazio contiene tutti i comandi di base di Windows PowerShell.
Se si vuole che l'applicazione esponga solo un subset dei comandi di Windows PowerShell, è necessario creare un spazio personalizzato.

## <a name="using-the-default-runspace"></a>Uso del spazio predefinito

Per iniziare, si userà il valore predefinito spazio e si useranno i metodi della classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) per aggiungere comandi, parametri, istruzioni e script a una pipeline.

### <a name="addcommand"></a>AddCommand

Usare il metodo [System. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) per aggiungere comandi alla pipeline.
Si supponga, ad esempio, di voler ottenere l'elenco dei processi in esecuzione nel computer.
La modalità di esecuzione di questo comando è la seguente:

1. Creare un oggetto [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Aggiungere il comando che si desidera eseguire.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Richiamare il comando.

   ```csharp
   ps.Invoke();
   ```

Se si chiama il metodo AddCommand più di una volta prima di chiamare il metodo [System. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , il risultato del primo comando viene reindirizzato al secondo e così via.
Se non si vuole inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) .

### <a name="addparameter"></a>AddParameter

Nell'esempio precedente viene eseguito un unico comando senza parametri.
È possibile aggiungere parametri al comando usando il metodo [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .
Il codice seguente, ad esempio, ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione nel computer.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

È possibile aggiungere altri parametri chiamando ripetutamente il Metodo AddParameter.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

È anche possibile aggiungere un dizionario di nomi e valori di parametro chiamando il metodo [System. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

È possibile simulare la suddivisione in batch usando il metodo [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , che aggiunge un'altra istruzione alla fine della pipeline.
Il codice seguente ottiene un elenco di processi in esecuzione con il nome `PowerShell`e quindi ottiene l'elenco dei servizi in esecuzione.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

È possibile eseguire uno script esistente chiamando il metodo [System. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .
Nell'esempio seguente viene aggiunto uno script alla pipeline ed eseguito.
In questo esempio si presuppone che esista già uno script denominato `MyScript.ps1` in una cartella denominata `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Esiste anche una versione del metodo AddScript che accetta un parametro booleano denominato `useLocalScope`.
Se questo parametro è impostato su `true`, lo script viene eseguito nell'ambito locale.
Nel codice seguente viene eseguito lo script nell'ambito locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Creazione di un spazio personalizzato

Mentre il spazio predefinito usato negli esempi precedenti carica tutti i comandi di Windows PowerShell di base, è possibile creare un spazio personalizzato che carica solo un subset specificato di tutti i comandi.
Questa operazione può essere utile per migliorare le prestazioni (il caricamento di un numero maggiore di comandi è un riscontro delle prestazioni) o per limitare la capacità dell'utente di eseguire operazioni.
Un spazio che espone solo un numero limitato di comandi è denominato spazio vincolato.
Per creare un spazio vincolato, usare le classi [System. Management. Automation. Runspaces. spazio](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

### <a name="creating-an-initialsessionstate-object"></a>Creazione di un oggetto InitialSessionState

Per creare un spazio personalizzato, è prima necessario creare un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .
Nell'esempio seguente viene usato [System. Management. Automation. Runspaces. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) per creare un spazio dopo la creazione di un oggetto InitialSessionState predefinito.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Limitazione del spazio

Nell'esempio precedente è stato creato un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) predefinito che carica tutte le funzionalità di base di Windows PowerShell.
Avremmo anche chiamato il metodo [System. Management. Automation. Runspaces. InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) per creare un oggetto InitialSessionState che caricherà solo i comandi nello snap-in Microsoft. PowerShell. Core.
Per creare un spazio più vincolato, è necessario creare un oggetto InitialSessionState vuoto chiamando il metodo [System. Management. Automation. Runspaces. InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) , quindi aggiungere i comandi a InitialSessionState.

L'uso di un spazio che carica solo i comandi specificati fornisce prestazioni significativamente migliorate.

Usare i metodi della classe [System. Management. Automation. Runspaces. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) per definire i cmdlet per lo stato della sessione iniziale.
Nell'esempio seguente viene creato uno stato sessione iniziale vuoto, quindi vengono definiti e aggiunti i comandi `Get-Command` e `Import-Module` allo stato sessione iniziale.
Viene quindi creato un spazio vincolato da tale stato della sessione iniziale ed eseguito i comandi in tale spazio.

Creare lo stato della sessione iniziale.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definire e aggiungere comandi allo stato della sessione iniziale.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Creare e aprire spazio.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Eseguire un comando e visualizzare il risultato.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Quando viene eseguito, l'output di questo codice sarà simile al seguente.

```powershell
Get-Command
Import-Module
```
