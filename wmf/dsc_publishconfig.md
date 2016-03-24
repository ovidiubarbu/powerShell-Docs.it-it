# Recapitare un documento di configurazione senza applicarlo

Il cmdlet **Publish-DscConfiguration** copia un file MOF di configurazione in un nodo di destinazione, ma non applica la configurazione. La configurazione viene applicata durante il passaggio di controllo della coerenza successivo o quando si esegue il cmdlet `Update-DscConfiguration`.

```powershell
Publish-DscConfiguration [-Path] <string> [[-ComputerName] <string[]>] [-Force] [-Credential <pscredential>] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]

Publish-DscConfiguration [-Path] <string> -CimSession <CimSession[]> [-Force] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<!--HONumber=Mar16_HO2-->
