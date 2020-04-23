---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Group DSC
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954658"
---
# <a name="dsc-group-resource"></a>Risorsa Group DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **Group** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Descrizione |
|---|---|
|GroupName |Il nome del gruppo per cui si vuole specificare un determinato stato. |
|Credenziale |Le credenziali necessarie per accedere a risorse remote. per aggiungere tutti gli account non locali al gruppo, questo account deve avere le autorizzazioni di Active Directory appropriate. In caso contrario, quando la configurazione viene eseguita nel nodo di destinazione, si verifica un errore.
|Descrizione |La descrizione dell'attività. |
|Members |Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati. Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`. Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**. Questa operazione genera un errore. |
|MembersToExclude |Usare questa proprietà per rimuovere membri dall'appartenenza al gruppo esistente. Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. Questa operazione genera un errore. |
|MembersToInclude |Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente. Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`. Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**. In caso contrario, verrà generato un errore. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Descrizione |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se il gruppo esiste. Impostare questa proprietà su **Absent** per assicurarsi che il gruppo non esista. Impostando il valore su **Present** ci si assicura che il gruppo esista. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example-1-ensure-group-is-not-present"></a>Esempio 1: Assicurarsi che il gruppo non sia presente

L'esempio seguente illustra come specificare che un gruppo denominato "TestGroup" sia assente.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a>Esempio 2: Aggiungere un utente di dominio al gruppo locale

L'esempio seguente illustra come aggiungere un utente Active Directory al gruppo Administrators locale come parte della compilazione di un ambiente con più computer in cui è già in uso un PSCredential per l'account Amministratore locale. Questo utente viene anche usato per l'account amministratore di dominio (dopo l'innalzamento di livello di un dominio). A questo punto è necessario convertire il PSCredential esistente in credenziali descrittive del dominio. Ciò consente l'aggiunta di un utente di dominio al gruppo Administrators locale del server membro.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Esempio 3

L'esempio seguente illustra come garantire che un gruppo locale, TigerTeamAdmins, nel server TigerTeamSource.Contoso.Com non contenga un account di dominio specifico, Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```