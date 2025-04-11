# README

```
auxiliary/scanner/http/azure_ad_login
```

```
# Import the Azure AD PowerShell module:
Import-Module -Name Azure
# List the cmdlets provided by the module (750+):
Get-Command -Module Azure 
Add-AzureAccount
Get-AzureAccount
Get-AzureSubscription

# Import the Azure AD PowerShell module for MSOnline:
Import-Module -Name MSOnline
# List the cmdlets provided by the MSOnline module:
Get-Command -Module MSOnline

# Connect and authenticate to Azure AD, where your username will
# be similar to '<yourusername>@<yourdomain>.onmicrosoft.com':
$creds = Get-Credential
Connect-MsolService -Credential $creds


# Get subscriber company contact information:
Get-MsolCompanyInformation


# Get subscription and license information:
Get-MsolSubscription | Format-List *
Get-MsolAccountSku   | Format-List *


# Get Azure AD users:
Get-MsolUser


# Get list of Azure AD management roles:
Get-MsolRole


# Show the members of each management role:
Get-MsolRole | ForEach { "`n`n" ; "-" * 30 ; $_.Name ; "-" * 30 ; Get-MsolRoleMember -RoleObjectId $_.ObjectId | ForEach { $_.DisplayName } }
```

https://securitycafe.ro/2022/04/29/pentesting-azure-recon-techniques/