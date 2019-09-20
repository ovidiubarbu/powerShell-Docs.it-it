---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Cmdlet nuovi e aggiornati
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147591"
---
# <a name="new-and-updated-cmdlets"></a>Cmdlet nuovi e aggiornati

Sono stati aggiunti nuovi cmdlet e aggiornati alcuni cmdlet esistenti in base ai suggerimenti della community.

## <a name="archive-cmdlets"></a>Cmdlet Archive

Due nuovi cmdlet, `Compress-Archive` e `Expand-Archive`, consentono di comprimere ed espandere i file con estensione ZIP.

Per altre informazioni, vedere la documentazione relativa al modulo [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/).

## <a name="catalog-cmdlets"></a>Cmdlet di catalogo

Sono stati aggiunti due nuovi cmdlet nel modulo Microsoft.PowerShell.Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Questi cmdlet generano e convalidano i file di catalogo di Windows.

## <a name="clipboard-cmdlets"></a>Cmdlet Clipboard

`Get-Clipboard` e `Set-Clipboard` rendono più semplice il trasferimento del contenuto in e da una sessione di Windows PowerShell. I cmdlet Clipboard supportano immagini, file audio, elenchi di file e testo.

Per altre informazioni, vedere:

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdlet CMS (Cryptographic Message Syntax)

I cmdlet CMS (Cryptographic Message Syntax) supportano la crittografia e la decrittografia del contenuto con il formato standard IETF per la protezione crittografica dei messaggi, come documentato in [RFC5652](https://tools.ietf.org/html/rfc5652.html).

Lo standard di crittografia CMS implementa la crittografia a chiave pubblica, in cui la chiave usata per crittografare il contenuto (*chiave pubblica*) e la chiave usata per decrittografare il contenuto (*chiave privata*) sono separate.

La chiave pubblica può essere condivisa liberamente e non contiene dati sensibili. Qualsiasi contenuto crittografato con la chiave pubblica può essere decrittografato solo usando la chiave privata. Per altre informazioni, vedere: [Crittografia a chiave pubblica](https://en.wikipedia.org/wiki/Public-key_cryptography).

Per ulteriori informazioni, vedere:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

I certificati richiedono un identificatore univoco di utilizzo delle chiavi (EKU) per identificarli come certificati di crittografia dei dati in PowerShell, ad esempio identificatori per la firma del codice o per la posta crittografata. Per visualizzare i certificati di crittografia dei documenti nel provider di certificati, è possibile usare il parametro dinamico **DocumentEncryptionCert** di `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Estrarre e analizzare oggetti strutturati da contenuto di tipo stringa

### <a name="convertfrom-string"></a>ConvertFrom-String

Il nuovo cmdlet `ConvertFrom-String` supporta due modalità:

- Analisi delimitata di base
- Analisi basata su un esempio generato automaticamente

L'analisi delimitata divide l'input per impostazione predefinita in corrispondenza di spazi vuoti e assegna i nomi delle proprietà ai gruppi risultanti.

Il parametro **UpdateTemplate** salva i risultati dell'algoritmo di apprendimento in un commento nel file di modello. In questo modo il processo di apprendimento (la fase più lenta) diventa un costo una tantum. L'esecuzione di `ConvertFrom-String` con un modello che contiene l'algoritmo di apprendimento codificato è ora quasi istantanea.

Per altre informazioni, vedere [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` consente di fornire esempi di prima e dopo dell'aspetto desiderato per il testo. Il cmdlet formatta automaticamente il testo.

Per altre informazioni, vedere [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Aggiornamenti dell'oggetto FileInfo

Le informazioni sulla versione dei file possono essere fuorvianti, in particolare in seguito all'applicazione di patch ai file. In WMF 5.0 sono state aggiunte le nuove proprietà di script **FileVersionRaw** e **ProductVersionRaw** per gli oggetti **FileInfo**.
Ecco le proprietà come vengono visualizzate per powershell.exe (presupponendo che $pid è l'ID del processo di PowerShell):

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` consente di visualizzare dati di testo o binari in formato esadecimale.

Per altre informazioni, vedere [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Parametro -Depth per Get-ChildItem

`Get-ChildItem` include ora un parametro **Depth** utilizzabile con **Recurse** per limitare la ricorsione:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Supporto di moduli per la dichiarazione di intervalli di versione (1.* e così via)

È ora possibile combinare **MinimumVersion** e **MaximumVersion** per importare un modulo entro un intervallo specifico. I parametri supportano anche i caratteri jolly.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

Esistono molti scenari in cui è necessario un identificatore univoco. Il cmdlet `New-GUID` consente di creare un nuovo GUID in modo semplice.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>Parametro NoNewLine

Per `Out-File`, `Add-Content` e `Set-Content` è ora disponibile una nuova opzione **NoNewline** che omette una nuova riga dopo l'output. Ad esempio:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

Senza specificare **NoNewline**, ogni frammento sarebbe su una riga separata:

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Collegamenti simbolici con i cmdlet Item

I cmdlet Item e alcuni cmdlet correlati sono stati estesi per supportare i collegamenti simbolici.

### <a name="symbolic-link-files"></a>File di collegamenti simbolici

In questo esempio viene creato un nuovo file di collegamento simbolico denominato MySymLinkFile.txt in C:\Temp collegato a $pshome\profile.ps1. Tutti e tre gli esempi producono lo stesso risultato.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Directory di collegamenti simbolici

In questo esempio, viene creata una nuova directory di collegamento simbolico denominata MySymLinkDir in C:\Temp collegata alla cartella $pshome. Tutti e tre gli esempi producono lo stesso risultato.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Collegamenti reali

Le stesse combinazioni di **Path** e **Name** consentite come descritto in precedenza.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Giunzioni di directory

Le stesse combinazioni di **Path** e **Name** consentite come descritto in precedenza.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` visualizza ora una 'l' nella proprietà **Mode** per indicare un file o una directory di collegamento simbolico.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove-Item

La rimozione dei collegamenti simbolici funziona come la rimozione di qualsiasi altro tipo di elemento.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Usare il parametro **Force** per rimuovere i file nella directory di destinazione e il collegamento simbolico.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

A volte, negli script è necessario creare un file temporaneo. È ora possibile eseguire questa operazione con il cmdlet `New-TemporaryFile`:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Gestione del commutatore di rete con PowerShell

I cmdlet per il commutatore di rete, introdotti in WMF 5.0, consentono di applicare la configurazione di commutatore, LAN virtuale (VLAN) e porte del commutatore di rete di livello 2 di base ai commutatori di rete con certificazione per il logo di Windows Server 2012 R2. Usando questi cmdlet è possibile eseguire:

- Configurazioni globali del commutatore, ad esempio:
  - Impostare il nome host
  - Impostare il banner del commutatore
  - Rendere persistente la configurazione
  - Abilitare o disabilitare funzionalità

- Configurazione della VLAN:
  - Creare o rimuovere VLAN
  - Abilitare o disabilitare VLAN
  - Enumerare VLAN
  - Impostare un nome descrittivo per una VLAN

- Configurazione delle porte di livello 2:
  - Enumerare le porte
  - Abilitare o disabilitare le porte
  - Impostare modalità e proprietà per le porte
  - Aggiungere o associare la modalità trunk o di accesso per la VLAN sulla porta

Per altre informazioni, vedere la documentazione relativa a [NetworkSwitchManager](/powershell/module/networkswitchmanager/).

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Generare cmdlet di PowerShell in base a un endpoint OData con ODataUtils

Il modulo ODataUtils consente la generazione di cmdlet di PowerShell da endpoint REST che supportano OData. Il modulo Microsoft.PowerShell.ODataUtils include le funzionalità seguenti:

- Informazioni aggiuntive del canale dall'endpoint sul lato server al lato client.
- Supporto del paging sul lato client
- Filtro sul lato server tramite il parametro -Select
- Supporto delle intestazioni di richieste Web

I cmdlet proxy generati dal cmdlet `Export-ODataEndPointProxy` forniscono informazioni aggiuntive dall'endpoint OData sul lato server sul flusso di **informazioni**.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

Nell'esempio seguente viene recuperato il prodotto principale e l'output viene acquisito nella variabile `$infoStream`.

Specificando il parametro **IncludeTotalResponseCount** si ottiene il numero totale di tutti i record **Product** disponibili nel server.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

È possibile ottenere i record dal server in batch usando il supporto del paging sul lato client. Ciò è utile quando è necessario ottenere una grande quantità di dati dal server tramite la rete.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

I cmdlet proxy generati supportano il parametro **Select** che viene usato come filtro per ricevere solo le proprietà dei record necessarie per il client. Il filtro viene applicato nel server e in questo modo si riduce la quantità di dati trasferiti in rete.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Il cmdlet `Export-ODataEndpointProxy` e i cmdlet proxy generati da questo supportano ora il parametro **Headers**. L'intestazione può essere usata per incanalare le informazioni aggiuntive previste dall'endpoint OData.

Nell'esempio seguente, per il parametro **Headers** viene specificata una tabella hash che contiene una chiave di sottoscrizione. Questo è un esempio tipico per i servizi che prevedono una chiave di sottoscrizione per l'autenticazione.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
