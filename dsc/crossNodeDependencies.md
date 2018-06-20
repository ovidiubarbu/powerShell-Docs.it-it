---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Specifica delle dipendenze tra nodi
ms.openlocfilehash: c1802d6baa1f2b3449603e0374a83e213abf598e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218621"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="4f8af-103">Specifica delle dipendenze tra nodi</span><span class="sxs-lookup"><span data-stu-id="4f8af-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="4f8af-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4f8af-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4f8af-105">DSC fornisce risorse speciali quali **WaitForAll**, **WaitForAny** e **WaitForSome** che possono essere usate nelle configurazioni per specificare le dipendenze nelle configurazioni di altri nodi.</span><span class="sxs-lookup"><span data-stu-id="4f8af-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="4f8af-106">Il comportamento di queste risorse è il seguente:</span><span class="sxs-lookup"><span data-stu-id="4f8af-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="4f8af-107">**WaitForAll**: ha esito positivo se la risorsa specificata è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4f8af-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="4f8af-108">**WaitForAny**: ha esito positivo se la risorsa specificata è nello stato desiderato in almeno uno dei nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4f8af-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="4f8af-109">**WaitForSome**: specifica una proprietà **NodeCount** oltre alla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4f8af-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="4f8af-110">La risorsa ha esito positivo se si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4f8af-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="4f8af-111">Uso delle risorse WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="4f8af-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="4f8af-112">Per usare le risorse **WaitForXXXX**, creare un blocco di risorsa contenente il tipo di risorsa che specifica la risorsa DSC e i nodi da attendere.</span><span class="sxs-lookup"><span data-stu-id="4f8af-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="4f8af-113">Quindi usare la proprietà **DependsOn** su eventuali altri blocchi di risorse nella configurazione per attendere che le condizioni specificate nel nodo **WaitForXXXX** abbiano esito positivo.</span><span class="sxs-lookup"><span data-stu-id="4f8af-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="4f8af-114">Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa **xADDomain** nel nodo **MyDC** con un numero massimo di 30 tentativi, a intervalli di 15 secondi, prima che il nodo di destinazione possa essere aggiunto al dominio.</span><span class="sxs-lookup"><span data-stu-id="4f8af-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

><span data-ttu-id="4f8af-115">**Nota**: per impostazione predefinita, le risorse WaitForXXX eseguono un solo tentativo prima dell'esito negativo.</span><span class="sxs-lookup"><span data-stu-id="4f8af-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="4f8af-116">Sebbene non sia obbligatorio, è consigliabile specificare un intervallo per i tentativi e il loro numero.</span><span class="sxs-lookup"><span data-stu-id="4f8af-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f8af-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4f8af-117">See Also</span></span>
* [<span data-ttu-id="4f8af-118">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="4f8af-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="4f8af-119">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="4f8af-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="4f8af-120">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="4f8af-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)