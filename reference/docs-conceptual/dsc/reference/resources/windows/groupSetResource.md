---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
description: Fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.
title: Risorsa GroupSet DSC
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953178"
---
# <a name="dsc-groupset-resource"></a>Risorsa GroupSet DSC

> Si applica a: Windows PowerShell 5.x

La risorsa **GroupSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione. Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa Group](groupResource.md) per ogni gruppo specificato nel parametro `GroupName`.

Usare questa risorsa quando si vuole aggiungere e/o rimuovere lo stesso elenco di membri per più di un gruppo, rimuovere più di un gruppo o aggiungere più di un gruppo con lo stesso elenco di membri.

## <a name="syntax"></a>Sintassi

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|GroupName |Nomi dei gruppi per cui si vuole specificare un determinato stato. |
|Members |Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati. Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`. Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**. In caso contrario, verrà generato un errore. |
|Description |La descrizione dell'attività. |
|MembersToInclude |Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente. Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. In caso contrario, verrà generato un errore. |
|MembersToExclude |Usare questa proprietà per rimuovere membri dall'appartenenza a gruppi esistenti. Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. In caso contrario, verrà generato un errore. |
|Credential |Le credenziali necessarie per accedere a risorse remote. questo account deve avere le autorizzazioni di Active Directory appropriate per aggiungere tutti gli account non locali al gruppo. In caso contrario, si verifica un errore. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se i gruppi esistono. Impostare questa proprietà su **Absent** per assicurarsi che i gruppi non esistano. Impostando il valore su **Present** ci si assicura che i gruppi esistano. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example-1-ensuring-groups-are-present"></a>Esempio 1: Verifica che i gruppi siano presenti

L'esempio seguente illustra come assicurarsi che siano presenti due gruppi denominati "myGroup" e "myOtherGroup".

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> In questo esempio vengono usate credenziali in testo non crittografato per maggiore semplicità. Per informazioni sulla crittografia delle credenziali nel file MOF della configurazione, vedere [Protezione del file MOF](../../../pull-server/secureMOF.md).