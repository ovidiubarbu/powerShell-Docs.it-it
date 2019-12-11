---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Package DSC
ms.openlocfilehash: efac07b4b051564cadd5aa1542a6afda6cd453ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953148"
---
# <a name="dsc-package-resource"></a>Risorsa Package DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **Package** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per installare o disinstallare pacchetti, ad esempio i pacchetti di Windows Installer e setup.exe, nei nodi di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Nome |Indica il nome del pacchetto per cui si vuole specificare un determinato stato. |
|Path |Percorso in cui si trova il pacchetto. |
|ProductId |Indica l'ID prodotto che identifica in modo univoco il pacchetto. |
|Arguments |Elenca una stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato. |
|Credential |Fornisce l'accesso al pacchetto in un'origine remota. Questa proprietà non viene usata per installare il pacchetto. Il pacchetto viene sempre installato nel sistema locale. |
|LogPath |Indica il percorso completo in cui il provider deve salvare un file di log per installare o disinstallare il pacchetto. |
|ReturnCode |Indica il codice restituito previsto. Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se il pacchetto è installato. Impostare questa proprietà su **Absent** per assicurarsi che il pacchetto non sia installato (o disinstallare il pacchetto se è installato). Impostarla su **Present** per assicurarsi che il pacchetto sia installato. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

Questo esempio esegue il programma di installazione MSI che si trova nel percorso specificato e che ha l'ID prodotto indicato.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```