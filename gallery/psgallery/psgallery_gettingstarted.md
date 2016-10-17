# Introduzione a PowerShell Gallery

## Che cos'è PowerShell Gallery?

PowerShell Gallery è il repository centrale per i contenuti PowerShell.
Al suo interno è possibile trovare utili moduli di PowerShell che contengono comandi di PowerShell o risorse DSC (Desired State Configuration). Sono anche disponibili script di PowerShell, alcuni dei quali possono contenere flussi di lavoro di PowerShell e descrivono e stabiliscono la sequenza di un set di attività.
Alcuni di questi elementi vengono creati da Microsoft, altri dalla community di PowerShell.

## Requisiti

Per eseguire il download di elementi da PowerShell Gallery nel sistema, è necessario il modulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Il modulo PowerShellGet è disponibile nei prodotti indicati di seguito. Non è necessario eseguire l'accesso per scaricare elementi da PowerShell Gallery.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [Programma di installazione MSI (per PowerShell 3 e 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet richiede anche il [provider NuGet](http://go.microsoft.com/fwlink/?LinkId=722208) per funzionare con PowerShell Gallery. La prima volta che si usa PowerShellGet verrà richiesto automaticamente di installare il provider NuGet, se non si trova in uno dei percorsi seguenti:

-   $env:ProgramFiles\\PackageManagement\\ProviderAssemblies
-   $env:LOCALAPPDATA\\PackageManagement\\ProviderAssemblies

In alternativa, è possibile eseguire **Install-PackageProvider -Name NuGet -Force** per automatizzare il download e l'installazione del provider NuGet.

  
Se si ha una versione di NuGet precedente a 2.8.5.201, sarà necessario chiamare i cmdlet di PowerShell seguenti per eseguire l'installazione e passare alla versione più recente di NuGet.

1.  Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force
2.  Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force
3.  Eliminare la versione precedente di NuGet dal percorso di installazione precedente.

Per altre informazioni, vedere <http://oneget.org/>.

  
Nota: a causa delle variazioni di formato dei pacchetti, è consigliabile eseguire l'aggiornamento alla versione più recente di PowerShellGet e PackageManagement per installare gli elementi aggiornati di recente. PowerShellGet è incluso in Windows 10. Per altre informazioni, vedere [qui](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet fa anche parte di Windows Management Framework (WMF) 5.0, che è possibile scaricare [qui](http://go.microsoft.com/fwlink/?LinkId=398175).

## Individuazione di elementi da PowerShell Gallery

È possibile trovare elementi in PowerShell Gallery usando il controllo **Ricerca** in questo sito Web o sfogliando le pagine Moduli e Script. Per trovare elementi in PowerShell Gallery è possibile anche eseguire i cmdlet [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), a seconda dal tipo di elemento, con **-Repository PSGallery**.

Per filtrare i risultati dalla raccolta, è possibile usare i parametri seguenti di [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409):

- Name
- AllVersions
- MinimumVersion
- RequiredVersion
- Tag
- Includes
- DscResource
- RoleCapability
- Command
- Filter

Se si vogliono solo trovare risorse DSC specifiche nella raccolta, è possibile eseguire il cmdlet [**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) restituisce dati sulle risorse DSC contenute nella raccolta. Dato che le risorse DSC vengono sempre fornite come parte di un modulo, è comunque necessario eseguire [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) per installare tali risorse DSC.

## Informazioni sugli elementi in PowerShell Gallery

Dopo avere identificato un elemento di interesse, può essere utile ottenere altre informazioni che lo riguardano. A questo scopo, è possibile esaminare la pagina specifica dell'elemento nella raccolta. In quella pagina verranno indicati tutti i metadati caricati con l'elemento. I metadati per un elemento vengono forniti dall'autore dell'elemento e non sono verificati da Microsoft. Il proprietario dell'elemento è fortemente legato all'account della raccolta usato per pubblicare l'elemento ed è più affidabile rispetto al campo relativo all'autore.

Se si individua un elemento che si ritiene non essere stato pubblicato in buona fede, fare clic su **Report Abuse** (Segnala abusi) nella pagina dell'elemento.

Se si esegue [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), è possibile visualizzare questi dati nell'oggetto PSGetModuleInfo restituito. Ad esempio, l'esecuzione di [**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) restituisce dati sul modulo PSReadLine nella raccolta.

## Download di elementi da PowerShell Gallery

Per il download di elementi da PowerShell Gallery è consigliabile seguire il processo seguente:

### Controllare

Per scaricare un elemento dalla raccolta per ispezionarlo, eseguire il cmdlet [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), a seconda del tipo di elemento. In questo modo è possibile salvare l'elemento in locale senza installarlo, quindi ispezionarne il contenuto. L'elemento salvato dovrà poi essere eliminato manualmente.

Alcuni di questi elementi vengono creati da Microsoft, altri dalla community di PowerShell. Microsoft consiglia di esaminare il contenuto e il codice degli elementi in questa raccolta prima dell'installazione.

Se si individua un elemento che si ritiene non essere stato pubblicato in buona fede, fare clic su **Report Abuse** (Segnala abusi) nella pagina dell'elemento.

### Installare

Per installare un elemento dalla raccolta per usarlo, eseguire il cmdlet [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), a seconda del tipo di elemento.

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installa il modulo in $env:ProgramFiles\\WindowsPowerShell\\Modules per impostazione predefinita. È necessario un account Administrator. Se si aggiunge il parametro **-Scope CurrentUser**, il modulo viene installato in $env:USERPROFILE\\Documents\\WindowsPowerShell\\Modules.

[Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installa lo script in $env:ProgramFiles\\WindowsPowerShell\\Scripts per impostazione predefinita. È necessario un account Administrator. Se si aggiunge il parametro **-Scope CurrentUser**, lo script viene installato in $env:USERPROFILE\\Documents\\WindowsPowerShell\\Scripts.

Per impostazione predefinita, [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installano la versione più recente di un elemento. Per installare una versione precedente dell'elemento, aggiungere il parametro **-RequiredVersion**.

### Distribuire

Per distribuire un elemento da PowerShell Gallery in Automazione di Azure, fare clic su **Deploy to Azure Automation** (Distribuisci in Automazione di Azure) nella pagina dei dettagli dell'elemento. Si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure. Se si distribuiscono elementi con dipendenze, verranno distribuite tutte le dipendenze in Automazione di Azure. Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag **AzureAutomationNotSupported** ai metadati dell'elemento.

Per altre informazioni su Automazione di Azure, vedere il [sito Web di Automazione di Azure](http://azure.microsoft.com/en-us/services/automation/).

## Aggiornamento di elementi da PowerShell Gallery

Per aggiornare gli elementi installati da PowerShell Gallery, eseguire il cmdlet [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Quando viene eseguito senza parametri aggiuntivi, [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) prova ad aggiornare ogni modulo installato eseguendo [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
Per aggiornare i moduli in modo selettivo, aggiungere il parametro **-Name**.

Analogamente, anche [Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), quando viene eseguito senza parametri aggiuntivi, prova ad aggiornare ogni script installato eseguendo [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
Per aggiornare gli script in modo selettivo, aggiungere il parametro **-Name**.

## Ottenere l'elenco degli elementi installati da PowerShell Gallery

Per scoprire quali moduli sono stati installati da PowerShell Gallery, eseguire il cmdlet [**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Questo comando elenca tutti i moduli presenti nel sistema che sono stati installati direttamente da PowerShell Gallery.

Analogamente, per scoprire quali script sono stati installati da PowerShell Gallery, eseguire il cmdlet [**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Questo comando elenca tutti gli script presenti nel sistema che sono stati installati direttamente da PowerShell Gallery.


<!--HONumber=Aug16_HO3-->


