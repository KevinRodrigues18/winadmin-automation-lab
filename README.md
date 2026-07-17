# winadmin-automation-lab
A Homelab project to learn and document on scripting and automation of tasks as an admin, from bulk user creation in AD to resetting passwords and checking disk space across machines.

Click [here](Setup.md) for Prerequisites and Setup of Windows Server and AD.

# Bulk User Creation in Active Directory using Powershell
1.Create a `.csv' file and enter User details in the format below
- The Fields `SAMAccount1`, `FirstName`, `LastName` must be mandatory.
- Alternatively u can open the file in nmicrosoft Excel for a clearer view.
```
SamAccountName,FirstName,LastName,Phone,Address,OU,Password
svsmith,Silvester,Smith,"(555) 234-5678","104 Willow Lane, Springfield, IL 62701","OU=Bulk Users,DC=homelab,DC=local",P@ssword123!
anbrad,Anna,Bradley,"(555) 876-5432","782 Maple Avenue, Austin, TX 78701","OU=Bulk Users,DC=homelab,DC=local",SecurePass456!
bdtylor,Brandon,Tyler,"(555) 432-1098","435 Pine Road, Seattle, WA 98101","OU=Bulk Users,DC=homelab,DC=local",Brndon1@1997
glnmlr,Glenn,Miller,"(555) 678-9012","219 Birch Street, Orlando, FL 32801","OU=Bulk Users,DC=homelab,DC=local",PassMiller#321
```

<br><br>
2.Run the following script inside your PowerShell (admin)





