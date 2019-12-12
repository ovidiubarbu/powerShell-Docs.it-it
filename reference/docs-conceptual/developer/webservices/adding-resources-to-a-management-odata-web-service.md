---
title: Aggiunta di risorse a un servizio Web OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359820"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Aggiunta di risorse a un servizio Web OData di gestione

Questo esempio illustra come aggiungere una risorsa a un servizio Web OData di gestione esistente usando la finestra di progettazione dello schema di gestione OData. Nell'esempio [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) viene creato un servizio Web che espone il processo e le risorse del server. In questo esempio verrà aggiunta una risorsa della macchina virtuale (VM) al servizio Web.

## <a name="prerequisites"></a>Prerequisiti

In questo argomento si presuppone che sia stato scaricato e installato l'esempio [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) , come descritto in [creazione di un servizio Web di Windows PowerShell](./creating-a-management-odata-web-service.md), e che sia stato scaricato e installato la [finestra di progettazione dello schema di gestione OData](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). In questo argomento si presuppone inoltre che nel computer in cui si configura l'endpoint OData di gestione sia installato il modulo Hyper-V di Windows PowerShell.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Aggiunta di una macchina virtuale come risorsa al servizio Web

Il primo passaggio consiste nell'importare lo schema dall'endpoint OData di gestione esistente in progettazione schema. Nella procedura riportata di seguito viene descritto come eseguire questa operazione.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importazione di uno schema esistente nella finestra di progettazione dello schema

1. Aprire la finestra di progettazione dello schema OData di gestione.

2. Scegliere **file** dal menu **file** . **Nuovo** ; **File**. Verrà visualizzata la finestra di dialogo **nuovo file** .

3. Fare clic su **Gestione modello OData**, quindi fare clic su **Apri**.

4. Fare clic con il pulsante destro del mouse nella finestra principale, quindi scegliere **file di schema** . **Importa**. Verrà visualizzata la finestra di dialogo **Apri** .

5. Passare alla cartella in cui è stato configurato il servizio Web di gestione OData per l'esempio [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) . Se è stato usato lo script di Windows PowerShell fornito con tale esempio per configurare l'endpoint senza modificare lo script, la cartella è **C:\inetpub\wwwroot\Modata**. Selezionare Schema. mof, quindi fare clic su **Apri**.

   A questo punto, aprire i file schema. mof e schema. XML in un editor di testo e notare che contengono i mapping per le risorse del processo e del servizio. Il file schema. MOF utilizza lo standard MOF ( [Distributed Management Task Force](https://www.dmtf.org/) ). Nel file schema. XML viene utilizzato un XML Schema descritto in [schema di mapping delle risorse](./resource-mapping-schema.md).

   Nella procedura seguente viene descritto come importare i cmdlet di Hyper-V in nel modello di schema.

#### <a name="importing-cmdlets-into-the-schema"></a>Importazione di cmdlet nello schema

1. Fare clic con il pulsante destro del mouse su un'area vuota della finestra di progettazione schema, quindi scegliere **Importa cmdlet**. Verrà visualizzata la finestra di dialogo **importazione guidata cmdlet** .

2. Verificare che il **computer locale** sia selezionato e fare clic su **Avanti**.

3. Assicurarsi che sia selezionata l'opzione moduli di Windows PowerShell installati e selezionare Hyper-V dall'elenco a discesa. Fare clic su **Avanti**. Fare clic su **Avanti**.

4. Nell'elenco **nome cmdlet** selezionare **VM**. Fare clic su **Avanti**.

5. Per questo esempio, vengono associati solo i comandi Get ed Delete con i cmdlet. Deselezionare le caselle di controllo **Crea** e **Aggiorna** e verificare che le caselle di controllo **Ottieni** ed **Elimina** siano selezionate. Verificare che il cmdlet `Get-VM` sia selezionato per **Get**e che il cmdlet `Remove-VM` sia selezionato per l' **eliminazione**.

6. Poiché i metadati per i cmdlet della macchina virtuale non specificano un tipo di output, sarà necessario eseguire il cmdlet per specificare il tipo di output. Selezionare **Fornisci tipo di output** e fare clic su **Esegui cmdlet**. Verrà visualizzata la finestra di dialogo **Esegui cmdlet** . Fare clic su **Esegui**. La casella **tipo CLR** viene popolata con il tipo di `VirtualMachine`. Fare clic su **OK**, quindi su **Avanti**.

7. Per impostazione predefinita, vengono selezionate tutte le proprietà dell'oggetto VirtualMachine. È possibile deselezionare tutte le proprietà che non si desidera includere come parte dei dati restituiti quando si richiede questa risorsa dal servizio Web. Fare clic su **Avanti**.

8. È necessario selezionare almeno una proprietà da utilizzare come chiave. Selezionare **nome** nell'elenco e fare clic su **Avanti**.

9. La finestra successiva consente di eseguire il mapping delle proprietà della risorsa OData di gestione alle proprietà dei cmdlet sottostanti. Per impostazione predefinita, la procedura guidata esegue il mapping delle proprietà con nomi identici. Ad esempio, la proprietà `ComputerName` della risorsa viene mappata alla proprietà `ComputerName` dei cmdlet.  In questo modo è possibile specificare la proprietà `ComputerName` in una richiesta al servizio Web e fare in modo che il valore specificato venga passato al cmdlet `Get-VM`. per impostazione predefinita vengono inoltre mappati `Id` e `Name`.

   10. Fare clic su **Avanti**, quindi su **fine**.

       La risorsa VM viene ora visualizzata nella finestra Progettazione schema. È possibile esaminare le proprietà e le operazioni associate alla risorsa. Successivamente, i file di schema aggiornati vengono esportati nella directory virtuale per il servizio Web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Esportazione di file di schema da progettazione schema

1. Fare clic con il pulsante destro del mouse su un'area vuota della finestra di progettazione schema, quindi scegliere **file di schema** . **Esporta**. Verrà visualizzata la finestra **di dialogo Salva con nome** .

2. Passare alla stessa directory da cui è stato importato il file MOF. Denominare il file come il file MOF originale (schema. mof per impostazione predefinita) e fare clic su **Salva**. Confermare che si desidera sovrascrivere il file esistente.

   Sebbene non sia indicato in modo esplicito nella finestra di dialogo **Salva con nome** , sostituisce i file schema. mof e schema. XML.

## <a name="next-steps"></a>Passaggi successivi

Prima di accedere alla nuova risorsa VM dal servizio Web di gestione OData, è necessario aggiornare il file RbacConfiguration. XML per consentire l'accesso al modulo di Windows PowerShell per Hyper-V, come descritto in [configurazione dell'autorizzazione basata sui ruoli](./configuring-role-based-authorization.md). Inoltre, sarà necessario riavviare il servizio Web.