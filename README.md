# winadmin-automation-lab
A Homelab project to learn and document on scripting and automation of tasks as an admin, from bulk user creation in AD to resetting passwords and checking disk space across machines.

Click [here](Setup.md) for Prerequisites and Setup of Windows Server and AD.

# Bulk User Creation in Active Directory using Powershell
1.Create a `.csv' file and enter User details in the format below
- The Fields `SAMAccount1`, `FirstName`, `LastName` must be mandatory.
- You can add or remove fields according to your user preference.
- Alternatively u can open the file in nmicrosoft Excel for a clearer view.
<img width="1877" height="217" alt="image" src="https://github.com/user-attachments/assets/e5d98cb5-36b8-45d7-814d-90f8a3ccc5ff" />  

<br><br>
2.Run the following script inside your PowerShell (admin)
```
# Import the csv file with the proper path and file name you used
$Users = Import-Csv -Path "C:\BulkUsers.csv.txt"

foreach ($User in $Users) {
    # Check if the SamAccountName already exists in Active Directory, if it exists then print a warning and skip creation
    if (Get-ADUser -Filter "SamAccountName -eq '$($User.SamAccountName)'") {

        Write-Warning "Skipping creation: A user account with username '$($User.SamAccountName)' already exists."
    }
    else {
        $SecurePassword = ConvertTo-SecureString $User.Password -AsPlainText -Force

    # Map the CSV fields to the Active Directory (If you added more fields u will need to add it under $UserParam
    $UserParams = @{
        SamAccountName        = $User.SamAccountName
        UserPrincipalName     = "$($User.SamAccountName)@homelab.local"
        GivenName             = $User.FirstName
        Surname               = $User.LastName
        Name                  = "$($User.FirstName) $($User.LastName)"
        OfficePhone           = $User.Phone
        StreetAddress         = $User.Address
        Path                  = $User.OU
        AccountPassword       = $SecurePassword
        Enabled               = $true
        ChangePasswordAtLogon = $false
    }

    try {
        New-ADUser @UserParams
        Write-Host "Successfully created user: $($User.SamAccountName)" -ForegroundColor Green
    }
    catch {
        Write-Error "Failed to create user $($User.SamAccountName): $_"
    }
  }
}
```
if its successfull, it should give an output like this:
```
Successfully created user: svsmith
Successfully created user: anbrad
Successfully created user: bdtylor
Successfully created user: glnmlr
```
3. Confirm the creation of Users in you Active Directory Users and Computers.
<img width="470" height="277" alt="image" src="https://github.com/user-attachments/assets/31fb36d1-bec6-40ed-aa66-75a8da92989e" />






