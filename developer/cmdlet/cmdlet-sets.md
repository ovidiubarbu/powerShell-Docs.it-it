---
title: Set di cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcf0739e-920e-4dd8-afca-2c6d6927bc2a
caps.latest.revision: 10
ms.openlocfilehash: ef3b5bab5dcafc578397bcb4f071776bbdeaced1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058267"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="d5ffc-102">Set di cmdlet</span><span class="sxs-lookup"><span data-stu-id="d5ffc-102">Cmdlet Sets</span></span>

<span data-ttu-id="d5ffc-103">Quando si progettano i cmdlet, potrebbero verificarsi casi in cui è necessario eseguire diverse operazioni sullo stesso elemento di dati.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="d5ffc-104">Ad esempio, si potrebbe essere necessario ottenere e impostare i dati o avviare e arrestare un processo.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="d5ffc-105">Anche se è necessario creare i cmdlet separati per ogni azione, la progettazione dei cmdlet deve includere una classe di base da cui derivano le classi per i singoli cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="d5ffc-106">Tenere presente quanto segue quando si implementa una classe di base.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="d5ffc-107">Dichiarare parametri comuni utilizzati da tutti i cmdlet derivati nella classe di base.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="d5ffc-108">Aggiungere parametri cmdlet specifici per la classe cmdlet appropriato.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="d5ffc-109">Eseguire l'override di metodo nella classe di base di elaborazione dell'input appropriati.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="d5ffc-110">Dichiarare la [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributo in tutte le classi di cmdlet, ma non dichiarato nella classe di base.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-110">Declare the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="d5ffc-111">Implementare una [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) oppure [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe il cui nome e descrizione rispecchia il set di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-111">Implement a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="d5ffc-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="d5ffc-112">Example</span></span>

<span data-ttu-id="d5ffc-113">Nell'esempio seguente viene illustrata l'implementazione di una classe di base che viene usato da Get-Process e il cmdlet Stop-Process che derivano dalla stessa classe di base.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProcessCommands

  /// <summary>
  /// This class implements a Stop-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>
  [Cmdlet(VerbsLifecycle.Stop, "Proc", SupportsShouldProcess = true)]
  public class StopProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      if (ShouldProcess(process.ProcessName, "Stop-Proc"))
      {
        process.Kill();
      }
    }
  }

  /// <summary>
  /// This class implements a Get-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>

  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      WriteObject(process);
    }
  }

  /// <summary>
  /// This class is the base class that defines the common
  /// functionality used by the Get-Proc and Stop-Proc
  /// cmdlets.
  /// </summary>
  public class BaseProcCommand : Cmdlet
  {
    #region Parameters

    // Defines the Name parameter that is used to
    // specify a process by its name.
    [Parameter(
               Position = 0,
               Mandatory = true,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true
    )]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    // Defines the Exclude parameter that is used to
    // specify which processes should be excluded when
    // the cmdlet performs its action.
    [Parameter()]
    public string[] Exclude
    {
      get { return excludeNames; }
      set { excludeNames = value; }
    }
    private string[] excludeNames = new string[0];
    #endregion Parameters

    public virtual void ProcessObject(Process process)
    {
      throw new NotImplementedException("This method should be overridden.");
    }

    #region Cmdlet Overrides
    // <summary>
    // For each of the requested process names, retrieve and write
    // the associated processes.
    // </summary>
    protected override void ProcessRecord()
    {
      // Set up the wildcard characters used in resolving
      // the process names.
      WildcardOptions options = WildcardOptions.IgnoreCase |
                                WildcardOptions.Compiled;

      WildcardPattern[] include = new WildcardPattern[Name.Length];
      for (int i = 0; i < Name.Length; i++)
      {
        include[i] = new WildcardPattern(Name[i], options);
      }

      WildcardPattern[] exclude = new WildcardPattern[Exclude.Length];
      for (int i = 0; i < Exclude.Length; i++)
      {
        exclude[i] = new WildcardPattern(Exclude[i], options);
      }

      foreach (Process p in Process.GetProcesses())
      {
        foreach (WildcardPattern wIn in include)
        {
          if (wIn.IsMatch(p.ProcessName))
          {
            bool processThisOne = true;
            foreach (WildcardPattern wOut in exclude)
            {
              if (wOut.IsMatch(p.ProcessName))
              {
                processThisOne = false;
                break;
              }
            }
            if (processThisOne)
            {
              ProcessObject(p);
            }
            break;
          }
        }
      }
    }
    #endregion Cmdlet Overrides
  }
    #endregion ProcessCommands
}
```

## <a name="see-also"></a><span data-ttu-id="d5ffc-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d5ffc-114">See Also</span></span>

[<span data-ttu-id="d5ffc-115">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5ffc-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
