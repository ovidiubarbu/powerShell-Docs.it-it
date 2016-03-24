# Specifica delle dipendenze tra nodi

Grazie alle risorse predefinite WaitFor\* (WaitForAll, WaitForAny e WaitForSome), è ora possibile specificare le dipendenze tra i computer durante le esecuzioni della configurazione, senza orchestrazione esterna. Il comportamento di ogni risorsa WaitFor\* è il seguente:

* **WaitForAll** aspetta che la risorsa specificata sia nello stato desiderato in *tutti* i nodi di destinazione definiti nella proprietà NodeName.
* **WaitForAny** aspetta che la risorsa specificata sia nello stato desiderato in *qualsiasi* nodo di destinazione definito nella proprietà NodeName.
* **WaitForSome** aspetta che la risorsa specificata sia nello stato desiderato nel numero specificato, definito dalla proprietà NodeCount, dei nodi di destinazione definiti nella proprietà NodeName.

Queste risorse consentono la sincronizzazione tra nodi tramite connessioni CIM sul protocollo WS-Man. Grazie a queste risorse, una configurazione può aspettare la modifica dello stato di una risorsa specifica di un altro computer, prima di continuare con la propria configurazione. 

Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa **xADDomain** nel nodo **MyDC** con alcuni tentativi, prima che il nodo di destinazione possa essere aggiunto al dominio.

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
**Suggerimento:** per impostazione predefinita, le risorse WaitFor\* eseguono un solo tentativo prima dell'esito negativo, quindi anche se non è obbligatorio è in genere consigliabile specificare un intervallo per i tentativi e il loro numero.
<!--HONumber=Mar16_HO2-->
