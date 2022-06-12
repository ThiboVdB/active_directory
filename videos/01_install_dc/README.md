# 01 - Installing the Domain Controller


````
# On Server
Enable-PSRemoting

# Not necessary when client is part of domain
get-item wsman:\localhost\Client\TrustedHosts
set-item wsman:\localhost\Client\TrustedHosts -value {ip}

# On Client
New-PSSession -ComputerName {ip} -Credential (Get-Credential)
Enter-PSSession {id}
````
---

1. Sconfig
    - change the hostname
````

````

    - assign static IP
````

````
    - change DNS server to own IP (of DC)
    ````
    Get-NetIPAddress -IPAddress {ip}
    Set-DnsClientServerAddress -InterfaceIndex {index} -ServerAddresses {ip}
    ````

2. Install ADDS

````
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Import-Module ADDSDeployment
Install-ADDSForest
````

3. Join domain - client
````
Add-Computer -DomainName {domainname} -Credential (Get-Credential) -Force -Restart
````

