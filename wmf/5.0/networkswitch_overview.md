---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 2b6b81d250c3d745f3ab21ebadb9a657583638b0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="d5551-102">Gestione del commutatore di rete con PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5551-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="d5551-103">Il cmdlet **Get-NetworkSwitchEthernetPort** restituisce ora le informazioni aggiuntive seguenti con le istanze:</span><span class="sxs-lookup"><span data-stu-id="d5551-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="d5551-104">IPAddress - indirizzo IP associato alla porta</span><span class="sxs-lookup"><span data-stu-id="d5551-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="d5551-105">PortMode - modalità della porta: accesso, route o trunk</span><span class="sxs-lookup"><span data-stu-id="d5551-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="d5551-106">AccessVLAN - ID della VLAN associata a questa porta in modalità di accesso</span><span class="sxs-lookup"><span data-stu-id="d5551-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="d5551-107">TrunkedVLANList - elenco di ID delle VLAN associate a questa porta in modalità trunk</span><span class="sxs-lookup"><span data-stu-id="d5551-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="d5551-108">Operazioni fondamentali per la gestione del commutatore di rete con Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5551-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="d5551-109">I cmdlet per il commutatore di rete, introdotti in WMF 5.0, consentono di applicare la configurazione di commutatore, LAN virtuale (VLAN) e porte del commutatore di rete di livello 2 di base ai commutatori di rete con certificazione per il logo di Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="d5551-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="d5551-110">Microsoft rinnova il suo impegno per il supporto della visione [DAL (Datacenter Abstraction Layer)](http://technet.microsoft.com/cloud/dal.aspx) e per dimostrare il valore per i clienti e partner in questo spazio.</span><span class="sxs-lookup"><span data-stu-id="d5551-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="d5551-111">Usando questi cmdlet è possibile eseguire:</span><span class="sxs-lookup"><span data-stu-id="d5551-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="d5551-112">Configurazioni globali del commutatore, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="d5551-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="d5551-113">Impostare il nome host</span><span class="sxs-lookup"><span data-stu-id="d5551-113">Set host name</span></span>
    - <span data-ttu-id="d5551-114">Impostare il banner del commutatore</span><span class="sxs-lookup"><span data-stu-id="d5551-114">Set switch banner</span></span>
    - <span data-ttu-id="d5551-115">Rendere persistente la configurazione</span><span class="sxs-lookup"><span data-stu-id="d5551-115">Persist configuration</span></span>
    - <span data-ttu-id="d5551-116">Abilitare o disabilitare funzionalità</span><span class="sxs-lookup"><span data-stu-id="d5551-116">Enable or disable feature</span></span>

- <span data-ttu-id="d5551-117">Configurazione della VLAN:</span><span class="sxs-lookup"><span data-stu-id="d5551-117">VLAN configuration:</span></span>
    - <span data-ttu-id="d5551-118">Creare o rimuovere VLAN</span><span class="sxs-lookup"><span data-stu-id="d5551-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="d5551-119">Abilitare o disabilitare VLAN</span><span class="sxs-lookup"><span data-stu-id="d5551-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="d5551-120">Enumerare VLAN</span><span class="sxs-lookup"><span data-stu-id="d5551-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="d5551-121">Impostare un nome descrittivo per una VLAN</span><span class="sxs-lookup"><span data-stu-id="d5551-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="d5551-122">Configurazione delle porte di livello 2:</span><span class="sxs-lookup"><span data-stu-id="d5551-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="d5551-123">Enumerare le porte</span><span class="sxs-lookup"><span data-stu-id="d5551-123">Enumerate ports</span></span>
    - <span data-ttu-id="d5551-124">Abilitare o disabilitare le porte</span><span class="sxs-lookup"><span data-stu-id="d5551-124">Enable or disable ports</span></span>
    - <span data-ttu-id="d5551-125">Impostare modalità e proprietà per le porte</span><span class="sxs-lookup"><span data-stu-id="d5551-125">Set port modes and properties</span></span>
    - <span data-ttu-id="d5551-126">Aggiungere o associare la modalità trunk o di accesso per la VLAN sulla porta</span><span class="sxs-lookup"><span data-stu-id="d5551-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="d5551-127">È possibile iniziare l'esplorazione cercando tutti i cmdlet NetworkSwitch.</span><span class="sxs-lookup"><span data-stu-id="d5551-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="d5551-128">Altre informazioni sono disponibili nel post di blog di Jeffrey Snover per l'annuncio dell'anteprima di WMF 5.0: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="d5551-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>