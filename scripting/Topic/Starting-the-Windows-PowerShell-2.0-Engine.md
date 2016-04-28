---
title: Avvio del motore di Windows PowerShell 2.0
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
---
# Avvio del motore di Windows PowerShell 2.0
Questa sezione illustra come avviare il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] in [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], che includono il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], e in altri sistemi in cui sono installati [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)].

[!INCLUDE[psversion4](../Token/psversion4_md.md)] e [!INCLUDE[psversion3](../Token/psversion3_md.md)] sono progettati per essere compatibili con le versioni precedenti, ovvero [!INCLUDE[psversion2](../Token/psversion2_md.md)]. I cmdlet, i provider, gli snap-in, i moduli e gli script scritti per [!INCLUDE[psversion2](../Token/psversion2_md.md)] possono essere eseguiti senza modifiche in [!INCLUDE[psversion4](../Token/psversion4_md.md)] e [!INCLUDE[psversion3](../Token/psversion3_md.md)]. Tuttavia, a causa di una modifica nei criteri di attivazione di runtime in Microsoft .NET Framework 4, i programmi host di [!INCLUDE[wps_2](../Token/wps_2_md.md)] scritti per [!INCLUDE[psversion2](../Token/psversion2_md.md)] e compilati con Common Language Runtime (CLR) 2.0 non possono essere eseguiti senza modifiche in [!INCLUDE[psversion3](../Token/psversion3_md.md)] o [!INCLUDE[psversion4](../Token/psversion4_md.md)], compilati con CLR 4.0. Il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] deve essere usato solo quando non è possibile eseguire un programma host o uno script esistente perché non è compatibile con [!INCLUDE[psversion4](../Token/psversion4_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] o Microsoft .NET Framework 4. È previsto che questi casi siano rari.

Molte applicazioni che richiedono l'uso del motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] lo avviano automaticamente. Queste istruzioni sono incluse per i rari casi in cui è necessario avviare il motore manualmente.

## Installazione e abilitazione delle applicazioni necessarie
Prima di avviare il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], abilitare il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] e Microsoft .NET Framework 3.5 con Service Pack 1. Per istruzioni, vedere [Installazione di Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

I sistemi in cui è installato [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] hanno tutti i componenti necessari. Non è richiesta alcuna configurazione aggiuntiva. Per informazioni sull'installazione di [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], vedere [Installazione di Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

## Come avviare il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Quando si avvia [!INCLUDE[mshshort](../Token/mshshort_md.md)], per impostazione predefinita viene eseguita la versione più recente. Per avviare [!INCLUDE[mshshort](../Token/mshshort_md.md)] con il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], usare il parametro Version di PowerShell.exe. Si può eseguire il comando in qualsiasi prompt dei comandi, inclusi Windows PowerShell e Cmd.exe.

```
PowerShell.exe -Version 2
```

## Come avviare una sessione remota con il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Per eseguire il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] in una sessione remota, creare una configurazione di sessione (detta anche "endpoint") nel computer remoto che carica il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]. La configurazione di sessione viene salvata nel computer remoto e può essere usata da qualsiasi utente autorizzato a creare sessioni che usano il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)].

Si tratta di un'attività avanzata, che in genere viene eseguita dagli amministratori di sistema.

La procedura seguente usa il parametro **PSVersion** del cmdlet [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) per creare una configurazione di sessione che usa il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Si può anche usare il parametro **PowerShellVersion** del cmdlet [New-PSSessionConfigurationFile](assetId:///5f3e3633-6e90-479c-aea9-ba45a1954866) per creare un file di configurazione per una sessione che carica il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Per modificare una configurazione di sessione in modo che usi il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] si può usare il parametro **PSVersion** del cmdlet [Set-PSSessionConfiguration](assetId:///b21fbad3-1759-4260-b206-dcb8431cd6ea).

Per altre informazioni sui file di configurazione della sessione, vedere [about_Session_Configuration_Files](assetId:///c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Per informazioni sulle configurazioni di sessione, incluse impostazione e sicurezza, vedere [about_Session_Configurations [v4]](assetId:///a2fbe12a-350c-4d04-be50-24102824e3ab).

#### Per avviare una sessione di [!INCLUDE[psversion2](../Token/psversion2_md.md)] remota

1.  Per creare una configurazione di sessione che richiede il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], usare il parametro **PSVersion** del cmdlet [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) impostando il valore "2.0". Eseguire questo comando nel computer che si trova sul "lato server" o ricevente della connessione.

    Il comando di esempio seguente crea la configurazione di sessione PS2 nel computer Server01. Per eseguire il comando, avviare [!INCLUDE[psversion4](../Token/psversion4_md.md)] o [!INCLUDE[psversion3](../Token/psversion3_md.md)] con l'opzione **Esegui come amministratore**.

    ```
    Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
    ```

2.  Per creare nel computer Server01 una sessione che usa la configurazione di sessione PS2, usare il parametro **ConfigurationName** dei cmdlet per la creazione di una sessione remota, ad esempio [New-PSSession](assetId:///76f6628c-054c-4eda-ba7a-a6f28daaa26f).

    All'avvio di una sessione che usa la configurazione di sessione, il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)] viene caricato automaticamente.

    Il comando seguente avvia nel computer Server01 una sessione che usa la configurazione di sessione PS2. Il comando salva la sessione nella variabile $s.

    ```
    $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
    ```

## Come avviare un processo in background con il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Per avviare un processo in background con il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)], usare il parametro **PSVersion** del cmdlet [Start-Job](assetId:///2bc04935-0deb-4ec0-b856-d7290cca6442).

Il comando seguente avvia un processo in background con il motore di [!INCLUDE[psversion2](../Token/psversion2_md.md)]

```
Start-Job {Get-Process} -PSVersion 2.0
```

Per altre informazioni sui processi in background, vedere [about_Jobs [v4]](assetId:///7362512a-8a4e-4575-b2ea-a740e5c4f002).



<!--HONumber=Apr16_HO1-->


