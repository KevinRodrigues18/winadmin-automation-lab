# winadmin-automation-lab
A Homelab project to learn and document on scripting and automation of tasks as an admin, from bulk user creation in AD to resetting passwords and checking disk space across machines.

# Prerequisites
- An installation of the Windows Server 2022 Standard or Data Center Evaluation.
- A static IP addresss for the server.
- Change of Server Name before promoting it to domain controller.

# Setting up AD in Windows Server 2022 
1. Go to Server Manager
2. Click on the Manage Option in the tob right
3. Add Roles & Features
4. Select Role-Based in installation type and select your domain
5. In the Server Roles Tab Select - Active Directory Domain Services
6. Then Click next till the install screen
7. After the installation is complete restart the server.

<img width="50%%" height="50%%" alt="image" src="https://github.com/user-attachments/assets/e1eda5f7-706a-4cce-ae6e-115dab2ff1a9" />

## Promote your server to Domain Controller
Once the installation finishes, click on the yellow notification flag in the top right of Server Manager.
In the Setup Window
Select Add a new forest.
Type in a private domain name for your lab. ex: homelab.local, private.internal etc.

In the Domain Controller Options:
Leave the Functional Levels at Windows Server 2016 (or the highest default version available).
Type in a Directory Services Restore Mode password. (Remember it since its a recovery password)

If you get a delegation warning on the DNS tab ignore it and click next

Additional Options: It will automatically fill in your NetBIOS domain name (e.g., HOMELAB)

Paths / Review Options: Leave the default folder paths for database and logs. 

Click Next, then Next again after the system verifies prerequisites. Install: Click Install.

   
