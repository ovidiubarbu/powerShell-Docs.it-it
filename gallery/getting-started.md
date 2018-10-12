---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Introduzione a PowerShell Gallery
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523056"
---
# <a name="get-started-with-the-powershell-gallery"></a>Introduzione a PowerShell Gallery

La modalità appropriata per installare elementi di PowerShell Gallery consiste nell'usare i cmdlet inclusi nel modulo [PowerShellGet](/powershell/module/powershellget). Non è necessario eseguire l'accesso per scaricare elementi da PowerShell Gallery.

> [!NOTE]
> È possibile scaricare un pacchetto direttamente da PowerShell Gallery, ma non è un approccio consigliato. Per altre informazioni, vedere [Download manuale del pacchetto](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).  


## <a name="discovering-items-from-the-powershell-gallery"></a>Individuazione di elementi da PowerShell Gallery

È possibile trovare elementi in PowerShell Gallery usando il controllo **Ricerca** in questo sito Web o sfogliando le pagine Moduli e Script. Per trovare elementi in PowerShell Gallery, è anche possibile eseguire i cmdlet [Find-Module][] e [Find-Script][] (a seconda dal tipo di elemento) con `-Repository PSGallery`.

Per filtrare i risultati dalla raccolta è possibile usare i parametri seguenti:

- Nome
- AllVersions
- MinimumVersion
- RequiredVersion
- Tag
- Includes
- DscResource
- RoleCapability
- Command
- Filter

Se si vogliono solo trovare risorse DSC specifiche nella raccolta, è possibile eseguire il cmdlet [Find-DscResource]. Find-DscResource restituisce dati sulle risorse DSC contenute nella raccolta.
Dato che le risorse DSC vengono sempre fornite come parte di un modulo, è comunque necessario eseguire [Install-Module][] per installare tali risorse DSC.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Informazioni sugli elementi in PowerShell Gallery

Dopo avere identificato un elemento di interesse, può essere utile ottenere altre informazioni che lo riguardano. A questo scopo, è possibile esaminare la pagina specifica dell'elemento nella raccolta. In quella pagina verranno indicati tutti i metadati caricati con l'elemento. I metadati per un elemento vengono forniti dall'autore dell'elemento e non sono verificati da Microsoft. Il proprietario dell'elemento è fortemente legato all'account della raccolta usato per pubblicare l'elemento ed è più affidabile rispetto al campo relativo all'autore.

Se si individua un elemento che si ritiene non essere stato pubblicato in buona fede, fare clic su **Report Abuse** (Segnala abusi) nella pagina dell'elemento.

Se si esegue [Find-Module][] o [Find-Script][], è possibile visualizzare questi dati nell'oggetto PSGetModuleInfo restituito. Ad esempio, l'esecuzione di `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
restituisce i dati nel modulo PSReadLine nella raccolta.

## <a name="downloading-items-from-the-powershell-gallery"></a>Download di elementi da PowerShell Gallery

Per il download di elementi da PowerShell Gallery è consigliabile seguire il processo seguente:

### <a name="inspect"></a>Controllare

Per scaricare un elemento dalla raccolta per ispezionarlo, eseguire il cmdlet [Save-Module][] o [Save-Script][], a seconda del tipo di elemento. In questo modo è possibile salvare l'elemento in locale senza installarlo, quindi ispezionarne il contenuto. L'elemento salvato dovrà poi essere eliminato manualmente.

Alcuni di questi elementi vengono creati da Microsoft, altri dalla community di PowerShell.
Microsoft consiglia di esaminare il contenuto e il codice degli elementi in questa raccolta prima dell'installazione.

Se si individua un elemento che si ritiene non essere stato pubblicato in buona fede, fare clic su **Report Abuse** (Segnala abusi) nella pagina dell'elemento.

### <a name="install"></a>Installare

Per installare un elemento dalla raccolta per usarlo, eseguire il cmdlet [Install-Module][] o [Install-Script][], a seconda del tipo di elemento.

[Install-Module][] installa il modulo in `$env:ProgramFiles\WindowsPowerShell\Modules` per impostazione predefinita.
È necessario un account Administrator. Se si aggiunge il parametro `-Scope CurrentUser` il modulo viene installato in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script][] installa lo script in `$env:ProgramFiles\WindowsPowerShell\Scripts` per impostazione predefinita.
È necessario un account Administrator. Se si aggiunge il parametro `-Scope CurrentUser` lo script viene installato in `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

Per impostazione predefinita, [Install-Module][] e [Install-Script][] installano la versione più recente di un elemento.
Per installare una versione precedente dell'elemento aggiungere il parametro `-RequiredVersion`.

### <a name="deploy"></a>Distribuire

Per distribuire un elemento da PowerShell Gallery in Automazione di Azure, fare clic su **Deploy to Azure Automation** (Distribuisci in Automazione di Azure) nella pagina dei dettagli dell'elemento. Si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure. Se si distribuiscono elementi con dipendenze, verranno distribuite tutte le dipendenze in Automazione di Azure. Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag **AzureAutomationNotSupported** ai metadati dell'elemento.

Per altre informazioni su Automazione di Azure, vedere la documentazione di [Automazione di Azure](/azure/automation).

## <a name="updating-items-from-the-powershell-gallery"></a>Aggiornamento di elementi da PowerShell Gallery

Per aggiornare gli elementi installati da PowerShell Gallery eseguire i cmdlet [Update-Module][] o [Update-Script][]. Quando viene eseguito senza parametri aggiuntivi, [Update-Module][] prova ad aggiornare ogni modulo installato eseguendo [Install-Module][]. Per aggiornare i moduli in modo selettivo aggiungere il parametro `-Name`.

In modo analogo, anche [Update-Script][] eseguito senza parametri aggiuntivi prova ad aggiornare ogni script installato eseguendo [Install-Script][]. Per aggiornare gli script in modo selettivo aggiungere il parametro `-Name`.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Ottenere l'elenco degli elementi installati da PowerShell Gallery

Per scoprire quali moduli sono stati installati da PowerShell Gallery, eseguire il cmdlet [Get-InstalledModule][]. Questo comando elenca tutti i moduli presenti nel sistema che sono stati installati direttamente da PowerShell Gallery.

Analogamente, per scoprire quali script sono stati installati da PowerShell Gallery, eseguire il cmdlet [Get-InstalledScript][]. Questo comando elenca tutti gli script presenti nel sistema che sono stati installati direttamente da PowerShell Gallery.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script