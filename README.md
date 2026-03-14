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
The installation of Active Directory Domain Services only prepares the server for directory services. The server must still be promoted to a Domain Controller before it can manage users, computers,and authentication.

<h2>Promote This Server to a Domain Controller</h2>

<p>
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
This step begins the second stage of the deployment. The server now has the AD DS role installed, and this post-deployment task starts the process of creating the domain and promoting the server into a Domain Controller.

<h2>Configure a New Forest</h2>

<p>
<img width="1536" height="1024" alt="LabA21" src="https://github.com/user-attachments/assets/6f7cc0cb-cf7e-4a65-94f3-800f1bbc68c1" />
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
This step confirms that Active Directory has been successfully deployed. At this point, the server is no longer just a Windows Server VM — it is now a working Domain Controller capable of managing the domain.

<h2>Verify Server Manager After Restart</h2>

<p>
<img width="1536" height="1024" alt="LabA24" src="https://github.com/user-attachments/assets/c5d67c88-96e7-4b02-ad9b-924d88d4f93f" />
</p>
<p>
Steps:
  
Logged back into dc-1 after the restart.
Opened Server Manager.
Reviewed the dashboard.
Confirmed that AD DS and DNS were now installed server roles.
Verified that the server was ready for Active Directory administration.

Explanation
This step confirms that the reboot completed successfully and that the new Domain Controller roles are active. DNS and AD DS are both essential for managing a Windows domain environment.

<h2>Verify the Domain in Active Directory Users and Computers/h2>

<p>
<img width="1536" height="1024" alt="LabA26" src="https://github.com/user-attachments/assets/32aeaa00-4f23-4ac9-8cb9-262cef558387" />

</p>
<p>
Steps:

Opened Server Manager.
Clicked Tools.
Selected Active Directory Users and Computers.
Waited for the management console to open.
Expanded the left-side pane.
Located the newly created domain.
Expanded the domain to view the default containers, such as:
Users
Computers
Domain Controllers

Explanation
This confirms that the domain was created successfully and that the Active Directory structure is now available for administration. This is one of the first places an IT administrator checks after promoting a Domain Controller.


<h2> Create the _EMPLOYEES Organizational Unit</h2>

<img width="1536" height="1024" alt="LabA28" src="https://github.com/user-attachments/assets/ea90c386-6d5f-4d06-b9cc-578965a8a223" />
</p>
<p>
Step:
  
In Active Directory Users and Computers, right-clicked the domain name.
Selected New.
Clicked Organizational Unit.
Entered the name:
 _EMPLOYEES
Left Protect container from accidental deletion checked.
Clicked OK.

Explanation
Organizational Units are used to organize users and computers inside Active Directory. This makes administration easier and allows policies to be applied to specific groups of objects. Creating OUs is a common best practice in IT environments.


<h2>Join Client-1 to the Domain</h2>

<p>
<img width="1536" height="1024" alt="LabA31" src="https://github.com/user-attachments/assets/035951ca-779a-4108-8b15-5cf32d8f3e8d" />
</p>
<p>
Step:
  
Logged into Client-1.
Opened Settings.
Navigated to System > About.
Selected the option to rename the PC or join a domain/workgroup.
Opened the Computer Name/Domain Changes window.
Selected Domain.
Entered the domain name:
 mydomain.com
Clicked OK.
Entered domain administrator credentials when prompted.
Accepted the domain join.
Confirmed the successful domain join message.

Explanation
Joining the client machine to the domain allows it to be managed through Active Directory. In a business environment, this is how workstations become part of the company network and can use centralized authentication and policy settings.


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


