---
title: Installazione del motore di Windows PowerShell 2.0
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
---
# Installazione del motore di Windows PowerShell 2.0
In questo argomento viene descritto come installare il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)].

[!INCLUDE[psversion3](../Token/psversion3_md.md)] è progettato per essere compatibile con le versioni precedenti, ovvero con [!INCLUDE[psversion2](../Token/psversion2_md.md)]. I cmdlet, i provider, gli snap-in, i moduli e gli script scritti per [!INCLUDE[psversion2](../Token/psversion2_md.md)] possono essere eseguiti senza modifiche in [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)]. Tuttavia, a causa di una modifica nei criteri di attivazione di runtime in Microsoft .NET Framework 4, i programmi host di Windows PowerShell scritti per [!INCLUDE[psversion2](../Token/psversion2_md.md)] e compilati con Common Language Runtime (CLR) 2.0 non possono essere eseguiti senza modifiche nelle versioni successive di [!INCLUDE[wps_2](../Token/wps_2_md.md)], compilato con CLR 4.0.

Per mantenere la compatibilità con le versioni precedenti di comandi e programmi host interessati da queste modifiche, i motori di [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)] sono progettati per l'esecuzione side-by-side. Inoltre, il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] è incluso in [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] e [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. Il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] deve essere usato solo quando non è possibile eseguire un programma host o uno script esistente perché non è compatibile con [!INCLUDE[psversion3](../Token/psversion3_md.md)], [!INCLUDE[psversion4](../Token/psversion4_md.md)] o Microsoft .NET Framework 4. È previsto che questi casi siano rari.

Il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] è una funzionalità facoltativa di [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] e [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)]. Nelle versioni precedenti di Windows, quando si installa [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], l'installazione di [!INCLUDE[psversion3](../Token/psversion3_md.md)] sostituisce completamente l'installazione di [!INCLUDE[psversion2](../Token/psversion2_md.md)] nella directory di installazione di [!INCLUDE[wps_2](../Token/wps_2_md.md)]. Tuttavia, il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] viene mantenuto.

Per informazioni sull'avvio del motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], vedere [Avvio del motore di Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## In [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] e [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]
In [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] e [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] la funzionalità del motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] è attivata per impostazione predefinita. Tuttavia, per usarla è necessario attivare l'opzione per Microsoft .NET Framework 3.5 richiesta. Questa sezione spiega anche come attivare e disattivare la funzionalità del motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Per attivare .NET Framework 3.5

1.  Nella schermata **Start** digitare **funzionalità di Windows**.

2.  Nella barra delle app** ** fare clic su **Impostazioni** e quindi su **Attivazione o disattivazione delle funzionalità Windows**.

3.  Nella casella **Funzionalità Windows** fare clic su **.NET Framework 3.5 (include .NET 2.0 e 3.0** per selezionarlo.

    Quando si seleziona **.NET Framework 3.5 (include .NET 2.0 e 3.0**, la casella viene compilata per indicare che la funzionalità è selezionata solo in parte. Tuttavia, per il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] è sufficiente.

#### Per attivare e disattivare il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]

1.  Nella schermata **Start** digitare **funzionalità di Windows**.

2.  Nella barra delle app** ** fare clic su **Impostazioni** e quindi su **Attivazione o disattivazione delle funzionalità Windows**.

3.  Nella casella **Funzionalità Windows** espandere il nodo **[!INCLUDE[psversion2](../Token/psversion2_md.md)]** e fare clic sulla casella **Motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]** per selezionarla o deselezionarla.

## In [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]
Usare le procedure seguenti per aggiungere le funzionalità del motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] e Microsoft .NET Framework 3.5. Il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] richiede come minimo Microsoft .NET Framework 2.0.50727. È possibile soddisfare questo requisito con Microsoft .NET Framework 3.5.

#### Per aggiungere la funzionalità .NET Framework 3.5

1.  In **Server Manager** scegliere **Aggiungi ruoli e funzionalità** dal menu **Gestione**.

    In alternativa, in **Server Manager** fare clic su **Tutti i server**, fare clic con il pulsante destro del mouse sul nome di un server e quindi selezionare **Aggiungi ruoli e funzionalità**.

2.  Nella pagina **Tipo di installazione** selezionare **Installazione basata su ruoli o basata su funzionalità**.

3.  Nella pagina **Funzionalità** espandere il nodo **Funzionalità di .NET Framework 3.5** e selezionare **.NET Framework 3.5 (include .NET 2.0 e 3.0)**.

    Le altre opzioni di tale nodo non sono necessarie per il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Per aggiungere la funzionalità del motore [!INCLUDE[psversion2](../Token/psversion2_md.md)]

-   In **Server Manager** scegliere **Aggiungi ruoli e funzionalità** dal menu **Gestione**.

    In alternativa, in **Server Manager** fare clic su **Tutti i server**, fare clic con il pulsante destro del mouse sul nome di un server e quindi selezionare **Aggiungi ruoli e funzionalità**.

-   Nella pagina **Tipo di installazione** selezionare **Installazione basata su ruoli o basata su funzionalità**.

-   Nella pagina **Funzionalità** espandere il nodo **[!INCLUDE[mshshort](../Token/mshshort_md.md)] (installato)** e selezionare **Motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]**.

Per informazioni sull'avvio del motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], vedere [Avvio del motore di Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Nei sistemi precedenti
Il pacchetto [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) che consente di installare [!INCLUDE[psversion4](../Token/psversion4_md.md)] in [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], include il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] è abilitato e pronto per l'uso, se necessario, senza che siano necessari ulteriori interventi di installazione, configurazione o impostazione.

Il pacchetto di [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], che consente di installare [!INCLUDE[psversion3](../Token/psversion3_md.md)] in [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)], include il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] è abilitato e pronto per l'uso, se necessario, senza che siano necessari ulteriori interventi di installazione, configurazione o impostazione.

## Vedere anche
[Requisiti di sistema di Windows PowerShell](../Topic/Windows-PowerShell-System-Requirements.md)
[Installazione di Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Avvio di Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[Avvio del motore di Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)



<!--HONumber=Apr16_HO1-->


