#### Experimewnts with MSSQL in k3s

Install MSSQL in Kubernetes

    $ kubectl apply -k k3s/

Use PowerShell Module for
[SqlServer](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-manage-powershell-core?view=sql-server-ver15)

    > Install-Module -Name SqlServer
    > Import-Module SqlServer
    > Get-Module -Name SqlServer
    > $cred = Get-Credential # see ./k3s/deployment.yaml
    > Get-SqlInstance -ServerInstance $K3S_SERVICE_IP -Credential $cred
