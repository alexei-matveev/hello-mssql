#### Experiments with MSSQL in k3s

Install MSSQL in Kubernetes

    $ kubectl apply -k k3s/

Use PowerShell Module for
[SqlServer](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-manage-powershell-core?view=sql-server-ver15)

    > Install-Module -Name SqlServer
    > Import-Module SqlServer
    > Get-Module -Name SqlServer
    > $cred = Get-Credential # see ./k3s/deployment.yaml
    > Get-SqlInstance -ServerInstance $K3S_MSSQL_IP -Credential $cred

TIL, you can use CoreDNS from outside of the cluster too. First get
the ClusterIP of the kube-dns Service:

    > kubectl get svc kube-dns --namespace=kube-system

and use it to lookup the "mssql" service like this:

    > host mssql.hello-mssql.svc.cluster.local $K3S_KUBE_DNS_IP
