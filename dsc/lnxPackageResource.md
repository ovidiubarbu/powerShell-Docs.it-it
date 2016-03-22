# Risorsa nxPackage DSC per Linux

La risorsa **nxPackage** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i pacchetti in un nodo Linux.

## Sintassi

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## Proprietà

|  Proprietà |  Descrizione | 
|---|---|
| Name| Nome del pacchetto per cui si vuole specificare un determinato stato.| 
| Ensure| Determina se verificare l'esistenza del pacchetto. Impostare questa proprietà su "Present" per specificare che il pacchetto esiste. Impostarla su "Absent" per specificare che il pacchetto non esiste. Il valore predefinito è "Present".|  
| PackageManager| I valori supportati sono "yum", "apt" e "zypper". Specifica lo strumento di gestione dei pacchetti da usare durante l'installazione dei pacchetti. Se si specifica **FilePath**, verrà usato il percorso fornito per installare il pacchetto. In caso contrario, verrà usato uno strumento di gestione dei pacchetti per installare il pacchetto da un repository preconfigurato. Se non si specifica né **PackageManager** né **FilePath**, viene usato il sistema di gestione dei pacchetti predefinito per il sistema.| 
| FilePath| Percorso in cui si trova il pacchetto| 
| PackageGroup| Se **$true**, **Name** sarà il nome di un gruppo di pacchetti da usare con **PackageManager**. **PacakgeGroup** non è un valore valido quando si specifica **FilePath**.| 
| Arguments| Stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.| 
| ReturnCode| Codice restituito previsto. Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

## Esempio

L'esempio seguente specifica che il pacchetto denominato "httpd" è installato in un computer Linux, usando lo strumento di gestione dei pacchetti "Yum".

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```
<!--HONumber=Feb16_HO4-->
