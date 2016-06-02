---
title:  Installazione di Windows PowerShell SDK
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  c3636b45-61aa-4720-85f0-58312c4fc8f9
---

# Installazione di Windows PowerShell SDK
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>L'argomento seguente descrive come installare PowerShell SDK in diverse versioni di Windows.</para>
  </introduction>
  <section>
    <title>Installazione di Windows PowerShell 3.0 SDK per Windows 8 e Windows Server 2012</title>
    <content>
      <para>Windows PowerShell 3.0 viene automaticamente installato con Windows 8 e Windows Server 2012. È inoltre possibile scaricare e installare gli assembly di riferimento per Windows PowerShell 3.0 come parte di Windows 8 SDK. Questi assembly permettono di scrivere cmdlet, provider e programmi host per Windows PowerShell 3.0. Quando si installa Windows SDK per Windows 8, gli assembly di Windows PowerShell vengono automaticamente installati nella cartella degli assembly di riferimento, in \Programmi (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Per altre informazioni, vedere il <externalLink><linkText>sito di download di Windows 8 SDK</linkText><linkUri>http://msdn.microsoft.com/windows/hardware/hh852363.aspx</linkUri></externalLink>. Alcuni esempi di codice di Windows PowerShell sono disponibili anche in Dev Center. Per altre informazioni, vedere la pagina degli esempi di codice per sistemi desktop nel <externalLink><linkText>sito Dev Center</linkText><linkUri>http://code.msdn.microsoft.com/windowsdesktop/</linkUri></externalLink>. </para>
      <para>Inoltre, Windows PowerShell 3.0 è compatibile con la versione precedente, Windows PowerShell 2.0 SDK, che include diversi esempi di codice. Per altre informazioni su come scaricare Windows PowerShell 2.0 SDK, vedere di seguito. Nota: benché gli esempi di codice della versione 2.0 siano compatibili con Windows 8 e Windows PowerShell 3.0, non è possibile installare Windows PowerShell 2.0 in una piattaforma Windows 8. </para>
    </content>
  </section>
  <section>
    <title>Installazione di Windows PowerShell 3.0 SDK per Windows 7 e Windows Server 2008 R2</title>
    <content>
      <para>Windows PowerShell 2.0 viene installato automaticamente in Windows 7 e Windows Server 2008 R2. In questi sistemi, inoltre, è possibile installare PowerShell 3.0. Per altre informazioni, vedere <link xlink:href="6fbb0409-5a54-48ec-95e6-7f8b7d8c4969">Installazione di Windows PowerShell</link>. Come descritto sopra, è possibile installare anche Windows 8 SDK in Windows 7 e Windows Server 2008 R2.</para>
    </content>
  </section>
  <section>
    <title>Installazione di Windows PowerShell 2.0 SDK per Windows 7, Windows Vista, Windows XP, Windows Server 2003 e Windows Server 2008</title>
    <content>
      <para><token>mshshort</token> 2.0 SDK fornisce gli assembly di riferimento necessari per scrivere cmdlet, provider e applicazioni di hosting, nonché il codice di esempio C# che può essere usato come punto di partenza quando si inizia a scrivere il codice. </para>
      <para>Per installare l'SDK, vedere <externalLink><linkText>Windows PowerShell 2.0 SDK</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=184611</linkUri></externalLink>.</para>
    </content>
    <sections>
      <section>
        <title>Assembly di riferimento</title>
        <content>
          <para>Per impostazione predefinita, gli assembly di riferimento vengono installati nel percorso seguente: <codeInline>c:\Programmi\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0</codeInline>.</para>
          <alert class="note">
            <para>Il codice compilato per gli assembly di Windows PowerShell 2.0 non può essere caricato nelle installazioni di Windows PowerShell 1.0. Al contrario, il codice compilato per gli assembly di Windows PowerShell 1.0 può essere caricato nelle installazioni di Windows PowerShell 2.0.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Esempi</title>
        <content>
          <para>Per impostazione predefinita, gli esempi di codice vengono installati nel percorso seguente: <codeInline>C:\Programmi\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\</codeInline>.</para>
          <para>Le sezioni seguenti contengono una breve descrizione di ogni esempio.</para>
        </content>
        <sections>
          <section>
            <title>Esempi per cmdlet</title>
            <content>
              <definitionTable>
                <definedTerm>GetProcessSample01</definedTerm>
                <definition>
                  <para>Mostra come scrivere un semplice cmdlet che ottiene tutti i processi nel computer locale.</para>
                </definition>
                <definedTerm>GetProcessSample02</definedTerm>
                <definition>
                  <para>Mostra come aggiungere parametri al cmdlet. Il cmdlet accetta uno o più nomi di processo e restituisce i processi corrispondenti.</para>
                </definition>
                <definedTerm>GetProcessSample03</definedTerm>
                <definition>
                  <para>Mostra come aggiungere parametri che accettano input dalla pipeline.</para>
                </definition>
                <definedTerm>GetProcessSample04</definedTerm>
                <definition>
                  <para>Mostra come gestire errori non fatali.</para>
                </definition>
                <definedTerm>GetProcessSample05</definedTerm>
                <definition>
                  <para>Mostra come visualizzare un elenco di processi specificati.</para>
                </definition>
                <definedTerm>SelectObject</definedTerm>
                <definition>
                  <para>Mostra come scrivere un filtro per selezionare solo determinati oggetti. </para>
                </definition>
                <definedTerm>SelectString</definedTerm>
                <definition>
                  <para>Mostra come cercare file per modelli specificati.</para>
                </definition>
                <definedTerm>StopProcessSample01</definedTerm>
                <definition>
                  <para>Mostra come implementare un parametro <parameterReference>PassThru</parameterReference> e come richiedere i commenti degli utenti tramite chiamate ai metodi <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldProcess</codeEntityReference> e <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldContinue</codeEntityReference>. Gli utenti specificano il parametro <parameterReference>PassThru</parameterReference> quando vogliono forzare il cmdlet perché restituisca un oggetto. </para>
                </definition>
                <definedTerm>StopProcessSample02</definedTerm>
                <definition>
                  <para>Mostra come arrestare un processo specifico.</para>
                </definition>
                <definedTerm>StopProcessSample03</definedTerm>
                <definition>
                  <para>Mostra come dichiarare alias per i parametri e come supportare i caratteri jolly.</para>
                </definition>
                <definedTerm>StopProcessSample04</definedTerm>
                <definition>
                  <para>Mostra come dichiarare set di parametri e l'oggetto accettato dal cmdlet come input e come specificare il set di parametri predefinito da usare.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Esempi per l'esecuzione remota</title>
            <content>
              <definitionTable>
                <definedTerm>RemoteRunspace01</definedTerm>
                <definition>
                  <para>Mostra come creare uno spazio di esecuzione remoto usato per stabilire una connessione remota.</para>
                </definition>
                <definedTerm>RemoteRunspacePool01</definedTerm>
                <definition>
                  <para>Mostra come creare un pool di spazi di esecuzione remoti ed eseguire più comandi simultaneamente usando questo pool.</para>
                </definition>
                <definedTerm>Serialization01</definedTerm>
                <definition>
                  <para>Mostra come esaminare una classe .NET esistente e assicurarsi che le informazioni ottenute dalle proprietà pubbliche selezionate di questa classe vengano mantenute durante la serializzazione/deserializzazione.</para>
                </definition>
                <definedTerm>Serialization02</definedTerm>
                <definition>
                  <para>Mostra come esaminare una classe .NET esistente e assicurarsi che le informazioni ottenute dall'istanza di questa classe vengano mantenute durante la serializzazione/deserializzazione quando le informazioni non sono disponibili nelle proprietà pubbliche della classe.</para>
                </definition>
                <definedTerm>Serialization03</definedTerm>
                <definition>
                  <para>Mostra come esaminare una classe .NET esistente e assicurarsi che le istanze di questa classe e delle classi derivate vengano deserializzate (riattivate) in oggetti .NET attivi.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Esempi per eventi</title>
            <content>
              <definitionTable>
                <definedTerm>Event01</definedTerm>
                <definition>
                  <para>Mostra come creare un cmdlet per la registrazione eventi mediante la derivazione da ObjectEventRegistrationBase.</para>
                </definition>
                <definedTerm>Event02</definedTerm>
                <definition>
                  <para>Mostra come ricevere notifiche di eventi di <token>mshshort</token> generati in computer remoti. Usa l'evento PSEventReceived esposto tramite la classe <codeEntityReference>T:System.Management.Automation.Runspaces.Runspace</codeEntityReference>.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Esempi per applicazioni di hosting</title>
            <content>
              <definitionTable>
                <definedTerm>Runspace01</definedTerm>
                <definition>
                  <para>Mostra come usare la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> per eseguire il cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> in modo sincrono. Il cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> restituisce oggetti <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> per ogni processo in esecuzione nel computer locale.</para>
                </definition>
                <definedTerm>Runspace02</definedTerm>
                <definition>
                  <para>Mostra come usare la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> per eseguire i cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> e <externalLink><linkText>Sort-Object</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=113403</linkUri></externalLink> in modo sincrono. Il cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> restituisce oggetti <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> per ogni processo in esecuzione nel computer locale e Sort-Object ordina gli oggetti in base alla rispettiva proprietà <codeEntityReference>P:System.Diagnostics.Process.Id</codeEntityReference>. I risultati di questi comandi vengono visualizzati usando un controllo <codeEntityReference>T:System.Windows.Forms.DataGridView</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace03</definedTerm>
                <definition>
                  <para>Mostra come usare la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> per eseguire uno script in modo sincrono e come gestire errori non fatali. Lo script riceve un elenco di nomi di processo e quindi recupera tali processi. I risultati dello script, inclusi tutti gli errori non fatali generali durante la sua esecuzione, vengono visualizzati in una finestra della console.</para>
                </definition>
                <definedTerm>Runspace04</definedTerm>
                <definition>
                  <para>Mostra come usare la classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> per eseguire comandi e come intercettare gli errori fatali generati durante la loro esecuzione. Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido. Di conseguenza, non viene restituito alcun oggetto e viene generato un errore fatale.</para>
                </definition>
                <definedTerm>Runspace05</definedTerm>
                <definition>
                  <para>Mostra come aggiungere uno snap-in a un oggetto <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> in modo che il cmdlet dello snap-in sia disponibile quando viene aperto lo spazio di esecuzione. Lo snap-in fornisce un cmdlet Get-Proc (definito dall'<legacyLink xlink:href="7b48bf80-cbf0-4cb1-8d5b-3b8d06196598">esempio GetProcessSample01</legacyLink>) che viene eseguito in modo sincrono usando un oggetto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace06</definedTerm>
                <definition>
                  <para>Mostra come aggiungere un modulo a un oggetto <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> in modo che il modulo venga caricato all'apertura dello spazio di esecuzione. Il modulo fornisce un cmdlet Get-Proc (definito dall'<legacyLink xlink:href="481f557d-3344-4d33-b2da-4736a0165181">esempio GetProcessSample02</legacyLink>) eseguito in modo sincrono usando un oggetto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace07</definedTerm>
                <definition>
                  <para>Mostra come creare uno spazio di esecuzione e quindi usarlo per eseguire due cmdlet in modo sincrono usando un oggetto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace08</definedTerm>
                <definition>
                  <para>Mostra come aggiungere comandi e argomenti alla pipeline di un oggetto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> e come eseguire i comandi in modo sincrono.</para>
                </definition>
                <definedTerm>Runspace09</definedTerm>
                <definition>
                  <para>Mostra come aggiungere uno script alla pipeline di un oggetto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> e come eseguire lo script in modo asincrono. Vengono usati eventi per gestire l'output dello script.</para>
                </definition>
                <definedTerm>Runspace10</definedTerm>
                <definition>
                  <para>Mostra come creare uno stato sessione iniziale predefinito, come aggiungere un cmdlet a <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>, come creare uno spazio di esecuzione che usa lo stato sessione iniziale e come eseguire il comando usando un oggetto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace11</definedTerm>
                <definition>
                  <para>Mostra come usare la classe <codeEntityReference>T:System.Management.Automation.ProxyCommand</codeEntityReference> per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili. Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato. Questo significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.</para>
                </definition>
                <definedTerm>PowerShell01</definedTerm>
                <definition>
                  <para>Mostra come creare uno spazio di esecuzione vincolato usando un oggetto <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>.</para>
                </definition>
                <definedTerm>PowerShell02</definedTerm>
                <definition>
                  <para>Mostra come usare un pool di spazi di esecuzione per eseguire più comandi simultaneamente.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Esempi per host</title>
            <content>
              <definitionTable>
                <definedTerm>Host01</definedTerm>
                <definition>
                  <para>Mostra come implementare un'applicazione host che usa un host personalizzato. In questo esempio viene creato uno spazio di esecuzione che usa l'host personalizzato e quindi viene usata l'API <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> per eseguire uno script che chiama "exit". L'applicazione host esamina l'output dello script e stampa i risultati.</para>
                </definition>
                <definedTerm>Host02</definedTerm>
                <definition>
                  <para>Mostra come scrivere un'applicazione host che usa il runtime di <token>mshshort</token> insieme a un'implementazione host personalizzata. L'applicazione host imposta le impostazioni cultura dell'host su Tedesco, esegue il cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> e visualizza i risultati allo stesso modo di quando si usa pwrsh.exe e quindi stampa la data e l'ora correnti in tedesco.</para>
                </definition>
                <definedTerm>Host03</definedTerm>
                <definition>
                  <para>Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati alla console.</para>
                </definition>
                <definedTerm>Host04</definedTerm>
                <definition>
                  <para>Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati alla console. Questa applicazione host supporta anche la visualizzazione di prompt che permettono all'utente di specificare scelte multiple.</para>
                </definition>
                <definedTerm>Host05</definedTerm>
                <definition>
                  <para>Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati alla console. Questa applicazione host supporta anche le chiamate a computer remoti tramite i cmdlet <externalLink><linkText>Enter-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135210</linkUri></externalLink> e <externalLink><linkText>Exit-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135212</linkUri></externalLink>.</para>
                </definition>
                <definedTerm>Host06</definedTerm>
                <definition>
                  <para>Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati alla console. Questo esempio usa inoltre le API del tokenizer per specificare il colore del testo immesso dall'utente.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Esempi per provider</title>
            <content>
              <definitionTable>
                <definedTerm>AccessDBProviderSample01</definedTerm>
                <definition>
                  <para>Mostra come dichiarare una classe provider che deriva direttamente dalla classe <codeEntityReference>T:System.Management.Automation.Provider.CmdletProvider</codeEntityReference>. Questo esempio è incluso qui solo per completezza.</para>
                </definition>
                <definedTerm>AccessDBProviderSample02</definedTerm>
                <definition>
                  <para>Mostra come sovrascrivere i metodi <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.NewDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> e <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> per supportare le chiamate ai cmdlet New-PSDrive e Remove-PSDrive. La classe provider in questo esempio deriva dalla classe <codeEntityReference>T:System.Management.Automation.Provider.DriveCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample03</definedTerm>
                <definition>
                  <para>Mostra come sovrascrivere i metodi <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.GetItem(System.String)</codeEntityReference> e <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.SetItem(System.String,System.Object)</codeEntityReference> per supportare le chiamate ai cmdlet Get-Item e Set-Item. La classe provider in questo esempio deriva dalla classe <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample04</definedTerm>
                <definition>
                  <para>Mostra come sovrascrivere metodi contenitore per supportare le chiamate ai cmdlet Copy-Item, Get-ChildItem, New-Item e Remove-Item. Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. La classe provider in questo esempio deriva dalla classe <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample05</definedTerm>
                <definition>
                  <para>Mostra come sovrascrivere metodi contenitore per supportare le chiamate ai cmdlet Move-Item e Join-Path. Questi metodi devono essere implementati quando l'utente deve spostare elementi all'interno di un contenitore e se l'archivio dati contiene contenitori annidati. La classe provider in questo esempio deriva dalla classe <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample06</definedTerm>
                <definition>
                  <para>Mostra come sovrascrivere i metodi contenitore per supportare le chiamate ai cmdlet Clear-Content, Get-Content e Set-Content. Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati. La classe provider in questo esempio deriva dalla classe <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> e implementa l'interfaccia <codeEntityReference>T:System.Management.Automation.Provider.IContentCmdletProvider</codeEntityReference>.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>



<!--HONumber=May16_HO4-->


