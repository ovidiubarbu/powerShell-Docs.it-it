---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Protezione del file MOF
ms.openlocfilehash: 70dec03f3b883eb88661e27c411248b8e1bb2177
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="5abb5-103">Protezione del file MOF</span><span class="sxs-lookup"><span data-stu-id="5abb5-103">Securing the MOF File</span></span>

><span data-ttu-id="5abb5-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5abb5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5abb5-105">DSC indica ai nodi di destinazione quale configurazione devono avere inviando un file MOF che contiene queste informazioni a ogni nodo, in cui Gestione configurazione locale implementa la configurazione desiderata.</span><span class="sxs-lookup"><span data-stu-id="5abb5-105">DSC tells the target nodes what configuration they should have by sending a MOF file with that information to each node, where the Local Configuration Manager (LCM) implements the desired configuration.</span></span> <span data-ttu-id="5abb5-106">Poiché questo file contiene i dettagli della configurazione, è importante garantirne la sicurezza.</span><span class="sxs-lookup"><span data-stu-id="5abb5-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span> <span data-ttu-id="5abb5-107">A tale scopo, è possibile impostare Gestione configurazione locale per verificare le credenziali di un utente.</span><span class="sxs-lookup"><span data-stu-id="5abb5-107">To do this, you can set the LCM to check the credentials of a user.</span></span> <span data-ttu-id="5abb5-108">Questo argomento descrive come trasmettere queste credenziali in modo sicuro al nodo di destinazione crittografandole con i certificati.</span><span class="sxs-lookup"><span data-stu-id="5abb5-108">This topic describes how to transmit those credentials securely to the target node by encrypting them with certificates.</span></span>

><span data-ttu-id="5abb5-109">**Nota:** questo argomento illustra i certificati usati per la crittografia.</span><span class="sxs-lookup"><span data-stu-id="5abb5-109">**Note:** This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="5abb5-110">Per la crittografia è sufficiente un certificato autofirmato, dal momento che la chiave privata viene sempre mantenuta segreta e la crittografia non implica l'attendibilità del documento.</span><span class="sxs-lookup"><span data-stu-id="5abb5-110">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="5abb5-111">I certificati autofirmati *non* vanno usati a scopo di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-111">Self-signed certificates should *not* be used for authentication purposes.</span></span> <span data-ttu-id="5abb5-112">È consigliabile usare un certificato proveniente da un'Autorità di certificazione attendibile a scopo di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-112">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5abb5-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5abb5-113">Prerequisites</span></span>

<span data-ttu-id="5abb5-114">Per crittografare correttamente le credenziali usate per proteggere una configurazione DSC, assicurarsi di avere a disposizione quanto segue:</span><span class="sxs-lookup"><span data-stu-id="5abb5-114">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="5abb5-115">**Uno strumento per l'emissione e la distribuzione dei certificati**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-115">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="5abb5-116">Questo argomento e gli esempi che contiene presuppongono l'uso di Autorità di certificazione Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5abb5-116">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="5abb5-117">Per altre informazioni generali su Servizi certificati Active Directory, vedere [Panoramica di Servizi certificati Active Directory](https://technet.microsoft.com/library/hh831740.aspx) e [Servizi certificati Active Directory in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="5abb5-117">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="5abb5-118">**Accesso amministrativo al nodo o ai nodi di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-118">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="5abb5-119">**Ogni nodo di destinazione ha un certificato che supporta la crittografia, salvato nel proprio archivio personale**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-119">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="5abb5-120">In Windows PowerShell il percorso di questo archivio è Cert:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="5abb5-120">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="5abb5-121">Gli esempi in questo argomento usano il modello "Autenticazione workstation", disponibile (insieme ad altri modelli di certificato) in [Modelli di certificato predefiniti](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="5abb5-121">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="5abb5-122">Se si intende eseguire questa configurazione in un computer diverso dal nodo di destinazione, **esportare la chiave pubblica del certificato** e quindi importarla nel computer da cui verrà eseguita la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-122">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="5abb5-123">Assicurarsi di esportare solo la chiave **pubblica**, mantenendo protetta quella privata.</span><span class="sxs-lookup"><span data-stu-id="5abb5-123">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="5abb5-124">Processo completo</span><span class="sxs-lookup"><span data-stu-id="5abb5-124">Overall process</span></span>

 1. <span data-ttu-id="5abb5-125">Configurare i certificati, le chiavi e le identificazioni personali, verificando che ogni nodo di destinazione abbia copie del certificato e che il computer di configurazione abbia la chiave pubblica e l'identificazione personale.</span><span class="sxs-lookup"><span data-stu-id="5abb5-125">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="5abb5-126">Creare un blocco di dati di configurazione che contenga il percorso e l'identificazione personale della chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="5abb5-126">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="5abb5-127">Creare uno script di configurazione che definisca la configurazione desiderata per il nodo di destinazione e che configuri la decrittografia nei nodi di destinazione indicando a Gestione configurazione locale di decrittografare i dati di configurazione usando il certificato e l'identificazione personale.</span><span class="sxs-lookup"><span data-stu-id="5abb5-127">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="5abb5-128">Eseguire la configurazione, che specifica le impostazioni di Gestione configurazione locale e avvia la configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="5abb5-128">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="5abb5-130">Requisiti dei certificati</span><span class="sxs-lookup"><span data-stu-id="5abb5-130">Certificate Requirements</span></span>

<span data-ttu-id="5abb5-131">Per applicare la crittografia delle credenziali, è necessario che un certificato di chiave pubblica sia disponibile nel _nodo di destinazione_ considerato **attendibile** dal computer usato per creare la configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="5abb5-131">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="5abb5-132">Questo certificato di chiave pubblica presenta requisiti specifici ai fini dell'uso per la crittografia delle credenziali DSC:</span><span class="sxs-lookup"><span data-stu-id="5abb5-132">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="5abb5-133">**Utilizzo chiavi**:</span><span class="sxs-lookup"><span data-stu-id="5abb5-133">**Key Usage**:</span></span>
   - <span data-ttu-id="5abb5-134">Deve contenere: 'KeyEncipherment' e 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="5abb5-134">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="5abb5-135">_Non_ deve contenere: 'Firma digitale'.</span><span class="sxs-lookup"><span data-stu-id="5abb5-135">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="5abb5-136">**Utilizzo chiavi avanzato**:</span><span class="sxs-lookup"><span data-stu-id="5abb5-136">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="5abb5-137">Deve contenere: Crittografia documento (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="5abb5-137">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="5abb5-138">_Non_ deve contenere: Autenticazione client (1.3.6.1.5.5.7.3.2) e Autenticazione server (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="5abb5-138">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="5abb5-139">La chiave privata per il certificato è disponibile nel *nodo di destinazione_.</span><span class="sxs-lookup"><span data-stu-id="5abb5-139">The Private Key for the certificate is available on the *Target Node_.</span></span>
 4. <span data-ttu-id="5abb5-140">Il **provider** per il certificato deve essere "Microsoft RSA SChannel Cryptographic Provider".</span><span class="sxs-lookup"><span data-stu-id="5abb5-140">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>
 
><span data-ttu-id="5abb5-141">**Procedura consigliata:** è possibile usare un certificato con l'uso di chiavi "Firma digitale" o uno degli EKU di autenticazione, ma in questo modo la chiave di crittografia sarà più esposta a usi non autorizzati o vulnerabile agli attacchi.</span><span class="sxs-lookup"><span data-stu-id="5abb5-141">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="5abb5-142">È consigliabile usare un certificato creato in modo specifico per la protezione delle credenziali DSC che omette questi utilizzi chiave ed EKU.</span><span class="sxs-lookup"><span data-stu-id="5abb5-142">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>
  
<span data-ttu-id="5abb5-143">Qualsiasi certificato esistente nel _nodo di destinazione_ che soddisfa questi criteri può essere usato per proteggere le credenziali DSC.</span><span class="sxs-lookup"><span data-stu-id="5abb5-143">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="5abb5-144">Creazione di certificati</span><span class="sxs-lookup"><span data-stu-id="5abb5-144">Certificate creation</span></span>

<span data-ttu-id="5abb5-145">Esistono due approcci per creare e usare il certificato di crittografia richiesto (coppia di chiavi pubblica/privata).</span><span class="sxs-lookup"><span data-stu-id="5abb5-145">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="5abb5-146">Creare il certificato nel **Nodo di destinazione** ed esportare solo la chiave pubblica nel **Nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-146">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="5abb5-147">Creare il certificato sul **Nodo di creazione** ed esportare la coppia di chiavi nel **Nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-147">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="5abb5-148">È consigliabile usare il metodo 1 poiché la chiave privata usata per decrittografare le credenziali nel MOF rimane sempre nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-148">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="5abb5-149">Creazione del certificato sul nodo di destinazione</span><span class="sxs-lookup"><span data-stu-id="5abb5-149">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="5abb5-150">La chiave privata deve essere mantenuta segreta poiché viene usata per decrittare il MOF nel **nodo di destinazione**. Il modo più facile per fare ciò è creare il certificato della chiave privata nel **nodo di destinazione** e copiare il **certificato di chiave pubblica** sul computer usato per compilare la configurazione DSC in un file MOF.</span><span class="sxs-lookup"><span data-stu-id="5abb5-150">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="5abb5-151">L'esempio seguente consente di:</span><span class="sxs-lookup"><span data-stu-id="5abb5-151">The following example:</span></span>
 1. <span data-ttu-id="5abb5-152">creare un certificato nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-152">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="5abb5-153">esportare il certificato di chiave pubblica nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-153">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="5abb5-154">importare il certificato di chiave pubblica nell'archivio certificati **my** del **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-154">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="5abb5-155">Sul nodo di destinazione: creare ed esportare il certificato</span><span class="sxs-lookup"><span data-stu-id="5abb5-155">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="5abb5-156">Nodo di creazione: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="5abb5-156">Authoring Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="5abb5-157">Dopo l'esportazione, ```DscPublicKey.cer``` deve essere copiato nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-157">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="5abb5-158">Nodo di creazione: Windows Server 2012 R2/Windows 8.1 e versioni precedenti</span><span class="sxs-lookup"><span data-stu-id="5abb5-158">Authoring Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="5abb5-159">Poiché il cmdlet New-SelfSignedCertificate nei sistemi operativi Windows precedenti a Windows 10 e Windows Server 2016 non supportano il parametro **Type**, è richiesto un metodo alternativo per creare il certificato in questi sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="5abb5-159">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="5abb5-160">In questo caso è possibile usare ```makecert.exe``` o ```certutil.exe``` per creare il certificato.</span><span class="sxs-lookup"><span data-stu-id="5abb5-160">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="5abb5-161">In alternativa, è possibile [scaricare lo script New-SelfSignedCertificateEx.ps1 da Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usarlo per creare il certificato:</span><span class="sxs-lookup"><span data-stu-id="5abb5-161">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
    -StoreName 'My' `
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
<span data-ttu-id="5abb5-162">Dopo l'esportazione, ```DscPublicKey.cer``` deve essere copiato nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-162">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="5abb5-163">Sul nodo di creazione: importare la chiave pubblica del certificato</span><span class="sxs-lookup"><span data-stu-id="5abb5-163">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="5abb5-164">Creazione del certificato sul nodo di creazione</span><span class="sxs-lookup"><span data-stu-id="5abb5-164">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="5abb5-165">In alternativa, è possibile creare il certificato di crittografia nel **nodo di creazione**, esportarlo con la **chiave privata** come file PFX e quindi importarlo nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-165">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="5abb5-166">Questo è il metodo corrente per l'implementazione della crittografia delle credenziali DSC in _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="5abb5-166">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="5abb5-167">Anche se il file PFX è protetto da password, è opportuno mantenere il file in sicurezza durante il trasferimento.</span><span class="sxs-lookup"><span data-stu-id="5abb5-167">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="5abb5-168">L'esempio seguente consente di:</span><span class="sxs-lookup"><span data-stu-id="5abb5-168">The following example:</span></span>
 1. <span data-ttu-id="5abb5-169">creare un certificato nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-169">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="5abb5-170">esportare il certificato con la chiave privata nel **nodo di creazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-170">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="5abb5-171">rimuove la chiave privata dal **nodo di creazione**, mantenendo il certificato della chiave pubblica nell'archivio **My**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-171">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="5abb5-172">importare il certificato di chiave privata nell'archivio certificati radice nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-172">imports the private key certificate into the root certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="5abb5-173">È necessario aggiungerlo all'archivio radice in modo che risulti attendibile per il **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-173">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="5abb5-174">Sul nodo di creazione: creare ed esportare il certificato</span><span class="sxs-lookup"><span data-stu-id="5abb5-174">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="5abb5-175">Nodo di destinazione: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="5abb5-175">Target Node: Windows Server 2016 and Windows 10</span></span>

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
<span data-ttu-id="5abb5-176">Dopo l'esportazione, ```DscPrivateKey.cer``` deve essere copiato nel **nodo di destinazione**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-176">Once exported, the ```DscPrivateKey.cer``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="5abb5-177">Nodo di destinazione: Windows Server 2012 R2/Windows 8.1 e versioni precedenti</span><span class="sxs-lookup"><span data-stu-id="5abb5-177">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="5abb5-178">Poiché il cmdlet New-SelfSignedCertificate nei sistemi operativi Windows precedenti a Windows 10 e Windows Server 2016 non supportano il parametro **Type**, è richiesto un metodo alternativo per creare il certificato in questi sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="5abb5-178">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="5abb5-179">In questo caso è possibile usare ```makecert.exe``` o ```certutil.exe``` per creare il certificato.</span><span class="sxs-lookup"><span data-stu-id="5abb5-179">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="5abb5-180">In alternativa, è possibile [scaricare lo script New-SelfSignedCertificateEx.ps1 da Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usarlo per creare il certificato:</span><span class="sxs-lookup"><span data-stu-id="5abb5-180">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="5abb5-181">Sul nodo di destinazione: importare la chiave privata del certificato come attendibile</span><span class="sxs-lookup"><span data-stu-id="5abb5-181">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\Root -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="5abb5-182">Dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="5abb5-182">Configuration data</span></span>

<span data-ttu-id="5abb5-183">Il blocco di dati di configurazione definisce i nodi di destinazione su cui operare, se crittografare o meno le credenziali, gli strumenti di crittografia e altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="5abb5-183">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="5abb5-184">Per altre informazioni sul blocco di dati di configurazione, vedere [Separazione dei dati di configurazione e dell'ambiente](configData.md).</span><span class="sxs-lookup"><span data-stu-id="5abb5-184">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="5abb5-185">Gli elementi che possono essere configurati per ogni nodo correlati alla crittografia delle credenziali sono:</span><span class="sxs-lookup"><span data-stu-id="5abb5-185">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="5abb5-186">**NodeName** - nome del nodo di destinazione per cui viene configurata la crittografia delle credenziali.</span><span class="sxs-lookup"><span data-stu-id="5abb5-186">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="5abb5-187">**PsDscAllowPlainTextPassword** - indica se le credenziali non crittografate potranno essere passate a questo nodo.</span><span class="sxs-lookup"><span data-stu-id="5abb5-187">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="5abb5-188">Si tratta di un'**operazione sconsigliata**.</span><span class="sxs-lookup"><span data-stu-id="5abb5-188">This is **not recommended**.</span></span>
* <span data-ttu-id="5abb5-189">**Thumbprint** - identificazione personale del certificato che verrà usato per decrittografare le credenziali nella configurazione DSC nel _nodo di destinazione_.</span><span class="sxs-lookup"><span data-stu-id="5abb5-189">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="5abb5-190">**Questo certificato deve essere presente nell'archivio certificati del computer locale nel nodo di destinazione.**</span><span class="sxs-lookup"><span data-stu-id="5abb5-190">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="5abb5-191">**CertificateFile** - file di certificato (contenente solo la chiave pubblica) che deve essere usato per crittografare le credenziali per il _nodo di destinazione_.</span><span class="sxs-lookup"><span data-stu-id="5abb5-191">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="5abb5-192">Deve trattarsi di un file di certificato in formato X.509 binario con codifica DER o X.509 con codifica Base-64.</span><span class="sxs-lookup"><span data-stu-id="5abb5-192">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="5abb5-193">Questo esempio mostra un blocco di dati di configurazione che specifica un nodo di destinazione su cui operare denominato targetNode, il percorso del file di certificato della chiave pubblica (denominato targetNode.cer) e l'identificazione personale per la chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="5abb5-193">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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


## <a name="configuration-script"></a><span data-ttu-id="5abb5-194">Script di configurazione</span><span class="sxs-lookup"><span data-stu-id="5abb5-194">Configuration script</span></span>

<span data-ttu-id="5abb5-195">Nello script di configurazione stesso usare il parametro `PsCredential` per specificare che le credenziali devono essere archiviate per il periodo di tempo più breve possibile.</span><span class="sxs-lookup"><span data-stu-id="5abb5-195">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="5abb5-196">Quando si esegue l'esempio fornito, DSC chiede le credenziali e quindi crittografa il file MOF usando la risorsa CertificateFile associata al nodo di destinazione nel blocco di dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-196">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="5abb5-197">Questo esempio di codice copia un file da una condivisione protetta a un utente.</span><span class="sxs-lookup"><span data-stu-id="5abb5-197">This code example copies a file from a share that is secured to a user.</span></span>

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

## <a name="setting-up-decryption"></a><span data-ttu-id="5abb5-198">Configurazione della decrittografia</span><span class="sxs-lookup"><span data-stu-id="5abb5-198">Setting up decryption</span></span>

<span data-ttu-id="5abb5-199">Prima che [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) funzioni correttamente, è necessario indicare a Gestione configurazione locale in ogni nodo di destinazione il certificato da usare per decrittografare le credenziali, usando la risorsa CertificateID per verificare l'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="5abb5-199">Before [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="5abb5-200">Questa funzione di esempio trova il certificato locale appropriato e potrebbe dover essere personalizzata perché trovi l'esatto certificato che si vuole usare:</span><span class="sxs-lookup"><span data-stu-id="5abb5-200">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="5abb5-201">Con il certificato indicato dall'identificazione personale, lo script di configurazione può essere aggiornato in modo da usare il valore:</span><span class="sxs-lookup"><span data-stu-id="5abb5-201">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="5abb5-202">Esecuzione della configurazione</span><span class="sxs-lookup"><span data-stu-id="5abb5-202">Running the configuration</span></span>

<span data-ttu-id="5abb5-203">A questo punto, è possibile eseguire la configurazione, che genera due file:</span><span class="sxs-lookup"><span data-stu-id="5abb5-203">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="5abb5-204">Un file *.meta.mof che configura Gestione configurazione locale per decrittografare le credenziali usando il certificato archiviato nell'archivio del computer locale e indicato dalla relativa identificazione personale.</span><span class="sxs-lookup"><span data-stu-id="5abb5-204">A *.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="5abb5-205">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) si applica al file *.meta.mof.</span><span class="sxs-lookup"><span data-stu-id="5abb5-205">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) applies the *.meta.mof file.</span></span>
 * <span data-ttu-id="5abb5-206">Un file MOF che applica effettivamente la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-206">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="5abb5-207">Start-DscConfiguration applica la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-207">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="5abb5-208">I comandi seguenti eseguono questi passaggi:</span><span class="sxs-lookup"><span data-stu-id="5abb5-208">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="5abb5-209">Questo esempio eseguirebbe il push della configurazione DSC al nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="5abb5-209">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="5abb5-210">La configurazione DSC può essere applicata anche tramite un server di pull DSC, se disponibile.</span><span class="sxs-lookup"><span data-stu-id="5abb5-210">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="5abb5-211">Vedere [Configurazione di un client di pull DSC](pullClient.md) per altre informazioni sull'applicazione delle configurazioni DSC tramite un server di pull DSC.</span><span class="sxs-lookup"><span data-stu-id="5abb5-211">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="5abb5-212">Esempio di modulo di crittografia delle credenziali</span><span class="sxs-lookup"><span data-stu-id="5abb5-212">Credential Encryption Module Example</span></span>

<span data-ttu-id="5abb5-213">Ecco un esempio completo che contiene tutti i passaggi, insieme a un cmdlet helper che esporta e copia le chiavi pubbliche:</span><span class="sxs-lookup"><span data-stu-id="5abb5-213">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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

