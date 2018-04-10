---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa nxSshAuthorizedKeys DSC per Linux
ms.openlocfilehash: a36d158735839727e98893ce9fce174a0f37f764
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>Risorsa nxSshAuthorizedKeys DSC per Linux

La risorsa **nxSshAuthorizedKeys** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le chiavi ssh autorizzate per un utente specificato.

## <a name="syntax"></a>Sintassi

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà |  Description |
|---|---|
| KeyComment| Commento univoco per la chiave. Questa proprietà viene usata per identificare in modo univoco la chiave.|
| Ensure| Specifica se la chiave è definita. Impostare questa proprietà su "Absent" per specificare che la chiave non esiste nel file delle chiavi autorizzate dell'utente. Impostarla su "Absent" per specificare che la chiave è definita nel file delle chiavi autorizzate dell'utente.|
| Username| Nome utente per cui gestire le chiavi ssh autorizzate. Se questa proprietà non è definita, l'utente predefinito è "root".|
| Key| Contenuto della chiave. Questa proprietà è obbligatoria se la proprietà **Ensure** è impostata su "Present".|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Esempio

L'esempio seguente definisce una chiave ssh autorizzata pubblica per l'utente "monuser".

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```