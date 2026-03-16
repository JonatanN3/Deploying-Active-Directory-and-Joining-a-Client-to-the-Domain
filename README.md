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
  
- Launch the Windows Server virtual machine dc-1.
- Sign into the server using administrative credentials.
- Wait for the desktop environment to finish loading.
- Open Server Manager.
- Review the dashboard to confirm the server is available for configuration.
- Prepare to begin installing the Active Directory Domain Services role.

**Explanation:**
This shows the starting point of the server configuration process. Server Manager is the primary tool used to install roles and features on Windows Server, including Active Directory Domain Services.

<h2>Select Active Directory Domain Services</h2>

<img width="1536" height="1024" alt="LabA4" src="https://github.com/user-attachments/assets/2d816114-175d-43f2-908d-af886d61575b" />
</p>
<p>
Steps:
  
- Open Server Manager on dc-1.
- Click Manage in the top-right corner.
- Choose Add Roles and Features.
- Proceed through the wizard until reaching the Server Roles page.
- Locate Active Directory Domain Services in the list of available roles.
- Check the box for Active Directory Domain Services.
- Review the description shown on the right side of the wizard.
- Prepare to continue with the required supporting features.

**Explanation:**
This step selects the core server role required to build an Active Directory environment. Choosing Active Directory Domain Services allows the server to later be promoted into a Domain Controller.

<h2>Confirm Installation Selections</h2>

<img width="1536" height="1024" alt="LabA10" src="https://github.com/user-attachments/assets/0b505116-9503-4e42-981f-7e06595d96be" />
</p>
<p>
Steps:
  
- Open Server Manager on dc-1.
- Click Manage in the top-right corner.
- Choose Add Roles and Features.
- Proceed through the wizard until reaching Server Roles.
- Select Active Directory Domain Services.
- Accept the additional required features when prompted.
- Continue through the wizard until reaching Confirm installation selections.
- Review the selected roles and features, including:<br>
  **Active Directory Domain Services**<br>
  **Group Policy Management**<br>
  **Remote Server Administration Tools**<br>
- Check  Restart the destination server automatically if required.
- Click  Install.

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
- Configuration required
- Installation succeeded on dc-1
- Read the notice explaining that further steps are needed to make the machine a domain controller.
- Locate the link:<br>
  **Promote this server to a domain controller**
- Prepare to continue post-deployment configuration.

**Explanation:**
After installing the Active Directory Domain Services role, a domain is not created automatically. The role is now available on the server, but the system must still be promoted to a Domain Controller before it can manage users, computers, and authentication within the network.

<h2>Promote This Server to a Domain Controller</h2>

<img width="1536" height="1024" alt="LabA14" src="https://github.com/user-attachments/assets/f404e925-9fd2-420b-9db1-de5e85483b2d" />
</p>
<p>
Steps:

- Go back to the Server Manager dashboard after the AD DS role finished installing.
- Observe the notification flag in the upper-right corner.
- Click the notification flag.
- Review the post-deployment message indicating that configuration is required for Active Directory Domain Services on dc-1.
- Locate the option:<br>
  **Promote this server to a domain controller**
- Select the promotion link to begin the Active Directory Domain Services Configuration Wizard.

**Explanation:**
Promoting the server to a Domain Controller configures the server to run Active Directory and manage the domain. This allows the server to control user accounts, computers, and security policy across the network.

<h2>Configure a New Forest</h2>

<img width="1536" height="1024" alt="LabA15" src="https://github.com/user-attachments/assets/15e3dfd9-26ad-47cb-bcfa-97c61cbd6e44" />
</p>
<p>
Steps:
  
- Open the Active Directory Domain Services Configuration Wizard from Server Manager.
- Review the available deployment options.
- Select Add a new forest.
- Click into the Root domain name field.
- Type the domain name:<br>
  **mydomain.com**
- Ensure that the new forest option was selected.
- Click Next to continue.

**Explanation:**
During this step, a new Active Directory forest is created and the root is defined. The forest serves as the top-level container of the directory structure, while the root domain acts as the primary administrative control point for the network.

<h2>Configure Domain Controller Options</h2>

<img width="1536" height="1024" alt="LabA16" src="https://github.com/user-attachments/assets/3ac3d1dd-eba0-4e29-80af-064e9d1a3691" />
</p>
<p>
Steps:
  
- Proceed to the Domain Controller Options page.
- Review the default Forest functional level.
- Review the default **Domain functional level.
- Verify that the DNS server option was selected.
- Verify that the Global Catalog (GC) option was enabled.
- Leave domain controller (RODC) unselected.
- Type a Directory Services Restore Mode (DSRM) password.
- Confirm the DSRM password in the second field.
- Select Next to continue.

**Explanation**
This step defines important domain controller settings. It enables DNS integration, confirms the server’s role in the domain, and sets the DSRM password used for recovery and maintenance of Active Directory services.

<h2>Prerequisites Check</h2>

<img width="1536" height="1024" alt="LabA19" src="https://github.com/user-attachments/assets/e06971cc-688c-4e6d-a05b-4f7903eb35e4" />
</p>
<p>
Steps:

- Proceed through the configuration wizard after reviewing the deployment options.
- Reach the Prerequisites Check page.
- Wait while Windows validates the configuration.
- Review the results shown in the wizard.
- Varify the message stated:<br>
  **All prerequisite checks passed successfully**
- Review the warning messages listed in the results panel.
- Confirm that no blocking errors prevented the promotion process.
- Prepare to click Install.

**Explanation:**
This step checks the server’s readiness to become a Domain Controller. The wizard validates required settings, confirms prerequisites are met, and alerts you to any warnings or errors before the promotion process starts.

<h2>Domain Controller Promotion Complete</h2>

<img width="1536" height="1024" alt="LabA21" src="https://github.com/user-attachments/assets/2cfd0841-77d9-41c4-970e-0c1a57b19257" />
</p>
<p>
Step:
  
- Click Install on the Prerequisites Check page.
- Wait while Active Directory is configured.
- Review the Results page after the promotion process completes
- Confirm the message showing:<br>
  **This server was successfully configured as a domain controller**
- Observe the notification indicating that the computer is about to be signed out.
- Read the restart message explaining that the server would reboot because Active Directory Domain Services had been installed.
- Allow the restart process to continue.

**Explanation**
This step indicates that the Domain Controller promotion process finished successfully. Restarting the server finalizes the configuration and allows Active Directory Domain Services to begin operating.

<h2>Server Manager After Restart</h2>

<img width="1536" height="1024" alt="LabA24" src="https://github.com/user-attachments/assets/f79503ae-dceb-4519-b9ed-3aca659d8be1" />
</p>
<p>
Step:
  
- Wait for dc-1 to restart after Domain Controller promotion.
- Sign back into the server.
- Launch Server Manager.
- Review the dashboard after the reboot is complete.
- Verify that the left navigation pane now displayed:<br>
  **AD DS**<br>
  **DNS**
- Verifiy that the new roles appeared as active components of the server.

**Explanation:**
This step shows that the server reboot finished and that both AD DS and DNS services are active on the machine. This confirms the server is now functioning as a configured Domain Controller.

<h2>Verify Domain Presence in Active Directory Users and Computers</h2>

<img width="1536" height="1024" alt="LabA26" src="https://github.com/user-attachments/assets/0101d8c7-9809-43de-afc5-fef6fd41f268" />
</p>
<p>
Step:
  
Open Server Manager on dc-1.
Click Tools in the top-right corner.
Select Active Directory Users and Computers.
Locate the domain tree in the left panel.
Verify that mydomain.com appears under Active Directory Users and Computers.
Select mydomain.com without expanding it.
Confirm that the domain is listed and accessible in the console.

**Explanation**
This step confirms that the Active Directory domain was successfully created and is now visible within the Active Directory Users and Computers management console. Seeing the domain listed indicates that the Domain Controller is properly managing the new directory environment and that administrators can begin managing users, computers, and organizational units within the domain.

<h2>Create Organizational Unit</h2>

<img width="1536" height="1024" alt="LabA27" src="https://github.com/user-attachments/assets/a5209f7c-c6fe-409e-bc54-bc69e5dd69b7" />
</p>
<p>
Step:
  
- Open Active Directory Users and Computers.
- Select the mydomain.com domain.
- Right-click the domain name.
- Choose New.
- Select Organizational Unit.
- Click into the Name field.
- Type the name:<br>
**_EMPLOYEES**
- Leave Protect container from accidental deletion checked.
- Click OK to create the Organizational Unit.

**Explanation**
An Organizational Unit is created to organize and manage user accounts within the domain. OUs allow administrators to structure resources logically and make it easier to delegate administrative tasks and apply group policies.

<h2>Create New User Account</h2>

<img width="1536" height="1024" alt="LabA28" src="https://github.com/user-attachments/assets/66cb3f21-8771-475b-929f-9112ed62ff17" />
</p>
<p>
Step:
  
- Open Active Directory Users and Computers.
- Select the target Organizational Unit for the user account.
- Right-clicked the OU.
- Choose New.
- Select User.
- Enter the user’s first name:<br>
  **Jane**
- Enter the user’s last name:<br>
  **Doe**
- Review the automatically generated full name.
- Enter the user logon name.
- Review the pre-Windows 2000 logon name.
- Click  Next to continue user creation.

**Explanation**
A new user account is added to Active Directory so the individual can access network resources. Administrators use these accounts to control authentication, assign permissions, and place users into appropriate groups within the organization.

<h2>Verify User Account Creation</h2>

<img width="1536" height="1024" alt="LabA29" src="https://github.com/user-attachments/assets/52400f1d-fb7e-4edf-813f-099ed1f182fc" />
</p>
<p>
Step:
  
- Complete the New User wizard.
- Return to Active Directory Users and Computers.
- Select the OU where the user was created.
- Review the right pane.
- Verify that the new account appeared in the directory listing.
- Confirm that the account name displays as:<br>
  **Jane Doe**
- Confirm the object type shows User.

**Explanation**
This step verifies that the user account was successfully created in Active Directory. Seeing the account in the directory confirms that the object now exists and can be managed like any other domain user.

<h2>Add User to Domain Admins</h2>

<img width="1536" height="1024" alt="LabA30" src="https://github.com/user-attachments/assets/50ef5bdd-dc27-4372-9baa-4e72dd98e869" />
</p>
<p>
Step:
  
- Open the properties of the user account in Active Directory Users and Computers.
- Locate the Member Of tab.
- Click Add.
- Open the Select Groups window.
- Click into the object name field.
- Enter:<br>
- **Domain Admins**
- Review the location field to confirm the correct domain.
- Prepare to validate and add the group membership.

**Explanation**
This step assigns the user administrative privileges by adding the account to the Domain Admins group. Group membership is a common way to manage permissions and administrative roles in Active Directory.

<h2>Join Client-1 to the Domain</h2>

<img width="1536" height="1024" alt="LabA31" src="https://github.com/user-attachments/assets/2238c07b-c736-48ec-8c54-d9289e9bbdc2" />
</p>
<p>
Step:
  
- Log into the Client-1 virtual machine.
- Open Settings.
- Navigate to System > About.
- Select the option to change the computer’s domain or workgroup settings.
- Open the Computer Name/Domain Changes window.
- Select the Domain option under membership.
- Click into the domain field.
- Type:<br>
  **mydomain.com**
- Prepare to confirm the domain join request.


**Explanation**
By joining the workstation to the domain, it becomes part of the Active Directory environment. This integration allows administrators to manage the computer, apply group policies, and provide users with domain-based login access.

<h2>Restart Client-1 After Domain Join</h2>

<img width="1536" height="1024" alt="LabA34" src="https://github.com/user-attachments/assets/fa6a4779-fc83-4578-9a45-2b9de8071314" />
</p>
<p>
Step:
  
- Enter the domain name on Client-1.
- Authenticate with domain credentials when prompted.
- Receive confirmation that the computer successfully joined the domain.
- Accept the restart prompt.
- Allow Client-1 to begin restarting.
- Wait while the restart process is completed.

**Explanation**
A system restart is necessary to finalize joining the domain. This allows the computer to apply the new domain settings and connect fully with the Domain Controller for authentication and policy management.

<h2>Verify Client-1 in Active Directory</h2>

<img width="1536" height="1024" alt="LabA35" src="https://github.com/user-attachments/assets/6f91ffe6-edc7-4d0a-94e3-4dc29140671b" />
</p>
<p>
Step:
  
- Return to dc-1 after the client restart.
- Open Active Directory Users and Computers.
- Expand the mydomain.com domain.
- Select the Computers container.
- Review the objects listed in the right pane.
- Confirm that Client-1 appeared as a Computer object.
- Open the computer object properties to verify the name and DNS information.

**Explanation**
The workstation is now listed in Active Directory, confirming it joined the domain successfully. The Domain Controller can now manage the computer, enforce policies, and control access like any other domain member.

<h2>Summary</h2>
  
By the end of this phase, the Windows Server virtual machine successfully operates as a Domain Controller within the environment. Active Directory Domain Services is installed, the new domain is created, and the directory structure is verified using Active Directory management tools. An Organizational Unit is implemented to improve administrative organization, and the client workstation is successfully joined to the domain, confirming that domain services and authentication are functioning correctly.


.


