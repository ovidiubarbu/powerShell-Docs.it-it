---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Registry DSC
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953078"
---
# <a name="dsc-registry-resource"></a>Risorsa Registry DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **Registry** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i valori e le chiavi del Registro di sistema in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Key |Indica il percorso della chiave del Registro di sistema per cui si vuole specificare un determinato stato. Questo percorso deve includere l'hive. |
|ValueName |Indica il nome del valore del Registro di sistema. Per aggiungere o rimuovere una chiave del Registro di sistema, specificare questa proprietà come stringa vuota, senza specificare **ValueType** o **ValueData**. Per modificare o rimuovere il valore predefinito di una chiave del Registro di sistema, specificare questa proprietà come stringa vuota e specificare anche **ValueType** o **ValueData**. |
|Force |Se la chiave del Registro di sistema è presente, **Force** la sovrascrive con il nuovo valore. Se si elimina una chiave del Registro di sistema con sottochiavi il valore deve essere `$true`. |
|Hex |Indica se i dati verranno espressi in formato esadecimale. Se questa proprietà è specificata, i dati con valori DWORD o QWORD vengono presentati in formato esadecimale. La proprietà non è valida per altri tipi. Il valore predefinito è `$false`. |
|ValueData |Dati per il valore del Registro di sistema. |
|ValueType |Indica il tipo di valore. I tipi supportati sono: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (REG_DWORD a 32 bit), **Qword** (REG_QWORD a 64 bit), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ). |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se la chiave e il valore esistono. Impostare questa proprietà su **Present** per assicurarsi che esistano. Impostare questa proprietà su **Absent** per assicurarsi che non esistano. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

Questo esempio garantisce che sia presente una chiave denominata "ExampleKey" nell'hive **HKEY\_LOCAL\_MACHINE**.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> La modifica di un'impostazione del Registro di sistema nell'hive `HKEY_CURRENT_USER` richiede l'esecuzione della configurazione con le credenziali dell'utente anziché come il sistema. È possibile usare la proprietà **PsDscRunAsCredential** per specificare le credenziali utente per la configurazione. Per un esempio, vedere [Esecuzione di DSC con le credenziali dell'utente](../../../configurations/runAsUser.md).