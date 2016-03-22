# Configurazioni DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Le configurazioni DSC sono script di PowerShell che definiscono un tipo speciale di funzione. 
Per definire una configurazione, usare la parola chiave __Configuration__ di PowerShell.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

Salvare lo script come file PS1.

## Sintassi di configurazione

Uno script di configurazione è costituito dalle parti seguenti:

- Blocco **Configuration**. Si tratta del blocco più esterno dello script. Per definirlo, usare la parola chiave **Configuration** e specificare un nome. In questo caso, il nome della configurazione è "MyDscConfiguration".
- Uno o più blocchi **Node**. Definiscono i nodi (computer o macchine virtuali) configurati. La configurazione precedente include un blocco **Node** che ha come destinazione un computer chiamato "TEST-PC1".
- Uno o più blocchi di risorse. Si tratta del punto in cui la configurazione imposta le proprietà per le risorse configurate. In questo caso, sono presenti due blocchi di risorse, ognuno dei quali chiama la risorsa "WindowsFeature".

All'interno di un blocco **Configuration** è possibile eseguire tutte le operazioni che è possibile eseguire anche in una funzione di PowerShell. Ad esempio, se nell'esempio precedente non si vuole codificare il nome del computer di destinazione nella configurazione, è possibile aggiungere un parametro per il nome del nodo:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$computerName="localhost"
    )
    Node $computerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

In questo esempio è necessario specificare il nome del nodo passandolo come parametro $computerName quando si [compila la configurazione](# Compilazione della configurazione). Per impostazione predefinita, il nome è "localhost".

## Compilazione della configurazione
Prima di poter applicare una configurazione, è necessario compilarla in un documento MOF. A questo scopo, è necessario chiamare la configurazione allo stesso modo in cui si chiama una funzione di PowerShell.
>__Nota:__ per chiamare una configurazione, la funzione deve essere nell'ambito globale (come per qualsiasi funzione di PowerShell). A questo scopo, è possibile effettuare il "dot-sourcing" dello script oppure eseguire lo script di configurazione premendo F5 o facendo clic sul pulsante __Esegui script__ in ISE. Per effettuare il dot-sourcing dello script, eseguire il comando `. .\myConfig.ps1`, dove `myConfig.ps1` è il nome del file di script che contiene la configurazione.

Quando si chiama la configurazione, vengono creati gli elementi seguenti:

- Una cartella nella directory locale con lo stesso nome della configurazione.
- Un file denominato _NomeNodo_.mof nella nuova directory, dove _NomeNodo_ è il nome del nodo di destinazione della configurazione. In presenza di più nodi, viene creato un file MOF per ognuno.

>__Nota__: il file MOF contiene tutte le informazioni di configurazione per il nodo di destinazione. Per questo motivo, è importante garantirne la sicurezza. Per altre informazioni, vedere [Protezione del file MOF](secureMOF.md).

La compilazione della prima configurazione sopra produce la struttura di cartelle seguente:

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

Se la configurazione accetta un parametro, come nel secondo esempio, il parametro deve essere specificato in fase di compilazione. La configurazione avrà un aspetto simile al seguente:

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -computerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## Uso di DependsOn
Un'utile parola chiave di DSC è __DependsOn__. In genere, anche se non necessariamente sempre, DSC applica le risorse nell'ordine in cui sono visualizzate all'interno della configurazione. Tuttavia, __DependsOn__ specifica le dipendenze tra le risorse e Gestione configurazione locale garantisce che le risorse vengano applicate nell'ordine corretto, indipendentemente da quello in cui sono definite le rispettive istanze. Ad esempio, una configurazione può specificare che un'istanza della risorsa __User__ dipende dalla presenza di un'istanza di __Group__:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            FullName = "TestUser"
            DependsOn = "GroupExample"
        }
    }
}
```

## Uso di nuove risorse nella configurazione
Eseguendo gli esempi precedenti, si ricevere un avviso che informa che è stata usata una risorsa senza importarla in modo esplicito.
Oggi DSC include 12 risorse come parte del modulo PSDesiredStateConfiguration. Le altre risorse nei moduli esterni devono essere inserite in `$env:PSModulePath` nell'ordine perché Gestione configurazione locale sia in grado di riconoscerle. È possibile usare un nuovo cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), per determinare le risorse installate nel sistema e disponibili per l'uso da parte di Gestione configurazione locale. 
Dopo che i moduli vengono inseriti in `$env:PSModulePath` e sono riconosciuti correttamente da [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), devono comunque essere caricati nella configurazione. __Import-DscResource__ è una parola chiave dinamica che può essere riconosciuta solo all'interno di un blocco __Configuration__, ovvero non è un cmdlet. __Import-DscResource__ supporta due parametri:
* __ModuleName__ corrisponde al modo consigliato di usare __Import-DscResource__. Questo parametro accetta il nome del modulo che contiene le risorse da importare, nonché una matrice di stringhe di nomi di modulo. 
* __Name__ è il nome della risorsa da importare. Non si tratta del nome descrittivo restituito come "Name" da [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), ma del nome di classe usato per definire lo schema della risorsa (restituito come __ResourceType__ da [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)). 

## Vedere anche
* [Panoramica di Windows PowerShell DSC (Desired State Configuration)](overview.md).
* [Risorse DSC](resources.md)
* [Configurazione di Gestione configurazione locale](metaconfig.md)
<!--HONumber=Feb16_HO4-->
