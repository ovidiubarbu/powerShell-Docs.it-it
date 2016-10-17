---
title: Convenzione di denominazione della configurazione parziale pull
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##Convenzione di denominazione della configurazione parziale pull
Nelle versioni precedenti la convenzione di denominazione di una configurazione parziale prevedeva che il nome del file MOF del servizio o del server di pull corrispondesse al nome della configurazione parziale specificato nelle impostazioni di Gestione configurazione locale che doveva a sua volta corrispondere al nome di configurazione incorporato nel file MOF. Vedere gli snapshot seguenti:- •   Impostazioni della configurazione locale che definisce una configurazione parziale che un nodo è autorizzato a ricevere.

![Metaconfigurazione di esempio](../../images/MetaConfigPartialOne.png)

•   Definizione di configurazione parziale di esempio 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

•   'ConfigurationName' incorporato nel file MOF generato.

![Esempio di file MOF generato](../../images/PartialGeneratedMof.png)

•   FileName nel repository di configurazione pull 

![FileName nel repository di configurazione](../../images/PartialInConfigRepository.png)

Il nome del servizio di Automazione di Azure ha generato i file MOF come ``<ConfigurationName>.<NodeName>.mof``. La configurazione seguente verrà compilata in PartialOne.Localhost.mof.  
Questo ha impedito l'esecuzione del pull di una configurazione parziale dal servizio di Automazione di Azure.

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

In WMF 5.1 la configurazione parziale nel server di pull/servizio può essere denominata ``<ConfigurationName>.<NodeName>.mof``. Inoltre, se un computer effettua il pull di una configurazione singola da un server/servizio di pull, il documento di configurazione nel repository di configurazione del server di pull potrà avere qualsiasi nome. Questa flessibilità di denominazione consente di gestire la configurazione parziale di un nodo usando il servizio di pull locale o di Automazione di Azure. Ad esempio, si può avere una configurazione parziale "di base" con push in locale e un'altra configurazione parziale con pull eseguito dal servizio di Automazione di Azure.

La metaconfigurazione seguente imposta un nodo che viene gestito sia localmente che dal servizio di automazione di Azure.

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```





<!--HONumber=Aug16_HO3-->


