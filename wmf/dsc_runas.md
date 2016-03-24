# Supporto di RunAs automatico per le risorse DSC
Supporto per le credenziali RunAs DSC
--------------------------------

La versione di aprile 2015 di WMF 5.0 Preview include il supporto per l'esecuzione di **qualsiasi** risorsa DSC con un set specificato di credenziali tramite la proprietà PsDscRunAsCredential. In questo modo diventano possibili scenari come l'installazione di pacchetti MSI in un contesto utente specifico, l'accesso a hive del Registro di sistema dell'utente, l'accesso a una directory locale specifica dell'utente, l'accesso a una condivisione di rete e così via.

L'esempio seguente mostra come usare la proprietà PsDscRunAsCredential in DSC per modificare il colore di sfondo del prompt dei comandi di un utente.

ChangeCmdBackGroundColor per una configurazione

{

    Node ("localhost")

    {

        Registry CmdPath

        {

            Key = "HKEY\_CURRENT\_USER\\\\Software\\Microsoft\\\\Command Processor"

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = get-credential

        }

    }

}

$configData = @{

AllNodes = @(

@{

NodeName="localhost";

CertificateFile = "C:\\publicKeys\\targetNode.cer"

}

)

}

ChangeCmdBackGroundColor -ConfigurationData $configData

## Problemi noti

In questa versione sono presenti i seguenti problemi noti per la funzionalità delle credenziali RunAs per DSC:

-   La risorsa WindowsProcess non supporta credenziali RunAs.

<!--HONumber=Mar16_HO2-->
