---
title: Modalità di utilizzo dei profili in Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# Modalità di utilizzo dei profili in Windows PowerShell ISE
Questo argomento illustra come usare i profili in [!INCLUDE[ise_1](../Token/ise_1_md.md)]. Prima di eseguire le attività in questa sezione, è consigliabile consultare [about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054) oppure digitare "get-help about_profiles" nel riquadro della console e premere **INVIO**.

Un profilo è uno script di [!INCLUDE[ise_2](../Token/ise_2_md.md)] che viene eseguito automaticamente quando si avvia una nuova sessione.  È possibile creare uno o più profili di [!INCLUDE[wps_2](../Token/wps_2_md.md)] per [!INCLUDE[ise_2](../Token/ise_2_md.md)] e usarli per configurare l'ambiente [!INCLUDE[wps_2](../Token/wps_2_md.md)] o [!INCLUDE[ise_2](../Token/ise_2_md.md)], prepararlo per l'uso, con le variabili, gli alias, le funzioni e le preferenze di colore e tipo di carattere che si vuole avere a disposizione. Il profilo interessa ogni sessione di [!INCLUDE[ise_2](../Token/ise_2_md.md)] avviata.

> [!NOTE]
> I criteri di esecuzione di [!INCLUDE[wps_2](../Token/wps_2_md.md)] determinano se è possibile eseguire gli script e caricare un profilo. I criteri di esecuzione predefiniti, "Restricted", impediscono l'esecuzione di tutti gli script, inclusi i profili. Se si usano i criteri "Restricted", il profilo non potrà essere caricato. Per altre informazioni sui criteri di esecuzione, vedere [about_Execution_Policies [v4]](assetId:///347708dc-1515-4d74-978b-8334603472e6).

## Selezione di un profilo da usare in Windows PowerShell ISE
[!INCLUDE[ise_2](../Token/ise_2_md.md)] supporta i profili per l'utente corrente e per tutti gli utenti. Supporta anche i profili [!INCLUDE[wps_2](../Token/wps_2_md.md)] che si applicano a tutti gli host.

Il profilo usato dipende da come si usano [!INCLUDE[wps_2](../Token/wps_2_md.md)] e [!INCLUDE[ise_2](../Token/ise_2_md.md)].

-   Se si usa solo [!INCLUDE[ise_2](../Token/ise_2_md.md)] per eseguire Windows PowerShell, salvare tutti gli elementi in uno dei profili ISE specifici, ad esempio il profilo CurrentUserCurrentHost per [!INCLUDE[ise_2](../Token/ise_2_md.md)] o il profilo AllUsersCurrentHost per [!INCLUDE[ise_2](../Token/ise_2_md.md)].

-   Se si usano più programmi host per l'esecuzione di Windows PowerShell, salvare funzioni, alias, variabili e comandi in un profilo che interessa tutti i programmi host, ad esempio il profilo CurrentUserAllHosts o il profilo AllUsersAllHosts, e quindi salvare le funzionalità ISE specifiche, come la personalizzazione di colori e tipi di carattere, nel profilo CurrentUserCurrentHost per il profilo [!INCLUDE[ise_2](../Token/ise_2_md.md)] o il profilo AllUsersCurrentHost per [!INCLUDE[ise_2](../Token/ise_2_md.md)].

I seguenti profili possono essere creati e usati in [!INCLUDE[ise_2](../Token/ise_2_md.md)]. Ogni profilo viene salvato nel proprio percorso specifico.

|Tipo di profilo|Percorso del profilo|
|----------------|----------------|
|"Utente corrente, PowerShell ISE"|$profile.CurrentUserCurrentHost o $profile|
|"Tutti gli utenti, PowerShell ISE"|$profile.AllUsersCurrentHost|
|"Utente corrente, tutti gli host"|$profile.CurrentUserAllHosts|
|"Tutti gli utenti, tutti gli host"|$profile.AllUsersAllHosts|

## Per creare un nuovo profilo
Per creare un nuovo profilo "Utente corrente, Windows PowerShell ISE", eseguire questo comando:

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

Per creare un nuovo profilo "Tutti gli utenti, Windows PowerShell ISE", eseguire questo comando:

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

Per creare un nuovo profilo "Utente corrente, tutti gli host", eseguire questo comando:

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

Per creare un nuovo profilo "Tutti gli utenti, tutti gli host", digitare:

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## Per modificare un profilo

1.  Per aprire il profilo, eseguire il comando psedit con la variabile che specifica il profilo da modificare. Ad esempio, per aprire il profilo "Utente corrente, Windows PowerShell ISE", digitare: `psEdit $profile`

2.  Aggiungere alcuni elementi al profilo. Di seguito sono riportati alcuni esempi per iniziare:

    -   Per modificare il colore di sfondo predefinito del riquadro della console impostandolo sul blu, nel file del profilo digitare: `$psISE.Options.OutputPaneBackground = 'blue'` . Per altre informazioni sulla variabile $psISE, vedere [Riferimenti al modello a oggetti di Windows PowerShell ISE](assetId:///e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c).

    -   Per modificare le dimensioni del carattere impostandole su 20, nel file del profilo digitare: `$psISE.Options.FontSize =20`

3.  Per salvare il file del profilo, nel menu **File** fare clic su **Salva**. Alla successiva apertura di [!INCLUDE[ise_2](../Token/ise_2_md.md)], le personalizzazioni verranno applicate.

## Vedere anche
[about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Uso di Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


