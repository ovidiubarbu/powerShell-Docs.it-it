---
title: Parametri dinamici del cmdlet provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359950"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Parametri dinamici del cmdlet del provider

I provider possono definire parametri dinamici che vengono aggiunti a un cmdlet del provider quando l'utente specifica un determinato valore per uno dei parametri statici del cmdlet. Ad esempio, un provider può aggiungere parametri dinamici diversi in base al percorso specificato dall'utente quando chiama il `Get-Item` o `Set-Item` cmdlet del provider.

## <a name="dynamic-parameter-methods"></a>Metodi di parametri dinamici

I parametri dinamici vengono definiti implementando uno dei metodi di parametro dinamici, ad esempio i metodi [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) e [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s. Questi metodi restituiscono un oggetto con proprietà pubbliche decorate con attributi simili a quelli dei cmdlet autonomi. Di seguito è riportato un esempio di implementazione del metodo [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) tratto dal provider di certificati:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

A differenza dei parametri statici dei cmdlet del provider, è possibile specificare le caratteristiche di questi parametri nello stesso modo in cui i parametri sono definiti nei cmdlet autonomi. Di seguito è riportato un esempio di una classe di parametri dinamici eseguita dal provider di certificati:

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

Di seguito è riportato un elenco dei parametri statici che possono essere usati per aggiungere parametri dinamici.

`Clear-Content` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet Clear-Clear implementando il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

`Clear-Item` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet `Clear-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

`Clear-ItemProperty` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet `Clear-ItemProperty` implementando il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

`Copy-Item` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path`, `Destination`e `Recurse` del cmdlet `Copy-Item` implementando il metodo [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

Cmdlet Get-ChildItem è possibile definire parametri dinamici attivati dal `Path` e `Recurse` parametri del cmdlet `Get-ChildItem` implementando i metodi [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) e [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .

`Get-Content` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet `Get-Content` implementando il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) .

`Get-Item` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet `Get-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

`Get-ItemProperty` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path` e `Name` del cmdlet `Get-ItemProperty` implementando il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

`Invoke-Item` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet `Invoke-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

`Move-Item` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path` e `Destination` del cmdlet `Move-Item` implementando il metodo [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .

`New-Item` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path`, `ItemType`e `Value` del cmdlet `New-Item` implementando il metodo [System. Management. Automation. provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

`New-ItemProperty` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path`, `Name`, `PropertyType`e `Value` del cmdlet `New-ItemProperty` implementando il metodo [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

`New-PSDrive` cmdlet è possibile definire parametri dinamici attivati dall'oggetto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) restituito dal cmdlet `New-PSDrive` implementando il metodo [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item` è possibile definire parametri dinamici attivati dai parametri `Path` e `Recurse` del cmdlet `Remove-Item` implementando il metodo [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

`Remove-ItemProperty` è possibile definire parametri dinamici attivati dai parametri `Path` e `Name` del cmdlet `Remove-ItemProperty` implementando il metodo [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

`Rename-Item` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path` e `NewName` del cmdlet `Rename-Item` implementando il metodo [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

`Rename-ItemProperty` è possibile definire parametri dinamici attivati dai parametri `Path`, `Name`e `NewName` del cmdlet `Rename-ItemProperty` implementando il metodo [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

`Set-Content` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet `Set-Content` implementando il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) .

`Set-Item` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path` e `Value` del cmdlet `Set-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

`Set-ItemProperty` cmdlet è possibile definire parametri dinamici attivati dai parametri `Path` e `Value` del cmdlet `Set-Item` implementando il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

`Test-Path` cmdlet è possibile definire parametri dinamici attivati dal parametro `Path` del cmdlet `Test-Path` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

## <a name="see-also"></a>Vedere anche

[Scrittura di un provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)