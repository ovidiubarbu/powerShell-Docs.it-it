# Introduzione a PowerShell DSC (Desired State Configuration) #

Questa guida descrive come iniziare a creare documenti di PowerShell DSC (Desired State Configuration) e applicarli ai computer. Si presuppone una familiarità di base con i cmdlet, i moduli e le funzioni di PowerShell. 


## Creare una configurazione ##

Le <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)"><ctype="x-NOTFOUND" mdpre="**" mdpost="**">configurazioni</ctype="x-NOTFOUND"></ctype="x-NOTFOUND"> sono documenti che descrivono un ambiente. Gli ambienti sono costituiti da "<ctype="x-NOTFOUND" mdpre="**" mdpost="**">nodi</ctype="x-NOTFOUND">", che sono in genere macchine virtuali o computer fisici. 

Le configurazioni possono avere svariate forme. Il metodo più semplice per creare una nuova configurazione consiste nel creare un file PS1 (script di PowerShell). A questo scopo, aprire l'editor preferito. PowerShell ISE è un'ottima scelta, perché riconosce DSC in modo nativo. Salvare il codice seguente come file PS1:

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## Parti di una configurazione ##
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">Configuration</ctype="x-NOTFOUND"> è una parola chiave che è stata aggiunta in PowerShell 4.0. Significa un tipo speciale di funzione di PowerShell usata da DSC (Desired State Configuration). In questo esempio la funzione si chiama myFirstConfiguration. 

La riga successiva è un'istruzione di importazione, simile all'importazione di un modulo. Questa riga verrà descritta più avanti.

Il termine "nodo" definisce il nome del computer su cui agirà questa configurazione. Benché questa configurazione venga modificata in locale, le configurazioni possono raggiungere nodi remoti e configurarli. 

I nodi possono essere nomi di computer o indirizzi IP. Un singolo documento di configurazione può contenere più nodi. Usando <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)">dati di configurazione</ctype="x-NOTFOUND"> è possibile fare in modo che la stessa configurazione venga applicata a più nodi. In questo caso il nodo è "localhost", ovvero il computer locale. 

L'elemento successivo è una <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/resources)"><ctype="x-NOTFOUND" mdpre="**" mdpost="**">risorsa</ctype="x-NOTFOUND"></ctype="x-NOTFOUND">. Le risorse sono blocchi predefiniti di configurazioni. Ogni risorsa è un modulo che definisce la logica di implementazione di un singolo aspetto di un computer. È possibile visualizzare ogni risorsa nel computer eseguendo <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Get-DscResource</ctype="x-NOTFOUND"> in PowerShell. Le risorse devono essere presenti nel computer locale e prima di poter essere usate in una configurazione devono essere importate con <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Import-DscResource</ctype="x-NOTFOUND">, che si trova nella seconda riga di questa configurazione. 

**Applicazione di una configurazione**

Se lo script sopra viene salvato ed eseguito, non viene prodotto alcun output. Il motivo è che una configurazione è solo una funzione e lo script sopra ha definito la funzione, ma senza eseguirla. Dopo che la funzione è stata definita, deve essere richiamata:
```powershell
myFirstConfiguration
```

Quando vengono eseguite, le funzioni di configurazione verificano la validità della configurazione. La configurazione non deve includere errori di sintassi, per le risorse devono essere definiti tutti i parametri obbligatori e tutte le risorse devono essere importate prima dell'esecuzione.

Quando la configurazione viene eseguita, crea una cartella con il nome della configurazione stessa che contiene un <ctype="x-NOTFOUND" mdpre="**" mdpost="**">file MOF</ctype="x-NOTFOUND"> per ogni nodo nella configurazione. Il file MOF è un formato di gestione basato sugli standard usato da PowerShell DSC per comunicare in rete.

Per applicare la configurazione:
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
Viene creato un processo di PowerShell che raggiunge i nodi nella configurazione e li configura. Per visualizzare l'output del processo, usare -Wait. 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```



<!--HONumber=Mar16_HO1-->


