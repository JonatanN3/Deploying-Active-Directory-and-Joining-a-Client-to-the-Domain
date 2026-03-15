<p align="center">
<img width="310" height="163" alt="image" src="https://github.com/user-attachments/assets/bb4c5c16-a0ae-4d4e-b1cc-c25894632644" />

<h1>Deploying Active Directory and Joining a Client to the Domain</h1>
After preparing the Azure infrastructure, this section focuses on deploying Active Directory Domain Services. The Windows Server virtual machine is promoted to a Domain Controller, creating the central directory service for the environment. After the domain is established, Active Directory is validated, an Organizational Unit is created for structured management, and the Windows client system is joined to the domain.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop Protocol (RDP)
- Active Directory Domain Services (AD DS)
- Active Directory Users and Computers (ADUC)
- DNS
  
<h2>Operating Systems Used </h2>

- Windows Server 2022 (Datacenter Azure Edition Hotpatch-x64 Gen2)
- Windows 11 Pro (Version 25H2-x64)

<h2>Server Manager Dashboard</h2>

<img width="1536" height="1024" alt="LabA1" src="https://github.com/user-attachments/assets/46116115-7809-4cd5-87a7-7ffcb761e8ef" />
</p>
<p>
Steps:
  
- Launch the Windows Server virtual machine **dc-1**.
- Sign into the server using administrative credentials.
- Wait for the desktop environment to finish loading.
- Open **Server Manager**.
- Review the dashboard to confirm the server is available for configuration.
- Prepare to begin installing the Active Directory Domain Services role.

**Explanation:**
This shows the starting point of the server configuration process. Server Manager is the primary tool used to install roles and features on Windows Server, including Active Directory Domain Services.

<h2>Select Active Directory Domain Services</h2>

<img width="1536" height="1024" alt="LabA4" src="https://github.com/user-attachments/assets/2d816114-175d-43f2-908d-af886d61575b" />
</p>
<p>
Steps:
  
- Open **Server Manager** on **dc-1**.
- Click **Manage** in the top-right corner.
- Choose **Add Roles and Features**.
- Proceed through the wizard until reaching the Server **Roles page**.
- Locate **Active Directory Domain Services** in the list of available roles.
- Check the box for **Active Directory Domain Services**.
- Review the description shown on the right side of the wizard.
- Prepare to continue with the required supporting features.

**Explanation:**
This step selects the core server role required to build an Active Directory environment. Choosing Active Directory Domain Services allows the server to later be promoted into a Domain Controller.

<h2>Confirm Installation Selections</h2>

<img width="1536" height="1024" alt="LabA10" src="https://github.com/user-attachments/assets/0b505116-9503-4e42-981f-7e06595d96be" />
</p>
<p>
Steps:
  
- Open **Server Manager** on **dc-1**.
- Click **Manage** in the top-right corner.
- Choose **Add Roles and Features**.
- Proceed through the wizard until reaching **Server Roles**.
- Select **Active Directory Domain Services**.
- Accept the additional required features when prompted.
- Continue through the wizard until reaching **Confirm installation selections**.
- Review the selected roles and features, including:<br>
  **Active Directory Domain Services**<br>
  **Group Policy Management**<br>
  **Remote Server Administration Tools**<br>
- Check  **Restart the destination server automatically if required**.
- Click  **Install**.

**Explanation:**
This represents the starting point of configuring the server. The Server Manager dashboard in Windows Server is used to install and manage server roles and features. One of the key roles installed through this tool is Active Directory, which allows the server to function as a domain controller.

<h2>AD DS Installation Complete</h2>
  
<img width="1536" height="1024" alt="LabA13" src="https://github.com/user-attachments/assets/f021bed9-0ed0-47f4-966d-d7b6ae1e6288" />
</p>
<p>
Steps:
  
- Wait for the role installation process to finish.
- Review the completion message in the wizard.
- Confirm that the message indicated:
- **Configuration required**
- **Installation succeeded on dc-1**
- Read the notice explaining that further steps are needed to make the machine a domain controller.
- Locate the link:
- **Promote this server to a domain controller**
- Prepare to continue post-deployment configuration.

**Explanation:**
After installing the Active Directory Domain Services role, a domain is not created automatically. The role is now available on the server, but the system must still be promoted to a Domain Controller before it can manage users, computers, and authentication within the network.

<h2>Promote This Server to a Domain Controller</h2>

<img width="1536" height="1024" alt="LabA14" src="https://github.com/user-attachments/assets/f404e925-9fd2-420b-9db1-de5e85483b2d" />
</p>
<p>
Steps:

- Go back to the **Server Manager** dashboard after the AD DS role finished installing.
- Observe the notification flag in the upper-right corner.
- Click the notification flag.
- Review the post-deployment message indicating that configuration is required for Active Directory Domain Services on **dc-1**.
- Locate the option:
- **Promote this server to a domain controlle**r
- Select the promotion link to begin the Active Directory Domain Services Configuration Wizard.

**Explanation:**
Promoting the server to a Domain Controller configures the server to run Active Directory and manage the domain. This allows the server to control user accounts, computers, and security policy across the network.

<h2>Configure a New Forest</h2>

<img width="1536" height="1024" alt="LabA15" src="https://github.com/user-attachments/assets/15e3dfd9-26ad-47cb-bcfa-97c61cbd6e44" />
</p>
<p>
Steps:
  
- Open the **Active Directory Domain Services Configuration Wizard** from Server Manager.
- Review the available deployment options.
- Select **Add a new forest.**
- Click into the **Root domain name** field.
- Type the domain name:
- **mydomain.com**
- Ensure that the new forest option was selected.
- Click **Next** to continue.

**Explanation:**
During this step, a new Active Directory forest is created and the root is defined. The forest serves as the top-level container of the directory structure, while the root domain acts as the primary administrative control point for the network.

<h2>Configure Domain Controller Options</h2>

<img width="1536" height="1024" alt="LabA24" src="https://github.com/user-attachments/assets/c5d67c88-96e7-4b02-ad9b-924d88d4f93f" />
</p>
<p>
Steps:
  
- Proceed to the **Domain Controller Options** page.
- Review the default **Forest functional level.**
- Review the default **Domain functional level.**
- Verify that the **DNS server** option was selected.
- Verify that the **Global Catalog (GC)** option was enabled.
- Left Read only **domain controller (RODC)** unselected.
- Type a **Directory Services Restore Mode (DSRM)** password.
- Confirm the DSRM password in the second field.
- Select **Next** to continue.

**Explanation**
This step defines important domain controller settings. It enables DNS integration, confirms the server’s role in the domain, and sets the DSRM password used for recovery and maintenance of Active Directory services.

<h2>Prerequisites Check</h2>

<img width="1536" height="1024" alt="LabA19" src="https://github.com/user-attachments/assets/e06971cc-688c-4e6d-a05b-4f7903eb35e4" />
</p>
<p>
Steps:

Proceed through the configuration wizard after reviewing the deployment options.
Reach the **Prerequisites Check** page.
Wait while Windows validates the configuration.
Review the results shown in the wizard.
Varify the message stated:
**All prerequisite checks passed successfully**
Review the warning messages listed in the results pane.
Confirm that no blocking errors prevented the promotion process.
Prepare to click **Install.**

**Explanation:**
At this stage, the server is evaluated for promotion to a Domain Controller. The wizard reviews configuration requirements, flags potential issues, and ensures everything is properly set before proceeding with the installation.


<h2>Domain Controller Promotion Complete</h2>

<img width="1536" height="1024" alt="LabA21" src="https://github.com/user-attachments/assets/2cfd0841-77d9-41c4-970e-0c1a57b19257" />
</p>
<p>
Step:
  
Click **Install** on the Prerequisites Check page.
Wait while Active Directory is configured.
Review the **Results** page after the promotion process completes
Confirm the message stated:
**This server was successfully configured as a domain controller**
Observe the notification indicating that the computer was about to be signed out.
Read the restart message explaining that the server would reboot because Active Directory Domain Services had been installed.
Allow the restart process to continue.

**Explanation**
This step confirms that the server was successfully promoted to a Domain Controller. A restart is required to finalize the Active Directory configuration and bring the domain services online.


<h2>Server Manager After Restart</h2>

<img width="1536" height="1024" alt="LabA24" src="https://github.com/user-attachments/assets/f79503ae-dceb-4519-b9ed-3aca659d8be1" />
</p>
<p>
Step:
  
- Wait for **dc-1** to restart after Domain Controller promotion.
- Log back into the server.
- Launch **Server Manager.**
- Review the dashboard after the reboot completed.
- Verify that the left navigation pane now displayed:
- **AD DS**
- **DNS**
- Verifiy that the new roles appeared as active components of the server.

**Explanation:**
This step shows that the server restart completed successfully and that Active Directory Domain Services and DNS are now installed as active server roles. This also indicates that the domain controller configuration is in place.

<h2>Verify Client-1 Appears in Active Directory</h2>

<img width="1536" height="1024" alt="LabA35" src="https://github.com/user-attachments/assets/46f34c9e-d331-4756-87db-7bfbec444b41" />
</p>
<p>
Step:
  
Returned to Active Directory Users and Computers on the Domain Controller.
Expanded the domain structure.
Clicked the Computers container.
Looked for Client-1 in the object list.
Confirmed that its object type was Computer.
Verified that the client had successfully joined the domain.

Explanation
This final verification step confirms that the client machine is now part of the Active Directory environment. From an IT support perspective, this is an important check because it proves the domain join worked correctly and the client can now be managed through the domain.


<h2>Summary</h2>
  
By the end of this section, the Windows Server machine had been successfully promoted to a Domain Controller, the new domain had been verified in Active Directory, an Organizational Unit had been created for better organization, and the Windows client machine had been joined to the domain. These steps established the core Active Directory environment needed for user, computer, and policy management.

.


