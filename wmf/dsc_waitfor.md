# Specifica delle dipendenze tra nodi

Grazie alle risorse predefinite WaitFor\* (WaitForAll, WaitForAny e WaitForSome), è ora possibile specificare le dipendenze tra i computer durante le esecuzioni della configurazione, senza orchestrazione esterna. Il comportamento di ogni risorsa WaitFor\* è il seguente:

* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAll</ctype="x-NOTFOUND"> aspetta che la risorsa specificata sia nello stato desiderato in <ctype="x-NOTFOUND" mdpre="*" mdpost="*">tutti</ctype="x-NOTFOUND"> i nodi di destinazione definiti nella proprietà NodeName.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAny</ctype="x-NOTFOUND"> aspetta che la risorsa specificata sia nello stato desiderato in <ctype="x-NOTFOUND" mdpre="*" mdpost="*">qualsiasi</ctype="x-NOTFOUND"> nodo di destinazione definito nella proprietà NodeName.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForSome</ctype="x-NOTFOUND"> aspetta che la risorsa specificata sia nello stato desiderato nel numero specificato, definito dalla proprietà NodeCount, di nodi di destinazione definiti nella proprietà NodeName.

Queste risorse consentono la sincronizzazione tra nodi tramite connessioni CIM sul protocollo WS-Man. Grazie a queste risorse, una configurazione può aspettare la modifica dello stato di una risorsa specifica di un altro computer, prima di continuare con la propria configurazione. 

Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa <ctype="x-NOTFOUND" mdpre="**" mdpost="**">xADDomain</ctype="x-NOTFOUND"> nel nodo <ctype="x-NOTFOUND" mdpre="**" mdpost="**">MyDC</ctype="x-NOTFOUND"> con alcuni tentativi, prima che il nodo di destinazione possa essere aggiunto al dominio.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

    WaitForAll DC
    {
        ResourceName      = '[xADDomain]NewDomain'
        NodeName          = 'MyDC'
        RetryIntervalSec  = 15
        RetryCount        = 30
    }

    xComputer JoinDomain
    {
        Name             = 'MyPC'
        DomainName       = 'Contoso.com'
        Credential       = (get-credential)
        DependsOn        ='[WaitForAll]DC'
    }
}
```
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">Suggerimento:</ctype="x-NOTFOUND"> per impostazione predefinita, le risorse WaitFor\* eseguono un solo tentativo prima dell'esito negativo, quindi anche se non è obbligatorio è in genere consigliabile specificare un intervallo per i tentativi e il loro numero.


<!--HONumber=Mar16_HO3-->


