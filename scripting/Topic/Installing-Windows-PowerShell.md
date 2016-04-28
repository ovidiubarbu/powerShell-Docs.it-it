---
title: Installazione di Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---
# Installazione di Windows PowerShell
[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] e [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] includono [!INCLUDE[psversion3](../Token/psversion3_md.md)] e tutti i relativi prerequisiti. Il sistema include anche il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] per la compatibilità con le versioni precedenti dei programmi host che non possono usare [!INCLUDE[psversion3](../Token/psversion3_md.md)].

Questo argomento descrive come installare [!INCLUDE[psversion3](../Token/psversion3_md.md)] nei sistemi precedenti, nonché come installare e abilitare le funzionalità necessarie.

Questo argomento include le sezioni seguenti:

-   [Installazione di Windows PowerShell in Windows 8 e Windows Server 2012](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Installazione di Windows PowerShell in Windows 7 e Windows Server 2008 R2](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Installazione di Windows PowerShell in Windows Server 2008](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Installazione di Windows PowerShell in Server Core](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Distribuzione di Accesso Web Windows PowerShell](assetId:///639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Installazione del motore di Windows PowerShell 2.0](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installazione di Windows PowerShell in Windows 8 e Windows Server 2012
[!INCLUDE[psversion3](../Token/psversion3_md.md)] viene fornito già installato, configurato e pronto per l'utilizzo. [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] viene installato e abilitato. Per informazioni sull'avvio di [!INCLUDE[mshshort](../Token/mshshort_md.md)], vedere [Avvio di Windows PowerShell in Windows 8](assetId:///d7be1668-8617-4890-ad90-dd9765fbd2c3) e [Avvio di Windows PowerShell in Windows Server 2012](assetId:///4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968).

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installazione di Windows PowerShell in Windows 7 e Windows Server 2008 R2
Queste istruzioni spiegano come installare [!INCLUDE[psversion3](../Token/psversion3_md.md)] nei computer che eseguono [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] con Service Pack 1 e [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] con Service Pack 1. Di seguito sono disponibili istruzioni di installazione separate per i computer con l'opzione di installazione Server Core di [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)].

#### Preparativi per l'installazione

-   Prima di installare [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], disinstallare eventuali versioni precedenti di Windows Management Framework 3.0.

#### Per installare [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Oppure installare Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

2.  Installare [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Per informazioni sull'avvio di [!INCLUDE[psversion3](../Token/psversion3_md.md)], vedere [Avvio di Windows PowerShell in versioni precedenti di Windows](../Topic/Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).

## <a name="BKMK_InstallingOnServerCore"></a>Installazione di Windows PowerShell in Server Core
Queste istruzioni spiegano come installare [!INCLUDE[psversion3](../Token/psversion3_md.md)] nei computer che eseguono l'opzione di installazione Server Core di [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] con Service Pack 1.

I primi passaggi della procedura usano i comandi Gestione e manutenzione immagini distribuzione per installare Microsoft [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] per Server Core e [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Questi programmi sono prerequisiti di [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], che viene installato in un passaggio successivo.

#### Preparativi per l'installazione

-   Prima di installare [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], disinstallare eventuali versioni precedenti di Windows Management Framework 3.0.

#### Per installare [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Avviare Cmd.exe

2.  Eseguire i seguenti comandi Gestione e manutenzione immagini distribuzione. Questi comandi installano [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] e [!INCLUDE[psversion2](../Token/psversion2_md.md)].

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Eseguire l'installazione completa di [!INCLUDE[netfx40_short](../Token/netfx40_short_md.md)] per Server Core dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).

4.  Installare [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installazione di Windows PowerShell in Windows Server 2008
Queste istruzioni spiegano come installare [!INCLUDE[psversion3](../Token/psversion3_md.md)] nei computer che eseguono [!INCLUDE[lserver](../Token/lserver_md.md)] con Service Pack 2.

Nei sistemi [!INCLUDE[lserver](../Token/lserver_md.md)] Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], KB 968930) è un prerequisito di [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. La funzionalità di "protezione estesa per l'autenticazione" protegge il computer da attacchi di inoltro dell'autenticazione e consente di usare il parametro **UseSSL** durante la creazione delle sessioni remote. Per installare [!INCLUDE[psversion3](../Token/psversion3_md.md)] e il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], usare la procedura seguente.

#### Preparativi per l'installazione

-   Prima di installare [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], disinstallare eventuali versioni precedenti di Windows Management Framework 3.0.

#### Per installare [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Installare Microsoft .NET Framework 3.5 con Service Pack 1 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).

2.  Installare Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], KB 968930) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Oppure installare Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

4.  Installare la "protezione estesa per l'autenticazione" (KB 968389) da [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Installare [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## Vedere anche
[Requisiti di sistema di Windows PowerShell](../Topic/Windows-PowerShell-System-Requirements.md)
[Avvio di Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO1-->


