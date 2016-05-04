---
title: Avvio di Windows PowerShell in versioni precedenti di Windows
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# Avvio di Windows PowerShell in versioni precedenti di Windows
Questa sezione descrive come avviare [!INCLUDE[wps_2](../Token/wps_2_md.md)] e [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] in [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)], [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)]. Illustra anche come abilitare la funzionalità facoltativa per [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] in [!INCLUDE[psversion2](../Token/psversion2_md.md)] su [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)].

Per installare [!INCLUDE[psversion4](../Token/psversion4_md.md)] nei sistemi supportati, scaricare e installare [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Per altre informazioni, vedere [Installazione di Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

Per installare [!INCLUDE[psversion3](../Token/psversion3_md.md)] nei sistemi supportati, scaricare e installare [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Per altre informazioni, vedere [Installazione di Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

## Come avviare [!INCLUDE[mshshort](../Token/mshshort_md.md)] nelle versioni precedenti di Windows
Usare uno dei metodi seguenti per avviare la versione installata di [!INCLUDE[psversion3](../Token/psversion3_md.md)] o [!INCLUDE[psversion4](../Token/psversion4_md.md)], se applicabile.

#### Dal menu Start

-   Fare clic su **Start**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell**.

-   Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell**.

#### Al prompt dei comandi

-   In Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)], o [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE, per avviare [!INCLUDE[wps_2](../Token/wps_2_md.md)], digitare:

    ```
    PowerShell
    ```

    È anche possibile usare i parametri del programma PowerShell.exe per personalizzare la sessione. Per altre informazioni, vedere [Guida della riga di comando PowerShell.exe](../Topic/PowerShell.exe-Command-Line-Help.md).

#### Con privilegi amministrativi ("Esegui come amministratore")

1.  Fare clic su **Start**, digitare **PowerShell**, fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi fare clic su **Esegui come amministratore**.

## Come avviare [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] nelle versioni precedenti di Windows
Per avviare [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)], usare uno dei seguenti metodi.

#### Dal menu Start

-   Fare clic su **Start**, digitare **ISE** e quindi fare clic su **Windows PowerShell ISE**.

-   Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.

#### Al prompt dei comandi

-   In Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)], o [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE, per avviare [!INCLUDE[wps_2](../Token/wps_2_md.md)], digitare:

    ```
    PowerShell_ISE
    ```

    o

    ```
    ISE
    ```

#### Con privilegi amministrativi ("Esegui come amministratore")

1.  Fare clic su **Start**, digitare **ISE**, fare clic con il pulsante destro del mouse su **Windows PowerShell ISE** e quindi fare clic su **Esegui come amministratore**.

## Come abilitare [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] nelle versioni precedenti di Windows
In [!INCLUDE[psversion4](../Token/psversion4_md.md)] e [!INCLUDE[psversion3](../Token/psversion3_md.md)], [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] è abilitato per impostazione predefinita in tutte le versioni di Windows. Se non è già abilitato, viene abilitato da Windows Management Framework 4.0 o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)].

In [!INCLUDE[psversion2](../Token/psversion2_md.md)] [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] è abilitato per impostazione predefinita in [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]. Tuttavia, in [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)] costituisce una funzionalità facoltativa.

Per abilitare [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] in [!INCLUDE[psversion2](../Token/psversion2_md.md)] su [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] o [!INCLUDE[lserver](../Token/lserver_md.md)], attenersi alla seguente procedura.

#### Per abilitare [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

1.  Avviare Server Manager.

2.  Fare clic su **Funzionalità** e quindi su **Aggiungi funzionalità**.

3.  In Selezione funzionalità fare clic su [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)].



<!--HONumber=Apr16_HO1-->


