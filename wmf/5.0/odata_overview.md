# Generare cmdlet di PowerShell in base a un endpoint OData
Generare cmdlet di Windows PowerShell in base a un endpoint OData
--------------------------------------------------------------

**Export-ODataEndpointProxy** è un cmdlet che genera un set di cmdlet di Windows PowerShell basati sulle funzionalità esposte da un determinato endpoint OData.

L'esempio seguente mostra come usare questo nuovo cmdlet:

\# Caso d'uso di base di Export-ODataEndpointProxy

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

Parti dei principali casi d'uso per questa funzionalità sono ancora in fase di sviluppo, ad esempio:
-   Associazioni
-   Passaggio di flussi

Generare cmdlet di Windows PowerShell in base a un endpoint OData con ODataUtils
------------------------------------------------------------------------------
Il modulo ODataUtils consente la generazione di cmdlet di Windows PowerShell da endpoint REST che supportano OData. I seguenti miglioramenti incrementali sono disponibili nel modulo di Windows PowerShell Microsoft.PowerShell.ODataUtils.
-   Informazioni aggiuntive del canale dall'endpoint sul lato server al lato client.
-   Supporto del paging sul lato client
-   Filtro sul lato server tramite il parametro -Select
-   Supporto delle intestazioni di richieste Web

I cmdlet proxy generati dal cmdlet Export-ODataEndPointProxy forniscono informazioni aggiuntive (non indicate nei $metadata usati durante la generazione di proxy sul lato client) dall'endpoint OData sul lato server sul flusso di informazioni (una nuova funzionalità di Windows PowerShell 5.0). Di seguito è riportato un esempio di come ottenere tali informazioni.
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

È possibile ottenere i record dal lato server in batch usando il supporto del paging sul lato client. Ciò è utile quando è necessario ottenere una grande quantità di dati dal server tramite la rete.
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

I cmdlet proxy generato supportano il parametro -Select che è possibile usare come filtro per ricevere solo le proprietà dei record necessarie per il client. In questo modo si riduce la quantità di dati trasferiti in rete, perché il filtro viene applicato sul lato server.
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Il cmdlet Export-ODataEndpointProxy e i cmdlet proxy generati da questo cmdlet supportano ora il parametro Headers (specificare i valori come tabella hash), che è possibile usare per canalizzare qualsiasi informazione aggiuntiva prevista dall'endpoint OData sul lato server. Nell'esempio seguente, è possibile canalizzare una chiave della sottoscrizione tramite Headers per i servizi che prevedono una chiave della sottoscrizione per l'autenticazione.
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```


<!--HONumber=Jun16_HO4-->


