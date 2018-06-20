---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187538"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Consentire risorse duplicate identiche in una configurazione

DSC non consente o non gestisce definizioni di risorse in conflitto all'interno di una configurazione. Anziché tentare di risolvere il conflitto, l'esito è semplicemente negativo. Dato che il riutilizzo delle configurazioni diventa sempre più comune tramite risorse composite, i conflitti si verificheranno sempre più spesso. Quando le definizioni delle risorse in conflitto sono identiche, DSC dovrebbe essere intelligente e consentire questa situazione. In questa versione è supportata la presenza di più istanze di risorse con definizioni identiche:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

Nelle versioni precedenti, il risultato sarebbe la non riuscita della compilazione a causa di un conflitto tra le istanze di WindowsFeature FE_IIS e WindowsFeature Worker_IIS nel tentativo di assicurarsi che il ruolo 'Web-Server' sia installato. Si noti che *tutte* le proprietà da configurare in queste due configurazioni sono identiche. Dato che *tutte* le proprietà in queste due risorse sono identiche, il risultato sarà ora una compilazione corretta.

In presenza di differenze per qualsiasi proprietà tra le due risorse, non verranno considerate identiche e la compilazione avrà esito negativo:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

Questa configurazione molto simile non riuscirà perché le risorse WindowsFeature FE_IIS e WindowsFeature Worker_II non sono più identiche e pertanto sono in conflitto.
