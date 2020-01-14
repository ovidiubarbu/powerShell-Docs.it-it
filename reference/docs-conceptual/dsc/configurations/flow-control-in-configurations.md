---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Istruzioni condizionali e cicli nelle configurazioni
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736897"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Istruzioni condizionali e cicli in una configurazione

È possibile rendere la [configurazione](configurations.md) più dinamica usando le parole chiave di controllo del flusso di PowerShell. Questo articolo illustra come è possibile usare le istruzioni condizionali e i cicli per rendere più dinamica `Configuration`. La combinazione di istruzioni condizionali e cicli con [parametri](add-parameters-to-a-configuration.md) e [dati di configurazione](configData.md) consente di ottenere maggiori flessibilità e controllo durante la compilazione di `Configuration`.

Proprio come una funzione o un blocco di script, è possibile usare qualsiasi funzione del linguaggio di PowerShell in una `Configuration`.
Le istruzioni usate verranno valutate solo quando si chiama la `Configuration` per compilare un file `.mof`. Gli esempi seguenti illustrano alcuni scenari per una dimostrazione dei concetti. Le istruzioni condizionali e i cicli vengono usati più spesso con i parametri e i dati di configurazione.

In questo esempio il blocco di risorse **Service** recupera lo stato corrente di un servizio in fase di compilazione per generare un file `.mof` che mantiene lo stato corrente.

> [!NOTE]
> L'uso di blocchi di risorse dinamici comprometterà l'efficacia di Intellisense. Il parser di PowerShell non è in grado di determinare se i valori specificati sono accettabili fino a quando non viene compilata la `Configuration`.

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
        foreach ($service in $(Get-Service))
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

È anche possibile creare una `Configuration` solo per i computer online usando un'istruzione `if`.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> I blocchi di risorse dinamici negli esempi precedenti fanno riferimento al computer corrente. In questa istanza sarebbe il computer in cui viene creata la `Configuration` e non il nodo di destinazione.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Summary

In breve, è possibile usare qualsiasi funzione del linguaggio di PowerShell in una `Configuration`,

inclusi elementi come i seguenti:

- Oggetti personalizzati
- Tabelle hash
- Modifica di stringhe
- Comunicazione remota
- WMI e CIM
- Oggetti di Active Directory
- altro...

Qualsiasi codice di PowerShell definito in una `Configuration` viene valutato in fase di compilazione, ma è anche possibile inserire codice nello script che contiene la `Configuration`. Qualsiasi codice esterno al blocco `Configuration` viene eseguito quando si importa la `Configuration`.

## <a name="see-also"></a>Vedere anche

- [Aggiungere parametri a una configurazione](add-parameters-to-a-configuration.md)
- [Separare i dati di configurazione dalle configurazioni](configData.md)
