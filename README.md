<p align="center">
<img src="https://github.com/user-attachments/assets/21fe72e9-5880-4222-9f1c-9f03d8b0a315" alt="Microsoft Active Directory Logo"/>
</p>

<!--
<img src="https://github.com/user-attachments/assets/21fe72e9-5880-4222-9f1c-9f03d8b0a315" height="30%" width="30%"/>
-->

# Chapter 3: Install Active Directory on Windows 2022 Server

- On the Windows 2022 Server we will install Active Directory Domain Services using the `Server Manager's` `Add Roles and Features Wizard`.
- Then we will promote our Windows 2022 Server as a Domain Controller as part of the post-deployment configuration.
- Finally, we will restart the server and log back into the server using our Domain\Username (`IanBates.com\Admin-DC`) instead of a simple username.

---

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022 Datacenter Azure edition


<h2>High-Level Configuration Steps</h2>

- Part 1: [Install Active Directory Domain Services](https://github.com/ian-bates-it/Install-Active-Directory-on-Windows-2022-Server?tab=readme-ov-file#install-active-directory-domain-services)
- Part 2: [Promote Controller As Domain Controller](https://github.com/ian-bates-it/Install-Active-Directory-on-Windows-2022-Server?tab=readme-ov-file#promote-controller-as-domain-controller)
- Step 3: [Restart Server and Sign in with Domain\Username (`IanBates.com\Admin-DC`)](https://github.com/ian-bates-it/Install-Active-Directory-on-Windows-2022-Server?tab=readme-ov-file#restart-server-and-sign-in-with-domainusername-ianbatescomadmin-dc)



<h2>Prerequisites</h2>

1. Complete [Chapter 1 of this series, Creating a Windows 10 Pro and Windows 2022 Server Virtual Machines in Azure.](https://github.com/ian-bates-it/Azure-Virtual-Machine-Setup)

2. Complete [Chapter 2 of this series, Configuring the DNS settings for our Windows 10 Pro (Client) and Windows 2022 Server (Domain Controller).](https://github.com/ian-bates-it/Azure-Controller-Client-Configuration)




<br />
<br />

---

<h1>Part 1:</h1>

<h2>Install Active Directory Domain Services</h2>

- We will remote into our Windows 2022 Server with Remote Desktop.
- Then we will use the `Server Manager` to install Active Directory as outlined below.

---
<br />

<h3>Step 1: Add Roles and Features </h3>

- Remote into the Windows 2022 Server using Remote Desktop.
- In the Server Manager > Dashboard click on the option for `Add roles and features` as shown below.
- This will open up the `Add Roles and Features Wizard`.


<img src="https://github.com/user-attachments/assets/f009f313-d990-4967-85c3-2e8912a52d39" height="80%" width="80%" />


---
<br />

<h3>Use the Add Roles and Features Wizard</h3>


---
<br />
<h4>Before You Begin Tab</h4>

- Click the `Next` Button to continue

  <img src="https://github.com/user-attachments/assets/1be9d660-d6f5-4bf9-998a-353e5264fd0a" height="80%" width="80%" />


---
<br />
<h4>Installation Type</h4>

- Select `Role-based or feature-based installation` as shown below.

  <img src="https://github.com/user-attachments/assets/16b7e287-370d-4362-8d3a-46eb424b735c" height="80%" width="80%" />


---
<br />
<h4>Server Selection</h4>


- The only server option should be our Azure Windows 2022 Server.
- Click `Next` to continue as shown below.

  <img src="https://github.com/user-attachments/assets/a26fa7bf-fb49-46fc-bfa5-7a9b953b2c70" height="80%" width="80%" />




---
<br />
<h3>Server Roles</h3>

- Select the `Active Directory Domain Services` as shown below.


  <img src="https://github.com/user-attachments/assets/d5e122d7-3020-4fc5-9794-3e04f7f3eeeb" height="80%" width="80%" />



<br />
<br />
- Accept the pop-up box as shown below.
- Click `Add Features`.


  <img src="https://github.com/user-attachments/assets/4e7b1c10-e4e3-4ff6-95ba-8bb17f35bc50" height="50%" width="50%" />



---
<br />
<h3>Features</h3>

- Accept the default features and click `Next` as shown below.


  <img src="https://github.com/user-attachments/assets/ac71ec87-eb29-4071-9579-f735d9d33a69" height="80%" width="80%" />




---
<br />
<h3>Active Directory Domain Services</h3>

- Active Directory Domain Services stores information about users, computers, and other devices on the network.
- Active Directory Domain Services requires a DNS server to be installed on the network.
- If you do not have a DNS server installed, you will be prompted to install the DNS Server role on this machine. 
- Review the message and click `Next` to continue.


  <img src="https://github.com/user-attachments/assets/f5da0087-03fc-4876-a800-1cf112dae7d5" height="80%" width="80%" />



---
<br />
<h3>Confirmation</h3>


- Review the confirmation of the roles, role services and features to be installed on our Windows 2022 Server.

1. Click the `Restart the destination server automatically if required` check box.
2. Click `Yes` to the restart notification pop-up menu.
3. Click `Install` to complete the installation as shown below.

  <img src="https://github.com/user-attachments/assets/bad9c85d-cd9b-4fa5-90b1-b65fdc356754" height="80%" width="80%" />



---
<br />
<h4>AD Roles and Features Installation Complete</h4>

- After the installation is complete, click the `Close` button and restart your Windows 2022 Server.

  <img src="https://github.com/user-attachments/assets/ddba9c59-450e-4e87-8a8f-e3de898bdaab" height="80%" width="80%" />


<br />
<br />

---

<h1>Part 2:</h1>

<h2>Promote Controller as Domain Controller</h2>

<!--
(4:13)
-->

- Active directory is installed, but it is not yet set up as a domain controller. 
- So now we will configure our Windows 2022 Server as a domain controller in a new forest. 


- Remote back into the Windows 2022 Server and log in with your administrator account.
- In the Server Manager Dashboard, click the flag with a warning sign.
- Select the link `Promote this server to a domain controller` as shown below.


  <img src="https://github.com/user-attachments/assets/312c346f-1dce-44ae-8842-8aeda7077bfb" height="60%" width="60%" />



---
<br />
<h3>Deployment Configuration</h3>

1. Click the option for `Add a new forest`
2. Enter in any domain name. I used `IanBates.com`
3. Click the `Next` button as shown below.

  <img src="https://github.com/user-attachments/assets/d909bedc-afc7-4129-b635-4f83704e2a3e" height="60%" width="60%" />


---
<br />
<h3>Domain Controller Options</h3>

- Leave all the default options selected.
- Add a password for the <b>Directory Services Restore Mode (DSRM)</b>.
- Click `Next` as shown below.

  <img src="https://github.com/user-attachments/assets/6f44ee6e-745d-49ec-bd6c-8689fe12afe7" height="60%" width="60%" />


---
<br />
<h3>DNS Options</h3>

- Uncheck the `Create DNS delegation` checkbox.
- Click `Next` as shown below.

  <img src="https://github.com/user-attachments/assets/330c5a1c-2773-42c4-9797-5bf2651962b7" height="60%" width="60%" />


---
<br />
<h3>Additional Options</h3>

- You can adjust your NetBIOS name.
- By default, the Active Directory configuration wizard will use your domain name before the domain extension.
- Here, I went with `IANBATES` as my NetBIOS name.
- Click `Next` to continue.

  <img src="https://github.com/user-attachments/assets/70fb9431-3618-49c1-b52a-e8b3f4bb139f" height="80%" width="80%" />


---
<br />
<h3>Paths</h3>

- Accept the default paths for the `Database folder`, `Log files folder` and `SYSVOL folder` and click `Next` as shown below.

  <img src="https://github.com/user-attachments/assets/beff2c08-f5e7-4a6d-a5b2-4bc97da0a861" height="60%" width="60%" />


---
<br />
<h3>Review Options</h3>

- Review your selections.
- Click `Next` to continue.


  <img src="https://github.com/user-attachments/assets/2d48310d-f02a-4f9b-bbbd-cf58de9ba296" height="60%" width="60%" />



---
<br />
<h3>Prerequisites Check</h3>

- Prerequisites need to be validated before Active Directory Domain Services can be installed on our Windows 2022 Server.
- After the prerequisites check is completed, select `Install` to continue as shown below.

  <img src="https://github.com/user-attachments/assets/78a1b435-2db9-4ee2-a12f-0b737ec9d2fd" height="80%" width="80%" />


<br />
<br />

---

<h1>Part 3:</h1>

<h2>Restart Server and Sign in with Domain\Username (`IanBates.com\Admin-DC`)</h2>


---
<br />
<h3>Restart Windows 2022 Server</h3>

- After installation is complete, the Windows 2022 Server needs to be restarted.
- Accept the notifications and let the server restart. This will disconnect your remote desktop connection.

  <img src="https://github.com/user-attachments/assets/f1026da9-c028-4a68-b7af-cf26c22e04ba" height="80%" width="80%" />


---
<br />
<h3>Sign Back Into Windows 2022 Server with your new Domain</h3>


- Because our Windows 2022 Server is now a Domain Controller, we have to specify the context to which we want to log into from the Remote Desktop client.
- The user accounts exist in a domain.
- So now we have to specify the domain name that we added as the domain controller above.
- In this example, my domain is `IanBates.com` and my administrator username is `Admin-DC`.
- So in my Remote Desktop client, I will enter `IanBates.com\Admin-DC` into the User name field as shown below.

  <img src="https://github.com/user-attachments/assets/002ed335-7a7c-4337-b9ef-6477fe9b8280" height="40%" width="40%" />




