---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Introduzione a PowerShell Gallery
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225676"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Introduzione a PowerShell Gallery

Il modo appropriato per installare pacchetti di PowerShell Gallery consiste nell'usare i cmdlet inclusi nel modulo [PowerShellGet](/powershell/module/powershellget). Non è necessario eseguire l'accesso per scaricare elementi da PowerShell Gallery.

> [!NOTE]
> È possibile scaricare un pacchetto direttamente da PowerShell Gallery, ma non è un approccio consigliato.
> Per altre informazioni, vedere [Download manuale del pacchetto](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Individuazione di pacchetti da PowerShell Gallery

È possibile trovare pacchetti in PowerShell Gallery usando il controllo **Ricerca** in questo sito Web o sfogliando le pagine Moduli e Script. Per trovare pacchetti in PowerShell Gallery, è anche possibile eseguire i cmdlet [Find-Module][] e [Find-Script][] (a seconda dal tipo di elemento) con `-Repository PSGallery`.

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

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Informazioni sui pacchetti in PowerShell Gallery

Dopo avere identificato un pacchetto di interesse, può essere utile ottenere altre informazioni che lo riguardano. A questo scopo, è possibile esaminare la pagina specifica del pacchetto nella raccolta. In tale pagina verranno indicati tutti i metadati caricati con il pacchetto. Questi metadati vengono forniti dall'autore del pacchetto e non sono verificati da Microsoft. Il proprietario del pacchetto è strettamente legato all'account della raccolta usato per pubblicare il pacchetto ed è più affidabile rispetto al campo relativo all'autore.

Se si individua un pacchetto che si ritiene non essere stato pubblicato in buona fede, fare clic su **Report Abuse** (Segnala abusi) nella pagina del pacchetto.

Se si esegue [Find-Module][] o [Find-Script][], è possibile visualizzare questi dati nell'oggetto PSGetModuleInfo restituito. Ad esempio, l'esecuzione di `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
restituisce i dati nel modulo PSReadLine nella raccolta.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Download di pacchetti da PowerShell Gallery

Per il download di pacchetti da PowerShell Gallery è consigliabile seguire questa procedura:

### <a name="inspect"></a>Controllare

Per scaricare un pacchetto dalla raccolta per esaminarlo, eseguire il cmdlet [Save-Module][] o [Save-Script][], a seconda del tipo di pacchetto. In questo modo è possibile salvare il pacchetto in locale senza installarlo, quindi esaminarne il contenuto. Ricordarsi di eliminare il pacchetto salvato manualmente.

Alcuni di questi pacchetti sono creati da Microsoft, altri dalla community di PowerShell.
Microsoft consiglia di esaminare il contenuto e il codice dei pacchetti in questa raccolta prima dell'installazione.

Se si individua un pacchetto che si ritiene non essere stato pubblicato in buona fede, fare clic su **Report Abuse** (Segnala abusi) nella pagina del pacchetto.

### <a name="install"></a>Installare

Per installare un pacchetto dalla raccolta per usarlo, eseguire il cmdlet [Install-Module][] o [Install-Script][], a seconda del tipo di pacchetto.

[Install-Module][] installa il modulo in `$env:ProgramFiles\WindowsPowerShell\Modules` per impostazione predefinita.
È necessario un account Administrator. Se si aggiunge il parametro `-Scope CurrentUser` il modulo viene installato in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script][] installa lo script in `$env:ProgramFiles\WindowsPowerShell\Scripts` per impostazione predefinita.
È necessario un account Administrator. Se si aggiunge il parametro `-Scope CurrentUser` lo script viene installato in `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

Per impostazione predefinita, [Install-Module][] e [Install-Script][] installano la versione più recente di un pacchetto.
Per installare una versione precedente del pacchetto, aggiungere il parametro `-RequiredVersion`.

### <a name="deploy"></a>Distribuire

Per distribuire un pacchetto da PowerShell Gallery in Automazione di Azure, fare clic su **Deploy to Azure Automation** (Distribuisci in Automazione di Azure) nella pagina dei dettagli del pacchetto. Si verrà reindirizzati al portale di gestione di Azure, a cui si accede usando le credenziali del proprio account di Azure. Se si distribuiscono pacchetti con dipendenze, verranno distribuite tutte le dipendenze in Automazione di Azure. Il pulsante 'Deploy to Azure Automation' (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag **AzureAutomationNotSupported** ai metadati del pacchetto.

Per altre informazioni su Automazione di Azure, vedere la documentazione di [Automazione di Azure](/azure/automation).

## <a name="updating-packages-from-the-powershell-gallery"></a>Aggiornamento dei pacchetti da PowerShell Gallery

Per aggiornare i pacchetti installati da PowerShell Gallery eseguire il cmdlet [Update-Module][] o [Update-Script][]. Quando viene eseguito senza parametri aggiuntivi, [Update-Module][] prova ad aggiornare ogni modulo installato eseguendo [Install-Module][]. Per aggiornare i moduli in modo selettivo aggiungere il parametro `-Name`.

In modo analogo, anche [Update-Script][] eseguito senza parametri aggiuntivi prova ad aggiornare ogni script installato eseguendo [Install-Script][]. Per aggiornare gli script in modo selettivo aggiungere il parametro `-Name`.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Ottenere l'elenco dei pacchetti installati da PowerShell Gallery

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
