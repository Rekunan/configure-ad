# Active Directory Deployed in the Cloud (Azure)

This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

## Operating Systems Used

- Windows Server 2022
- Windows 10 (21H2)

## Deployment and Configuration Steps

- Open the `Server Manager Dashboard`

![](https://safe.reku.me/B51byw0c9zzH.png)
- Click on `Add roles and features`
- Keep pressing `Next` until `Server Roles`
- Check `Active Directory Domain Services`

![](https://safe.reku.me/oAsnoXVo0HrQ.png)
- Click on `Add Features`
- Select `Active Directory Domain Services` > Next > Next > Next > Now select `Restart the destination server automatically if required` and click `Install`:

![](https://safe.reku.me/TSTeDv1QXZDK.png)
- Click on the flag icon at the top-right 
- Click `Promote this server to a domain controller`

![](https://safe.reku.me/gK911epmpuP7.png)
- Click on `Add new forest`
- Type in your domain in `Root domain name` (`mydomain.com` here)

![](https://safe.reku.me/zgx5Dt4tm48e.png)
- Click on `Next`
- Type in a password

![](https://safe.reku.me/2hPoNyPELkSF.png)
- Click on `Next` until `Prerequisites Check`

![](https://safe.reku.me/vqDXcGDjc8pI.png)
- Click `Install`
- The machine will now restart
- Sign back in using `your domain\username`, and `your password` (`mydomain.com\labuser` here)

![](https://safe.reku.me/IOABc8ntLEZ0.png)
- In the start search bar, search for `Active Directory Users and Computers`

![](https://safe.reku.me/oAMLRMfwwoF2.png)
- Right click on `mydomain.com`
- Click on `New` > `Organizational Unit`
- Name it (`_EMPLOYEES` here)
- Same steps to create an `Organizational Unit` (filled out here)

![](https://safe.reku.me/eCKZ6OEUOeXY.png)
- Right-clicking on `_ADMINS` 
- Click on `New` > `User`
- Fill appropriately (`_ADMINS` here)

![](https://safe.reku.me/K5paYu5l36qm.png)
- Create a password
- (optional) Uncheck `User must change password at next logon`
- (not recommended, just for lab) Check `Password never expires`

![](https://safe.reku.me/bKT25FTmznwT.png)
- Click on `Next` until done
- Right-click on the User's name
- Click on `Properties` > `Member Of` > `Add...` > Enter `domain admins` > `Check Names` > `OK` > `Apply` > `OK`

![](https://safe.reku.me/PRipy7yZ8nEU.png)
- Log out of DC
- Log back in using the user's credentials (Jane's here)

![](https://safe.reku.me/kiTQ6CljWzM9.png)
-  Also log into a client computer (client-1 VM here)
- Right-click the start menu
- Click on`Systems` > `Rename this PC (advanced)` > `Change` > `Domain`
- Type in your domain (`mydomain.com` here)
- Click `OK`

![](https://safe.reku.me/chgS6jAO8OhO.png)
- Enter in your admin credentials (Jane's here)

![](https://safe.reku.me/UUDH9RiHILUk.png)
- Click on `OK`
- It will now restart
- The client pc is now a member of the domain.
- To check, in the DC machine start seach bar, search for `Active Directory Users and Computers` > your doman (`mydomain.com` here) > `Computers` > client pc (`client-1` here) should be listed

![](https://safe.reku.me/g5LUHiU250Q3.png)
- Create OU's as necessary (`_CLIENTS` here)
- Then drag and drop client pc's from `computers` to respective OU's (`_CLIENTS` here)

![](https://safe.reku.me/3WeEh7UXUGzh.png)

You have now implemented Active Directory.