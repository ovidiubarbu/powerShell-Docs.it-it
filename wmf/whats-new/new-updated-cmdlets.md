---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Cmdlet nuovi e aggiornati
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298661"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="f05b9-103">Cmdlet nuovi e aggiornati</span><span class="sxs-lookup"><span data-stu-id="f05b9-103">New and updated cmdlets</span></span>

<span data-ttu-id="f05b9-104">Sono stati aggiunti nuovi cmdlet e aggiornati alcuni cmdlet esistenti in base ai suggerimenti della community.</span><span class="sxs-lookup"><span data-stu-id="f05b9-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="f05b9-105">Cmdlet Archive</span><span class="sxs-lookup"><span data-stu-id="f05b9-105">Archive cmdlets</span></span>

<span data-ttu-id="f05b9-106">Due nuovi cmdlet, `Compress-Archive` e `Expand-Archive`, consentono di comprimere ed espandere i file con estensione ZIP.</span><span class="sxs-lookup"><span data-stu-id="f05b9-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="f05b9-107">Per altre informazioni, vedere la documentazione relativa al modulo [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/).</span><span class="sxs-lookup"><span data-stu-id="f05b9-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="f05b9-108">Cmdlet di catalogo</span><span class="sxs-lookup"><span data-stu-id="f05b9-108">Catalog Cmdlets</span></span>

<span data-ttu-id="f05b9-109">Sono stati aggiunti due nuovi cmdlet nel modulo Microsoft.PowerShell.Security.</span><span class="sxs-lookup"><span data-stu-id="f05b9-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="f05b9-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="f05b9-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="f05b9-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="f05b9-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="f05b9-112">Questi cmdlet generano e convalidano i file di catalogo di Windows.</span><span class="sxs-lookup"><span data-stu-id="f05b9-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="f05b9-113">Cmdlet Clipboard</span><span class="sxs-lookup"><span data-stu-id="f05b9-113">Clipboard cmdlets</span></span>

<span data-ttu-id="f05b9-114">`Get-Clipboard` e `Set-Clipboard` rendono più semplice il trasferimento del contenuto in e da una sessione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f05b9-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="f05b9-115">I cmdlet Clipboard supportano immagini, file audio, elenchi di file e testo.</span><span class="sxs-lookup"><span data-stu-id="f05b9-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="f05b9-116">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="f05b9-116">For more information, see:</span></span>

- [<span data-ttu-id="f05b9-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f05b9-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="f05b9-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f05b9-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="f05b9-119">Cmdlet CMS (Cryptographic Message Syntax)</span><span class="sxs-lookup"><span data-stu-id="f05b9-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="f05b9-120">I cmdlet CMS (Cryptographic Message Syntax) supportano la crittografia e la decrittografia del contenuto con il formato standard IETF per la protezione crittografica dei messaggi, come documentato in [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="f05b9-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="f05b9-121">Lo standard di crittografia CMS implementa la crittografia a chiave pubblica, in cui la chiave usata per crittografare il contenuto (*chiave pubblica*) e la chiave usata per decrittografare il contenuto (*chiave privata*) sono separate.</span><span class="sxs-lookup"><span data-stu-id="f05b9-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="f05b9-122">La chiave pubblica può essere condivisa liberamente e non contiene dati sensibili.</span><span class="sxs-lookup"><span data-stu-id="f05b9-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="f05b9-123">Qualsiasi contenuto crittografato con la chiave pubblica può essere decrittografato solo usando la chiave privata.</span><span class="sxs-lookup"><span data-stu-id="f05b9-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="f05b9-124">Per altre informazioni, vedere: [Crittografia a chiave pubblica](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="f05b9-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="f05b9-125">Per ulteriori informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="f05b9-125">For more information see:</span></span>

- [<span data-ttu-id="f05b9-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="f05b9-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="f05b9-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="f05b9-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="f05b9-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="f05b9-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="f05b9-129">I certificati richiedono un identificatore univoco di utilizzo delle chiavi (EKU) per identificarli come certificati di crittografia dei dati in PowerShell, ad esempio identificatori per la firma del codice o per la posta crittografata.</span><span class="sxs-lookup"><span data-stu-id="f05b9-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="f05b9-130">Per visualizzare i certificati di crittografia dei documenti nel provider di certificati, è possibile usare il parametro dinamico **DocumentEncryptionCert** di `Get-ChildItem`:</span><span class="sxs-lookup"><span data-stu-id="f05b9-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="f05b9-131">Estrarre e analizzare oggetti strutturati da contenuto di tipo stringa</span><span class="sxs-lookup"><span data-stu-id="f05b9-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="f05b9-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="f05b9-132">ConvertFrom-String</span></span>

<span data-ttu-id="f05b9-133">Il nuovo cmdlet `ConvertFrom-String` supporta due modalità:</span><span class="sxs-lookup"><span data-stu-id="f05b9-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="f05b9-134">Analisi delimitata di base</span><span class="sxs-lookup"><span data-stu-id="f05b9-134">Basic delimited parsing</span></span>
- <span data-ttu-id="f05b9-135">Analisi basata su un esempio generato automaticamente</span><span class="sxs-lookup"><span data-stu-id="f05b9-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="f05b9-136">L'analisi delimitata divide l'input per impostazione predefinita in corrispondenza di spazi vuoti e assegna i nomi delle proprietà ai gruppi risultanti.</span><span class="sxs-lookup"><span data-stu-id="f05b9-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="f05b9-137">Il parametro **UpdateTemplate** salva i risultati dell'algoritmo di apprendimento in un commento nel file di modello.</span><span class="sxs-lookup"><span data-stu-id="f05b9-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="f05b9-138">In questo modo il processo di apprendimento (la fase più lenta) diventa un costo una tantum.</span><span class="sxs-lookup"><span data-stu-id="f05b9-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="f05b9-139">L'esecuzione di `ConvertFrom-String` con un modello che contiene l'algoritmo di apprendimento codificato è ora quasi istantanea.</span><span class="sxs-lookup"><span data-stu-id="f05b9-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="f05b9-140">Per altre informazioni, vedere [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="f05b9-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="f05b9-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="f05b9-141">Convert-String</span></span>

<span data-ttu-id="f05b9-142">`Convert-String` consente di fornire esempi di prima e dopo dell'aspetto desiderato per il testo.</span><span class="sxs-lookup"><span data-stu-id="f05b9-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="f05b9-143">Il cmdlet formatta automaticamente il testo.</span><span class="sxs-lookup"><span data-stu-id="f05b9-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="f05b9-144">Per altre informazioni, vedere [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="f05b9-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="f05b9-145">Aggiornamenti dell'oggetto FileInfo</span><span class="sxs-lookup"><span data-stu-id="f05b9-145">Updates to FileInfo object</span></span>

<span data-ttu-id="f05b9-146">Le informazioni sulla versione dei file possono essere fuorvianti, in particolare in seguito all'applicazione di patch ai file.</span><span class="sxs-lookup"><span data-stu-id="f05b9-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="f05b9-147">In WMF 5.0 sono state aggiunte le nuove proprietà di script **FileVersionRaw** e **ProductVersionRaw** per gli oggetti **FileInfo**.</span><span class="sxs-lookup"><span data-stu-id="f05b9-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="f05b9-148">Ecco le proprietà come vengono visualizzate per powershell.exe (presupponendo che $pid è l'ID del processo di PowerShell):</span><span class="sxs-lookup"><span data-stu-id="f05b9-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="f05b9-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="f05b9-149">Format-Hex</span></span>

<span data-ttu-id="f05b9-150">`Format-Hex` consente di visualizzare dati di testo o binari in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="f05b9-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="f05b9-151">Per altre informazioni, vedere [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="f05b9-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="f05b9-152">Parametro -Depth per Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f05b9-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="f05b9-153">`Get-ChildItem` include ora un parametro **Depth** utilizzabile con **Recurse** per limitare la ricorsione:</span><span class="sxs-lookup"><span data-stu-id="f05b9-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="f05b9-154">Supporto di moduli per la dichiarazione di intervalli di versione (1.\* e così via)</span><span class="sxs-lookup"><span data-stu-id="f05b9-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="f05b9-155">È ora possibile combinare **MinimumVersion** e **MaximumVersion** per importare un modulo entro un intervallo specifico.</span><span class="sxs-lookup"><span data-stu-id="f05b9-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="f05b9-156">I parametri supportano anche i caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="f05b9-156">The parameters also support wildcards.</span></span>

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

## <a name="new-guid"></a><span data-ttu-id="f05b9-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="f05b9-157">New-Guid</span></span>

<span data-ttu-id="f05b9-158">Esistono molti scenari in cui è necessario un identificatore univoco.</span><span class="sxs-lookup"><span data-stu-id="f05b9-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="f05b9-159">Il cmdlet `New-GUID` consente di creare un nuovo GUID in modo semplice.</span><span class="sxs-lookup"><span data-stu-id="f05b9-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="f05b9-160">Parametro NoNewLine</span><span class="sxs-lookup"><span data-stu-id="f05b9-160">NoNewLine parameter</span></span>

<span data-ttu-id="f05b9-161">Per `Out-File`, `Add-Content` e `Set-Content` è ora disponibile una nuova opzione **NoNewline** che omette una nuova riga dopo l'output.</span><span class="sxs-lookup"><span data-stu-id="f05b9-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="f05b9-162">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f05b9-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="f05b9-163">Senza specificare **NoNewline**, ogni frammento sarebbe su una riga separata:</span><span class="sxs-lookup"><span data-stu-id="f05b9-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="f05b9-164">Collegamenti simbolici con i cmdlet Item</span><span class="sxs-lookup"><span data-stu-id="f05b9-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="f05b9-165">I cmdlet Item e alcuni cmdlet correlati sono stati estesi per supportare i collegamenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="f05b9-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="f05b9-166">File di collegamenti simbolici</span><span class="sxs-lookup"><span data-stu-id="f05b9-166">Symbolic link files</span></span>

<span data-ttu-id="f05b9-167">In questo esempio viene creato un nuovo file di collegamento simbolico denominato MySymLinkFile.txt in C:\Temp collegato a $pshome\profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="f05b9-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="f05b9-168">Tutti e tre gli esempi producono lo stesso risultato.</span><span class="sxs-lookup"><span data-stu-id="f05b9-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="f05b9-169">Directory di collegamenti simbolici</span><span class="sxs-lookup"><span data-stu-id="f05b9-169">Symbolic link directories</span></span>

<span data-ttu-id="f05b9-170">In questo esempio, viene creata una nuova directory di collegamento simbolico denominata MySymLinkDir in C:\Temp collegata alla cartella $pshome.</span><span class="sxs-lookup"><span data-stu-id="f05b9-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="f05b9-171">Tutti e tre gli esempi producono lo stesso risultato.</span><span class="sxs-lookup"><span data-stu-id="f05b9-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="f05b9-172">Collegamenti reali</span><span class="sxs-lookup"><span data-stu-id="f05b9-172">Hard links</span></span>

<span data-ttu-id="f05b9-173">Le stesse combinazioni di **Path** e **Name** consentite come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f05b9-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="f05b9-174">Giunzioni di directory</span><span class="sxs-lookup"><span data-stu-id="f05b9-174">Directory junctions</span></span>

<span data-ttu-id="f05b9-175">Le stesse combinazioni di **Path** e **Name** consentite come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f05b9-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="f05b9-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f05b9-176">Get-ChildItem</span></span>

<span data-ttu-id="f05b9-177">`Get-ChildItem` visualizza ora una 'l' nella proprietà **Mode** per indicare un file o una directory di collegamento simbolico.</span><span class="sxs-lookup"><span data-stu-id="f05b9-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

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

### <a name="remove-item"></a><span data-ttu-id="f05b9-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="f05b9-178">Remove-Item</span></span>

<span data-ttu-id="f05b9-179">La rimozione dei collegamenti simbolici funziona come la rimozione di qualsiasi altro tipo di elemento.</span><span class="sxs-lookup"><span data-stu-id="f05b9-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="f05b9-180">Usare il parametro **Force** per rimuovere i file nella directory di destinazione e il collegamento simbolico.</span><span class="sxs-lookup"><span data-stu-id="f05b9-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="f05b9-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="f05b9-181">New-TemporaryFile</span></span>

<span data-ttu-id="f05b9-182">A volte, negli script è necessario creare un file temporaneo.</span><span class="sxs-lookup"><span data-stu-id="f05b9-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="f05b9-183">È ora possibile eseguire questa operazione con il cmdlet `New-TemporaryFile`:</span><span class="sxs-lookup"><span data-stu-id="f05b9-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="f05b9-184">Gestione del commutatore di rete con PowerShell</span><span class="sxs-lookup"><span data-stu-id="f05b9-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="f05b9-185">I cmdlet per il commutatore di rete, introdotti in WMF 5.0, consentono di applicare la configurazione di commutatore, LAN virtuale (VLAN) e porte del commutatore di rete di livello 2 di base ai commutatori di rete con certificazione per il logo di Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="f05b9-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="f05b9-186">Usando questi cmdlet è possibile eseguire:</span><span class="sxs-lookup"><span data-stu-id="f05b9-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="f05b9-187">Configurazioni globali del commutatore, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f05b9-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="f05b9-188">Impostare il nome host</span><span class="sxs-lookup"><span data-stu-id="f05b9-188">Set host name</span></span>
  - <span data-ttu-id="f05b9-189">Impostare il banner del commutatore</span><span class="sxs-lookup"><span data-stu-id="f05b9-189">Set switch banner</span></span>
  - <span data-ttu-id="f05b9-190">Rendere persistente la configurazione</span><span class="sxs-lookup"><span data-stu-id="f05b9-190">Persist configuration</span></span>
  - <span data-ttu-id="f05b9-191">Abilitare o disabilitare funzionalità</span><span class="sxs-lookup"><span data-stu-id="f05b9-191">Enable or disable feature</span></span>

- <span data-ttu-id="f05b9-192">Configurazione della VLAN:</span><span class="sxs-lookup"><span data-stu-id="f05b9-192">VLAN configuration:</span></span>
  - <span data-ttu-id="f05b9-193">Creare o rimuovere VLAN</span><span class="sxs-lookup"><span data-stu-id="f05b9-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="f05b9-194">Abilitare o disabilitare VLAN</span><span class="sxs-lookup"><span data-stu-id="f05b9-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="f05b9-195">Enumerare VLAN</span><span class="sxs-lookup"><span data-stu-id="f05b9-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="f05b9-196">Impostare un nome descrittivo per una VLAN</span><span class="sxs-lookup"><span data-stu-id="f05b9-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="f05b9-197">Configurazione delle porte di livello 2:</span><span class="sxs-lookup"><span data-stu-id="f05b9-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="f05b9-198">Enumerare le porte</span><span class="sxs-lookup"><span data-stu-id="f05b9-198">Enumerate ports</span></span>
  - <span data-ttu-id="f05b9-199">Abilitare o disabilitare le porte</span><span class="sxs-lookup"><span data-stu-id="f05b9-199">Enable or disable ports</span></span>
  - <span data-ttu-id="f05b9-200">Impostare modalità e proprietà per le porte</span><span class="sxs-lookup"><span data-stu-id="f05b9-200">Set port modes and properties</span></span>
  - <span data-ttu-id="f05b9-201">Aggiungere o associare la modalità trunk o di accesso per la VLAN sulla porta</span><span class="sxs-lookup"><span data-stu-id="f05b9-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="f05b9-202">Per altre informazioni, vedere la documentazione relativa a [NetworkSwitchManager](/powershell/module/networkswitchmanager/).</span><span class="sxs-lookup"><span data-stu-id="f05b9-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="f05b9-203">Generare cmdlet di PowerShell in base a un endpoint OData con ODataUtils</span><span class="sxs-lookup"><span data-stu-id="f05b9-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="f05b9-204">Il modulo ODataUtils consente la generazione di cmdlet di PowerShell da endpoint REST che supportano OData.</span><span class="sxs-lookup"><span data-stu-id="f05b9-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="f05b9-205">Il modulo Microsoft.PowerShell.ODataUtils include le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="f05b9-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="f05b9-206">Informazioni aggiuntive del canale dall'endpoint sul lato server al lato client.</span><span class="sxs-lookup"><span data-stu-id="f05b9-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="f05b9-207">Supporto del paging sul lato client</span><span class="sxs-lookup"><span data-stu-id="f05b9-207">Client-side paging support</span></span>
- <span data-ttu-id="f05b9-208">Filtro sul lato server tramite il parametro -Select</span><span class="sxs-lookup"><span data-stu-id="f05b9-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="f05b9-209">Supporto delle intestazioni di richieste Web</span><span class="sxs-lookup"><span data-stu-id="f05b9-209">Support for web request headers</span></span>

<span data-ttu-id="f05b9-210">I cmdlet proxy generati dal cmdlet `Export-ODataEndPointProxy` forniscono informazioni aggiuntive dall'endpoint OData sul lato server sul flusso di **informazioni**.</span><span class="sxs-lookup"><span data-stu-id="f05b9-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="f05b9-211">Nell'esempio seguente viene recuperato il prodotto principale e l'output viene acquisito nella variabile `$infoStream`.</span><span class="sxs-lookup"><span data-stu-id="f05b9-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="f05b9-212">Specificando il parametro **IncludeTotalResponseCount** si ottiene il numero totale di tutti i record **Product** disponibili nel server.</span><span class="sxs-lookup"><span data-stu-id="f05b9-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="f05b9-213">È possibile ottenere i record dal server in batch usando il supporto del paging sul lato client.</span><span class="sxs-lookup"><span data-stu-id="f05b9-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="f05b9-214">Ciò è utile quando è necessario ottenere una grande quantità di dati dal server tramite la rete.</span><span class="sxs-lookup"><span data-stu-id="f05b9-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="f05b9-215">I cmdlet proxy generati supportano il parametro **Select** che viene usato come filtro per ricevere solo le proprietà dei record necessarie per il client.</span><span class="sxs-lookup"><span data-stu-id="f05b9-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="f05b9-216">Il filtro viene applicato nel server e in questo modo si riduce la quantità di dati trasferiti in rete.</span><span class="sxs-lookup"><span data-stu-id="f05b9-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="f05b9-217">Il cmdlet `Export-ODataEndpointProxy` e i cmdlet proxy generati da questo supportano ora il parametro **Headers**.</span><span class="sxs-lookup"><span data-stu-id="f05b9-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="f05b9-218">L'intestazione può essere usata per incanalare le informazioni aggiuntive previste dall'endpoint OData.</span><span class="sxs-lookup"><span data-stu-id="f05b9-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="f05b9-219">Nell'esempio seguente, per il parametro **Headers** viene specificata una tabella hash che contiene una chiave di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="f05b9-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="f05b9-220">Questo è un esempio tipico per i servizi che prevedono una chiave di sottoscrizione per l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="f05b9-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
