---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "distribuzione e manutenzione con più computer"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 784806197a64eb30af1ecea4af55575434ce7b87

---

# Distribuzione e manutenzione con più computer
A questo punto, JEA è stato distribuito più volte ai sistemi locali.
Poiché l'ambiente di produzione probabilmente è costituito da più di un computer, è importante esaminare i passaggi essenziali del processo di distribuzione che dovranno essere ripetuti in ogni computer.

## Passaggi di alto livello:
1.  Copiare i moduli (con capacità del ruolo) in ogni nodo.
2.  Copiare i file di configurazione di sessione in ogni nodo.
3.  Eseguire `Register-PSSessionConfiguration` con la configurazione di sessione.
4.  Conservare una copia della configurazione di sessione e dei toolkit in un luogo sicuro.
Quando si apportano modifiche, è opportuno usare un'unica "origine di dati reali".

## Script di esempio
Di seguito è riportato un esempio di script per la distribuzione.
Per usarlo nel proprio ambiente, è necessario usare i nomi o i percorsi dei moduli e delle condivisioni di file reali.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## Modifica delle capacità
Quando si gestiscono molti computer, è importante che le modifiche vengano implementate in modo coerente.
Se per JEA è già disponibile una risorsa DSC, l'ambiente è sincronizzato.
In caso contrario, è consigliabile conservare una copia master delle configurazioni di sessione e distribuirla di nuovo ogni volta che si apporta una modifica.

## Rimozione delle capacità
Per rimuovere la configurazione JEA dai sistemi, usare il comando seguente in ogni computer:
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```




<!--HONumber=Aug16_HO3-->


