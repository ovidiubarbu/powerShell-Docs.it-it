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
# <a name="network-switch-management-with-powershell"></a>Gestione del commutatore di rete con PowerShell

Il cmdlet **Get-NetworkSwitchEthernetPort** restituisce ora le informazioni aggiuntive seguenti con le istanze:

- IPAddress - indirizzo IP associato alla porta
- PortMode - modalità della porta: accesso, route o trunk
- AccessVLAN - ID della VLAN associata a questa porta in modalità di accesso
- TrunkedVLANList - elenco di ID delle VLAN associate a questa porta in modalità trunk

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Operazioni fondamentali per la gestione del commutatore di rete con Windows PowerShell

I cmdlet per il commutatore di rete, introdotti in WMF 5.0, consentono di applicare la configurazione di commutatore, LAN virtuale (VLAN) e porte del commutatore di rete di livello 2 di base ai commutatori di rete con certificazione per il logo di Windows Server 2012 R2. Microsoft rinnova il suo impegno per il supporto della visione [DAL (Datacenter Abstraction Layer)](http://technet.microsoft.com/cloud/dal.aspx) e per dimostrare il valore per i clienti e partner in questo spazio. Usando questi cmdlet è possibile eseguire:

- Configurazioni globali del commutatore, ad esempio:
    - Impostare il nome host
    - Impostare il banner del commutatore
    - Rendere persistente la configurazione
    - Abilitare o disabilitare funzionalità

- Configurazione della VLAN:
    - Creare o rimuovere VLAN
    - Abilitare o disabilitare VLAN
    - Enumerare VLAN
    - Impostare un nome descrittivo per una VLAN

- Configurazione delle porte di livello 2:
    - Enumerare le porte
    - Abilitare o disabilitare le porte
    - Impostare modalità e proprietà per le porte
    - Aggiungere o associare la modalità trunk o di accesso per la VLAN sulla porta

È possibile iniziare l'esplorazione cercando tutti i cmdlet NetworkSwitch.

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

Altre informazioni sono disponibili nel post di blog di Jeffrey Snover per l'annuncio dell'anteprima di WMF 5.0: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>