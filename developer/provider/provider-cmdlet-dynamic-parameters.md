---
title: I parametri dinamici di provider cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: 803fe4ae24a4f8022639c5b6d6298100859177ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858357"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Parametri dinamici del cmdlet del provider

I provider possono definire i parametri dinamici che vengono aggiunti a un cmdlet del provider quando l'utente specifica un determinato valore per uno dei parametri statici del cmdlet. Ad esempio, un provider può aggiungere diversi parametri dinamici basati su quali tracciato l'utente specifica quando si chiama il `Get-Item` o `Set-Item` cmdlet del provider.

## <a name="dynamic-parameter-methods"></a>Metodi di parametro dinamico

I parametri dinamici vengono definiti mediante l'implementazione di uno dei metodi di parametro dinamico, ad esempio la [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) e [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)metodi s. Questi metodi restituiscono un oggetto contenente le proprietà pubbliche che sono decorate con attributi simili a quelle dei cmdlet autonomo. Ecco un esempio di un'implementazione del [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metodo eseguito dal provider di certificati:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

A differenza dei parametri statici di cmdlet del provider, è possibile specificare le caratteristiche di questi parametri nello stesso modo che i parametri sono definiti nei cmdlet autonomo. Di seguito è riportato un esempio di una classe di parametri dinamici dal provider di certificati:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Parametri dinamici

Ecco un elenco di parametri statici che può essere utilizzato per aggiungere i parametri dinamici.

`Clear-Content` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametri del cmdlet Clear-Clear implementando il [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) (metodo).

`Clear-Item` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametro del `Clear-Item` cmdlet implementando il [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metodo.

`Clear-ItemProperty` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametro del `Clear-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) (metodo).

`Copy-Item` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path`, `Destination`, e `Recurse` i parametri del `Copy-Item` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) (metodo).

Cmdlet Get-ChildItems è possibile definire i parametri dinamici che vengono attivati dal `Path` e `Recures` i parametri delle `Get-ChildItem` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metodi.

`Get-Content` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametro del `Get-Content` cmdlet implementando il [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) (metodo).

`Get-Item` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametro del `Get-Item` cmdlet implementando il [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metodo.

`Get-ItemProperty` cmdlet è possibile definire i parametri dinamici che vengono attivati dal `Path` e `Name` i parametri delle `Get-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) (metodo).

`Invoke-Item` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametro del `Invoke-Item` cmdlet implementando il [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) (metodo).

`Move-Item` cmdlet è possibile definire i parametri dinamici che vengono attivati dal `Path` e `Destination` i parametri delle `Move-Item` cmdlet implementando il [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) (metodo).

`New-Item` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path`, `ItemType`, e `Value` i parametri del `New-Item` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) (metodo).

`New-ItemProperty` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path`, `Name`, `PropertyType`, e `Value` parametri del `New-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) (metodo).

`New-PSDrive` cmdlet è possibile definire i parametri dinamici attivate dal trigger la [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) oggetto restituito dal `New-PSDrive` cmdlet implementando il [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) (metodo).

`Remove-Item` È possibile definire i parametri dinamici che vengono attivati dal `Path` e `Recurse` i parametri delle `Remove-Item` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) (metodo).

`Remove-ItemProperty` È possibile definire i parametri dinamici che vengono attivati dal `Path` e `Name` i parametri delle `Remove-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) (metodo).

`Rename-Item` cmdlet è possibile definire i parametri dinamici che vengono attivati dal `Path` e `NewName` i parametri delle `Rename-Item` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) (metodo).

`Rename-ItemProperty` È possibile definire i parametri dinamici attivate dal trigger la `Path`, `Name`, e `NewName` i parametri del `Rename-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) (metodo).

`Set-Content` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametro del `Set-Content` cmdlet implementando il [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) (metodo).

`Set-Item` cmdlet è possibile definire i parametri dinamici che vengono attivati dal `Path` e `Value` i parametri delle `Set-Item` cmdlet implementando il [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) (metodo).

`Set-ItemProperty` cmdlet è possibile definire i parametri dinamici che vengono attivati dal `Path` e `Value` i parametri delle `Set-Item` cmdlet implementando il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) (metodo).

`Test-Path` cmdlet è possibile definire i parametri dinamici attivate dal trigger la `Path` parametro del `Test-Path` cmdlet implementando il [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) (metodo).

## <a name="see-also"></a>Vedere anche

[Scrittura di un Provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)