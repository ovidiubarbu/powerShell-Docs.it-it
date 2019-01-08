---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Istruzioni condizionali e cicli nelle configurazioni
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401249"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Istruzioni condizionali e cicli nelle configurazioni

È possibile rendere il [configurazioni](configurations.md) più dinamico mediante parole chiave di controllo del flusso di PowerShell. Questo articolo illustrerà come è possibile usare le istruzioni condizionali e cicli per rendere più dinamico delle configurazioni. Combinazione condizionali e cicli con [parametri](add-parameters-to-a-configuration.md) e [i dati di configurazione](configData.md) consente maggiore flessibilità e controllo durante la compilazione delle configurazioni.

Proprio come una funzione o un blocco di Script, è possibile usare qualsiasi linguaggio di PowerShell all'interno di una configurazione. Le istruzioni usate verranno valutate solo quando si chiama la configurazione di compilare un file "con estensione MOF". Gli esempi seguenti mostrano gli scenari semplici per illustrare i concetti. Istruzioni condizionali sono i cicli vengono usati più spesso con i parametri e i dati di configurazione.

In questo semplice esempio, il **servizio** blocco di risorse recupera lo stato corrente di un servizio in fase di compilazione per generare un file "con estensione MOF" che mantiene lo stato corrente.

> [!NOTE]
> Utilizzo di blocchi di risorsa dinamici emergeranno l'efficacia di Intellisense. Il parser di PowerShell non è possibile determinare se i valori specificati sono accettabili fino a quando non viene compilata la configurazione.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Inoltre, è possibile creare un **Service** bloccare risorse per ogni servizio nel computer corrente, usando un `foreach` ciclo.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

È possibile anche creare configurazioni per i computer che sono online, usando una semplice `if` istruzione.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> La risorsa dinamica consente di bloccare nel riferimento negli esempi precedenti il computer corrente. In questa istanza, che sarebbe il computer si modifica la configurazione su, non il nodo di destinazione.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Riepilogo

In breve, è possibile usare qualsiasi linguaggio di PowerShell all'interno di una configurazione.

Sono incluse operazioni come:

- Oggetti personalizzati
- Tabelle hash
- Modifica di stringhe
- Comunicazione remota
- CIM e WMI
- Oggetti di Active Directory
- altro...

Qualsiasi codice di PowerShell definito in una configurazione verrà valutata una fase di compilazione, ma è anche possibile inserire codice nello script che contiene la configurazione. Verrà eseguito qualsiasi codice all'esterno del blocco di configurazione quando si importa la configurazione.

## <a name="see-also"></a>Vedere anche

- [Aggiungere parametri a una configurazione](add-parameters-to-a-configuration.md)
- [Separare i dati di configurazione dalle configurazioni](configData.md)
