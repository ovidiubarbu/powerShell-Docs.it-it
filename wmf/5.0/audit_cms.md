---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 14208e3b5d5c2fef80fa42a87cc00aeee81bd042
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="c8eed-102">Cmdlet CMS (Cryptographic Message Syntax)</span><span class="sxs-lookup"><span data-stu-id="c8eed-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="c8eed-103">I cmdlet CMS (Cryptographic Message Syntax) supportano la crittografia e la decrittografia del contenuto con il formato standard IETF per la protezione crittografica dei messaggi, come documentato in [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="c8eed-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

<span data-ttu-id="c8eed-104">Lo standard di crittografia CMS implementa la crittografia a chiave pubblica, in cui le chiavi usate per crittografare il contenuto (*chiave pubblica*) e le chiavi usate per decrittografare il contenuto (*chiave privata*) sono separate.</span><span class="sxs-lookup"><span data-stu-id="c8eed-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="c8eed-105">La chiave pubblica può essere condivisa liberamente e non contiene dati sensibili.</span><span class="sxs-lookup"><span data-stu-id="c8eed-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="c8eed-106">Eventuale contenuto crittografato con la chiave pubblica potrà essere decrittografato solo con la chiave privata.</span><span class="sxs-lookup"><span data-stu-id="c8eed-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="c8eed-107">Per altre informazioni, vedere: [Crittografia a chiave pubblica](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="c8eed-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="c8eed-108">Per essere riconosciuti in PowerShell, i certificati di crittografia richiedono un identificatore univoco di utilizzo delle chiavi (EKU) per identificarli come certificati di crittografia dei dati, ad esempio identificatori per la firma del codice o per la posta crittografata.</span><span class="sxs-lookup"><span data-stu-id="c8eed-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="c8eed-109">Di seguito è riportato un esempio di creazione di un certificato valido per la crittografia del documento:</span><span class="sxs-lookup"><span data-stu-id="c8eed-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

<span data-ttu-id="c8eed-110">Eseguire quindi:</span><span class="sxs-lookup"><span data-stu-id="c8eed-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="c8eed-111">E ora è possibile crittografare e decrittografare il contenuto:</span><span class="sxs-lookup"><span data-stu-id="c8eed-111">And you can now encrypt and decrypt content:</span></span>

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

<span data-ttu-id="c8eed-112">Qualsiasi parametro di tipo **CMSMessageRecipient** supporta identificatori nei formati seguenti:</span><span class="sxs-lookup"><span data-stu-id="c8eed-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="c8eed-113">Un certificato effettivo (recuperato dal provider di certificati)</span><span class="sxs-lookup"><span data-stu-id="c8eed-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="c8eed-114">Percorso di un file contenente il certificato</span><span class="sxs-lookup"><span data-stu-id="c8eed-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="c8eed-115">Percorso di una directory contenente il certificato</span><span class="sxs-lookup"><span data-stu-id="c8eed-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="c8eed-116">Identificazione personale del certificato (usata per la ricerca nell'archivio certificati)</span><span class="sxs-lookup"><span data-stu-id="c8eed-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="c8eed-117">Nome del soggetto del certificato (usato per la ricerca nell'archivio certificati)</span><span class="sxs-lookup"><span data-stu-id="c8eed-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="c8eed-118">Per visualizzare i certificati di crittografia dei documenti nel provider di certificati, è possibile usare il parametro dinamico **-DocumentEncryptionCert**:</span><span class="sxs-lookup"><span data-stu-id="c8eed-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```
