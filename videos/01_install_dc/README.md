# 01 - Installing the Domain Controller

1. Sconfig
    - change the hostname
    - assign static IP
    - change DNS server to own IP (of DC)

2. Install ADDS

````
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
````