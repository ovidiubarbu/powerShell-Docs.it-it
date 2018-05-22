---
ms.date: 10/31/2017
keywords: dsc,powershell,configurazione,installazione
title: Protezione del file MOF
ms.openlocfilehash: d6f213e497838192ca6ce8d537cc291ee3811e79
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="51d80-103">Protezione del file MOF</span><span class="sxs-lookup"><span data-stu-id="51d80-103">Securing the MOF File</span></span>

><span data-ttu-id="51d80-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="51d80-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="51d80-105">DSC gestisce la configurazione di nodi server applicando le informazioni archiviate in un file MOF, nel quale Gestione configurazione locale implementa lo stato finale richiesto.</span><span class="sxs-lookup"><span data-stu-id="51d80-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="51d80-106">Poiché questo file contiene i dettagli della configurazione, è importante garantirne la sicurezza.</span><span class="sxs-lookup"><span data-stu-id="51d80-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="51d80-107">In questo argomento viene descritto come verificare che il nodo di destinazione abbia crittografato il file.</span><span class="sxs-lookup"><span data-stu-id="51d80-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="51d80-108">A partire dalla versione 5.0 di PowerShell, l'intero file MOF viene crittografato per impostazione predefinita quando viene applicato al nodo usando il cmdlet **Start-DSCConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="51d80-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the **Start-DSCConfiguration** cmdlet.</span></span>
<span data-ttu-id="51d80-109">Il processo descritto in questo articolo è obbligatorio solo se si implementa una soluzione che usa il protocollo del servizio pull se i certificati non sono gestiti, al fine di garantire che le configurazioni scaricate dal nodo di destinazione possano essere crittografate e lette dal sistema prima che siano applicate (ad esempio il servizio pull disponibile in Windows Server).</span><span class="sxs-lookup"><span data-stu-id="51d80-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="51d80-110">Nei nodi registrati in [Automation DSC per Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview) i certificati vengono invece installati e gestiti automaticamente dal servizio senza un sovraccarico amministrativo.</span><span class="sxs-lookup"><span data-stu-id="51d80-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

><span data-ttu-id="51d80-111">**Nota:** questo argomento illustra i certificati usati per la crittografia.</span><span class="sxs-lookup"><span data-stu-id="51d80-111">**Note:** This topic discusses certificates used for encryption.</span></span>
><span data-ttu-id="51d80-112">Per la crittografia è sufficiente un certificato autofirmato, dal momento che la chiave privata viene sempre mantenuta segreta e la crittografia non implica l'attendibilità del documento.</span><span class="sxs-lookup"><span data-stu-id="51d80-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
><span data-ttu-id="51d80-113">I certificati autofirmati *non* vanno usati a scopo di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
><span data-ttu-id="51d80-114">È consigliabile usare un certificato proveniente da un'Autorità di certificazione attendibile a scopo di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="51d80-115">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="51d80-115">Prerequisites</span></span>

<span data-ttu-id="51d80-116">Per crittografare correttamente le credenziali usate per proteggere una configurazione DSC, assicurarsi di avere a disposizione quanto segue:</span><span class="sxs-lookup"><span data-stu-id="51d80-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="51d80-117">**Uno strumento per l'emissione e la distribuzione dei certificati**.</span><span class="sxs-lookup"><span data-stu-id="51d80-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="51d80-118">Questo argomento e gli esempi che contiene presuppongono l'uso di Autorità di certificazione Active Directory.</span><span class="sxs-lookup"><span data-stu-id="51d80-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="51d80-119">Per altre informazioni generali su Servizi certificati Active Directory, vedere [Panoramica di Servizi certificati Active Directory](https://technet.microsoft.com/library/hh831740.aspx) e [Servizi certificati Active Directory in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="51d80-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="51d80-120">**Accesso amministrativo al nodo o ai nodi di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-120">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="51d80-121">**Ogni nodo di destinazione ha un certificato che supporta la crittografia, salvato nel proprio archivio personale**.</span><span class="sxs-lookup"><span data-stu-id="51d80-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="51d80-122">In Windows PowerShell il percorso di questo archivio è Cert:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="51d80-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="51d80-123">Gli esempi in questo argomento usano il modello "Autenticazione workstation", disponibile (insieme ad altri modelli di certificato) in [Modelli di certificato predefiniti](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="51d80-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="51d80-124">Se si intende eseguire questa configurazione in un computer diverso dal nodo di destinazione, **esportare la chiave pubblica del certificato** e quindi importarla nel computer da cui verrà eseguita la configurazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="51d80-125">Assicurarsi di esportare solo la chiave **pubblica**, mantenendo protetta quella privata.</span><span class="sxs-lookup"><span data-stu-id="51d80-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="51d80-126">Processo completo</span><span class="sxs-lookup"><span data-stu-id="51d80-126">Overall process</span></span>

 1. <span data-ttu-id="51d80-127">Configurare i certificati, le chiavi e le identificazioni personali, verificando che ogni nodo di destinazione abbia copie del certificato e che il computer di configurazione abbia la chiave pubblica e l'identificazione personale.</span><span class="sxs-lookup"><span data-stu-id="51d80-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="51d80-128">Creare un blocco di dati di configurazione che contenga il percorso e l'identificazione personale della chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="51d80-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="51d80-129">Creare uno script di configurazione che definisca la configurazione desiderata per il nodo di destinazione e che configuri la decrittografia nei nodi di destinazione indicando a Gestione configurazione locale di decrittografare i dati di configurazione usando il certificato e l'identificazione personale.</span><span class="sxs-lookup"><span data-stu-id="51d80-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="51d80-130">Eseguire la configurazione, che specifica le impostazioni di Gestione configurazione locale e avvia la configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="51d80-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="51d80-132">Requisiti dei certificati</span><span class="sxs-lookup"><span data-stu-id="51d80-132">Certificate Requirements</span></span>

<span data-ttu-id="51d80-133">Per applicare la crittografia delle credenziali, è necessario che un certificato di chiave pubblica sia disponibile nel _nodo di destinazione_ considerato **attendibile** dal computer usato per creare la configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="51d80-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="51d80-134">Questo certificato di chiave pubblica presenta requisiti specifici ai fini dell'uso per la crittografia delle credenziali DSC:</span><span class="sxs-lookup"><span data-stu-id="51d80-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="51d80-135">**Utilizzo chiavi**:</span><span class="sxs-lookup"><span data-stu-id="51d80-135">**Key Usage**:</span></span>
   - <span data-ttu-id="51d80-136">Deve contenere: 'KeyEncipherment' e 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="51d80-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="51d80-137">_Non_ deve contenere: 'Firma digitale'.</span><span class="sxs-lookup"><span data-stu-id="51d80-137">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="51d80-138">**Utilizzo chiavi avanzato**:</span><span class="sxs-lookup"><span data-stu-id="51d80-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="51d80-139">Deve contenere: Crittografia documento (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="51d80-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="51d80-140">_Non_ deve contenere: Autenticazione client (1.3.6.1.5.5.7.3.2) e Autenticazione server (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="51d80-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="51d80-141">La chiave privata per il certificato è disponibile nel \*nodo di destinazione_.</span><span class="sxs-lookup"><span data-stu-id="51d80-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
 4. <span data-ttu-id="51d80-142">Il **provider** per il certificato deve essere "Microsoft RSA SChannel Cryptographic Provider".</span><span class="sxs-lookup"><span data-stu-id="51d80-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

><span data-ttu-id="51d80-143">**Procedura consigliata:** è possibile usare un certificato con l'uso di chiavi "Firma digitale" o uno degli EKU di autenticazione, ma in questo modo la chiave di crittografia sarà più esposta a usi non autorizzati o vulnerabile agli attacchi.</span><span class="sxs-lookup"><span data-stu-id="51d80-143">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="51d80-144">È consigliabile usare un certificato creato in modo specifico per la protezione delle credenziali DSC che omette questi utilizzi chiave ed EKU.</span><span class="sxs-lookup"><span data-stu-id="51d80-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="51d80-145">Qualsiasi certificato esistente nel _nodo di destinazione_ che soddisfa questi criteri può essere usato per proteggere le credenziali DSC.</span><span class="sxs-lookup"><span data-stu-id="51d80-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="51d80-146">Creazione di certificati</span><span class="sxs-lookup"><span data-stu-id="51d80-146">Certificate creation</span></span>

<span data-ttu-id="51d80-147">Esistono due approcci per creare e usare il certificato di crittografia richiesto (coppia di chiavi pubblica/privata).</span><span class="sxs-lookup"><span data-stu-id="51d80-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="51d80-148">Creare il certificato nel **Nodo di destinazione** ed esportare solo la chiave pubblica nel **Nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="51d80-149">Creare il certificato sul **Nodo di creazione** ed esportare la coppia di chiavi nel **Nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="51d80-150">È consigliabile usare il metodo 1 poiché la chiave privata usata per decrittografare le credenziali nel MOF rimane sempre nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="51d80-151">Creazione del certificato sul nodo di destinazione</span><span class="sxs-lookup"><span data-stu-id="51d80-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="51d80-152">La chiave privata deve essere mantenuta segreta poiché viene usata per decrittare il MOF nel **nodo di destinazione**. Il modo più facile per fare ciò è creare il certificato della chiave privata nel **nodo di destinazione** e copiare il **certificato di chiave pubblica** sul computer usato per compilare la configurazione DSC in un file MOF.</span><span class="sxs-lookup"><span data-stu-id="51d80-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="51d80-153">L'esempio seguente consente di:</span><span class="sxs-lookup"><span data-stu-id="51d80-153">The following example:</span></span>
 1. <span data-ttu-id="51d80-154">creare un certificato nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-154">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="51d80-155">esportare il certificato di chiave pubblica nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-155">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="51d80-156">importare il certificato di chiave pubblica nell'archivio certificati **my** del **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="51d80-157">Sul nodo di destinazione: creare ed esportare il certificato</span><span class="sxs-lookup"><span data-stu-id="51d80-157">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="51d80-158">Nodo di destinazione: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="51d80-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="51d80-159">Dopo l'esportazione, ```DscPublicKey.cer``` deve essere copiato nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-159">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="51d80-160">Nodo di destinazione: Windows Server 2012 R2/Windows 8.1 e versioni precedenti</span><span class="sxs-lookup"><span data-stu-id="51d80-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="51d80-161">Poiché il cmdlet New-SelfSignedCertificate nei sistemi operativi Windows precedenti a Windows 10 e Windows Server 2016 non supportano il parametro **Type**, è richiesto un metodo alternativo per creare il certificato in questi sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="51d80-161">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="51d80-162">In questo caso è possibile usare ```makecert.exe``` o ```certutil.exe``` per creare il certificato.</span><span class="sxs-lookup"><span data-stu-id="51d80-162">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="51d80-163">In alternativa, è possibile [scaricare lo script New-SelfSignedCertificateEx.ps1 da Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usarlo per creare il certificato:</span><span class="sxs-lookup"><span data-stu-id="51d80-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="51d80-164">Dopo l'esportazione, ```DscPublicKey.cer``` deve essere copiato nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="51d80-165">Sul nodo di creazione: importare la chiave pubblica del certificato</span><span class="sxs-lookup"><span data-stu-id="51d80-165">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="51d80-166">Creazione del certificato sul nodo di creazione</span><span class="sxs-lookup"><span data-stu-id="51d80-166">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="51d80-167">In alternativa, è possibile creare il certificato di crittografia nel **nodo di creazione**, esportarlo con la **chiave privata** come file PFX e quindi importarlo nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="51d80-168">Questo è il metodo corrente per l'implementazione della crittografia delle credenziali DSC in _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="51d80-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="51d80-169">Anche se il file PFX è protetto da password, è opportuno mantenere il file in sicurezza durante il trasferimento.</span><span class="sxs-lookup"><span data-stu-id="51d80-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="51d80-170">L'esempio seguente consente di:</span><span class="sxs-lookup"><span data-stu-id="51d80-170">The following example:</span></span>
 1. <span data-ttu-id="51d80-171">creare un certificato nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-171">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="51d80-172">esportare il certificato con la chiave privata nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-172">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="51d80-173">rimuove la chiave privata dal **nodo di creazione**, mantenendo il certificato della chiave pubblica nell'archivio **My**.</span><span class="sxs-lookup"><span data-stu-id="51d80-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="51d80-174">Importare il certificato di chiave privata nell'archivio certificati My(Personal) nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="51d80-175">È necessario aggiungerlo all'archivio radice in modo che risulti attendibile per il **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="51d80-176">Sul nodo di creazione: creare ed esportare il certificato</span><span class="sxs-lookup"><span data-stu-id="51d80-176">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="51d80-177">Nodo di destinazione: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="51d80-177">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```
<span data-ttu-id="51d80-178">Dopo l'esportazione, ```DscPrivateKey.pfx``` deve essere copiato nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="51d80-178">Once exported, the ```DscPrivateKey.pfx``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="51d80-179">Nodo di destinazione: Windows Server 2012 R2/Windows 8.1 e versioni precedenti</span><span class="sxs-lookup"><span data-stu-id="51d80-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="51d80-180">Poiché il cmdlet New-SelfSignedCertificate nei sistemi operativi Windows precedenti a Windows 10 e Windows Server 2016 non supportano il parametro **Type**, è richiesto un metodo alternativo per creare il certificato in questi sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="51d80-180">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="51d80-181">In questo caso è possibile usare ```makecert.exe``` o ```certutil.exe``` per creare il certificato.</span><span class="sxs-lookup"><span data-stu-id="51d80-181">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="51d80-182">In alternativa, è possibile [scaricare lo script New-SelfSignedCertificateEx.ps1 da Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usarlo per creare il certificato:</span><span class="sxs-lookup"><span data-stu-id="51d80-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="51d80-183">Sul nodo di destinazione: importare la chiave privata del certificato come attendibile</span><span class="sxs-lookup"><span data-stu-id="51d80-183">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="51d80-184">Dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="51d80-184">Configuration data</span></span>

<span data-ttu-id="51d80-185">Il blocco di dati di configurazione definisce i nodi di destinazione su cui operare, se crittografare o meno le credenziali, gli strumenti di crittografia e altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="51d80-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="51d80-186">Per altre informazioni sul blocco di dati di configurazione, vedere [Separazione dei dati di configurazione e dell'ambiente](configData.md).</span><span class="sxs-lookup"><span data-stu-id="51d80-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="51d80-187">Gli elementi che possono essere configurati per ogni nodo correlati alla crittografia delle credenziali sono:</span><span class="sxs-lookup"><span data-stu-id="51d80-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="51d80-188">**NodeName** - nome del nodo di destinazione per cui viene configurata la crittografia delle credenziali.</span><span class="sxs-lookup"><span data-stu-id="51d80-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="51d80-189">**PsDscAllowPlainTextPassword** - indica se le credenziali non crittografate potranno essere passate a questo nodo.</span><span class="sxs-lookup"><span data-stu-id="51d80-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="51d80-190">Si tratta di un'**operazione sconsigliata**.</span><span class="sxs-lookup"><span data-stu-id="51d80-190">This is **not recommended**.</span></span>
* <span data-ttu-id="51d80-191">**Thumbprint** - identificazione personale del certificato che verrà usato per decrittografare le credenziali nella configurazione DSC nel _nodo di destinazione_.</span><span class="sxs-lookup"><span data-stu-id="51d80-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="51d80-192">**Questo certificato deve essere presente nell'archivio certificati del computer locale nel nodo di destinazione.**</span><span class="sxs-lookup"><span data-stu-id="51d80-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="51d80-193">**CertificateFile** - file di certificato (contenente solo la chiave pubblica) che deve essere usato per crittografare le credenziali per il _nodo di destinazione_.</span><span class="sxs-lookup"><span data-stu-id="51d80-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="51d80-194">Deve trattarsi di un file di certificato in formato X.509 binario con codifica DER o X.509 con codifica Base-64.</span><span class="sxs-lookup"><span data-stu-id="51d80-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="51d80-195">Questo esempio mostra un blocco di dati di configurazione che specifica un nodo di destinazione su cui operare denominato targetNode, il percorso del file di certificato della chiave pubblica (denominato targetNode.cer) e l'identificazione personale per la chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="51d80-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```


## <a name="configuration-script"></a><span data-ttu-id="51d80-196">Script di configurazione</span><span class="sxs-lookup"><span data-stu-id="51d80-196">Configuration script</span></span>

<span data-ttu-id="51d80-197">Nello script di configurazione stesso usare il parametro `PsCredential` per specificare che le credenziali devono essere archiviate per il periodo di tempo più breve possibile.</span><span class="sxs-lookup"><span data-stu-id="51d80-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="51d80-198">Quando si esegue l'esempio fornito, DSC chiede le credenziali e quindi crittografa il file MOF usando la risorsa CertificateFile associata al nodo di destinazione nel blocco di dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="51d80-199">Questo esempio di codice copia un file da una condivisione protetta a un utente.</span><span class="sxs-lookup"><span data-stu-id="51d80-199">This code example copies a file from a share that is secured to a user.</span></span>

```
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="51d80-200">Configurazione della decrittografia</span><span class="sxs-lookup"><span data-stu-id="51d80-200">Setting up decryption</span></span>

<span data-ttu-id="51d80-201">Prima che [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) funzioni correttamente, è necessario indicare a Gestione configurazione locale in ogni nodo di destinazione il certificato da usare per decrittografare le credenziali, usando la risorsa CertificateID per verificare l'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="51d80-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="51d80-202">Questa funzione di esempio trova il certificato locale appropriato e potrebbe dover essere personalizzata perché trovi l'esatto certificato che si vuole usare:</span><span class="sxs-lookup"><span data-stu-id="51d80-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="51d80-203">Con il certificato indicato dall'identificazione personale, lo script di configurazione può essere aggiornato in modo da usare il valore:</span><span class="sxs-lookup"><span data-stu-id="51d80-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="51d80-204">Esecuzione della configurazione</span><span class="sxs-lookup"><span data-stu-id="51d80-204">Running the configuration</span></span>

<span data-ttu-id="51d80-205">A questo punto, è possibile eseguire la configurazione, che genera due file:</span><span class="sxs-lookup"><span data-stu-id="51d80-205">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="51d80-206">Un file \*.meta.mof che configura Gestione configurazione locale per decrittografare le credenziali usando il certificato archiviato nell'archivio del computer locale e indicato dalla relativa identificazione personale.</span><span class="sxs-lookup"><span data-stu-id="51d80-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="51d80-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) si applica al file \*.meta.mof.</span><span class="sxs-lookup"><span data-stu-id="51d80-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
 * <span data-ttu-id="51d80-208">Un file MOF che applica effettivamente la configurazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="51d80-209">Start-DscConfiguration applica la configurazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="51d80-210">I comandi seguenti eseguono questi passaggi:</span><span class="sxs-lookup"><span data-stu-id="51d80-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="51d80-211">Questo esempio eseguirebbe il push della configurazione DSC al nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="51d80-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="51d80-212">La configurazione DSC può essere applicata anche tramite un server di pull DSC, se disponibile.</span><span class="sxs-lookup"><span data-stu-id="51d80-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="51d80-213">Vedere [Configurazione di un client di pull DSC](pullClient.md) per altre informazioni sull'applicazione delle configurazioni DSC tramite un server di pull DSC.</span><span class="sxs-lookup"><span data-stu-id="51d80-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="51d80-214">Esempio di modulo di crittografia delle credenziali</span><span class="sxs-lookup"><span data-stu-id="51d80-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="51d80-215">Ecco un esempio completo che contiene tutti i passaggi, insieme a un cmdlet helper che esporta e copia le chiavi pubbliche:</span><span class="sxs-lookup"><span data-stu-id="51d80-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
