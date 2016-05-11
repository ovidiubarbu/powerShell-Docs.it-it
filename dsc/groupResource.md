# Risorsa Group DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa Group in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.

##Sintassi##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| GroupName| Indica il nome del gruppo per cui si vuole specificare un determinato stato.| 
| Credential| Indica le credenziali necessarie per accedere a risorse remote. **Nota**: questo account deve avere le autorizzazioni di Active Directory appropriate per aggiungere tutti gli account non locali al gruppo. In caso contrario, si verifica un errore.
| Description| Specifica la descrizione del gruppo.| 
| Ensure| Indica se il gruppo esiste. Impostare questa proprietà su "Absent" per specificare che il gruppo non esiste. Se la proprietà è impostata su "Present" (valore predefinito), specifica che il gruppo esiste.| 
| Members| Indica che si vuole specificare che questi membri formano il gruppo.| 
| MembersToExclude| Indica gli utenti da specificare come non membri del gruppo.| 
| MembersToInclude| Indica gli utenti da specificare come membri del gruppo.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"``.| 

## Esempio 1

L'esempio seguente mostra come specificare che un gruppo denominato TestGroup è assente. 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## Esempio 2
L'esempio seguente illustra come aggiungere un utente Active Directory al gruppo Administrators locale come parte della compilazione di un ambiente con più computer in cui è già in uso un PSCredential per l'account amministratore locale. Questo utente viene anche usato per l'account amministratore di dominio (dopo l'innalzamento di livello di un dominio). A questo punto è necessario convertire il PSCredential esistente in credenziali descrittive del dominio per consentire l'aggiunta di un utente di dominio al gruppo Administrators locale del server membro.

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

<!--HONumber=Apr16_HO3-->


