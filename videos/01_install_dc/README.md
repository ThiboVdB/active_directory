# 01 - Installing the Domain Controller

## PS Remoting
````powershell
# On Server
Enable-PSRemoting


# On Client

Start-Service winrm

# Not necessary when client is part of domain
get-item wsman:\localhost\Client\TrustedHosts
set-item wsman:\localhost\Client\TrustedHosts -value {ip}

New-PSSession -ComputerName {ip} -Credential (Get-Credential)
Enter-PSSession {id}
````

## Domain Controller things


1. Sconfig

- change the hostname
````powershell
````

- assign static IP
````powershell

````
- change DNS server to own IP (of DC)
````powershell
Get-NetIPAddress -IPAddress {ip}
Set-DnsClientServerAddress -InterfaceIndex {index} -ServerAddresses {ip}
````

2. Install ADDS

````powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Import-Module ADDSDeployment
Install-ADDSForest
````

## Join domain - client
````powershell
Add-Computer -DomainName {domainname} -Credential (Get-Credential) -Force -Restart
````

