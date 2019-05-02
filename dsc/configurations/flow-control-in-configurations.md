---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Istruzioni condizionali e cicli nelle configurazioni
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080136"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Istruzioni condizionali e cicli nelle configurazioni

È possibile rendere le [configurazioni](configurations.md) più dinamiche mediante le parole chiave di controllo del flusso di PowerShell. Questo articolo illustrerà come è possibile usare le istruzioni condizionali e i cicli per rendere più dinamiche le configurazioni. La combinazione di istruzioni condizionali e cicli con [parametri](add-parameters-to-a-configuration.md) e [dati di configurazione](configData.md) consente di ottenere maggiori flessibilità e controllo durante la compilazione delle configurazioni.

Proprio come una funzione o un blocco di script, è possibile usare qualsiasi elemento del linguaggio di PowerShell all'interno di una configurazione. Le istruzioni usate verranno valutate solo quando si chiama la configurazione per compilare un file "MOF". Gli esempi seguenti mostrano alcuni scenari semplici per una dimostrazione dei concetti. Le istruzioni condizionali e i cicli vengono usati più spesso con i parametri e i dati di configurazione.

In questo semplice esempio, il blocco di risorse **Service** recupera lo stato corrente di un servizio in fase di compilazione per generare un file "MOF" che mantiene lo stato corrente.

> [!NOTE]
> L'uso di blocchi di risorse dinamici comprometterà l'efficacia di Intellisense. Il parser di PowerShell non è in grado di determinare se i valori specificati sono accettabili fino a quando non viene compilata la configurazione.

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

Si potrebbe anche creare un blocco di risorse **Service** per ogni servizio nel computer corrente usando un ciclo `foreach`.

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

È anche possibile creare configurazioni solo per i computer online, usando una semplice istruzione `if`.

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
> I blocchi di risorse dinamici negli esempi precedenti fanno riferimento al computer corrente. In questa istanza, si tratterebbe del computer in cui viene creata la configurazione e non del nodo di destinazione.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Riepilogo

In breve, è possibile usare qualsiasi elemento del linguaggio di PowerShell all'interno di una configurazione,

inclusi elementi come i seguenti:

- Oggetti personalizzati
- Tabelle hash
- Modifica di stringhe
- Comunicazione remota
- WMI e CIM
- Oggetti di Active Directory
- altro...

Qualsiasi codice di PowerShell definito in una configurazione verrà valutato in fase di compilazione, ma è anche possibile inserire codice nello script che contiene la configurazione. Qualsiasi codice all'esterno del blocco di configurazione verrà eseguito quando si importa la configurazione.

## <a name="see-also"></a>Vedere anche

- [Aggiungere parametri a una configurazione](add-parameters-to-a-configuration.md)
- [Separare i dati di configurazione dalle configurazioni](configData.md)
