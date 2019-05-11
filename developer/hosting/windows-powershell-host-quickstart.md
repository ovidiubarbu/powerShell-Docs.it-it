---
title: Guida introduttiva di Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530614"
---
# <a name="windows-powershell-host-quickstart"></a>Guida introduttiva dell'host di Windows PowerShell

Per ospitare Windows PowerShell nell'applicazione, si utilizza il [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe.
Questa classe fornisce metodi che creano una pipeline di comandi e quindi eseguire questi comandi in uno spazio di esecuzione.
Il modo più semplice per creare un'applicazione host è usare lo spazio di esecuzione predefinito.
Lo spazio di esecuzione predefinito contiene tutti i comandi di Windows PowerShell core.
Se si desidera che l'applicazione da esporre solo un subset dei comandi di Windows PowerShell, è necessario creare uno spazio di esecuzione personalizzata.

## <a name="using-the-default-runspace"></a>Utilizzo spazio di esecuzione predefinito

Per iniziare, si sarà usare lo spazio di esecuzione predefinito e usare i metodi del [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe da aggiungere a una pipeline di comandi, parametri, istruzioni e script.

### <a name="addcommand"></a>AddCommand

Si utilizza il [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metodo per aggiungere comandi alla pipeline.
Si supponga, ad esempio ottenere l'elenco dei processi in esecuzione nel computer.
Il modo per eseguire questo comando è come indicato di seguito.

1. Creare un [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) oggetto.

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

Se si chiama il metodo AddCommand più volte prima di chiamare il [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metodo, il risultato del primo comando viene reindirizzato al secondo e così via.
Se non si desidera inviare tramite pipe il risultato di un comando precedente a un comando, aggiungerlo chiamando il [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) invece.

### <a name="addparameter"></a>AddParameter

Nell'esempio precedente esegue un comando singolo senza parametri.
È possibile aggiungere parametri al comando utilizzando il [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) (metodo).
Ad esempio, il codice seguente ottiene un elenco di tutti i processi denominati `PowerShell` in esecuzione nel computer.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

È possibile aggiungere parametri aggiuntivi chiamando il metodo AddParameter ripetutamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

È anche possibile aggiungere un dizionario di nomi dei parametri e valori chiamando il [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (metodo).

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

È possibile simulare l'invio in batch usando il [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metodo, che aggiunge un'ulteriore istruzione alla fine della pipeline.
Il codice seguente ottiene un elenco di processi in esecuzione con il nome `PowerShell`e quindi Ottiene l'elenco dei servizi in esecuzione.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

È possibile eseguire uno script esistente chiamando il [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (metodo).
Nell'esempio seguente aggiunge uno script alla pipeline e lo esegue.
In questo esempio si presuppone che è già presente uno script denominato `MyScript.ps1` in una cartella denominata `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

È inoltre disponibile una versione del metodo che accetta un parametro booleano denominato AddScript `useLocalScope`.
Se questo parametro è impostato su `true`, quindi lo script viene eseguito nell'ambito locale.
Il codice seguente verrà eseguito lo script nell'ambito locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Creazione di uno spazio di esecuzione personalizzata

Mentre lo spazio di esecuzione predefinito usato negli esempi precedenti carica tutti i comandi di Windows PowerShell core, è possibile creare uno spazio di esecuzione personalizzata che consente di caricare solo un subset specificato di tutti i comandi.
Si potrebbe voler eseguire questa operazione per migliorare le prestazioni, il caricamento di un numero maggiore di comandi è una riduzione delle prestazioni, o limitare la capacità dell'utente per eseguire operazioni.
Uno spazio di esecuzione che espone solo un numero limitato di comandi viene chiamato un spazio di esecuzione vincolato.
Per creare uno spazio di esecuzione vincolato, usare il [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classi.

### <a name="creating-an-initialsessionstate-object"></a>Creazione di un oggetto InitialSessionState

Per creare uno spazio di esecuzione personalizzata, è innanzitutto necessario creare un [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto.
Nell'esempio seguente, usiamo il [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) per creare uno spazio di esecuzione dopo la creazione di un oggetto InitialSessionState predefinito.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Vincolare lo spazio di esecuzione

Nell'esempio precedente è stato creato un valore predefinito [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) oggetto che consente di caricare tutti i core predefinito Windows PowerShell.
È possibile inoltre hanno chiamato la [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metodo per creare un oggetto InitialSessionState che carica solo i comandi nel Microsoft.PowerShell.Core snap-in.
Per creare uno spazio di esecuzione più limitato, è necessario creare un oggetto vuoto InitialSessionState chiamando il [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) (metodo), quindi aggiungere i comandi per il InitialSessionState.

Con uno spazio di esecuzione che carica solo i comandi che specificano offre prestazioni notevolmente migliorate.

Usare i metodi del [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe per definire i cmdlet per lo stato sessione iniziale.
Nell'esempio seguente crea uno stato sessione iniziale vuota, quindi definisce e aggiunge il `Get-Command` e `Import-Module` comandi per lo stato sessione iniziale.
Abbiamo quindi creare uno spazio di esecuzione vincolato dallo stato sessione iniziale ed eseguire i comandi in tale spazio di esecuzione.

Creare lo stato sessione iniziale.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definire e aggiungere i comandi per lo stato sessione iniziale.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Creare e aprire lo spazio di esecuzione.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Eseguire un comando e visualizza il risultato.

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

Quando eseguito, l'output di questo codice avrà un aspetto come indicato di seguito.

```powershell
Get-Command
Import-Module
```
