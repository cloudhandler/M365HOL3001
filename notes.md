1. [] Switch to @lab.VirtualMachine(VictimPC).SelectLink and log in with the password +++@lab.VirtualMachine(VictimPC).Password+++.

1. [] Switch to @lab.VirtualMachine(AdminPC).SelectLink and log in with the password +++@lab.VirtualMachine(AdminPC).Password+++.

1. [] Switch to @lab.VirtualMachine(ContosoDC).SelectLink and log in with the password +++@lab.VirtualMachine(ContosoDC).Password+++.

1. [] Switch to @lab.VirtualMachine(Scanner01).SelectLink and log in with the password +++@lab.VirtualMachine(Scanner01).Password+++.

1. [] Switch to @lab.VirtualMachine(Client01).SelectLink and log in with the password +++@lab.VirtualMachine(Client01).Password+++.

1. [] Switch to @lab.VirtualMachine(Client02).SelectLink and log in with the password +++@lab.VirtualMachine(Client02).Password+++.

1. [] Switch to @lab.VirtualMachine(Client03).SelectLink and log in with the password +++@lab.VirtualMachine(Client03).Password+++.

1. [] Log in using the credentials below:

	+++@lab.CloudCredential(134).Username+++

	+++@lab.CloudCredential(134).Password+++

- Create csv with username and passwords
- Create script to create users in Azure AD
- Create script to remove all licenses from existing users
    Connect-MSOLService
    $tenantfqdn = @lab.cloudcredential(134).TenantName
    $tenant = $tenantfqdn.Split('.')
    $x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
    $x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "$tenant(0):ENTERPRISEPREMIUM", "$tenant(0):EMSPREMIUM"}
- Create script to assign O365 E5 and EMS E5 licenses to only specific users

- Place csv and script on desktop
- Write instructions for running scripts

On Scanner01
Install-module MSonline

https://labondemand.com/AuthenticatedLaunch/48390?providerId=4 

Update AIP Client on Clients and Scanner

Set client systems internet to metered
Activate/rearm all clients and office on adminpc
