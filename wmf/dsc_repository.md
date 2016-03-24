# Separazione dei repository per configurazioni, risorse e report

In questa versione viene offerta tutta la flessibilità necessaria per elaborare pull e report con uno o più server di pull DSC. Ogni endpoint può essere definito separatamente, in modo da poter effettuare il pull delle configurazioni da una sola posizione, il pull delle risorse da un'altra e inviare i report a un'altra posizione ancora. La seguente metaconfigurazione esegue proprio queste operazioni.

```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
    }

    ConfigurationRepositoryWeb Configurations
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```

È anche possibile usare questi elementi in qualsiasi combinazione. La metaconfigurazione seguente consente di configurare un nodo di destinazione in modalità push, ma il nodo effettuerà il pull delle risorse non installate da un 'server di pull DSC' e invierà i report di stato a un altro 'server di pull DSC'.


```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "Push";
        RebootNodeIfNeeded = $true;
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```<!--HONumber=Mar16_HO2-->
